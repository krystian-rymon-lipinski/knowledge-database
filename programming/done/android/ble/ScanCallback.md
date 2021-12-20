### ScanCallback
```kotlin
override fun onScanResult(callbackType: Int, result: ScanResult?) { }  
override fun onBatchScanResults(results: MutableList<ScanResult>?) { }
override fun onScanFailed(errorCode: Int) { }  
```

Z obiektu **ScanResult** można wyciągnąć np. BluetoothDevice i inne ciekawe rzeczy, jak np. okres rozgłaszania się albo moc sygnału.
Ponadto można ściągnąć **ScanRecord** - surowe bajty, które wysyłało urządzenie podczas rozgłaszania się.

_onBatchScanResults()_ może zostać wywołane, gdy kilka urządzeń zostanie zakolejkowane, np. przez ustawienie niskiej częstotliwości skanowania lub czasowego opóźnienia na zwróceniu urządzenia.

---
#tech-area/android 