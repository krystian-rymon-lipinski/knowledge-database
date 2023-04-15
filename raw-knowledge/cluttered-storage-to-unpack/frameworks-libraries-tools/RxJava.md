#status/4-liquid-nitrogen 

Biblioteka (framework?). Opiera się na wzorcu Obserwatora.

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