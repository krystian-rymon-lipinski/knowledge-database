### Manifest Permissions
Do niektórych funkcji wymagana jest zgoda użytkownika. 

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

https://medium.com/kinandcartacreated/finally-a-clean-way-to-deal-with-permissions-in-android-539786a7846
https://developer.android.com/training/permissions/declaring
https://developer.android.com/training/permissions/requesting