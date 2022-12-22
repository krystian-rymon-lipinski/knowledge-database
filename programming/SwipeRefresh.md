Jeżeli użytkownik jest na samej górze listy (albo w ogóle jakiegoś widoku) i zrobi swipe w górę, to pokaże się animacja refreshu.

```kotlin
swipe_refresh_container.apply {  
    setOnRefreshListener {  
        this.isRefreshing = false  // trzeba, żeby się kółko nie kręciło w nieskończoność
        /* TU coś zrób w reakcji na swipe */
    }  
    setColorSchemeColors(...) /* kolory kręcącego się kółka */ 
    )  
}
```

**Musi on być zewnętrznym widokiem dla RecyclerView albo ScrollView!**
Żeby nie było takiej sytuacji, że użytkownik scrolluje w dół, a w górę nie może, bo odpala się swipe refresh.