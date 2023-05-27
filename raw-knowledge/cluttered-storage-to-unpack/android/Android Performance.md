#status/3-freezer 
#tech-area/android 

Generalnie, żeby zapewnić odświeżanie na poziomie 60 Hz, system mniej więcej co 16 ms odświeża ekran.

Więc wszystko co przeliczane powinno się zawierać w tych 16 ms, aby było wrażenie płynności.

Opcje developerskie dają możliwość podglądnięcia, ile to zajmuje tak naprawdę.

https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering#debug_overdraw

### GPU Profiler
### GPU overdraw

[[app startup time]]
