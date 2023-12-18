W Compose trzeba go powiązać ze Scaffold.

```kotlin
val snackBarHostState = remember { SnackbarHostState() }
val scope = rememberCoroutineScope()

Scaffold(
	snackbarHost = { SnackbarHost(snackBarHostState) }
	...
	scope.launch {
		snackBarHostState.showSnackbar(  
		    message = snackBarMessage,  
		    duration = SnackbarDuration.Short  
) }
	}
)
```