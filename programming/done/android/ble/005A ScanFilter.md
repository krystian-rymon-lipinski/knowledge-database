### ScanFilter
**Filtry skanowania.** Ustawiane przez Builder.
Urządzenia rozgłaszające się, które nie spełniają kryteriów, nie zostaną zwrócone w callbacku. 

Możliwe filtry:
- adres MAC urządzenia
- nazwa urządzenia
- manufacturer data - dane zdefiniowane przez producenta urządzenia 
- UUID serwisu
- informacje o serwisie - wówczas nie można UUID serwisu w filtrze, podaje się je jako osobny argument; długość tablicy filtru musi być nie większa niż długość service data
- service solicitation UUID (?) (https://www.bluetooth.com/blog/advertising-works-part-2/)
"Service solicitation allows the central receiving the advertising packets to find out which services the peripheral can access when it is acting as a GATT client. In certain cases, if the central is not exposing ant of these services at all as a GATT server it migth not even bother to connect to it, knowing that interaction would be extremely limited.

Na ostatnie cztery filtry można nałożyć maskę, wówczas muszą zgadzać się tylko wybrane bajty surowych danych. Maska musi mieć tę samą długość, co filtr.

Zdefiniowanie kilku filtrów naraz powoduje, że jeśli urządzenie spełni **choć jeden z nich**, zostanie wykryte i zgłoszone w callbacku. 

---
#tech-area/android 