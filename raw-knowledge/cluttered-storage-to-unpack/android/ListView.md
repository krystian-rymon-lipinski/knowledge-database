#status/3-freezer 
#tech-area/android 


ListView pokazuje zbiód danych w liście.
Potrzeba zdefiniować do niego adapter.

Można napisać swój adapter albo wykorzystać ArrayAdapter.
ArrayAdapter wymaga:
- zdefiniowania layoutu dla każdego widoku listy; można wykorzystać zdefiniowane androidowe albo napisać swój) 
- podania danych jako StringArray; można wyświetlać dane statyczne z resource'ów string-array albo wypełnić taką listę dynamicznie w kodzie


ViewHolder? Okazuje się, że rekomendacja jest taka, żeby dla każdej listy tworzyć ViewHolder. A czy rozszerza on ViewHolder z RecyclerView to inna rzecz.


ListView nie może być włączone wewnątrz \<ScrollView> - ma ona swoją własną obsługę scrollowania, podobnie jak np. RecyclerView. 
Wówczas trzeba pokombinować z np. NestedScroolView.