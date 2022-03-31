### Metoda Fabrykująca
**Wzorzec kreujący.**

**Metoda abstrakcyjna zawarta w klasie bazowej fabryki.** Zdefiniowanie jej implementacji spoczywa na klasach rozszerzających bazową abstrakcyjną fabrykę. Wówczas **każda taka klasa może tworzyć inne produkty.**

Tak jak w przypadku [[0055 Prosta Fabryka (-)|prostej fabryki]] kod kliencki opiera się na **abstrakcyjnym supertypie** produktów fabryki, który muszą one implementować/rozszerzać, zamiast na pojedynczych implementacjach.

---
