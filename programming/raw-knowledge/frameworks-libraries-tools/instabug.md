narzędzie do prostszego śledzenia i zgłaszania błędów  - wystarczy potrząsnąć telefonem, by zasygnalizować, że coś poszło nie tak

ogólnie jest to płatne - za darmo dla do dwóch osób

i wystarczy tylko dodać bibliotekę


https://www.instabug.com/platforms/android

```kotlin
implementation 'com.instabug.library:instabug:10.0.1'
```

‍
```kotlin
new Instabug.Builder(this, "YOUR_APP_TOKEN_HERE")
.setInvocationEvents(
	InstabugInvocationEvent.SHAKE,
	InstabugInvocationEvent.SCREENSHOT
).build()
```

Token dostaje się po rejestracji i kupieniu (duuh)