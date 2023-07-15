# Funcions

## Introducció

> Una **funció** és un conjunt d'instruccions que s'agrupen per realitzar una tasca concreta i que es poden **reutilitzar** fàcilment.

Es defineixen mitjançant la paraula reservada **`function`**, seguida del nom de la funció.

```javascript
function nomFuncio() {
  // Instruccions
  ...
}
```

## Arguments o paràmetres

> Les variables que necessiten les funcions s'anomenen **arguments o paràmetres**.

```javascript
function nomFuncio(parameter1, parameter2, parameter3) {
    // code to be executed
}
```

```markup
<!DOCTYPE html>
<html>
<body>

  <h2>JavaScript Functions</h2>

  <p>This example calls a function which performs a calculation, and returns the result:</p>

  <p id="demo"></p>

<script>
  function myFunction(p1, p2) {
      return p1 * p2;
  }

  document.getElementById("demo").innerHTML = myFunction(4, 3);
</script>

</body>
</html>
```

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjs\_functions)

**Paràmetres:**

* El **nombre d'arguments** que es passa a una funció hauria de ser el mateix que el nombre d'arguments que ha indicat la funció.&#x20;
* JavaScript **no mostra cap error** si es passen més o menys arguments dels necessaris.&#x20;
* L'**ordre dels arguments és fonamental**, les dades que s'esperen en la funció van directament relacionades amb els arguments especificats en la funció.&#x20;
*   No és obligatori que coincideixi el **nom dels arguments** que utilitza la funció i el nom&#x20;

    dels arguments que se li passen.

**Return:**

* La instrucció **`return`** serveix per indicar quin valor retorna la funció.
* Quan s'arriba a la instrucció **`return`**, la funció deixa d'executar-se.

## Àmbit global i local

**L'àmbit** fa referència a la visibilitat de les variables.&#x20;

Segons l'àmbit, existeixen dos tipus de variables:

* Variables **globals**
* Variables **locals**

#### Variables globals

* Les variables definides fora d'un bloc de funció tenen un **àmbit Global**.&#x20;
* Això significa que poden ser **utilitzades des de qualsevol lloc** al teu codi JavaScript.
* Les variables que es declaren sense les paraules clau **`let`** o **`const`** es creen automàticament en l'àmbit **Global.**
  * Això pot portar problemes amb variables que s'estan modificant a llocs inesperats.

{% hint style="danger" %}
Sempre has de declarar les teves variables amb **`let`** o **`const`**.
{% endhint %}

#### Variables locals

* Les variables que es declaren dins una funció tenen un **àmbit local**.&#x20;
* **Només són visibles dins d'aquesta funció.**

## Documentació i recursos

* **w3schools: Functions** [https://www.w3schools.com/js/js\_functions.asp](https://www.w3schools.com/js/js\_functions.asp)
