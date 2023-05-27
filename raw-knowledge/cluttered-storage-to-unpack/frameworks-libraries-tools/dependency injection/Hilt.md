up: [[013 Android Libraries MOC]]
#android/gradle-dependency #gradle/plugin
#status/2-backlog 

```groovy
/* Dependencja pluginu: */
id 'com.google.dagger.hilt.android' version '2.44' apply false
/* Dependencja biblioteki: */
implementation "com.google.dagger:hilt-android:2.44" /* Dla Kotlina 1.7.21 */
kapt "com.google.dagger:hilt-compiler:2.44"
```

**Opiera się na klasach daggera, tworzy na ich podstawie prostszy w obsłudze interfejs.**

Aby cokolwiek z Hiltem zacząć, należy oznaczyć aplikację:
```kotlin
@HiltAndroidApp  
class TestExerciseApplication : Application() { }
```

Wówczas można używać zależności Hiltowych w każdej z klas oznaczonej:
```kotlin
@AndroidEntryPoint  
class MainActivity : AppCompatActivity() { }
```

Można oznaczyć View Model jako Hiltowy - wówczas trzeba zdefiniować primary constructor tak, żeby był w nim jakiś @Inject
```kotlin
@HiltViewModel  
class MainActivityViewModel @Inject constructor(  
    private val httpService: HttpService  
) : ViewModel() {
```

Zdefiniowanie modułu i klasy, która będzie wstrzykiwana:
```kotlin
@Module  
@InstallIn(ViewModelComponent::class)  
object HttpModule {  
  
    @ViewModelScoped  
    @Provides    
    fun provideHttpService() : HttpService {  
        return Retrofit.Builder()  
            .baseUrl(INFO_BASE_URL)  
            .build()  
            .create(HttpService::class.java)  
    }  
}
```

Scope'y mogą być różne dla wstrzykiwanej zależności, może to być SingletonComponent, ActivityComponent, etc.

Annotacja @Provides jest kluczowa, ona sprawia, że hilt jest w stanie dostarczyć (podobnie z @Binds). Wówczas @Inject z konstruktora ViewModelu reaguje na @Provides z modułu DI i jest w stanie wykonać kod generujący HttpService.

---

Hilt provides a standard way to incorporate Dagger dependency injection into an Android application.

_The goals of Hilt are:_

-   To simplify Dagger-related infrastructure for Android apps.
-   To create a standard set of components and scopes to ease setup, readability/understanding, and code sharing between apps.
-   To provide an easy way to provision different bindings to various build types (e.g. testing, debug, or release).

## Hilt Design Overview

Hilt works by code generating your Dagger setup code for you. This takes away most of the boilerplate of using Dagger and really just leaves the aspects of defining how to create objects and where to inject them. Hilt will generate the Dagger components and the code to automatically inject your Android classes (like activities and fragments) for you.

https://developer.android.com/training/dependency-injection/hilt-android