up: [[Stylowanie Material Design]]

**Etykiety wskazujące na statyczne wartości definiujące element stylu. Większa ilość elementów, a nawet cały system designu może odwoływać się do tokenów (zamiast wartości), co upraszcza tworzenie spójnego motywu stylistycznego.** Wówczas zmiana statycznej wartości elementu stylu zostaje rozpropagowana na wszystkie komponenty korzystające z tokenu.

Statyczna wartość, na którą wskazuje token może być kolorem, elementem typografii, pomiarem (np. długością marginesu lub podwyższeniem) lub innym tokenem. Mogą one również wskazywać na różne wartości w zależności od **kontekstu**. Przykładami kontekstu są: rozmiary urządzenia, tryb nocny, czytanie/pisanie RTL.

Komponenty Material Design definiują swoje atrybuty (kolor tekstu, czcionka, etc.) poprzez różne typy tokenów:
- _ref_ - najbardziej niskopoziomowy token, wskazuje na statyczne wartości
- _sys_ - wskazuje na token typu _ref_; większa ich ilość definiuje spójny stylistycznie motyw
- _comp_ - wskazuje na token _ref_ lub _sys_; wybrane elementy spójnego motywu składają się na styl komponentu

Nazwy tokenów powstają zgodnie z zasadą:
_design_system.token_type.design_attribute_ -> _md.sys.color.primary_ (md = Material Design)

