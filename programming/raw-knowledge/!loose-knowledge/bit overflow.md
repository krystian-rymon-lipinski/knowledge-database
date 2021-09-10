Bit overflow:

Jeśli schodzimy z większej ilości bitów na mniejszą, zostają te najmniej istotne.

https://en.wikipedia.org/wiki/Integer_overflow
When an arithmetic operation produces a result larger than the maximum above for an N-bit integer, an overflow reduces the result to modulo N-th power of 2, retaining only the least significant bits of the result and effectively causing a wrap around.

Przykład:

258 na incie = 00000000 00000000 00000001 00000010
Obcięcie do typu byte pozostawi: 00000010
Czyli 258 na byte = 2

Inny przykład:

158 na incie = 00000000 00000000 00000000 10011110
Obcięcie do typu byte pozostawi: 10011110
Czyli 158 na byte = -98   -    BO PIERWSZY BIT W KODOWANIU U2 JEST UJEMNY!

Chyba że będzie konwersja na uint, wtedy z -98 zrobi się 158.

#tech-area/basics