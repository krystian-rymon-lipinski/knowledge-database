**Odwoływanie się do elementów UI przez Widok i podejmowanie na nich akcji** (np. zmiana tekstu lub widoczności). Może się dokonywać na [kilka sposobów](https://stackoverflow.com/questions/46482018/kotlin-android-view-binding-findviewbyid-vs-butterknife-vs-kotlin-android-exten):

1) findViewById() - przestarzała metoda
2) [[butterknife]] - biblioteka, raczej przestarzała
3) kotlin synthethics - mechanizm lepszy od powyższych, ale [niedługo również przestarzały](https://betterprogramming.pub/why-are-kotlin-synthetics-deprecated-and-what-are-the-alternatives-5c2b087dda1c)
4) [[0061 View Binding|ViewBinding]]
5) [[Data Binding|Data Binding]]

#android/ui 