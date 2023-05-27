
#status/3-freezer 
#tech-area/android 
#android/app-navigation 

Czasem zamiast tylko wysłać użytkownika gdzieś, trzeba go wysłać, żeby wrócił z informacją. Na przykład o tym, jaki plik wybrał i na tej podstawie go wczytać.

2 opcje:

1. startActivityForResult() + onActivityResult() - starsza wersja, dość prosta; onActivityResult wraca z Intentem i ekstrasami
	Działa też dla fragmentów - dokładnie tak samo. Należy wywołać metodę z fragmentu i nadpisać onActivityResult().

2. rejestracja callbacku

```kotlin
registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result ->  
    if (result.resultCode == SOME_CODE) {  
        result.data?.let { intent ->  /* dane, jeśli są takowe */
            val connectionState = intent.getIntExtra(  
                    DeviceServicesActivity.CONNECTION_STATE,  
                    BluetoothGatt.STATE_DISCONNECTED)  
            device?.let { viewModel.refreshConnectedDeviceInfo(device, connectionState) }  
        }    
	}  
}
```
Te **ActivityResultContracts** mogą być różne - można użyć na przykład specjalnych do permissions, etc.
https://medium.com/captech-corner/android-activity-results-contracts-54b2016a84db

A później tylko trzeba na tym callbacku zawołać:
```kotlin
activityResultCallback.launch(Intent()) // można dodać extrasy do intentu
```


_setResult_ żeby wrzucić ewentualne ekstrasy trzeba wywołać przed tym, jak zostanie wywołane _finish_ (jawnie bądź za kulisami). Można to zrobić w taki sposób:

```kotlin
	override fun finish() {  
    setActivityResult()  
    super.finish()  
}
```

-----
