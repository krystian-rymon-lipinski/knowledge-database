up: [[Jetpack Compose]]
#status/2-backlog

1. Jak działa dostawanie ViewModelu poprzez `viewModel`?
	- jakim cudem wiadomo, który ViewModel podać? (poprzez reified i podany typ?)
	- jaki jest scope tego ViewModelu? ViewModelStoreOwner defaultowy to LocalViewModelStoreOwner? Co to jest w ogóle? "For example, if the composable is used in an activity, `viewModel()` returns the same instance until the activity is finished or the process is killed."
	- skąd wziąć `hiltViewModel` i jak on się ma do scope'u?
2. Czym jest Scaffold??