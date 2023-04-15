#status/freezer 
#tech-area/android 

Żeby wykryć zmiany orientacji urządzenia, trzeba w manifeście dodać:

```xml
android:configChanges="orientation|keyboardHidden|screenSize"
```

Wówczas w kodzie można dostać callback:
```kotlin
override fun onConfigurationChanged(newConfig: Configuration) {  
    super.onConfigurationChanged(newConfig)  
}
```

Żeby dostać aktualną konfigurację wystarczy:
```kotlin
with(resources.configuration) { // referencja do obiektu Configuration
	orientation = ...
	screenWidthDp = ...
	/* I dużo innych parametrów aktualnej konfiguracji. */
}
```