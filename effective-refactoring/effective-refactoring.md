slidenumbers: true
autoscale: true
build-lists: true

# Effective refactorings

---

## What we have often

```java

public class MainActivity extends Activity implements TaskListener {

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);

		new NetworkTask(this).execute();
	}

	…
}

```

---

## What we have often

```java

public class MainActivity extends Activity implements TaskListener {

	…

	@Override
	public void onResult(String result) {
		if (!isFinishing()) {
			// update UI
		}
	}

	
}

```


---

## What we have often

```java

	private static class NetworkTask extends AsyncTask<Void, Integer, String> {

		private WeakReference<TaskListener> listener_;

		private NetworkTask(TaskListener listener) {
			listener_ = new WeakReference<>(listener);
		}

		…
	}

```



---

## What we have often

```java


		@Override
		protected String doInBackground(Void[] params) {
			try {
				URL url = new URL("http://www.android.com/");
				HttpURLConnection urlConnection = (HttpURLConnection)url.openConnection();
				try {
					InputStream in = new BufferedInputStream(urlConnection.getInputStream());
					return readStream(in);
				}
				finally {
					urlConnection.disconnect();
				}			
			} catch ( IOException e ) {
				Log.e("TAG", "Failed to call network");
			}

			return null;
		}


```
---

## What we have often

```java

	private static class NetworkTask extends AsyncTask<Void, Integer, String> {

		…
		@Override
		protected void onPostExecute(String result) {
			TaskListener taskListener = listener_.get();
			if ( taskListener != null) {
				taskListener.onResult(result);
			}
		}
	}

```
---

## So…

* Untestable
* Hardly maintainable
* Code duplication
* Unknown data model


---

![center fit](spaghetti.jpg)

---

## How to avoid?


---


## Iterative refactoring!

---

## Make testable

```java
private static class NetworkTask extends AsyncTask<Void, Integer, String> {

		@Override
		protected String doInBackground(Void[] params) {
			return getEntity();
		}

}
```

---

## Make testable

```java

public class MainActivity extends Activity {

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);

		getEntity()
				.subscribeOn(Schedulers.io())
				.observeOn(AndroidSchedulers.mainThread())
				.subscribe(s -> {
					// show on UI
				});
	}

	public Observable<String> getEntity() {
		// TODO : network call
	}

}
```


---


## Make testable

```java, [.highlight: 1,8,11,12,13]

public class MainActivity extends Activity {

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);

		viewModel.getEntity()
				.subscribeOn(Schedulers.io())
				.observeOn(AndroidSchedulers.mainThread())
				.subscribe(s -> {
					// show on UI
				});
	}

}
```

---


## Network abstraction

```java

public interface NetworkService {

	
	Observable<String> getEntity();

}
```


---


## Network implementation

```java

public class RetrofitNetworkService implements NetworkService {

	
	Observable<String> getEntity() {
		…
	}

}
```

---

## Use in ViewModel

```java

public class MyViewModel {

	@Inject NetworkService networkService;
	
	Observable<String> getEntity() {
		return networkService.getEntity();
	}

}

```


---

## Use in ViewModel

```java

public class MyViewModel {

	@Inject ConnectionService connection;
	@Inject NetworkService networkService;
	@Inject Storage storage;
	
	Observable<String> getEntity() {
		if (connection.isConnected()) {
			return networkService.getEntity();
		} else {
			return storage.getEntity();
		}
	}

}

```

——-

# Create unit test

```java
 	@Test
	public void shouldLoadEntity() {
		ViewModel viewModel = new ViewModel();
		
		viewModel.getEntity()
			.subscribe({entity, throwable} -> {
				checkEntity(entity);
			});
		
	}
```

---

## What it gives?

* Tests for network
* Tests for viewModel
* Data model is known now
* No spaghetti


---

![center](lasagna.jpg)

---

## Nobody is going to give me 3 months for refactoring!

---

## Deprecate

---

## Deprecation

```java
/**
 * Old api to download an entity.
 *
 * @deprecated use {@link NetworkService#getEntity()} instead.  
 */
@Deprecated
private static class NetworkTask extends AsyncTask<…> {


}

```

---

## Code separation

* Separate your app by layers
* Move the layer code to separate binary
* Test coverage -> 100%
* Save your approach

---

## About me

* Vladimir Ivanov - Lead Software Engineer at EPAM
* > 15 published application to Google Play
* Wide interest in Mobile Technologies


---

## QA
