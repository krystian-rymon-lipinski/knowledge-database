up: [[000 HOME]]
#gradle/plugin

Plugin ułatwiający serializację i deserializację danych.

```kotlin
id "org.jetbrains.kotlin.plugin.parcelize" version kotlinVersion apply false
```

Wystarczy oznaczyć klasę do parcelizacji annotacją `@Parcelize`. Chyba że parametry tej klasy nie będą obiektami prostymi, wtedy trzeba zaimplementować metody klasy `Parceler`:

```kotlin
@Parcelize
data class User(val firstName: String, val lastName: String) : Parcelable { 
	private companion object : Parceler<User> { 
		override fun User.write(parcel: Parcel, flags: Int) { 
			// Custom write implementation 
		}
		override fun create(parcel: Parcel): User { 
			// Custom read implementation
		}
	}
}
```


---
https://plugins.gradle.org/plugin/org.jetbrains.kotlin.plugin.parcelize
https://developer.android.com/kotlin/parcelize