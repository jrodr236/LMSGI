# JSON

JSON \(**J**ava **S**cript **O**bject **N**otacion**\)** és un format per emmagatzemar i intercanviar dades.

**JSON** és text, escrit amb sintaxi de JavaScript aprofitant l'ús dels objectes JavaScript.

Va néixer com a alternativa al **XML**.

S’utilitza molt per enviar informació des del servidor a una pàgina web.

Actualment està superant l'ús del **XML** en aplicacions web, gràcies a la **facilitat**, **portabilitat** i **llegibilitat.**

 L'**extensió** dels fitxers JSON és **`.json`**.

![json logo](https://i0.wp.com/dbaontap.com/wp-content/uploads/2015/11/json-logo.png?resize=300%2C143&ssl=1)

A JSON existeixen dos tipus d'elements: objectes i arrays.

## **Objectes**

Els objectes s'escriuen com a parelles de **`nom`** i **`valor`**.

Per **assignar** valor s'utilitza els dos punts \( **`:`** \)

**Exemple:**

```json
{ "name": "John" } 
```

> ⚠️ Els noms JSON requereixen **cometes dobles.**

Les dades se separen per comes \( **`,`** \)

**Exemple:**

```json
{
  "name" : "John",
  "surname" : "Smith"
} 
```

Els espais en blanc i salts de línia no són significatius.

**Exemple:**

```json
{ "name" : "John" , "surname" : "Smith" } 
```

## Arrays

Un **array** es una llista (col·lecció ordenada) de valors.

Els arrays s'envolten de **claudàtors `[ ]`** i cada valor de dins va separat per una coma \( **`,`** \).

**Exemple:**

```json
{
    "name":"John",
    "age":30,
    "cars": [ "Ford", "BMW", "Fiat" ]
}
```

Un valor d'un array també potser un objecte **JSON**.

**Exemple**:

```json
{"students": 
    [
        {"firstName":"Tom" , "lastName":"Jackson"} ,
        {"firstName":"Linda" , "lastName":"Garner"} ,
        {"firstName":"Adam" , "lastName":"Cooper"}
    ]
}
```

### Arrays anidats

Els valors d'un **array** també poden ser **altres arrays**:

**Exemple:**

```json
{
  "name":"John",
  "age":30,
  "cars": [
    { "name":"Ford", "models":[ "Fiesta", "Focus", "Mustang" ] },
    { "name":"BMW", "models":[ "320", "X3", "X5" ] },
    { "name":"Fiat", "models":[ "500", "Panda" ] }
  ]
 }
```

## Comparació de JSON i XML

Els següents exemples JSON i XML defineixen un objecte d'empleats, amb una matriu de 3 empleats:

#### Exemple JSON 

```json
{"employees":[
  { "firstName":"John", "lastName":"Doe" },
  { "firstName":"Anna", "lastName":"Smith" },
  { "firstName":"Peter", "lastName":"Jones" }
]}
```

#### Exemple XML

```xml
<employees>
  <employee>
    <firstName>John</firstName>
    <lastName>Doe</lastName>
  </employee>
  <employee>
    <firstName>Anna</firstName>
    <lastName>Smith</lastName>
  </employee>
  <employee>
    <firstName>Peter</firstName>
    <lastName>Jones</lastName>
  </employee>
</employees>
```

#### Similituds

Tant JSON com XML:

* Són "**autodescriptibles**" \(llegibles per humans\)
* Són **jeràrquics** \(valors dins dels valors\)
* Es poden analitzar i utilitzar en molts llenguatges de programació.

#### Avantatges de JSON

* No utilitza **etiquetes de tancament**.
* És més **curt**. Ocupa menys espai i es transfereix més ràpidament.
* És més ràpid de llegir i escriure.

## Validació

Podem comprovar la validesa d'un fitxer JSON amb eines on-line com per exemple:

* [JSONFormatter](https://jsonformatter.curiousconcept.com/)
* [JSONViewer](http://jsonviewer.stack.hu/)
* [JSONLint](https://jsonlint.com/)

Tot i que hi han editors o IDEs que, directament o afegint plugins, també ens permeten fer aquesta validació.

Però si, a més, ens volem assegurar que compleix una determinada estructura, podem fer servir:
* [JSON Schema](https://json-schema.org/)