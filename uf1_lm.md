# Llenguatges de marques

## Compartició d'informació

Les empreses necessiten **compartir** la informació entre elles (factures, comandes, etc).

La informació pot estar en **diversos formats** (fulles de càlcul, bases de dades, fitxer pdf, etc.).

**Problema:**

La informació **no està estructurada**.

Fa difícil l'**automatització** d'aquesta informació amb un sistema informàtic.

**Solució:**

**Acordar quin format** o estructura ha tenir la informació.

A més, podrem utilitzar **eines estàndards per validar** si el document compleix amb l'especificació acordada.

## Els llenguatges de marques

Un **llenguatge de marques** combina dades i etiquetes que les marquen i que contenen informació addicional sobre l'estructura del text o la seva presentació.

Les marques estan barrejades amb el propi text.

```xml
<persona>
    <nom>
        Sergi
    </nom>
    <cognom>
        Coll
    </cognom>
</persona>
```

Tot i que els sistemes de marques en que ens concentrarem són els d'estil web cal no oblidar que n'hi ha d'altres, com: Wikitext, TeX, DocBook, RTF, JSON

### Exemple Wikitext
```
You can ''italicize'' text by putting 2 
apostrophes on ''each'' side. 

3 apostrophes will '''bold''' the text. 

You can put formatting around a link.
Example: ''[[Wikipedia]]''
```

### Exemple JSON

```json
{
    "persona": {
        "nom": "Sergi",
        "cognom": "Coll"
    }
}
```

### Exemple yaml

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 10.10.10.2/24
      nameservers:
        search:
          - "mycompany.local"
        addresses:
          - 10.10.10.253
          - 8.8.8.8
```

### Exemple HTML

El llenguatge de marques més conegut és l'**HTML**, el de les pàgines web.

```html
<html>
    <head>
    <title>Pàgina</title>
    </head>
    <body>
        Hola!
    </body>
</html>
```


## Característiques dels llenguatges de marques

Els llenguatges de marques estan **basats en text**. Poden ser **creats i editats** amb qualsevol editor de textos.

Són fàcilment transportables. La utilització de sistemes de codificació estàndards (UNICODE), fa els documents **fàcilment transportables** entre diferents sistemes (Linux, Windows,etc).

Però no estan pensats per ser llegits per una persona.

La majoria permeten determinar de forma **automàtica** què **signifiquen** les dades (HTML no).

**Per exemple:**

**HTML**
```html
<html>
   <head><title>Professors</title></head>
   <body>
     <p>Pere Pi</p>
     <p>Marta Mata</p>
    <body>
</html>
```

**XML**
```xml
<professors>
  <professor>
    <nom>Pere</nom>
    <cognom>Pi</cognom>
  </professor>
  <professor>
    <nom>Marta</nom>
    <cognom>Mata</cognom>
  </professor>
</professors>
```

Es pot determinar automàticament:
* Quina informació conté el fitxer,
* Quina és l'estructura de la informació.
* Quines etiquetes s'han creat per descriure'n la informació.



## SGML

> La primera tecnologia estandarditzada de llenguatges de marques va ser l'**SGML**

Es va fer servir com estàndard de la informació **de propòsit general**.
Partia de la idea de que s'han de **separar les dades** d'un document **de la seva forma**.

Però:
* La majoria dels documents estaven destinats a la **impressió**.
* Era terriblement **complex** de manera que només el feien servir els especialistes.


## HTML

L'any 1989 Tim Berners-Lee i Anders Berglund van crear un llenguatge basat en etiquetes destinat a compartir informació per Internet: **HTML**.

HTML és un format que descriu la visualització d'una pàgina web.
  
La web s'ha fet cada vegada més i més popular:
* Cada dia es generen milions de pàgines web amb informació.
* Això implica que cal buscar per trobar la informació que ens interessa.

```html
<html>
   <head>
     <title>Professor</title>
   </head>
   <body>
      <p>Nom: Federicu Pi </p>
   </body>
</html>
```

En aquest exemple, una màquina no pot determinar automàticament qué és el nom, què és el cognom...

És necessari alguna forma de poder fer-hi recerques intel·ligents i seleccionar-ne el resultats.

En general, falta una forma de:

* **Buscar**, **moure**, **visualitzar** i **manipular** la informació continguda en els documents HTML.

### Naixement de l'XML

El consorci **W3C** va desenvolupar una alternativa a l'HTML que podés satisfer les necessitats futures del web.

El 1996 el consorci W3C es va proposar introduir el poder i la flexibilitat de l'**SGML** al web.

**SGML** oferia tres avantatges que l'HTML no tenia:

* Extensibilitat
* Estructura
* Validació

D'aquesta manera va néixer l'**XML**.