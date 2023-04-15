up: [[013 Android Libraries MOC]]
#status/freezer 

Wstrzykiwanie zależności. 
Zamiast inicjalizować samemu wszystkie obiekty, jest to przez zewnętrzną klasę.
Jest jeszcze [[Hilt]], który robi te same rzeczy, ale upraszcza i nie wymaga tyle pisania.
https://developer.android.com/codelabs/android-dagger#0
---

Dagger używa annotacji JSR 330 (cokolwiek to znaczy). I używa następujących:
@Component, @Module, @Provides, @Inject, @Singleton

@Component - zmusza Dagger do utworzenia grafu zależności 

@Component - użyte do obiektów, które chcemy wrzucić jako zależność
```java
@Component
public interface VehiclesComponent {
	Car buildCar();
}
```

**Typy zwracane z funkcji, które są obecne w komponencie, są typami, które można injectować!**

@Module - w klasie oznaczonej tą annotacją trzeba poprzez @Provides zdefiniować te dependencje, na których polega obiekt, który chcemy wstrzyknąć

```java
@Module 
public class VehiclesModule { 
	@Provides 
	public Engine provideEngine() { 
		return new Engine(); 
	} 
	
	@Provides 
	@Singleton 
	public Brand provideBrand() { 
		return new Brand("Baeldung"); 
	} 
}
```

@Component musi wiedzieć, z jakiego modułu korzysta:
```java
@Component(modules = VehiclesModule.class)
```