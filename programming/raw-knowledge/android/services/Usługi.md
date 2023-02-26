Komponenty aplikacji nie posiadające UI mogące robić rzeczy, ale nie mają UI.
Trzeba je zdefiniować w manifeście - nazwę klasy i atrybut exported, opisujący czy inne aplikacje mogą z nich skorzystać. (Jest też atrybut enabled, który może nie być domyślnie true.)

###### Usługi uruchomione 
- raz wystartowane mogą sobie pracować w tle, nawet jeśli aktywność (czy aplikacja nawet), z której została wystartowana, już dawno została zamknięta;
- klasa serwisu powinna rozszerzać IntentService; startuje się usługę poprzez utworzenie explicit intenta i wywołanie *startService*
- kod do wykonania przez serwis należy umieścić w *onHandleIntent()*
- kwestie konfiguracyjne można umieścić w *onStartCommand()*

Wraz z API 30, usługi uruchomione są uważane za przestarzałe, [oto powód](https://developer.android.com/reference/android/app/IntentService).
W ich miejsce do obsługiwania zakulisowych operacji należy użyć klasy [[WorkManager]].


###### [[Usługi powiązane]] 
- są skojarzone z komponentem (np. aktywność); kiedy komponent ginie, usługa również
- klasa serwisu powinna rozszerzać Service; startuje się usługę poprzez wywołanie bindService
- trzeba jeszcze zdefiniować klasę rozszerzającą klasę *Binder* (np. jako klasę wewnętrzną); obiekt typu binder jest zwracany w metodzie *onBind()* klasy serwisu