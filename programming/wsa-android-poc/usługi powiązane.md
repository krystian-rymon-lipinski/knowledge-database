https://developer.android.com/guide/components/bound-services#Binder

1) Klasa rozszerzająca Service
- metoda onBind(), która zwraca obiekt typu Binder
2) Klasa rozszerzająca Binder - potrzebny jest obiekt tej klasy, żeby zwrócić go w onBind klasy rozszerzającej Service
3) Klasa załatwiająca bindowanie. 
Potrzebuje kontekstu, żeby zawołać *bindService* i *unbindService*, a do tego potrzebuje obiektu *ServiceConnection* (to interfejs). Rozszerzane są dwie metody:
- onServiceConnected
- onServiceDisconnected

Z nich woła się *onBound* - abstrakcyjną metodę, której implementacja istnieje już w konkretnych aktywnościach i zależy od użytkownika.


Ogólnie to czasem lepiej oddzielić operacje związane z bindowaniem usługi od samych rzeczy, które ta usługa robi. 

Można zrobić klasę bazową dla usługi powiązanej (czy dla usług powiązanych wszystkich typów) i wtedy klasa bazowa obsługuje operacje bindowania, a konkretna już usługa robi rzeczy, które do niej należą. Z aktywności pozostanie zawołać zbindowanie i obsłużyć callback onBound.

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