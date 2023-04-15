up: [[0078 GAP Layer]]

Tryb 1. - szyfrowanie
- poziom 1 - brak szyfrowania
- poziom 2 - szyfrowanie nieuwierzytelnione; oznacza, że klucze użyte do szyfrowania zostały wygenerowane przy użyciu [[0064 Sposoby generowania kluczy szyfrujących|sposobu]] *Just Works*
- poziom 3 - szyfrowanie uwierzytelnione; oznacza, że klucze użyte do szyfrowania zostały wygenerowane przy użyciu innych sposobów - zapewniając ochronę przeciw atakom typu MITM *(man in the middle)*.

Możliwe jest przejście z poziomu 3 do 2 poprzez wygenerowanie nowych kluczy szyfrujących. Nie można jednak zejść niżej - szyfrowanie połączenia nie może zostać wyłączone (możliwe jest jedynie utworzenie nowego połączenia).

Tryb 2. - podpisywanie
- poziom 1 - podpisywanie nieuwierzytelnione; oznacza że klucze podpisujące nie są bezpieczne
- poziom 2 - podpisywanie uwierzytelnione

**Każde połączenie jest rozpoczynane w trybie 1. na poziomie 1! Dopiero później można dodać do niego dodatkowe środki bezpieczeństwa.** Np. urządzenia powiązane (*ang. bonded*), które po nawiązaniu ponownego połączenia wykonują procedurę reszyfrowania.

Ponadto możliwe jest zdefiniowanie urządzenia w trybie *non-bondable* lub *bondable*. Pierwszy z nich oznacza, że urządzenie może zostać tylko sparowane, procedura wiązania jest niemożliwa, ponieważ urządzenie nie może przechowywać i dytrybuować kluczy.

Przejście między zdefiniowanymi trybami jest możliwe poprzez [[Procedury bezpieczeństwa BLE|procedury bezpieczeństwa]].
Ponadto można zdefiniować dla operacji potrzebę jej **autoryzacji** - potwierdzenia (lub odrzucenia) z poziomu aplikacji jako wewnętrzne sprawdzenie lub poproszenie o wybór użytkownika (gdy urządzenie posiada UI).