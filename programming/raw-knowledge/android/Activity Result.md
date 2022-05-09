Czasem zamiast tylko wysłać użytkownika gdzieś, trzeba go wysłać, żeby wrócił z informacją. Na przykład o tym, jaki plik wybrał i na tej podstawie go wczytać.

2 opcje:

1. startActivityForResult() + onActivityResult() - starsza wersja, dość prosta; onActivityResult wraca z Intentem i ekstrasami
2. rejestracja callbacku

registerForActivityResult() i jakieś dziwne cuda na kiju