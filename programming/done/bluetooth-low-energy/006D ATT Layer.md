### ATT Layer
**Protokół odpowiedzialny za transfer danych podczas połączenia między urządzeniami BLE. Klient wysyła zapytanie o konkretne [[0047 Atrybuty protokołu ATT|atrybuty]] przechowywane na serwerze, który wysyła odpowiedź.

Każde z urządzeń może być klientem, serwerem lub spełniać obie te role jednocześnie. W praktyce serwerem najczęściej jest urządzenie pełniące [[0033 Role urządzeń BLE|rolę]] urządzenia peryferyjnego, przechowujące dane (np. sensor). Wówczas klientem jest telefon chcący te informacje uzyskać.

**Komunikacja jest kolejkowana - klient nie może wysłać kolejnego zapytania, jeśli serwer jeszcze nie odpowiedział** (oczywiście jeśli typ zapytania tej odpowiedzi wymaga).

Protokół definiuje różne [[006E Operacje protokołu ATT|operacje]].

---
#tech-area/bluetooth-low-energy 