up: [[RecyclerView Adapter]]

**Służy do zdefiniowania wszystkich składników interfejsu elementu. Musi dziedziczyć po klasie RecyclerView.ViewHolder.**

```kotlin
class CustomViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) { }
```

- `itemView` to główny layout elementu zbioru. Poprzez niego można odnieść się do jego składników, które zawiera (TextView, CheckBox, itp.) i ustawiać ich wartości.
- do resources można się dostać poprzez `itemView.context`

Można zadeklarować własny ViewHolder jako klasę wewnętrzną własnego Adaptera. (Ale nie może to być prywatna klasa wewnętrzna.)

**Ustawianie własności _alpha_ dla ViewHoldera może nie zostać wykonane przez system, ponieważ wykorzystuje on tę wartość do zasygnalizowania innych rzeczy podczas renderowania widoku.** Można albo użyć w to miejsce ustawiania kolorów albo ustawić _itemAnimator_ na null.