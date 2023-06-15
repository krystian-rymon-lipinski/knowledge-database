up: [[070 CI-CD MOC]]
X: [[Continuous Delivery]]

**Automatyzacja budowania i testowania kodu wrzucanego na zdalne repozytorium.**

Najczęstsze _triggery_:
- dodanie nowego _commita_ na dowolną gałąź
- utworzenie _pull requesta_ dowolnej gałęzi do głównej (lub jakiejś "ważnej"); można zablokować możliwość _merge'a_, jeśli kod pobocznej gałęzi nie przejdzie wymaganych operacji
- _merge_ dowolnej gałęzi do głównej

Pozwala to szybko wykrywać błędy i utrzymywać stabilny kod.

System CI jest w stanie dostarczyć informację zwrotną o statusie budowania i ewentualnych błędach na dowolnie wybrany kanał komunikacyjny (e-mail, Slack, etc.). Można również zaimplementować dodatkowe akcje dla określonych statusów.

**Operacje automatyzowane dla projektu Androidowego:**
- zbudowanie projektu
- przejście [[014 Android Testing|testów lokalnych]]
- przejście [[014 Android Testing|testów instrumentacyjnych]]; wymaga podpięcia pod serwer urządzeń, na których te testy mają zostać odpalone
- (utworzenie wykonywalnego artefaktu (pliku .apk), który można instalować na urządzeniu)