up: [[Podpisywanie pliku .apk]]
#status/freezer 
#tech-area/android-gradle-plugin 

```bash
keytool -genkey -v -keystore <keyname>.keystore -alias <some_alias> -keyalg RSA -keysize 2048 -validity 10000
```

validity w dniach

Po wpisaniu tego pojawią się opcje: dodania hasła do keystore'a i aliasu i pytania o dane generującego klucz.

Można też wykorzystać UI Android Studio poprzez: Build -> Generate Signed Bundle / APK -> Create new - do wypełnienia będą te same pola: o hasło, alias, dane otrzymującego certyfikat, etc.