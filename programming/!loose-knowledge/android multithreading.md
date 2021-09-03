Threading in Android

Każda aplikacja ma swój UI Thread. Tylko obiekty, które istnieją w stacku UI Threada mają dostęp do widoków i mogą je aktualizować (np. zmieniać teksty itp.).
Żeby przenieść dane z innego Threada do głównego (UI) można użyć Handlera.

Generalnie Handler tworzy się, żeby mieć nowy Thread, ale można też stworzyć Handlera, który jest powiązany z konkretnym Threadem. Wówczas kod który handluje wiadomości jest wykonywany na threadzie, z którym jest on powiązany.

____________________________

#tech-area/android 