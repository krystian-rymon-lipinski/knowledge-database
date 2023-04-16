 up: [[0065 Physical Layer]]
#status/revision-needed 
#bluetooth-spec/4-0 #bluetooth-spec/5-0 

**Wybór odpowiedniego wariantu zależy od tego, czy zależy nam na szybkości transmisji, czy też na mocy transmitowanego sygnału. Wzrost jednej z wielkości powoduje spadek drugiej i vice versa.**

Szybkość transmisji wyrażona jest w symbolach na sekundę, ale dla modulacji binarnej (jak w tym przypadku) 1 symbol oznacza 1 bit.

- LE 1M - 1Mbit/s, względna moc sygnału = 1 (wartość referencyjna do innych), przesunięcie częstotliwości na modulacji [[Gaussian Frequency Shift Key|GFSK]]: +-185kHz|
- LE 2M - 2Mbit/s, względna moc sygnału = 0.8, przesunięcie częstotliwości na modulacji [[Gaussian Frequency Shift Key|GFSK]]: +-370kHz
- LE Coded (S=2) - 500kbit/s, względna moc sygnału = 2
- LE Coded (S=8) - 125kbit/s, względna moc sygnału = 4

> [!NOTE] Jakie jest przesunięcie częstotliwości dla LE Coded? Jak się je wylicza i od czego zależy?


> [!NOTE] Chat-GPT
> The frequency deviation for the PHY LE Coded in Bluetooth Low Energy (BLE) is a bit more complex to define than for other modulation schemes because the PHY LE Coded uses a Gaussian Frequency Shift Keying (GFSK) modulation with a coding rate of 1/2 or 3/4.
> 
> In GFSK modulation, the frequency deviation is proportional to the BT product, which is the product of the modulation index and the symbol duration. The modulation index for PHY LE Coded is 0.35, and the symbol duration is 8 µs. The coding rate determines the number of bits per symbol, which is either 1 or 2. 
> 
> Using these parameters, the frequency deviation for PHY LE Coded can be calculated as follows:
> -   For coding rate 1/2: frequency deviation = 0.35 x (1/2) x 8 µs = 1.4 kHz
> -   For coding rate 3/4: frequency deviation = 0.35 x (3/4) x 8 µs = 2.1 kHz
>  
> Therefore, the frequency deviation for PHY LE Coded in BLE is either 1.4 kHz or 2.1 kHz, depending on the coding rate used. It's worth noting that the actual frequency deviation can vary slightly depending on the implementation and specific parameters used.


Warto zwrócić uwagę, że podane szybkości transmisji dla modulacji nie oznaczają, że pakiety będą słane z taką wydajnością. Na rzeczywistą szybkość transmisji wpływ mają również wyższe warstwy protokołów.

**Wariant LE 1M jest obecny od początków BLE (Bluetooth 4.0) i jest obowiązkowy dla każdego urządzenia. Warianty pozostałe są opcjonalne i pojawiły się wraz ze specyfikacją Bluetooth 5.0.**
