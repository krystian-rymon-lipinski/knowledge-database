**Protokół służący do zapewnienia bezpieczeństwa poprzez zastosowanie trzech mechanizmów:**
- szyfrowanie - zastosowane na wszystkich pakietach wymienianych przez ustanowione połączenie 
- prywatność - ukrycie publicznego [[0062 Adres BLE|adresu]] i zastąpienie go adresem typu *private resolvable*
- podpisywanie - wysyłanie nieszyfrowanych pakietów przez ustanowione połączenie z dodatkową informacją o ich źródle (którą odbiorca może w jakiś sposób zweryfikować i potwierdzić tożsamość nadawcy)

Mechanizmy te są implementowane poprzez odpowiednie [[Procedury bezpieczeństwa BLE|procedury bezpieczeństwa]] oraz [[0074 Klucze bezpieczeństwa BLE|klucze bezpieczeństwa]].

---
#tech-area/bluetooth-low-energy 