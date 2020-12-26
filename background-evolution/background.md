slidenumbers: true
autoscale: true
build-lists: true

![center](splash.jpg)

---

# Evolution of tools of background work in Android

---

# Disclaimer

Everything told here is a product of personal professional experience and not anything more.

---

# About me

* Vladimir Ivanov - Lead Software Engineer in EPAM
* Android apps: > 15 published, > 7 years
* Wide expertise in Mobile

---

# Agenda

* AsyncTasks
* Loaders
* Executors&Event bus
* RxJava
* Coroutines

---

# Out-of-scope

* Services
* Sync Adapters

---



# What it is your first Android OS you wrote code for?

---

# Why do we need background?

* 60 FPS
* UI updates only on the main thread

---

# Android 1.6: Async tasks

---

```java

public class LoadWeatherForecastTask 
	extends AsyncTask<String, Integer, Forecast> {

   public Forecast doInBackground(String... params) {
       HttpClient client = new HttpClient();
       HttpGet request = new HttpRequest(params[0]);
       HttpResponse response = client.execute(request);
       return parse(response);
   }
}

```

---

# Which thread the doInBackground() is called on?

---

# Which thread the doInBackground() is called on?

# Fixed-sized threadpool executor of size 1

---

```java

public static final Executor SERIAL_EXECUTOR 
						= new SerialExecutor();


```


---

```java

public static final Executor SERIAL_EXECUTOR 
						= new SerialExecutor();
...
private static volatile Executor sDefaultExecutor 
						= SERIAL_EXECUTOR;

```

---

# The result should be posted on the UI Thread

---

```java


public class LoadWeatherForecastTask 
	extends AsyncTask<String, Integer, Forecast> {

	public void onPostExecute(Forecast forecast) {

       		mTemperatureView.setText(forecast.getTemp());
	}

}
```

---

# Just Handler

---

# Minuses

* Boilerplate
* Lifecycle not-aware
* No result reusage across configuration changes
* Easy way to introduce memory leaks

---

# Android 3.0: Loaders
---

```kotlin
inner class WeatherForecastLoaderCallbacks : 
	LoaderManager.LoaderCallbacks<WeatherForecast> {
```

---

```kotlin
inner class WeatherForecastLoaderCallbacks : 
	LoaderManager.LoaderCallbacks<WeatherForecast> {

   override fun onCreateLoader(id: Int, args: Bundle?): 
								Loader<WeatherForecast> {
      
		return WeatherForecastLoader(applicationContext)
   }
}

```
---

```kotlin
inner class WeatherForecastLoaderCallbacks : 
	LoaderManager.LoaderCallbacks<WeatherForecast> {

   override fun onCreateLoader(id: Int, args: Bundle?): 
								Loader<WeatherForecast> {
      
		return WeatherForecastLoader(applicationContext)
   }

   override fun onLoadFinished(loader: Loader<WeatherForecast>?, 
								data: WeatherForecast) {
      
		temperatureTextView.text = data.temp.toString();
   }
}

```

---

```kotlin

class WeatherForecastLoader(context: Context) 
			: AsyncTaskLoader<WeatherForecast>(context) {

   override fun loadInBackground(): WeatherForecast {
      try {
         Thread.sleep(5000)
      } catch (e: InterruptedException) {
         return WeatherForecast("", 0F, "")
      }

      return WeatherForecast("Saint-Petersburg", 20F, "Sunny")
   }
}

```

---

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    ...
    val weatherForecastLoader = WeatherForecastLoaderCallbacks()

    loaderManager
      .initLoader(forecastLoaderId, 
			Bundle(), 
			weatherForecastLoader)
}
```
---

# How does the loader gets reused?

---

![](https://media.giphy.com/media/fUxTvSOnBg9e8/giphy.gif)

---

# How does the loader gets reused?

* LoaderManager saves all loaders internally
* Activity saves all LoaderManagers inside NonConfigurationInstances
* On activity recreation NonConfigurationInstances got passed to a new activity


---

# Minuses

* Still a lot of boilerplate
* Complex interfaces and abstract classes
* Loaders are Android API - you can’t create libs in pure Java


---

# Thread pool executors FTW!

---

```kotlin
public class Background {

	private val mService = ScheduledThreadPoolExecutor(5)

	fun execute(runnable: Runnable): Future<*> {
		return mService.submit(runnable)
	}

	fun <T> submit(runnable: Callable<T>): Future<T> {
		return mService.submit(runnable)
	}
}
```

---


```kotlin

public class Background {

	…
	private lateinit var mUiHandler: Handler

	public fun postOnUiThread(runnable: Runnable) {
		mUiHandler.post(runnable)
	}
}


