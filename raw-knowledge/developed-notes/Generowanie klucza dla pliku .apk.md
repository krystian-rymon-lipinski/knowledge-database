up: [[Podpisywanie pliku .apk]]
#status/freezer 
#tech-area/android #tech-area/gradle 

```bash
keytool -genkey -v -keystore <keyname>.keystore -alias <some_alias> -keyalg RSA -keysize 2048 -validity 10000
```

validity w dniach

Po wpisaniu tego pojawią się opcje: dodania hasła do keystore'a i aliasu i pytania o dane generującego klucz.