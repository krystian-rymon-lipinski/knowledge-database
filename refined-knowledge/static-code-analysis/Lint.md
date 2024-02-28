up: [[Statyczna analiza kodu]]

Narzędzie wbudowane w Android Studio, służące do statycznej analizy napisanego kodu w plikach Java, Kotlin i XML. W projekcie można takiej analizy dokonać poprzez odpowiednie [[Zadania AGP|zadanie AGP]] lub poprzez "Inspect code" w opcjach [[012 Android Studio MOC|Android Studio]].

Każdy problem wykrywany przez lint ma swoje konkretne ID. Pełną ich listę można podejrzeć poprzez: `lint --list`. Można kazać narzędziu ignorować konkretne błędy/ostrzeżenia poprzez annotację `@SuppressLint("IssueID")` w plikach Java/Kotlin lub poprzez `tools:ignore="IssueID"` w plikach XML.

Konfigurowanie linta jest możliwe poprzez blok `lint {}` w pliku `build.gradle`. Ustawienia dotyczące konkretnych błędów/ostrzeżeń (ignorowanie, sprawdzanie, etc.) dzieje się w pliku `lint.xml`, który powinien się znajdować w głównym folderze projektu.

Można zdefiniować w pliku `.xml` konkretną konfigurację linta i ustawić ją jako _baseline_. Wówczas raportowane będą tylko problemy nowego typu, o ID innym niż uwzględnione w tymże pliku.

---
https://developer.android.com/studio/write/lint