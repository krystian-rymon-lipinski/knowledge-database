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