```

---

# But how will out UI know it should be changed?

---

# Event bus!


---

![fit](https://cdn-images-1.medium.com/max/800/1*eM4KtxAtUN6GpIK9Rk333g.png)


---

# Event bus implementations

* Google guava
* Otto
* Greenbot eventbus


---

```kotlin

public class Background {

	private lateinit val mEventBus: Bus

	fun postEvent(event: Any) {
		mEventBus.post(event)
	}
}

```

---

```kotlin
mBackground.execute(Runnable {
	try {

		initDatabaseInternal()
		mBackground.post(DatabaseLoadedEvent())

	} catch (e: Exception) {
		Log.e("Failed to init db", e)
	}


```

---

```kotlin

public class SplashActivity : Activity() {

	@Subscribe
	fun on(event: DatabaseLoadedEvent) {
		progressBar.setVisibility(View.GONE)
		showMainActivity()
	}

	override fun onStart() {
		super.onStart()
		eventBus.register(this)
	}

	override fun onStop() {
		eventBus.unregister(this)
		super.onStop()
	}

}

```
---

# What is the problem here?

---

# UI is modified from the background thread!

---

```kotlin
public class Background {

	fun postEventOnUiThread(event: Any) {

		mUiHandler.post(Runnable { 
			mEventBus.post(event) 
		})

	}
}
```

---

# Minuses

* The posting code knows which thread is needed on the listeners code
* The actual projects begin to be unmaintanable with EventBus

---

# Next step: RxJava!

---

```kotlin

interface ApiClientRx {

	fun login(auth: Authorization) 
		: Single<GithubUser>
	fun getRepositories
		(reposUrl: String, auth: Authorization) 
		: Single<List<GithubRepository>>

}

```

---

```kotlin

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```

---

```kotlin, [.highlight: 3-6]

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```
---

```kotlin, [.highlight: 7]

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```
---

```kotlin, [.highlight: 8,9]

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```
---

```kotlin, [.highlight: 12-14]

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```

---

# Threading?

---

```kotlin, [.highlight: 8-9]

private fun attemptLoginRx() {
	showProgress(true)
	apiClient.login(auth)
			.flatMap { 
					user -> apiClient.getRepositories(user.repos_url, auth) 
			}
			.map { list -> list.map { it.full_name } }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.doFinally { showProgress(false) }
			.subscribe(
					{ 
						list -> showRepositories(this@LoginActivity, list)    
					},
					{ 
						error -> Log.e("TAG", "Failed to show repos", error) 
					}
			)
}

```

---

# Pluses

* Standard de-facto, 65% of new projects will use RxJava
* Powerful API, lots of operators
* Opensource and community driven library
* Adapters for popular libraries like Retrofit
* Relatively easy to provide unit-tests

---

# Minuses

* Touch learning curve
* Operators to learn
* Callback style
* Memory overhead
* Unrelated stacktraces 

---

# What’s next? 

---

# What’s next? 
# Kotlin coroutines!

---


```kotlin

	private fun attemptLogin() {
		launch(UI) {
			val auth = BasicAuthorization(login, pass)
			try {
				showProgress(true)
				val userInfo = login(auth).await()
				val repoUrl = userInfo.repos_url
				val list = getRepositories(repoUrl, auth).await()
				showRepositories(
						this@LoginActivity, 
						list.map { it -> it.full_name }
				)
			} catch (e: RuntimeException) {
				Toast.makeText(this@LoginActivity, e.message, LENGTH_LONG).show()
			} finally {
				showProgress(false)
			}
		}
	}


```

---

```kotlin, [.highlight: 6, 12, 10, 14]

	private fun attemptLogin() {
		…
		launch(UI) {
			val auth = BasicAuthorization(login, pass)
			try {
				showProgress(true)
				val userInfo = login(auth).await()
				val repoUrl = userInfo.repos_url
				val list = getRepositories(repoUrl, auth).await()
				showRepositories(this@LoginActivity, list.map { it -> it.full_name })
			} catch (e: RuntimeException) {
				Toast.makeText(this@LoginActivity, e.message, LENGTH_LONG).show()
			} finally {
				showProgress(false)
			}
		}
	}


```

---

# Suspension


---

![fit](https://d2p6rcax2lcn4u.cloudfront.net/wp-content/uploads/2017/04/passive-car-suspension.jpg)

---

# Pluses

* Non-blocking approach
* Async code, sync styled
* Language tools instead of operators
* Learning curve is almost straight-line
* Unit-tests are easy

---

# Minuses

* Fresh thing, status: experimental
* Library adapters are not ready(retrofit?)
* Not a replacement for Rx


---

# Summary

* Android went long path
* The modern tools are RxJava and Coroutines
* But legacy is still there, hence the talk

---

# Contacts

* https://github.com/Kotlin/kotlinx.coroutines :computer:
* https://twitter.com/vvsevolodovich :bird:
* https://medium.com/@dzigorium :pencil:

