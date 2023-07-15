# XML


## XML (Extensible Markup Language)

> **XML** és un llenguatge de descripció d'informació.

* XML és un format de text estandarditzat que serveix per representar i transportar informació estructurada.

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

Una de les idees més importants és:

> Separar les dades de la presentació

  * XML no es preocupa de com es presentaran les dades als usuaris
  * Per fer la presentació ja s'han desenvolupat mecanismes:
    *  **CSS**, **XSL-FO**, etc.


---
* Antigament per representar dades es feia separant els valors amb comes o algun altre símbol

```
"Nom","Cognom","Ofici","Naixament","Poblacio","Punts"
"Pere","Pi","Professor","10/04/1978","Olot",12
"Marta","Mata","Inforàtica","19/05/1990","Girona",20
```

* S'ha de saber que la primera línia són metadades
* Afegir-hi noves dades pot ser molt problemàtic pel programa que les llegeixi --&gt; Probablement haurem de canviar el programa
* El format **CSV (Comma separated value)** encara s'utilitza molt en el món de la informàtica, per exportar/importar dades normalment.
   * Es tracta d'enviar la informació utilitzant un caràcter per a separar cada un dels conceptes. Tot i que el nom pugui suggerir que sigui una coma, molts sistemes deixen definir el caràcter a utilitzar (punt i coma, salt de línia,...)
---


## Característiques dels llenguatges de marques

* Els llenguatges de marques estan **basats en text**.
   * Poden ser **creats i editats** amb qualsevol editor de textos.

* Són fàcilment transportables.
  * La utilització de sistemes de codificació estàndards (UNICODE), fa els documents **fàcilment transportables** entre diferents sistemes (Linux, Windows,etc).

* Però no estan pensats per ser llegits per una persona.

* A diferència d'HTML si que es pot determinar de forma **automàtica** què **signifiquen** les dades.

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
  * Quina informació conté el fitxer?
  * Quina és l'estructura de la informació?
  * Quines etiquetes s'han creat per descriure'n la informació?

## Extensible

Un altre dels avantatges de XML és que es fàcilment **extensible i adaptable**:

> XML **no defineix un nombre limitat d'etiquetes**.
 
Podem crear les etiquetes (tags) que tinguin significat per nosaltres.
Podem crear el vocabulari que ens faci falta per allò que busquem.

A més, hi ha formes de definir quina és la **estructura** que nosaltres definim.
  * Hi ha diversos estàndards ***DTD***, ***XML Schema Language***, ***Relax NG***, etc..
  * Ens serviran per comprovar que el document compleix amb les normes del vocabulari.

## Formats Estàndards

Tenim la capacitat de crear un vocabulari per representar dades d'un àmbit.

Ja hi ha vocabularis estàndards XML:

* **SVG**: Pensat per gràfics vectorials escalables 2D
* **MathML**: Representació de fórmules matemàtiques
* **CML**: Intercanvi d'informació química
* **SMIL**: Tractament de la informació multimèdia
* **SSML**: Síntesi de la veu

## Principals usos d'XML 

XML s'està fent servir en múltiples camps:

* Un dels estàndards que es fan servir en pàgines web XHTML està basat en XML.
* Desenvolupament de **documentació tècnica** en diferents àmbits acadèmics, investigació, ...
* Intercanvi d'informació entre sistemes informàtics (distribuïts). 
* Intercanvi d'informació entre empreses.
* Aplicacions ofimàtiques: **Microsoft Office, OpenOffice**, ..
  * Abans feien servir formats binaris però han passat a algun tipus d'XML.
  * Va passar de guardar els documents en binari `.DOC` a XML `.DOCX` (OOXML).
* Molts dels **documents de configuració** dels sistemes operatius estan en XML:

  **Linux**

  ```bash
  $ locate .xml | wc -l
  21829
  ```

  **Windows**
  ```bash
  C:\> dir /a-d /s *.xml | find /c /v “”
  698
  ```

## Desavantatges de XML

* Els fitxers XML tendeixen a ocupar molt d'espai.
  * XML ocupa més espai a disc que els seus equivalents en format binari. 
  * Lentitud en el temps de càrrega.
  * Temps de transferència més elevat.

Però això a vegades és compensat per:

* La facilitat d'interoperabilitat entre programes.
* El preu de l'emmagatzematge és baix.

## Versions

* El febrer de 1998 es llença l'especificació **1.0 d'XML**: <http://www.w3.org/TR/2004/REC-xml-20040204/>

* L'ultima especificació d'**XML és la 1.1** que va sortir el 2004: <http://www.w3.org/TR/xml11/>

* Però d'alguna manera s'ha millorat la 1.0 en posterioritat (2008): <https://www.w3.org/TR/2008/REC-xml-20081126/>

* Totes les especificacions es revisen periòdicament: <https://www.w3.org/standards/techs/xml#w3c_all>

