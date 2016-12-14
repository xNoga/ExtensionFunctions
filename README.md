# Extension Functions
<h2>Authors</h2>
Group members:
<ul>
<li>Magnus</li>
<li>Ingi</li>
<li>Kristoffer</li>
</ul>
<h2>The feature</h2>
Extension functions gør det muligt, som det angår af navnet, at extende functions på allerede eksisterende klasser og dermed give dem ny funktionalitet. Det betyder, at vi i stedet for at skrive den samme kode igen og igen kan vi skrive den en gang, undgå en masse boilerplate kode og gøre vores kode nemmere at læse. 
Udover extension functions er det også muligt at gøre brug af extension properties i Kotlin som tilføjer det samme koncept, men i stedet bare med properties. 

Det er vigtigt at forstå, at extension functions ikke modificerer klassen som de extend'er. De gør det dog muligt at kalde en function med dot notationen (.) på instanser af klassen, som man har extend'et. 

<h2>Example of use</h2>
<h3>Extension functions</h3>
```Kotlin
fun Fragment.toast(message: CharSequence, duration: Int = Toast.LENGTH_SHORT) { 
  Toast.makeText(getActivity(), message, duration).show()
}
```
Dette kunne også gøres på en activity eller en context - i dette tilfælde har vi lavet en extension function på Fragment klassen.
Dette gør det muligt fremover at kalde:
```Kotlin
fragment.toast("Hello world!")
```
Hvis man i stedet tilføjede det på Context klassen kan vi droppe helt at bruge objektet som argument og bare skrive functionen:
```Kotlin
fun Context.toast(message: CharSequence, duration: Int = Toast.LENGTH_SHORT) {
    Toast.makeText(this, message, duration).show()
}
```
Her har vi endda givet toast() functionen en default value på property'en 'duration', og vi kan derfor kalde metoden således: (uden objekt)
```Kotlin
toast("Hello world!")
toast("Hello world!", Toast.LENGTH_LONG)
```
<h3>Extension properties</h3>
Extension properties tilføjer det samme koncept til properties, og tilføjes f.eks. således på TextView klassen. Det kunne være hvilken som helst klasse i Kotlin. 
```Kotlin
var hej = "hej"
public var TextView.hello: String
    get() = hej
    set(v) {
      hej = v
    }

TextView.hello = "hej"
Println(TextView.hello) // = "hej"
```
Da extension properties rent faktisk IKKE indsætter nye medlemmer ind i klassen er det derfor heller ikke muligt at få adgang til et backing field. Derfor er initializors ikke tilladt for extension properties. Property'ens adfærd kan derfor kun defineres med get() og set()

<h2>List of sources</h2>
<ul>
<li>https://kotlinlang.org/docs/reference/extensions.html</li>
<li>Kotlin for Android Developers</li>
</ul>

