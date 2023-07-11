up: [[Usługi]]
#status/2-backlog
#tech-area/android 
#android/gradle-dependency
#android/multithreading (?)

```groovy
implementation 'androidx.work:work-runtime-ktx:2.6.0'
```

**Rekomendowana biblioteka do operacji ciągłych, dziejących się w tle, których żywotność nie powinna zależeć od żywotności aplikacji, tj. nie powinny one być anulowane nawet po ubiciu procesu aplikacji.**

Można zakolejkować operacje synchroniczne lub asynchroniczne. Dla operacji synchronicznych należy rozszerzyć klasę `Worker`, dla asynchronicznych - `ListenableWorker`. Oba typy operacji dostają 10 minut, by wyprodukować wynik. Po tym czasie zostają zakończone.

**WorkManager jest inicjalizowany z momentem odpalenia aplikacji i jest singletonem, do którego można się odwołać poprzez _getInstance()_ z każdego miejsca kodu aplikacji!**

###### Worker

1) Zdefiniowanie Workera dla operacji w tle.
```kotlin
class TimerWorker(context: Context, params: WorkerParameters) : Worker(context, params) {  
    override fun doWork(): Result {  
        /* Do something here */  
        return Result.success()  /* Or Return.failure(). Or other states. */
    }  
}
```
Worker może też zwracać proste dane i tablice w forme klucz-wartość.

```kotlin
val data = Data.Builder()  
    .putInt(RANDOM_NUMBER_KEY, number)  
    .build()
return Result.failure(data)
```


2) Zdefiniowanie obiektu typu `WorkRequest`
```kotlin
val request = OneTimeWorkRequest.Builder(TimerWorker::class.java)
	//.setInputData
	//.setConstraints
	.setInitialDelay(2L, TimeUnit.SECONDS)
	.build()
```

3) Utworzenie instancji klasy `WorkManager` i zakolejkowanie pracy:
```kotlin
workManager = WorkManager.getInstance(this).also {  
    it.enqueue(request)  
	/* Można również obserwować aktualny stan wykonywanej pracy. */
    val status = it.getWorkInfoByIdLiveData(request.id)  
    status.observe(this) {  
		// react to state or progress
    }}
```




---
https://developer.android.com/reference/androidx/work/WorkManager.html#summary