#android/ui 
#status/5-absolute-zero

**Jeśli zada się programistycznie na seekbar.progress taką samą wartość, jaką ma aktualnie, nie zostanie wywołany callback _onProgressChanged_**.

Minimum seekbara to zawsze 0!
Więc na jego samego nie można zadać offsetu, trzeba przeliczać wartości.


**Ogólnie to Slider z Material Design jest dużo lepszy!**

