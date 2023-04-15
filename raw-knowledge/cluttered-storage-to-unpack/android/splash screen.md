#status/backlog  
#tech-area/android
#android/gradle-dependency 

```groovy
implementation 'androidx.core:core-splashscreen:1.0.0'
```

ekran, który użytkownik widzi jako pierwszy, najczęściej z jakimś brandingiem (podczas [[app startup time|cold startu i warm startu]]); podczas jego wyświetlania można zasetupować potrzebne aplikacji rzeczy, np. dane z bazy, serwisy, etc.

Potrzebuje kotlina przynajmniej w wersji 1.6.21:
https://androidx.tech/artifacts/core/core-splashscreen/1.0.0

Od Androida 12 system sam ogarnia splash screeeny, ale dla Androidów wcześniejszych powstała wstecznie kompatybilna biblioteka, która emuluje zachowanie systemu na późniejszych wersjach: https://developer.android.com/develop/ui/views/launch/splash-screen/migrate#splashscreen_compat_library
Aczkolwiek domyślnie Android 12 pokazuje splash screena tylko jako launcher ikonkę, więc można ją nadpisać czymś lepszym.


```xml
<style name="SplashTheme" parent="Theme.SplashScreen">  
    <item name="windowSplashScreenBackground">@drawable/splash_screen_gradient</item>  
    <item name="postSplashScreenTheme">@style/MainAppTheme</item>  
    <item name="windowSplashScreenAnimatedIcon">@drawable/efr_splash_screen</item>  
</style>
```

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {  
    installSplashScreen()  /* To ta linijka spowoduje pokazanie się splash creenu i jego zniknięcie. */
  
    super.onCreate(savedInstanceState)  
    setContentView(R.layout.activity_main)
    ...
}
```

Trzeba zmienić theme aplikacji (lub tylko startowej aktywności) w manifeście. Później zostanie on zmieniony na wartość ustaloną w postSplashScreenTheme.

Na splash screen można zadać animację wyjścia (np. stój w miejscu przez sekundę) albo warunek, dla którego spełnienia dopiero znika.
```kotlin
installSplashScreen().apply {   
	setKeepOnScreenCondition()  
    setOnExitAnimationListener()  
}
```

https://itnext.io/a-comprehensive-guide-to-android-12s-splash-screen-api-644609c811fa