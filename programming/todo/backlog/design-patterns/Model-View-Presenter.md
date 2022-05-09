### Model-View-Presenter
**Wzorzec architektoniczny.**
**Pomaga oddzielić warstwy kodu dla aplikacji współpracujących z interfejsami użytkownika.**

### Model
**Dostarczyciel danych**, zarówno tych przechowujących wartości do wyświetlenia w widokach interfejsu, jak i wielkości pomocnych w logice ich przeliczania. W tym celu może korzystać z pobierania z baz danych, plików tekstowych, etc., jak i zapisywać informacje aplikacji w tych miejscach.

### View
Służy do przejmowania wszelkich wydarzeń aplikacji - zarówno akcji użytkownika na interfejsie, jak i komunikatów systemowych - a następnie przekazanie ich do Presentera.
Zawiera referencję do Presentera, przez którą **deleguje** do niego obsługę przechwyconych wydarzeń.

### Presenter
Pośrednik między widokiem a modelem. Po przechwyceniu wiadomości od widoku uaktualnia model, a następnie na podstawie stanu modelu zmienia wartości modelu (jeśli trzeba).
Zawiera referencje do Modelu i Widoku.

Presenter przekazuje wartości do Widoku (lub do Widoków) poprzez interfejs (lub interfejsy), który ten widok implementuje.

---
#tech-area/design/architectural-patterns 