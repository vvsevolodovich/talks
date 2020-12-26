slidenumbers: true
autoscale: true
build-lists: true


## [fit] Flow, StateFlow.

![right](https://i.insider.com/5de7b15979d75746496500c2?width=1100&format=jpeg&auto=webp)

---

## Vladimir Ivanov


## Solution Architect
## @ EPAM Systems

![right](newme.jpg)

---

# Search

* EditText
* Search by query
* Search only by last value
* Has timeout for change

![right fit](search.png)

---

## [fit] RxJava


![right fit](https://i.pinimg.com/originals/0e/01/c8/0e01c867c9a1fa680c741f32d1f8878a.jpg)

---

```kotlin

	publishSubject
			.debounce(300, TimeUnit.MILLISECONDS)
			.distinctUntilChanged()
			.switchMap { searchQuery -> 
apiClientRxImpl.searchRepositories(searchQuery) }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.subscribe {
			repos.adapter = ReposAdapter(
					it.map { it.full_name },
					this@RepositoriesActivity)
			}

```

---

```kotlin, [.highlight: 1]

	publishSubject
			.debounce(300, TimeUnit.MILLISECONDS)
			.distinctUntilChanged()
			.switchMap { searchQuery -> 
apiClientRxImpl.searchRepositories(searchQuery) }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.subscribe {
			repos.adapter = ReposAdapter(
					it.map { it.full_name },
					this@RepositoriesActivity)
			}

```

---

```kotlin, [.highlight: 4-5]

	publishSubject
			.debounce(300, TimeUnit.MILLISECONDS)
			.distinctUntilChanged()
			.switchMap { searchQuery -> 
apiClientRxImpl.searchRepositories(searchQuery) }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.subscribe {
			repos.adapter = ReposAdapter(
					it.map { it.full_name },
					this@RepositoriesActivity)
			}

```

---

```kotlin, [.highlight: 9-11]

	publishSubject
			.debounce(300, TimeUnit.MILLISECONDS)
			.distinctUntilChanged()
			.switchMap { searchQuery -> 
apiClientRxImpl.searchRepositories(searchQuery) }
			.subscribeOn(Schedulers.io())
			.observeOn(AndroidSchedulers.mainThread())
			.subscribe {
			repos.adapter = ReposAdapter(
					it.map { it.full_name },
					this@RepositoriesActivity)
			}

```
---

# [fit] BroadcastChannel

![fit original right](https://i.pinimg.com/originals/76/52/c9/7652c96ef79f99f06c32c06849f341db.jpg)


---

```kotlin

val broadcast = ConflatedBroadcastChannel<String>()

```

---

```kotlin

launch {
		broadcast.consumeEach { query ->
			delay(300)
			val foundRepositories = apiClient.searchRepositories(query).await()
			repos.adapter = ReposAdapter(
				foundRepositories.map { it.full_name },
				this@RepositoriesActivity
			)
		}
}

```

---

# But...

* Distinct until changed is missing

---

# [fit] Flow

![right fit original](https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/irish-actor-pierce-brosnan-as-james-bond-in-a-publicity-news-photo-138084872-1551742467.jpg?crop=1xw:1xh;center,top&resize=480:*)


---


```kotlin

	broadcast.asFlow().collect() {
		...
	}
	
```

```kotlin
	@OptIn(ExperimentalCoroutinesApi::class)
	override fun onStop() {
		super.onStop()
		broadcast.cancel()
	}
```

---

# [fit] StateFlow

A Flow that represents a read-only state with a single updatable data value that emits updates to the value to its collectors. 

![right](https://i.insider.com/5de7b15979d75746496500c2?width=1100&format=jpeg&auto=webp)


---

# Usage

```kotlin

searchFlow = MutableStateFlow("")

launch {
	searchFlow.collect {
		val foundRepositories = apiClient.searchRepositories(it).await()
		repos.adapter = ReposAdapter(
			foundRepositories.map { it.full_name },
			this@RepositoriesActivity)
	}
}


```

---

```kotlin
searchQuery.addTextChangedListener(object: TextWatcher {

	override fun afterTextChanged(s: Editable?) {
		searchFlow.value = s.toString()
	}
}
```

---

# StateFlow vs BroadcastChannel

* Interface segregation
* Default value
* .equals based comparison

---

## Strong equality-based conflation

# [fit] ```a.equals(b)```

---

# [fit] Backpressure

---

# Take away

StateFlow is a convenient way of reactive programming in Kotlin Coroutines world

---

# Links

* https://github.com/vlivanov/github-kotlin-coroutines
* https://twitter.com/vvsevolodovich :bird:
* https://vvsevolodovich.dev/ :pencil:

![fit right](newme.jpg)


