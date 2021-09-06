W systemie U2 zakres np. byte jest równy [-128; 127]
Pierwszy bit daje mnożnik 0 lub -1. Reszta bitów daje 0 lub 1.

00001111 = 15
011111111 = 127=  0*2^7 + 1*2^6 + ... 1*2^0
1000000 = -128 = -1*2^7 + 0*2^6 + ... 0*2^0
111111111 = -1 = -1*2^7 + 1*2^6 + ... 1*2^0 - pierwszy bit jest bitem znaku poprzez matematyczne manipulacje, to nie tak, że na znak potrzebny jest osobny bit

Ma to znaczenie np. przy przesyłaniu wartości charakterystyk przez bluetooth, gdzie przesyłana zostaje tablica bajtów, z których trzeba uczynić sens. 
A jako że większość wartości ma sens tylko jako unsigned, a bity pakowane są w systemie U2, to trzeba to przekonwertować.

#tech-area/basics 
#tech-area/bluetooth-low-energy 