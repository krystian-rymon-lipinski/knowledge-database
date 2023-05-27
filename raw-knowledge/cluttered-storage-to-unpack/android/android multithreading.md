#status/3-freezer 
#tech-area/android 

Threading in Android

Każda aplikacja ma swój UI Thread. Tylko obiekty, które istnieją w stacku UI Threada mają dostęp do widoków i mogą je aktualizować (np. zmieniać teksty itp.).
Żeby przenieść dane z innego Threada do głównego (UI) można użyć Handlera.

Oprócz UI Threada istnieje jeszcze coś takiego jak Render Thread.
W skrócie chodzi o to, że nowoczesne telefony mają CPU i GPU - gdzie GPU robi czystą matematykę, operacje na macierzach, transformacje ich, itp.

I jeśli UI Thread ma za dużo roboty, to może wysłać coś do obliczeń do GPU.
Bo generalnie UI Thread powinien się wyrobić ze wszystkimi obliczeniami w 16 ms, żeby zapewnić częstotliwość odświeżania ekranu na poziomie 60 Hz.

https://stackoverflow.com/questions/48618444/renderthread-vs-ui-thread
https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering#debug_overdraw






Generalnie Handler tworzy się, żeby mieć nowy Thread, ale można też stworzyć Handlera, który jest powiązany z konkretnym Threadem. Wówczas kod który handluje wiadomości jest wykonywany na threadzie, z którym jest on powiązany.

Co do powtarzających się zadań można wykorzystać po prostu Timer, na którym można wykonać schedule i wrzucić mu Runnable, któego on wykona na osobnym wątku.
Można też wykorzystać rozmaite klasy typu Executor. Np. SchedulerThreadPoolExecutor, który generalnie jest bardziej robust niż zwykły Timer.
