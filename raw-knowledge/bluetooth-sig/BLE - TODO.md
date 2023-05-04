#todo-list 

https://www.bluetooth.com/wp-content/uploads/2022/05/The-Bluetooth-LE-Primer-V1.1.0.pdf?__hstc=&__hssc=&hsCtaTracking=8e3cb9ce-2e7b-471a-b5cc-2343a4915b6a%7C090f705a-f0df-4f4b-8a54-c8f97c73eb69 - strona 12.
- [ ] Dokończyć opisywanie GATT Layera 
- [ ] Rozczłonkować definicje Link Layera i GAP Layera odnośnie ról urządzeń.
- [ ] Dodać jakoś stany urządzenia do opisu (Idle, Advertising, Scanning, Master, Slave, etc.)
Urządzenie może być we wszystkich stanach na raz - Advertising, Scanning i mieć połączenia jako central i jako slave! Na poziomie LinkLayera jest to możliwe.
		https://software-dl.ti.com/lprf/simplelink_cc2640r2_latest/docs/blestack/ble_user_guide/html/ble-stack-3.x/gap.html	  
- [ ] Zebrać wszystkie wszystkie stałe potrzebne w technologii (żeby łatwiej było śledzić zmiany).
	1. Advertiser data size
	2. Max MTU
	3. Protocol headers
	4. Connection parameters options
	5. Etc.
- [ ] Zrobić słowniczek! MTU, SDU, xxU, yyU, duuużo tego!
- [ ] Uporządkować całą wiedzę na temat technologii (foldery? linki?)
- [ ] Opisać Application layer z punktu widzenia Androida (Android API)
- [x] Zbadać stronę Bluetootha pod kątem BLE (i mesha?)