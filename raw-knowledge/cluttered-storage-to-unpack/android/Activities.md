#status/3-freezer 
#tech-area/android 

**Nie można wołać aktywności z parametrami, bo przy recreation i tak nie zostaną one zapamiętane!**

Jeśli aktywność jest w backstacku, to nie zostaje niszczona!

Np. jeśli A -> B, to na aktywności A nie zostanie wywołane onDestroy(). Natomiast jeśli w B kliknie się wstecz i zostanie zawołane onBackPressed(), to na aktywności B zostanie wywołane onDestroy() - bo nie ma jej już w stacku.
A tymczasem na aktywności A zostanie wywołane onStop(), a po kliku wstecz wywoła się **onRestart()** i onStart().


onDestroy() będzie wołane, jeśli ktoś explicite zawoła finish()


https://developer.android.com/reference/android/app/Activity#activity-lifecycle
https://developer.android.com/guide/components/activities/activity-lifecycle#asem