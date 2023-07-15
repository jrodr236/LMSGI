# Getters i setters

Utilitza **getters** (accessors) per obtenir valors d'un objecte i **setters** (mutadors) per definir el valor d'una propietat dins d'un objecte:

## Getters

Les funcions **getter** estan destinades a retornar (get) el valor de la variable privada d'un objecte a l'usuari sense que l'usuari accedeixi directament a la variable privada.

## Setters

Les funcions **setter** estan destinades a modificar (set) el valor de la variable privada dun objecte basat en el valor passat a la funció setter. Aquest canvi podria implicar càlculs, o fins i tot sobreescriure completament el valor anterior.

```javascript
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer() {
    return this._author;
  }
  // setter
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}
const novel = new Book('anonymous');
console.log(novel.writer);
novel.writer = 'newAuthor';
console.log(novel.writer);

//La consola mostrarà les cadenes anonymous i newAuthor.
```

Tingues en compte la sintaxi usada per invocar el getter i el setter. Ni tan sols es veuen com a funcions. Els getter i els setter són importants perquè amaguen els detalls interns de la implementació.

{% hint style="info" %}
**Nota**: És convenció precedir el nom d'una variable privada amb un guió baix (\_). Tot i això, la pràctica en si mateixa **no fa una variable privada**.
{% endhint %}
