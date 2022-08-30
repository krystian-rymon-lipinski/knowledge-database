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

Ponadto można dostosować jego wielkość względem okna. Należy zdefiniować w layoucie *match_parent* na pożądanym kierunku, a w kodzie nadpisać to wartością (już po utworzeniu widoku!). Drugi kierunek może pozostać po staremu.

```kotlin
override fun onViewCreated(view: View, savedInstanceState: Bundle?) {  
    super.onViewCreated(view, savedInstanceState)  
    val width = (resources.displayMetrics.widthPixels * 0.7).toInt()  
    dialog?.window?.setLayout(width, ViewGroup.LayoutParams.WRAP_CONTENT)  
}
```

Ten typ dialogu implementuje interfejs **OnDismissListener**. Można dzięki temu dać znać Widokowi, który go wywołał, że dialog został zamknięty. 
- w Widoku trzeba zaimplementować interfejs **DialogInterface.OnDismissListener**
- w dialogu trzeba przesłonić metodę onDismiss() i poza super.(), wywołać metodę Widoku

```kotlin
override fun onDismiss(dialog: DialogInterface) {  
    super.onDismiss(dialog)  
    (parentFragment as? DialogInterface.OnDismissListener)?.onDismiss(dialog)  
    /* Albo activity, jeśli to stamtąd wołano DialogFragment. */
} 
```

---
#tech-area/android 