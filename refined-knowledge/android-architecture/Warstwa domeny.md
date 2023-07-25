up: [[015 Android Architecture]]

**Warstwa domeny _(ang. domain layer_) - warstwa tworzona, by ograniczyć złożoność lub reużywać tę samą logikę przy pobieraniu danych. Klasy tej warstwy to _use case'y_, które korzystają z klas repozytoriów.** Najczęściej tworzone, gdy trzeba ściągnąć dane z kilku różnych repozytoriów, aby nie musieć obrabiać informacji we ViewModelu.

Obiekty _use case'ow_ nie powinny mieć żadnego stanu (tylko go przekazywać), a ich zasięg powinien być powiązany z zasięgiem obiektu, którego są zależnością (najczęściej jest to ViewModel).