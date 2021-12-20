### Manifest Permissions
Do niektórych funkcji wymagana jest zgoda użytkownika. 
Można albo zdefiniować w manifeście potrzebne zgody (wówczas użytkownik zostanie zapytany, czy wyraża zgodę podczas instalacji) lub w kodzie, np. w reakcji na kliknięcie przycisku (wówczas pojawia się popup).

###### W manifeście:
\<uses-permission android:name="android.permission.BLUETOOTH" />

###### W kodzie: 

requestPermissions
onRequestPermissionsResult - zwraca

