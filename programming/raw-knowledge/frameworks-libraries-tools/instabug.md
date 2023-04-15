#status/4-liquid-nitrogen 

narzędzie do prostszego śledzenia i zgłaszania błędów  - wystarczy potrząsnąć telefonem, by zasygnalizować, że coś poszło nie tak

ogólnie jest to płatne - za darmo dla do dwóch osób

i wystarczy tylko dodać bibliotekę

```kotlin
/* Gradle */
implementation 'com.instabug.library:instabug:10.0.1'
...
/* Application() */
new Instabug.Builder(this, "YOUR_APP_TOKEN_HERE")
.setInvocationEvents(
	InstabugInvocationEvent.SHAKE,
	InstabugInvocationEvent.SCREENSHOT
).build()
```

Token dostaje się po rejestracji i kupieniu (duuh)

https://www.instabug.com/platforms/android