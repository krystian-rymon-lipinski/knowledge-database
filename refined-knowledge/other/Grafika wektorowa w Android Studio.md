#tech-area/android/xml 

```xml
<vector xmlns:android="http://schemas.android.com/apk/res/android" >
	android:width="70dp"  
	android:height="70dp"  
	android:viewportWidth="50"  
	android:viewportHeight="50">

	<path  
    android:pathData="M10,90 v-75 l10,-5, h70, v75, l-10,5Z"  
    android:strokeWidth="2.2"  
    android:strokeColor="@color/black"  
    android:fillColor="@color/white"/>
</vector
```

`width` i `height` to rzeczywiste rozmiary grafiki na layoucie, zaś wymiary `viewport` oznaczają wielkość płótna, na którym rysowana jest grafika. Przykładowo, jeśli `viewportWidth` to 100, a rysowana jest linia H50, zajmie ona połowę szerokości płótna.

Rysować można poprzez współrzędne absolutne lub względne. Te pierwsze oznaczane są wielką literą alfabetu, te drugie - małą. Definiowane są następujące komendy:
- M / m (X,Y) - przesunięcie kursora do punktu o współrzędnych (X,Y)
- L / l (X,Y) -  linia z aktualnej pozycji kursora do punktu o współrzędnych (X,Y)
- H / h (X) - linia pozioma z aktualnej pozycji kursora do punktu o współrzędnych (X,Y0)
- V / v (Y) - linia pionowa z aktualnej pozycji kursora do punktu o współrzędnych (X0, Y)
- Z / z - linia z aktualnej pozycji kursora do punktu startowego ścieżki (_pathData_)

Możliwe jest również rysowanie łuków i okręgów, poprzez następujący format:
`A rx ry x-axis-rotation large-arc-flag sweep-flag x y`

- (Rx,Ry) - promienie x i y elipsy
- x-axis-rotation - rotacja osi X elipsy wokół osi X płótna; podawana w stopniach
- large-arc-flag - łuk do wyboru, większy lub mniejszy (0/1)
- sweep-flag - kierunek rysowania łuku (0/1)
- (X,Y) - współrzędne punktu kończącego łuk

---
https://www.w3.org/TR/SVG/paths.html
https://www.w3.org/TR/SVG/paths.html#PathDataEllipticalArcCommands