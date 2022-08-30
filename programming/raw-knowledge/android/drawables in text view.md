
app:drawableEndCompat="@drawable/ic_arrow_right" (Można też drawableEnd, ale pojawia się warning)
Nie trzeba tworzyć ImageView, można od razu wrzucić strzałkę i elo. 

W TextView jest to setCompoundDrawable...

Chodzi o to, że można użyć zasobów Drawable zdefiniowanych przez siebie w projekcie od razu w tekście.

Problem jest z marginesami/paddingami, ciężko je ustawić. 