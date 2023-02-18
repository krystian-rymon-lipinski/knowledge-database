Jeśli lista wartości jest statyczna i się nie zmienia, można ją wrzucić w XML-u jako android:entries, gdzie wartość tego to będzie string-array, zdefiniowana w strnig.xml.
Jeśli jest dynamiczna, to trzeba skonstruować adapter przy inicjalizacji widoku (trochę jak do RecyclerView ).

Przechwycenie wybrania opcji dzieje się przez onItemSelectedListener. Aczkolwiek to spowoduje, że zostanie to również wywołane **podczas inicjalizacji**!
Przechwycenie/ustawienie aktualnej pozycji spinnera dzieje się przez setSelection/getSelection.

