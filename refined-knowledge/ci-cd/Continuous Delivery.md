up: [[070 CI-CD MOC]]
X: [[Continuous Integration]]

**Automatyzacja dostarczania aplikacji (lub jej kolejnej wersji) na produkcję.** Ostateczna decyzja (finałowy klik) należy do człowieka, choć można skonfigurować skrypt w taki sposób, by również tę operację wykonywał samodzielnie - wówczas proces staje się _Continuous Deployment_.

Najczęstszym _triggerem_ jest dodanie na serwer gałęzi zaczynającej się od `release/`.

**Operacje najczęściej wykonywane po _triggerze_ dla projektu Androidowego:**
- integracja (zbudowanie i przetestowanie)
- utworzenie [[Pliki dystrybucji aplikacji Android|pliku dystrybucji aplikacji]] i [[Podpisywanie pliku .apk|podpisanie go kluczem]]
- przesłanie tegoż pliku do sklepu
- (dodanie pozostałych informacji potrzebnych do [[Udostępnianie aplikacji w konsoli Google Play|udostępnienia aplikacji]])
- (wypuszczenie aplikacji na produkcję)


Przykłady dla różnych środowisk:
- [[GitHub Action Android Delivery Pipeline]]