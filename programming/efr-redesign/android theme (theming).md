Można dodać w stylu, który jest zdefiniowy jako theme aplikacji (w manifeście) dodatkowe style, które będą opisywać wybrane elementy UI, dzięki czemu będą one wszędzie takie same.

Wówczas nie trzeba definiować stylu dla każdego elementu UI! Można je pogrupować w rodziny i zdefiniować raz na zawsze w głównym motywie aplikacji!

```xml
<item 
	  name="extendedFloatingActionButtonStyle">@style/Your.Defined.Style </item>
```
Nazwa stylu zdefiniowanego w głównym stylu musi odpowiadać modyfikowanemu elementowi UI, np. editTextStyle, imageButtonStyle, etc.

Zdefiniowany w aplikacji styl dla elemntu UI musi "dziedziczyć" po jakimś już istniejącym w Material Designie.

```xml
<style name="Your.Defined.Style" 
	   parent="Widget.MaterialComponents.ExtendedFloatingActionButton" >
	   <!-- insert style items here -->
</style>
```