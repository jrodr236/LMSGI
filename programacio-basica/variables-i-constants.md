# Variables i constants

> ℹ️ Una **variable** és un element que s'utilitza per emmagatzemar un valor.&#x20;

Les variables en JavaScript es creen mitjançant la paraula reservada **`var`**.

La paraula reservada **`var`** únicament s'ha d'indicar en definir per primera vegada la variable, el que es denomina **declarar una variable**.

```javascript
var numero_1 = 3;
var numero_2 = 1;
var resultat = numero_1 + numero_2;
```

### Problema en sobreescriure variables

Un dels problemes més grans amb la declaració de variables utilitzant la paraula clau **`var`** és que tu pots fàcilment sobreescriure declaracions de variables:

```javascript
var camper = "James";
var camper = "David"; 
console.log(camper); 
```

Al codi anterior, la variable **`camper`** es declara originalment com `James`, i s'anul·la per ser `David`. La consola després mostra la cadena de text `David`.

En una aplicació petita, potser no us trobeu amb aquest tipus de problema. Però a mesura que el teu codi base es fa més gran, **pot ser que accidentalment sobrescriguis una variable que no tenies la intenció de fer**.&#x20;

Com que aquest comportament no causa un error, la cerca i correcció d'errors es torna més difícil.

La paraula reservada **`let`** va ser introduïda a **ES6**, una actualització important per JavaScript, per resoldre aquest problema potencial amb la paraula clau var.

{% hint style="info" %}
És recomanable utilitzar en la decalarició de variables **let**
{% endhint %}

### Diferència entre var i let

**Diferències:**

* **`var`**NO té un àmbit de bloc.
* **`let`**SÍ té un àmbit de bloc.

**`var`**

```javascript
var elMeuNumero = 123;
if (true) {
    var elMeuNumero = 456;
}
console.log(elMeuNumero); // 456
```

**`let`**

```javascript
let elMeuNumero = 123;
if (true) {
    let elMeuNumero = 456;
}
console.log(elMeuNumero); // 123
```

### No és necessari declarar les variables

Una de les característiques més sorprenents de Javascript per als programadors habituats a altres llenguatges de programació és que **no és necessari declarar variables**.&#x20;

Per tant, es considera correcte:

```javascript
numero_1 = 3;
numero_2 = 1;
resultat = numero_1 + numero_2;
```

Si les variables no estan declarades, JavaScript crea una variable global i assigna el valor corresponent.

{% hint style="danger" %}
Es recomana i serà necessari **declarar totes les variables** que s'hagin d'utilitzar.
{% endhint %}

#### Exemple d'ús de variables

![](https://lh4.googleusercontent.com/YNgVRrd-Hsg91VoyPXj-0meHOVx1lGmn6lGhkkSVPsXTTzPfC6QFMm5Cl47LNn5d6WBC1KMAZk8fe-TGNIAW98qlEasUlrFD5sonGkpnfx1F\_qmOdYFEa4kFhguLiOK77dI9GcJoZQ)

### Declaració de constants

**Javascript** permet afegir _"variables immutables"_, també conegudes com a **constants**.

L'ús de `const` és una bona pràctica per a variables que no canviaran mai el seu valor, facilita el manteniment de l'aplicació i la llegibilitat.

{% hint style="warning" %}
Les **constants** han de ser declarades i **amb un valor assignat sempre**.
{% endhint %}

**Exemple:**

```javascript
const PI = 3.1416;
PI = 0; // NO permès
```

### Tipus de dades

```javascript
var length = 16;                               // Number
var length = 16.00;                            // Number with decimals


var lastName = "Johnson";                      // String
var lastName = 'Johnson';                      // String using single quotes

var condition = true;                          // Boolean
var cars = ["Saab", "Volvo", "BMW"];           // Array
var x = {firstName:"John", lastName:"Doe"};    // Object

```



{% hint style="info" %}
**Els tipus de JavaScript són dinàmics**
{% endhint %}

Això significa que la mateixa variable es pot utilitzar per contenir diferents tipus de dades:

```javascript
var x;           // Now x is undefined
x = 5;           // Now x is a Number
x = "John";      // Now x is a String
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs\_datatypes\_dynamic)
