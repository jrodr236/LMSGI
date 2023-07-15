# Accés al DOM

#### ¿Qué métodos podemos usar?

Te mostramos cómo puedes utilizar los siguientes métodos para encontrar uno o más elementos en tu página web:

* [`document.getElementById(id)`](https://developer.mozilla.org/en-US/docs/Web/API/document.getElementById)
* [`document.getElementsByClassName(nombreDeClase)`](https://developer.mozilla.org/en-US/docs/Web/API/document.getElementsByClassName)
* [`document.getElementsByTagName(nombreDeEtiqueta)`](https://developer.mozilla.org/en-US/docs/Web/API/document.getElementsByTagName)
* [`document.querySelector(selectorCss)`](https://developer.mozilla.org/en-US/docs/Web/API/document.querySelector)
* [`document.querySelectorAll(selectorCss)`](https://developer.mozilla.org/en-US/docs/Web/API/document.querySelectorAll)

#### ¿Qué es lo que regresan?

Hay dos métodos que regresan un único objeto [`Element`](https://developer.mozilla.org/en-US/docs/Web/API/Element), `getElementById` y `querySelector`:

```text
var salsMotto = document.getElementById("salsMotto");
salsMotto.innerHTML = "Las matemáticas son geniales";
```

Los métodos `getElementsByClassName` y `getElementsByTagName` regresan un objeto [`HTMLCollection`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCollection) que actúa como un arreglo. Esa colección está "viva", lo que significa que la colección se actualiza si al documento se le agregan elementos adicionales con nombre de etiqueta o nombre de clase.

```text
var teamMembers = document.getElementsByClassName("team-member");
for (var i = 0; i < teamMembers.length; i++) {
   console.log(teamMembers[i].innerHTML);
}
```

El método `querySelectorAll()` regresa un [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList), que también actúa como un arreglo. Esa lista es "estática", lo que significa que la lista no se actualizará aunque se le agreguen nuevos elementos coincidentes a la página. Lo más probable es que no te encuentres con la diferencia entre los dos tipos de datos de regreso cuando estés usando estos métodos, pero es bueno tenerlo en cuenta.

```text
var teamMembers = document.querySelectorAll(".team-member");
for (var i = 0; i < teamMembers.length; i++) {
   console.log(teamMembers[i].innerHTML);
}
```

#### Acceder con subconsultas

Una vez que hayas encontrado un elemento, puedes hacer subconsultas sobre él al usar los métodos que acabamos de mostrar. Por ejemplo:

```text
// encuentra el elemento con esa ID
var salsMotto = document.getElementById("salsMotto");
// encuentra los spans dentro de ese elemento:
var mottoWords = salsMotto.getElementsByTagName("span");
// escribe en consola cuántos hay
console.log(mottoWords.length);
```

#### Atravesar el DOM

Otra manera de acceder a los elementos es "atravesar" el árbol del DOM. Cada elemento tiene propiedades que apuntan a los elementos relacionados con él:

* `firstElementChild`
* `lastElementChild`
* `nextElementChild/nextElementSibling`
* `previousElementChild/previousElementSibling`
* `childNodes`
* `childElementCount`

Por ejemplo:

```text
var salsMotto = document.getElementById("salsMotto");
for (var i = 0; i < salsMotto.childNodes.length; i++) {
   console.log(salsMotto.childNodes[i]);
}
```

Estas propiedades **no** están disponibles en los nodos `Text`, solo en los nodos `Element`. Para asegurarte de que puedas atravesar un elemento, puedes revisar sus propiedades `nodeType`/`nodeValue`. Probablemente no necesites o quieras atravesar el DOM, pero es otra opción disponible para ti.

