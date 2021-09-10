JNI korzysta z Garbage Collectora.

jobject to referencja do obiektu. 
Obiekt ginie, jeśli nie ma do niego żadnej referencji.

Ale czy sama referencja ginie?

jObjectArray - referencja do tablicy referencji



Więc teoretycznie nie trzeba czyścić tego wszystkiego?




Get<PrimitiveType>ArrayElements - zwraca elementy z tablicy natywnej (np. jbyteArray); przyrównuje się to do wskaźnika typu natywnego (jbyte *) i dzięki temu można się po tej tablicy poruszać

Release<PrimitiveType>ArrayElements - kod natywny nie musi już mieć dostępu do elementów tablicy


Inna opcja?

New<PrimitiveType>Array - UTWORZENIE tablicy na poziomie JNI
Set<PrimitiveType>Array - WYPEŁNIENIE tablicy na poziomie JNI

Wówczas zamiast robienia wywołania "Release" wystarczy usunąć wywołanie.
DeleteLocalRef - usunięcie wywołania do obiektu utworzonego w JNI

Chyba że nie trzeba usuwać lokalnych referencji, bo one się usuną po dojścia do końca scope'u.
Ale wówczas po co byłaby ta funkcja? 
	
#tech-area/jni
	