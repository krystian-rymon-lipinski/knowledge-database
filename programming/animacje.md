You can do two things to add animations, first you can let android animate layout changes for you. That way every time you change something in the layout like changing view visibility or view positions android will automatically create fade/transition animations. To use that set

```java
android:animateLayoutChanges="true"
```

on the root node in your layout.

---

Jeżeli chcemy "zniknąć" widok, na którym została wywołana animacja (nawet czasowa, która już dawno się skończyła), trzeba wywołać clearAnimation. Inaczej widok zwolni miejsce w layoucie, ale nie zniknie z ekranu.