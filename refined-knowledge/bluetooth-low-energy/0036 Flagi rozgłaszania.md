up: [[0039 Dane rozgłoszeniowe]]

**Informacje o urządzeniu nadającym, które zawarte są wewnątrz jego danych rozgłaszających.** 
Każda z wartości flagi ma inne znaczenie i służy w innych przypadkach.

- **0x01** - Limited Discoverable Mode
- **0x02** - General Discoverable Mode
- **0x04** - BR/EDR Not Supported ("zwykły" bluetooth niewspierany, nie jest to urządzenie dual mode)
- **0x08** - Simultaneous LE and BR/EDR, Controller (dual mode na poziomie kontrolera)
- **0x10** - Simultaneous LE and BR/EDR, Host (dual mode na poziomie hosta)

Wartości flag można łączyć, dlatego właśnie każda z nich jest zapisana na osobnym bicie.
