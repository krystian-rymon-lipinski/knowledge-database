### MVVM w Androidzie

- customowy ViewModel musi rozszerzać klasę abstrakcyjną ViewModel
- widok, który korzysta z ViewModelu musi o niego zarequestować:
ViewModelProvider(this).get(CustomViewModel::class.java)
ViewModelProvider potrzebuje czegoś, co implementuje interfejs (LifecycleOwner) - każda aktywność go implementuje, więc no worries here

ViewModel jest... jakby singletonem? Każdy owner może mieć tylko jeden danego typu. W sensie jeżeli jeden fragment o niego poprosi, to go dostanie. A jak poprosi o niego następny, to dostanie tę samą instancję. Bo aktywność wciąż żyje, jej Lifecycle nie uległ zakończeniu. Dopiero po zakończeniu cyklu życia aktywności, jej ViewModel również ulega zniszczeniu.

No chyba że definiuje się ViewModel powiązany z cyklem aktywności fragmentu, bo też można. 

- widok, korzystający z ViewModelu rejestruje obserwatorów na każdym polu, o którego zmianach chce wiedzieć
Każde pole jest obiektem obserwowanym, a widok obserwuje je wszystkie (albo te, które go interesują).
viewModel.field.observe(this, {
// what to do after a change
})

ViewModel musi korzystać z pojemników na dane, które są Observablami, po to żeby ViewModel nie musiał korzystać z referencji do View. Można to zrobić na kilka sposobów:

- LiveData - pojemniki na dane, które są również Observablami; respektują one Lifecycles w taki sposób, że nie powiadamiają Obserwatorów, które nie są aktywne; oczywiście taki obserwator musi implementować interfejs 
- cokolwiek, co jest obserwowalnym obiektem - np. konstrukty z RxJavy
- data binding - to jest jakiś inny tam mechanizm, który chyba bezpośrednio wiąże elementy XML-a z konkretnym polem konkretnej klasy; I wouldn't know though, never used it



