- parowanie - wygenerowanie *klucza tymczasowego* do ustanowienia zaszyfrowanego połączenia - po jego zakończeniu klucz traci ważność; najpierw oba urządzenia wymieniają informacje potrzebne do wytworzenia klucza (jedną z takich informacji jest [[0064 Sposoby generowania kluczy szyfrujących|sposób jego wygenerowania]]), a później każde z nich generuje go niezależnie; **istnieje ryzyko przechwycenia tych informacji**
- wiązanie (ang. bonding) - procedura parowania, po której następuje wygenerowanie *kluczy trwałych* i *kluczy identyfikujących* po obu stronach połączenia, a następnie ich wymiana oraz zapisanie w pamięci obu urządzeń; **istnieje ryzyko przechwycenia tych informacji, jeśli ktoś przechwycił klucz tymczasowy podczas parowania**
- przywrócenie szyfrowania - po wykonaniu wiązania zachowane na obu urządzeniach klucze trwałe służą do szybkiego odtworzenia szyfrowania przy nawiązywaniu kolejnych połączeń; **takie informacje o szyfrowaniu są nie do przechwycenia**, opierają się bowiem na już wymienionych kluczach

Dzięki **wiązaniu** dwa urządzenia mogą rozpoznać się nawzajem podczas nawiązywania kolejnych połączeń, wciąż używając adresów typu *private resolvable*. W ten sposób urządzenie jest ukryte przed obcymi (potencjalnie śledzącymi), jednocześnie rozpoznając zaufane.

Dzięki **wiązaniu** możliwe jest łączenie się z urządzeniami **bez ich uprzedniego skanowania** (pod warunkiem, że są w zasięgu), nawet jeśli używają one adresów typu *private resolvable*. Zapisany klucz identyfikujący służy do odszyfrowania rzeczywistego adresu drugiego uczestnika połączenia, który wystarcza do wysłania prośby o nawiązanie połączenia. 
(Choć Android potrafi trochę to utrudnić, o czym [tu](https://stackoverflow.com/questions/23471364/private-vs-public-addresses-in-bluetooth-low-energy-on-android) i [tu](https://stackoverflow.com/questions/32886725/android-4-4-bluetooth-low-energy-connect-without-scanning-for-a-ble-device).)

---
#tech-area/bluetooth-low-energy 



