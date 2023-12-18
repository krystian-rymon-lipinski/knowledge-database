
**Występują w dwóch formatach:**
- .apk
- .aab
###### Najważniejsze różnice:
- **zasoby** - wrzucenie pliku .apk będzie skutkowało zainstalowaniem na urządzeniu końcowym paczki z wszystkimi zasobami niezależnie od rozdzielczości urządzenia, wybranego języka, etc.; plik .aab determinuje potrzebne zasoby w momencie instalacji, co powoduje pobieranie tylko tych potrzebnych dla konkretnego urządzenia i w konsekwencji sprawia, że sama aplikacja waży mniej; jeśli aktualizacja zmienia tylko niektóre z zasobów, nie będzie ona aplikowana dla tych urządzeń, których nie dotyczą zmienione zasoby
Można emulować zachowanie serwera Google za pomocą [bundletoola](https://developer.android.com/studio/command-line/bundletool) dla różnych ustawień urządzeń końcowych.

- **klucze** - dla plików .apk klucz podpisujący generuje deweloper; dla plików .aab klucz jest generowany przez Google'a

---
https://developer.android.com/guide/app-bundle