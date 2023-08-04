up: [[010 Android MOC]]
#status/3-freezer
#tech-area/multithreading

**Bezpieczeństwo wątku głównego (_ang. main-safety)_ to podejście do pisania kodu w Androidzie w taki sposób, aby wątek główny nie wykonywał żadnych czasochłonnych operacji, co mogłoby się negatywnie odbić na [[Android Performance|osiągach]] aplikacji.**

Najczęściej realizuje się to poprzez zdefiniowanie w metodach klas [[Warstwa danych|warstwy danych]] korutyn na puli wątków innej niż związanej z wątkiem głównym. W ten sposób niezależnie od tego, z którego miejsca w kodzie (z którego ViewModelu) zostanie zawołana metoda, ona sama zatroszczy się o przeniesienie pracy do wątku innego niż główny. Dzięki temu nie trzeba o tym pamiętać w każdym miejscu wywołania metody.