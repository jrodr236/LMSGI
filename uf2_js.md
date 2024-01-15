# JavaScript

## Introducció

### Tecnologies web

Fins ara heu treballat amb pàgines **web estàtiques**

* Estan allotjades a un servidor.
* Des del client es descarrega la pàgina i es _renderitza_ al navegador.
* Els llenguatges utilitzats son **HTML** (contingut) i **CSS** (format).

![](https://www.imaginanet.com/thumb.php?n=blog%2F10herramientas.jpg\&w=640\&h=250\&x=0\&y=0)

Es poden aconseguir pàgines **web dinàmiques** si hi afegim estructures de programació. Però…&#x20;

**A on s’executarà el codi, al navegador o al servidor?**

![](https://s3-us-west-2.amazonaws.com/devcodepro/media/blog/frontend-y-backend.png)

#### Front-end

Tecnologies que s'executen al costat del client (navegador).

![JavaScript](http://lineadecodigo.com/wp-content/uploads/2014/04/javascript.png)

#### Back-end

Tecnologies que s'executen al servidor.

![Llenguatges back-end](https://image.slidesharecdn.com/97d66a5b-e796-4247-b320-a623835d58f8-160630025826/95/computer-programming-for-lawyers-15-638.jpg?cb=1467292671)

### Què és JavaScript?

* **Javascript** és el que es coneix com un llenguatge de **script.**
  * És un codi inserit en un document
* Javascript és **interpretat** directament pel navegador.
* JavaScript i Java: diferents llenguatges, sintaxi semblant.

### Història

* **Brendan Eich**, treballant a Netscape, crea **LiveScript** al **Netscape Navigator 2.0**
  * Després canvia el nom a **JavaScript**.

![Brendan Eich](https://upload.wikimedia.org/wikipedia/commons/0/09/BEich.jpg)

* Microsoft llança **JScript** a Internet Explorer 3.
  * Igual que JavaScript, amb un altre nom per evitar problemes legals.
* Netscape estandarditza el llenguatge a l'organisme ECMA.&#x20;
  * El 1997, aquest organisme crea el primer estàndard del llenguatge JavaScript que va anomenar **ECMAScript**
* El juny de 2015 es va publicar l'estàndard **ECMAScript 6**
* La **versió 7 d'ECMAScript es coneix com a ECMAScript 2016**, i és l'última versió disponible, publicada el juny del 2016.



## Què es pot fer amb Javascript?

[_Teoria completa www.w3schools.com_ ](https://www.w3schools.com/js/js\_intro.asp)

### Canviar contingut

> ⚠️ Tot i que els següents exemples tenen l'html i el javascript al mateix document, les bones pràctiques recomanen que estiguin en fitxers separats.

```html
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can change HTML content.</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Hello JavaScript!"'>Click Me!</button>

</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_inner_html)

### Canviar valors d'atributs

```html
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p>JavaScript can change HTML attribute values.</p>

<p>In this case JavaScript changes the value of the src (source) attribute of an image.</p>

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulbon.gif'">Turn on the light</button>

<img id="myImage" src="https://www.w3schools.com/js/pic_bulboff.gif" style="width:100px">

<button onclick="document.getElementById('myImage').src='https://www.w3schools.com/js/pic_bulboff.gif'">Turn off the light</button>

</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_lightbulb)

### Canviar estils

```html
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can change the style of an HTML element.</p>

<button type="button" onclick="document.getElementById('demo').style.fontSize='35px'">Click Me!</button>


</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_style)

### Ocultar elements

```html
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p id="demo">JavaScript can hide HTML elements.</p>

<button type="button" onclick="document.getElementById('demo').style.display='none'">Click Me!</button>


</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_hide)

### Mostrar elements

```html
<!DOCTYPE html>
<html>
<body>

<h2>What Can JavaScript Do?</h2>

<p>JavaScript can show hidden HTML elements.</p>

<p id="demo" style="display:none">Hello JavaScript!</p>

<button type="button" onclick="document.getElementById('demo').style.display='block'">Click Me!</button>

</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_intro_show)

Fixa't en dos aspectes importants:

* **Esdeveniments (Events)**: "coses" que passen en els elements HTML. JavaScript pot "reaccionar" a aquests esdeveniments.
* **Accés al DOM**: JavaScript pot accedir i canviar tots els elements del document HTML.


## Incloure codi JS

[Teoria completa a w3schools.com](https://www.w3schools.com/js/js\_whereto.asp)

Podem **incloure codi Javascript** en una pàgina web de 3 formes diferents:

* En el mateix document
* En un fitxer extern
* En els elements HTML

### **En el mateix document**

El codi **Javascript** es troba tancat entre les etiquetes **`<script>`** en qualsevol part del document.

Es recomana la definició del codi en la capçalera del document **`<head>`**.

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>Exemple de codi JavaScript en el propi document</title>
	<script>
  		alert("Hola mòn!!");
	</script>
</head>
 
<body>
	<p>Benvinguts al mòn Javascript</p>
</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_whereto_head)

#### Inconvenients

* Una modificació del codi requereix **modificar totes les pàgines** que inclouen el bloc de codi.

### **En els elements HMTL**

```html
<!DOCTYPE html>
<html>
<body>

<h1>A Web Page</h1>
<p id="demo">A Paragraph</p>
<button type="button" onclick="myFunction()">Try it</button>

<script>
function myFunction() {
  document.getElementById("demo").innerHTML = "Paragraph changed.";
}
</script>

</body>
</html>
```

[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_whereto_body)

#### Inconvenient

* Embruta innecessàriament el codi HTML de la pàgina i **dificulta molt el manteniment** del codi Javascript.

### **En un fitxer extern**


```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Exemple de codi JavaScript en un document extern</title>
        <script src="/js/myScript.js"></script>
    </head>
    <body>
        <h2>External JavaScript</h2>
        
        <p id="demo">A Paragraph.</p>
        
        <button type="button" onclick="myFunction()">Try it</button>
        
        <p>(myFunction is stored in an external file called "myScript.js")</p>    
    </body>
</html>
```


```javascript
// File name: js/_myScript.js
function myFunction() {
    document.getElementById("demo").innerHTML="Paragraph changed.";
}
```


[Demo](https://www.w3schools.com/js/tryit.asp?filename=tryjs_whereto_external)

* Cada etiqueta **`<script>`** només pot enllaçar un únic arxiu.
* En una mateixa pàgina es poden incloure tantes etiquetes _`<script>`_ com siguin necessàries.
* Els arxius de tipus JavaScript són documents de text amb extensió **.js**.

#### Avantatges

* Separa HTML i del codi Javascript.
* Fa que l’HTML i el JavaScript siguin més fàcil de llegir i mantenir
* Qualsevol modificació que es realitza en l'arxiu Javascript es veu reflectida immediatament en totes les pàgines enllaçades.



## Sintaxi del llenguatge

### No es tenen en compte els espais en blanc i les noves línies

Com en HTML, JavaScript **ignora qualsevol espai en blanc sobrant**, el codi es pot ordenar per a entendre'l millor.

Per exemple: Tabulant, amb espais, etc.

### Es distingeixen les majúscules de les minúscules

JavaScript és **Case sensitive**.

En JavaScript una variable anomenada **`Comptador`** no és el mateix que **`comptador`**.

> ⚠️ **Majúscula != Minúscula**

> ⚠️ Comptador != comptador

### No es defineix el tipus de les variables

En crear una variable, no és necessari indicar el tipus de dada que emmagatzemarà.&#x20;

### No és necessari acabar cada sentència amb el caràcter de punt i coma (;)

Encara que JavaScript **no obliga** a fer-ho, **és convenient seguir la tradició** d'acabar cada sentència amb el caràcter **`;`**

### Comentaris

* Permeten afegir informació al codi font del programa.&#x20;
* El contingut dels comentaris no es visualitza per pantalla, però **s'envia al navegador** de l'usuari amb la resta del script i per tant es poden veure.

#### Comentaris d’una sola línia

```javascript
// Comentari una sola línia 
alert("Hi JS developers");
```

#### Comentaris de més d’una línia

```javascript
/* Els comentaris de varies línies son útils quan es necessita 
incloure molta informació en els comentaris */
alert("Hi JS developers");
```

## Altres aspectes

[GitBook d'en Sergi Coll](https://sergi-coll.gitbook.io/javascript/):
- [Variables i constants](https://sergi-coll.gitbook.io/javascript/programacio-basica/variables-i-constants)
- [Operadors](https://sergi-coll.gitbook.io/javascript/programacio-basica/operadors)
- [Condicionals i bucles](https://sergi-coll.gitbook.io/javascript/programacio-basica/condicional-i-bucles)
- ...