#status/3-freezer
  
1. Czy naprawdę nie da się zmienić nazwy urządzenia widocznego dla innych skanerów poprzez BluetoothAdapter? czy zawsze trzeba to robić przez advertisingData?  
    - a co z urządzeniami typu Classic? one nie mają advertising data (chyba?)  
  
2. Czy recyclerView.Adapter powininen (może) robić coś więcej niż tylko wyświetlać widoki? czy nie należy wyabstrahować całej logiki odpowiedzialnej za np. sortowanie czy filtrowanie do innego miejsca?  
  
3. Jak nie dublować danych we viewModelu i RecyclerView? Bo jeden jest do śledzenia stanu, więc dobrze jest mieć w nim listę rzeczy, a drugi potrzebuje na         tej liście operować, żeby wyświetlić dane z jej itemów w widokach  
    Trochę słabo jest najpierw setować/dodawać/usuwać rzeczy z viewModelu, a potem robić to samo w Adapterze.  
    Wiadomo, można rzucać za każdym razem pełną listę do setu (chociaż i tak trzeba trzymać ją jako pole na potrzeby onBindViewHolder), ale potem można tylko wołać onNotifyDataSetChanged(), co strasznie żre klatki i generalnie nie jest najlepszą opcją na handlowanie recycler view.  
  
    Można wrzucić LiveData value z ViewModelu jako parametr konstruktora adaptera - i jakoś działa - tylko że i tak trzeba wołać notify* na adapterach.  
    Najprościej chyba wrzucać za każdym razem nową listę i robić DiffUtil w adapterze - przeliczenie różnic w listach i dispatch ich i niech adapter sobie robi rzeczy.  
  
4. Czy korzystanie z LiveData we ViewModelu może być tak "po prostu" (z publicznym dostępem zmiennej), czy trzeba tworzyć pary, z których jedna jest publiczna i Mutable, a druga prywatna, non-mutable i zmienia się tylko ze zmianą tej pierwszej?  
    Generalnie chyba chodzi o to, że ViewModel udostępnia tylko metody, które mogą wpływać w określony sposób na tę zmienną, a sama zmienna jest prywatna.  
    Czyli jedna zmienna jest MutableLiveData i prywatna i zmienia się tylko przez metody publiczne.  
    A druga zmienna jest LiveData i już w inicjalizacji zostaje "zapięta" na pierwszą zmienną. Co chyba oznacza, że jest jej obserwatorem.  
    No i ta druga zmienna jest publiczna i UI kontroler jest z kolei jej obserwatorem.  
  
    Ta dostępna publicznie ma chroniony set na wartość, więc nie można jej ustawiać z zewnątrz! I bardzo dobrze. Dlatego właśnie potrzebne są pary - mutable można ustawiać wartość, ale ją trzeba zrobić prywatną, że ustawiać przez metody. A niemutable służy do obserwowania.
5. Po co są [[Własne annotacje zasięgu]] w Daggerze? Czy tylko na potrzeby subkomponentów? A jeśli jest tylko jeden komponent, to czy nie wystarczy utworzyć referencji do niego i korzystać tam, gdzie jest potrzebny (aktywność i jej fragmenty)?

	Nie do końca. Sam komponent, owszem, wystarczy jedna referencja do niego. Ale potem na tym komponencie trzeba wywołać `inject(target)` - i wówczas te annotacje mają znaczenie, bo bez nich po prostu utworzone zostaną nowe instancje klas grafu wszędzie tam, gdzie w miejscu wstrzykiwania pojawia się `@Inject`.

6. Jak poprawnie testować [[Produkcja stanu ekranu|operator .stateIn]]? Testowanie flow wydaje się działać przy zdefiniowaniu pary MutableStateFlow/StateFlow i aktualizowaniu pierwszego. Wówczas drugi odbiera wszystkie zmiany wartości. Ale już przy zdefiniowaniu StateFlow przy pomocy .stateIn testowanie nie działa.
Są problemy, opisane [tu](https://github.com/cashapp/turbine/issues/204), [tu](https://github.com/Kotlin/kotlinx.coroutines/issues/3143) i [tu](https://www.billjings.com/posts/title/testing-stateflow-is-annoying/). Można spróbować z [[Turbine]], ale też chyba niewiele pomaga.


To działa:
```kotlin
class FakeViewModel(  
    private val repository: FakeRepository  
) : ViewModel() {  
  
    val score: StateFlow<Int> = repository.scores  
        .stateIn(viewModelScope, SharingStarted.WhileSubscribed(), 0)  
}

@Test  
fun testFakeRepository() = runTest {  
    val unconfinedTestDispatcher = UnconfinedTestDispatcher(testScheduler)  
    Dispatchers.setMain(StandardTestDispatcher(testScheduler))  
    val fakeRepository = FakeRepository()  
    val viewModel = FakeViewModel(fakeRepository)  
  
    val items = mutableListOf<Int>()  
    val job = launch(unconfinedTestDispatcher) {  
        viewModel.score.collect {  
            items.add(it)  
        }  
    }  
    runCurrent()  
    fakeRepository.emit(1)  
    runCurrent()  
    fakeRepository.emit(2)  
    runCurrent()  
    fakeRepository.emit(3)  
  
    assertEquals(4, items.size)  
    assertEquals(listOf(0, 1, 2, 3), items)  
    assertEquals(3, viewModel.score.value)  
  
    job.cancel()  
    Dispatchers.resetMain()
```

A to już nie:

```kotlin
val uiState = tasklistRepository.getAllTasklists()  
    .stateIn(  
        scope = viewModelScope,  
        started = SharingStarted.WhileSubscribed(),  
        initialValue = emptyList()  
    )

@Test  
fun observeUiStateFromStateFlow() = runTest {  
    val unconfined = UnconfinedTestDispatcher(testScheduler)  
    val standard = StandardTestDispatcher(testScheduler)  
    Dispatchers.setMain(standard)  
  
    var collected = 0  
  
    val collectJob = launch(unconfined) {  
        testObj.uiState.collect {  
            collected = collected.inc()  
            println("collecting list")  
        }  
    }  
    val firstTasklist = Tasklist("aName")  
    val secondTasklist = Tasklist("bName")  
    val thirdTasklist = Tasklist("cName")  
  
    runCurrent()  
    fakeTasklistsRepository.emit(listOf(firstTasklist))  
    runCurrent()  
    fakeTasklistsRepository.emit(listOf(secondTasklist, thirdTasklist))  
  
    assertEquals(2, testObj.uiState.value.size)  
    assertEquals(secondTasklist, testObj.uiState.value[0])  
    assertEquals(thirdTasklist, testObj.uiState.value[1])  
  
  
    collectJob.cancel()  
    Dispatchers.resetMain()  
}
```