up: [[010 Android MOC]]
#status/3-freezer 
#tech-area/android 

**Do niektórych funkcji wymagana jest zgoda użytkownika.** 

Rozróżniane są dwa typy permisji:
- install-time permissions - wszystkie zadeklarowane w manifeście; wszystkie takie permisje są przyznane w momencie instalacji
- runtime permissions - trzeba o nie zapytać usera, np. o zgodę na lokalizację albo o wykorzystanie aparatu


###### Install-time:
```xml
<uses-permission android:name="android.permission.YOUR_PERMISSION" 
				  android:maxSdkVersion="30" <!-- dla legacy kodu -->
/>
```


###### Runtime: 
```kotlin
if (!checkSelfPermission(Manifest.permission.YOUR_PERMISSION) == 
        PackageManager.PERMISSION_GRANTED) {
	requestPermissions(arrayOf(Manifest.permission.YOUR_PERMISSION), requestCode)        
}
```

Wówczas w odpowiedzi system zwraca callback:

```kotlin
override fun onRequestPermissionsResult(  
    requestCode: Int,  
    permissions: Array<out String>,  
    grantResults: IntArray  
) {  
    super.onRequestPermissionsResult(requestCode, permissions, grantResults)  
}
```

---
Można wykorzystać *shouldShowRequestPermissionRationale*, żeby system zadecydował, czy trzeba wyświetlać ewentualny dialog wyjaśniający, po co są konkretne permisje (co jest generalnie dobrą praktyką). Np. zwraca to false, gdy wszystkie permisje są przyznane - albo gdy wszystkie są odrzucone z "Don't ask again".

**Gdy system już nie pyta o permisje (bo są granted albo user nie życzy sobie o nie pytać ponownie), to i tak wysłanie _requestPermissions_ spowoduje zwrotkę _onRequestPermissionsResults_, więc flow pozostanie taki sam**.



**shouldShowRequestPermissionRationale()**

> This method returns true if the app has requested this permission previously and the user denied the request.
> 
> Note: If the user turned down the permission request in the past and chose the Don't ask again option in the permission request system dialog, this method returns false.


https://medium.com/kinandcartacreated/finally-a-clean-way-to-deal-with-permissions-in-android-539786a7846
https://developer.android.com/training/permissions/declaring
https://developer.android.com/training/permissions/requesting