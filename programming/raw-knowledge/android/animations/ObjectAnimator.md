#status/4-liquid-nitrogen 
#tech-area/android 

Klasa ułatwiająca robienie animacji wszelakich!

Np. fadeout:
```kotlin
ObjectAnimator.ofFloat(it.view, View.ALPHA, 1f, 0f).apply {  
    duration = SYSTEM_SPLASH_SCREEN_FADE_OUT  
}.start()
```

Trzeba tylko zdefiniować własnośc widoku, np. View.ALPHA albo View.TRANSITION_Y.