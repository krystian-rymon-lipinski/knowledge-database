Setup:
1) Powiązanie lokalnego repo z remotem.
	a) Ustawienie nazwy i emaila na lokalnym repo.
2) Utworzenie pustego projektu w Android Studio
	a) zbudowanie i zainstalowanie projektu - prawie na pewno będzie jakiś bug, którego trzeba będzie naprawić (np. przez targetSdkVersion/compileSdkVersion)
3) Dodanie potrzebnych w projekcie dependencji.
4) Powiązanie remote repo z CI/CD - w zależności od tego, które CI/CD jest wykorzystywane.

Ponadto, jeśli trzeba:
- dodanie innych modułów (np. bibliotek) w tym samym projekcie
	-> junit: testImplementation 'junit:junit:4.12'
	-> mockito: 
			testImplementation 'org.mockito:mockito-core:$version'
			testImplementation 'org.mockito.kotlin:mockito-kotlin:$version'
			testImplementation 'org.mockito:mockito-inline:2.13.0' - żeby można było mockować finalne klasy i metody
	-> espresso:
			androidTestImplementation 'androidx.test.ext:junit:1.1.3'  
			androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0'
- podpięcie submodułów gitowych pod moduł