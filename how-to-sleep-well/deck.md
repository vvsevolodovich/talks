footer: *<EPAM>*
slidenumbers: true
slidecount: true
autoscale: true
build-lists: true


## How to have Kotlin Coroutines in Production and sleep well 

---

## Disclaimer

Everything presented here is a product of production experience and research findings and provided AS without any guarantees.

---

# About me

* Vladimir Ivanov - Lead Software Engineer
* Primary Skill: Android
* Doing some Solution Architecture from time to time.

---

* Android developers? 
* Did you use coroutines?
* Do you have them in prod?

---

![inline](http://i.imgur.com/n8Mc4X6.gif)

---
 
* What are you afraid of?  


---

# What are you afraid of?

* No reach tools(like for Rx)
* Crashes due to lifecycle 
* Complex tasks

---

# Earlier in the series

* Moving from RxJava to Kotlin Coroutines

---

# Why coroutines? 

* Simpler
* Same performance or better
* Tests are easy

---

```kotlin

interface ApiClient {

	suspend fun login(auth: Authorization) : <GithubUser>
	suspend fun getRepositories(reposUrl: String, auth: Authorization) 
		: List<GithubRepository>

}

```

---

```kotlin

private fun attemptLogin() {
	launch(UI) {
		val auth = BasicAuthorization(login, pass)
		try {
			showProgress(true)
			val userInfo = async { apiClient.login(auth) }.await()
			val repoUrl = userInfo.reposUrl
			val list = async { apiClient.getRepositories(repoUrl, auth) }.await()
			showRepositories(
				this, 
				list.map { it -> it.fullName }
			)
		} catch (e: RuntimeException) {
			showToast("Oops!")
		} finally {
			showProgress(false)
		}
	}
}


```


---

```kotlin, [.highlight: 6,8]

private fun attemptLogin() {
	launch(UI) {
		val auth = BasicAuthorization(login, pass)
		try {
			showProgress(true)
			val userInfo = async { apiClient.login(auth) }.await()
			val repoUrl = userInfo.reposUrl
			val list = async { apiClient.getRepositories(repoUrl, auth) }.await()
			showRepositories(
				this, 
				list.map { it -> it.fullName }
			)
		} catch (e: RuntimeException) {
			showToast("Oops!")
		} finally {
			showProgress(false)
		}
	}
}


```

---

# Coroutine builders

* async
* launch
* runBlocking
* withContext

---

# Await 

* Built-in or extension function awaiting on Job to return Value

---

```kotlin, [.highlight: 6-8, 10-12]

private fun attemptLogin() {
	launch(UI) {
		val auth = BasicAuthorization(login, pass)
		try {
			showProgress(true)
			val userInfo: GithubUser = withContext(background) { 
				apiClient.login(auth) 
			}.await()
			val repoUrl = userInfo.reposUrl
			val list: List<GithubRepositories> = withContext(background) { 
				apiClient.getRepositories(repoUrl, auth) 
			}.await()
			showRepositories(
				this, 
				list.map { it -> it.fullName }
			)
		} catch (e: RuntimeException) {
			showToast("Oops!")
		} finally {
			showProgress(false)
		}
	}
}


```

---

# withContext vs launch/async

* launch/async may create new Coroutine context
* withContext reuses an existing one

---

TODO: Add rule when to use which option

---

## Coroutine can leak as well as disposable, AsyncTask


---

* Thread.stop()

---

* ~~Thread.stop()~~

---

# Cancellation


---

* What we do with Rx? 

* CompositeDisposable!

---

# RxJava way

```kotlin

private val compositeDisposable = CompositeDisposable()

```

---

# RxJava way

```kotlin, [.highlight: 4,5,8]

private val compositeDisposable = CompositeDisposable()

fun requestSmth() {
  compositeDisposable.add(
	apiClientRx.requestSomething()
	.subscribeOn(Schedulers.io())
	.observeOn(AndroidSchedulers.mainThread())
	.subscribe(result -> {})
} 

```

---

# RxJava way

```kotlin, [.highlight: 10-13]

private val compositeDisposable = CompositeDisposable()

fun requestSmth() {
  compositeDisposable.add(
	apiClientRx.requestSomething()
	.subscribeOn(Schedulers.io())
	.observeOn(AndroidSchedulers.mainThread())
	.subscribe(result -> {})
} 

override fun onDestroy() {
  compositeDisposable.dispose()
} 

```

---

# Coroutines way

```kotlin

private val job: Job? = null


```

---


# Coroutines way

```kotlin

private val job: Job? = null

fun requestSmth() {
  job = launch(UI) { 
	val user = apiClient.requestSomething()
	...
  } 
} 

```

---

# Coroutines way

```kotlin

private val job: Job? = null

fun requestSmth() {
  job = launch(UI) { 
	val user = apiClient.requestSomething()
	...
  } 
} 

override fun onDestroy() {
  job?.cancel()
} 

```

---

# Issues?

* Cloning fields for every possible job
* Sustaining a registry for jobs
* Duplicating code 


---

# Alternatives

* CompositeJob
* Lifecycle


---

# CompositeJob

---

# CompositeJob

```kotlin

private val job: CompositeJob = CompositeJob()

fun requestSmth() {
  job.add(launch(UI) { 
	val user = apiClient.requestSomething()
	...
  	})
} 

override fun onDestroy() {
  job.cancel()
} 

```

---


# CompositeJob

```kotlin


class CompositeJob {

	private val map = hashMapOf<String, Job>()

	fun add(job: Job, key: String = job.hashCode().toString()) = map.put(key, job)?.cancel()

	fun cancel(key: String) = map[key]?.cancel()

	fun cancel() = map.forEach { _, u -> u.cancel() }
}

```


---


# Lifecycle-aware job

---

Lifecycle

---

![inline](https://developer.android.com/images/topic/libraries/architecture/lifecycle-states.png)

---

```java
public class MyObserver implements LifecycleObserver {
    @OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
    public void connectListener() {
        ...
    }

    @OnLifecycleEvent(Lifecycle.Event.ON_PAUSE)
    public void disconnectListener() {
        ...
    }
}
```

---

```kotlin
class AndroidJob(lifecycle: Lifecycle) : Job by Job(), LifecycleObserver {

    init {
        lifecycle.addObserver(this)
    }

    @OnLifecycleEvent(Lifecycle.Event.ON_DESTROY)
    fun destroy() {
        Log.d("AndroidJob", "Cancelling a coroutine")
        cancel()
    }
}
```

---

```kotlin
	private var parentJob = AndroidJob(lifecycle)

fun do() {
	job = launch(UI, parent = parentJob) {
		// code
	}
}

```
---

# Complex use-cases

* Repeat
* ???
* Cache

---

# Repeat - RxJava


```kotlin

repeatWhen()

```
---

# Repeat - Coroutines

```kotlin

suspend fun <T> retryDeferredWithDelay(
		deferred: () -> Deferred<T>, 
		tries: Int = 3, 
		timeDelay: Long = 1000L
	): T {

	for (i in 1..tries) {
		try {
			return deferred().await()
		} catch (e: Exception) {
			if (i < tries) delay(timeDelay) else throw e
		}
	}
	throw UnsupportedOperationException()
}

```

---

# Cache

* Network Source
* In-memory cache
* Persistent cache(with expiration)

---

# Cache

```kotlin

launch(UI) {
	var data = withContext(dispatcher) { persistence.getData() }
	if (data == null) {
		data = withContext(dispatcher) { memory.getData() }
		if (data == null) {
			data = withContext(dispatcher) { network.getData() }
			memory.cache(url, data)
			persistence.cache(url, data)
		}
	}
}

```

---

Rx has RxCache

---

Coroutine Cache in development! 

---


# Summary

* 

---


# Useful links

* 


---

![fit](epam.png)
