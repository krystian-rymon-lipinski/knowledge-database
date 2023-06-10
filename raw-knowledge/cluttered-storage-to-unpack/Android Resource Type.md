#android/xml 
#status/3-freezer 

W Androidzie są różne typy resourców. Definiuje się je w różnych podfolderach folderu `res`.
- animacje
	- res/animator/
	- res/anim/
- res/drawable ([[android drawable resources]])
- res/layout/ - widoki
- res/menu/ - menusy, duuuh
- res/navigation/ ([[Navigation Component]])
- res/values/ - pozostałe wartości, takie jak np.:
	- colors.xml
	- strings.xml
	- dimens.xml - długości marginesów, paddingów, wielkości czcionek, etc. (dp i sp generalnie)
	- styles.xml
	- themes.xml
- res/font/

https://developer.android.com/guide/topics/resources/available-resources

---
Sam Android posiada bibliotekę różnych resourców, np. kolory, animacje, style, etc.
Można się do nich odwołać w kodzie poprzez: *android.R.resource_type.resource*