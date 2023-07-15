# Modificació del DOM

### Modificar un elemento existente

Cubrimos varias maneras en las que puedes modificar los aspectos de un elemento existente:

### Modificar atributos

Puedes establecer un atributo en un elemento al establecer la propiedad con el mismo nombre. Por ejemplo, para cambiar el `src` de una `<img>`:

```javascript
imgEl.src = "http://www.dogs.com/dog.gif";
```

Adicionalmente, también puedes utilizar el método [`setAttribute`](https://developer.mozilla.org/en-US/docs/Web/API/Element.setAttribute), así:

```javascript
imgEl.setAttribute("src", "http://www.dogs.com/dog.gif");
```

Si quieres quitar un atributo, debes hacerlo con [`removeAttribute`](https://developer.mozilla.org/en-US/docs/Web/API/Element.removeAttribute), como para quitar el atributo `disabled` de un botón, habilitándolo:

```text
imgEl.removeAttribute("disabled");
```

#### Modificar estilos

Puedes cambiar estilos igual que como cambias los atributos, al acceder a la propiedad `style` del elemento, y establecr la propiedad correspondiente. Por ejemplo, para cambiar el color:

```text
headingEl.style.color = "hotpink";
```

Recuerda usar notación "camelCase" en los nombres de las propiedades de CSS de varias palabras, puesto que los guiones no son nombres de propiedad válidos en JS:

```text
headingEl.style.backgroundColor = "salmon";
```

#### Modificar nombres de clases

Para agregar una clase a un elemento, puedes establecer la propiedad `className`:

```text
mainEl.className = "warning";
```

Eso anulará las otras clases existentes, así que debes hacer esto en su lugar si solo quieres añadir a la lista de clases:

```text
mainEl.className += " warning";
```

En [los navegadores más recientes](http://caniuse.com/#search=classList), puedes utilizar la funcionalidad de [`classList`](https://developer.mozilla.org/en-US/docs/Web/API/Element.classList) en su lugar:

```text
mainEl.classList.add("warning");
```

#### Modificar HTML interno o texto

Para reemplazar por completo el contenido de un elemento con una cadena arbitraria de HTML, utiliza [`innerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element.innerHTML):

```text
mainEl.innerHTML = "los gatos son <strong>los más lindos</strong>";
```

Si no necesitas pasar etiquetas HTML, debes utilizar [`textContent`](https://developer.mozilla.org/en-US/docs/Web/API/Node.textContent) en su lugar:

```text
mainEl.textContent = "los gatos son los más lindos";
```

En general, debes tener cuidado al utilizar cualquiera de estas 2 propiedades, porque también eliminarán los detectores de eventos \(los cuales enseñamos en la siguiente lección\).

### Crear elementos desde cero

Hay todo un conjunto de funciones que puedes utilizar para crear elementos completamente nuevos y agregarlos a la página.Para crear un nuevo elemento, utiliza el acertadamente llamado [`createElement`](https://developer.mozilla.org/en-US/docs/Web/API/document.createElement):

```text
var imgEl = document.createElement("img");
```

Para anexarlo a la página, llama [`appendChild`](https://developer.mozilla.org/en-US/docs/Web/API/Node.appendChild) en el elemento padre de destino:

```text
document.body.appendChild(imgEl);
```

Del mismo modo, también puedes utilizar [`insertBefore`](https://developer.mozilla.org/en-US/docs/Web/API/Node.insertBefore), [`replaceChild`](https://developer.mozilla.org/en-US/docs/Web/API/Node/replaceChild), [`removeChild`](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild) e [`insertAdjacentHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML).

