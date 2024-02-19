up: [[015 Android Architecture]]

**Warstwa UI _(ang. UI layer)_ - warstwa mająca za zadanie przedstawienie informacji na ekranie poprzez [[Interfejs użytkownika|interfejs użytkownika]] oraz przechwytywanie zdarzeń wygenerowanych przez:
- użytkownika - interakcje z interfejsem poprzez [[android gestures|gesty]]
- system - rozmaite [[Zdarzenia systemu Android|zdarzenia systemowe]]

Składa się z następujących elementów:
- komponenty cyklu życia aplikacji ([[Activities|aktywności]], [[Fragments|fragmenty]]) - definiują _layouty_, które prezentują użytkownikowi informacje na ekranie (aktualny stan) poprzez wspomniany interfejs; są zależne od obiektów przechowujących stan
- przechowalniki stanu _(ang. state holders)_ - definiują aktualny stan aplikacji, który jest wyświetlany przez komponenty cyklu życia; wyróżniane są dwa ich typy:
	- [[Przechowalnik stanu ekranu|przechowalnik stanu ekranu]]
	- [[Przechowalnik stanu logiki UI|przechowalnik stanu logiki UI]]