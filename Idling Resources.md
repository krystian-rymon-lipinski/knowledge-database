up: [[013.3 Espresso MOC]]
#status/3-freezer
#tech-area/espresso

**Istnieją klasy IdlingResources w API. Można też rozszerzyć interfejs i stworzyć swój własny.**

```kotlin
class DialogFragmentIdlingResource(
	private val fragment: DialogFragment
) : IdlingResource { 

	private var callback: IdlingResou[Australia U23 - Sel. of Mediterranean](https://strims.top/AustraliaU23SelectionofMediterraneanU21.php)rce.ResourceCallback? = null 
	
	override fun getName(): String = "DialogFragmentIdlingResource" 
	override fun isIdleNow(): Boolean { 
		val idle = !fragment.isResumed || fragment.dialog?.isShowing != true 
		if (idle) { 
			callback?.onTransitionToIdle() 
		} 
		
		return idle 
	} 
	override fun registerIdleTransitionCallback(callback: IdlingResource.ResourceCallback?) { 
		this.callback = callback 
	} 
}
```

The `isIdleNow()` function is called by the Espresso framework to check the status of the `IdlingResource`. Espresso invokes this method periodically to determine if the resource is still busy or has become idle. The default refresh period for `isIdleNow()` is 5 milliseconds. You can change the refresh period to 100 milliseconds using `IdlingPolicies.setIdlingResourceTimeout(100, TimeUnit.MILLISECONDS)`.

---
[Idling Resources](https://developer.android.com/training/testing/espresso/idling-resource).