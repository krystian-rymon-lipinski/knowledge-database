up: [[Usługi powiązane]]
#status/in-progress  
#tech-area/android 

Można je powiązać z komponentami aplikacji (najczęściej z aktywnością). Serwisy te giną w momencie, w którym ginie komponent, który jest z nią powiązany.
Można też powiązać serwis z aplikacją, ale zamknięcie aplikacji nie musi oznaczać ubicia procesu przez system, więc może to prowadzić do wycieków pamięci.

```kotlin
class TimerService : Service() {  
    private val binder: IBinder = TimerBinder()  
  
    /* 1) Trzeba zwrócić tu 'binder'. */
    override fun onBind(intent: Intent): IBinder {  return binder  }  
  
    class Binding(private val context: Context, private val serviceListener: TimerListener) {  
	    /* 3) Obiekt 'ServiceConnection' jest potrzebny do wiązania. */
		private val connection: ServiceConnection = object : ServiceConnection {  
			override fun onServiceConnected(p0: ComponentName?, p1: IBinder?) {  
				val binder = p1 as TimerBinder  
				serviceListener.onTimerServiceBound(binder.getTimerService())  
			}  
	
			override fun onServiceDisconnected(p0: ComponentName?) {  
				serviceListener.onTimerServiceBound(null)  
			}  
	
		}  
	
		/* Interfejs do wiązania dla zewnętrznego komponentu. */
		fun bind() {  
			val intent = Intent(context, TimerService::class.java)  
			/* TUTAJ wiązana jest usługa. */
			context.bindService(intent, connection, Context.BIND_AUTO_CREATE)  
		}  
		fun unbind() {  
			context.unbindService(connection)  
		}  
}  
  
    interface TimerListener {  
        fun onTimerServiceBound(service: TimerService?)  
    }  
    /* 2) Wewnętrzna klasa rozszerzająca Binder na potrzeby pola. */
    inner class TimerBinder : Binder() {  
        fun getTimerService() : TimerService = this@TimerService  
    }  
}
```

Można oddzielić operacje związane z bindowaniem usługi od samych rzeczy, które ta usługa robi, poprzez stworzenie klasy bazowej dla usługi powiązanej (czy dla usług powiązanych wszystkich typów). Wówczas klasa bazowa obsługuje operacje bindowania, a konkretna już usługa robi rzeczy, które do niej należą. Komponentowi zewnętrznemu pozostanie utworzyć wiązanie i obsłużyć callback.

```kotlin
open class LocalService<T : LocalService<T>> : Service() {  
  
    private val binder = BluetoothBinder()  
  
  
    override fun onBind(intent: Intent): IBinder {  
        return binder  
    }  
  
    abstract class Binding<T : LocalService<T>>(private val context: Context) {  
  
        private val connection = object : ServiceConnection {  
            override fun onServiceConnected(p0: ComponentName?, p1: IBinder?) {  
                val binder = p1 as LocalService<T>.BluetoothBinder  
                onBound(binder.getService())  
            }  
  
            override fun onServiceDisconnected(p0: ComponentName?) {  
                onBound(null)  
            }  
        }  
  
        fun bind() : Boolean {  
            val serviceIntent = Intent(context, getServiceClass())  
            return context.bindService(serviceIntent, connection, BIND_AUTO_CREATE)  
        }  
  
        fun unbind() {  
            context.unbindService(connection)  
        }  
  
        abstract fun onBound(service: T?)  
        abstract fun getServiceClass() : Class<T>  
    }  

    inner class BluetoothBinder : Binder() {  
        fun getService() = this@LocalService as T  
    }  
}
```

https://developer.android.com/guide/components/bound-services#Binder