_@RunWith(MockitoJUnitRunner::class)_ - potrzebny do testów lokalnych Mockito

_@RunWith(AndroidJUnitRunner::class)_ - potrzebny do testów instrumentacyjnych (integracyjnych/UI) w Espresso (w Compose niekoniecznie)

_@RunWith(AndroidJUnit4::class)_ - potrzebny do testów bazy danych Room



> [!NOTE] Is that true?
> @RunWith is needed only when mixing JUnit3 and JUnit4 to distinguish which version should go (probably 4 if you have such a mix...)
> 
> https://www.artima.com/weblogs/viewpost.jsp?thread=126923
> 


#tech-area/mockito 
#status/3-freezer 