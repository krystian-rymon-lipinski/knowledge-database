#status/4-liquid-nitrogen

Biblioteka (framework?). Opiera się na paradygmacie [[033 Programowanie reaktywne|programowania reaktywnego]].

Trzeba utworzyć obiekt typu np. PublishSubject lub BehavioSubject po czym wywołać na nim:

```java
subject
 		.observeOn(AndroidSchedulers.mainThread())  
        .subscribeOn(Schedulers.io())  
        .subscribe(discover);
```
Parametrem _subscribe_ jest callback o zwracanym typie Subscriber\<T>, gdzie T jest typem, który chcemy dostać w zdarzeniu onNext().

```java
private Subscriber<List<ThunderBoardDevice>> discover =  
    new Subscriber<List<ThunderBoardDevice>>() {  
        @Override  
 		public void onCompleted() {  
			//do something; probably unsubscribe, since this is onCompleted()
		}  
          
        @Override  
 		public void onError(Throwable e) {  
  			//do something; probably unsubscribe, since something went wrong
 
        }  
  
        @Override  
 		public void onNext(List<ThunderBoardDevice> devices) {  
			//do something; maybe get the data from callback and push it further	
		}  
    };  
}
```

---

Programowanie reaktywne - oparte na wzorcu obserwatora [https://www.tutorialspoint.com/rxjava/rxjava_single_observable.htm](https://www.tutorialspoint.com/rxjava/rxjava_single_observable.htm)

Czy to jest Functional Reactive Programming?

Observable i Observer - dwa kluczowe obiekty programowania reakcyjnego Observable - strumień danych [tak jakby], ich źródło Observer - subskrybuje strumień danych - odbiera te dane

Observable wysyła - Observer wywołuje onNext() Observable kończy wysyłanie - Observer wywołuje onCompleted() Observable rzuca bład - Observer wywołuje onError()