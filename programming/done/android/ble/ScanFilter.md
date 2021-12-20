### ScanFilter
**Filtry skanowania.** Ustawiane przez Builder.
Urządzenia rozgłaszające się, które nie spełniają kryteriów, nie zostaną zwrócone w callbacku. 

Możliwe filtry:
- adres MAC urządzenia
- nazwa urządzenia
- manufacturer data - dane zdefiniowane przez producenta urządzenia
- UUID serwisu
- informacje o serwisie
- service solicitation UUID (?) (https://www.bluetooth.com/blog/advertising-works-part-2/)

Na ostatnie cztery filtry można nałożyć maskę, wówczas muszą zgadzać się tylko wybrane bajty surowych danych.

Zdefiniowanie kilku filtrów naraz powoduje, że jeśli urządzenie spełni **choć jeden z nich**, zostanie wykryte i zgłoszone w callbacku. 

---
#tech-area/android 