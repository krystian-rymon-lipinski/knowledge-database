### DialogFragment
**Odmiana [[Fragments|fragmentu]], która została stworzona do wyświetlania dialogów.**

Pozwala to podpiąć dialog pod element, który posiada cykl życia, co może się okazać pomocne, gdy aktywność zmienia swoją konfigurację. Wówczas "zwykły" Dialog mógłby nie zachować swojego stanu - a na pewno trzeba wygenerować dodatkowy kod, by temu przeciwdziałać.

Klasa ta posiada metodę _onCreateDialog()_. Wewnątrz niej należy ów dialog zdefiniować, a następnie zwrócić poprzez _return_. (Nie należy zwracać implementacji _super.onCreateDialog()_!)

Z zewnątrz taki fragment tworzy się poprzez:

```kotlin
CustomDialogFragment().show(supportFragmentManager, FRAGMENT_TAG)
```

Aby zapobiec zamknięciu dialogu po kliku gdziekolwiek poza nim:

```kotlin
override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View? {  
    dialog?.setCanceledOnTouchOutside(false)
}
```

---
#tech-area/android 