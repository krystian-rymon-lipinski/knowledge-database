### Callback
**Wzorzec (?)**

**Powiadamia kod wywołujący o zakończeniu wykonywania operacji. (?)**

W przeciwieństwie do Obserwatora, nie powiadamia on wielu obserwatorów, daje tylko znać jednemu - temu, który zlecił mu robienie czegoś

**Callback nie istnieje bez tego, co go wywołało!**
**Obiekt obserwowany nie musi mieć obserwatorów, by móc generować zdarzenia!** Co najwyżej nikt ich nie przechwyci.