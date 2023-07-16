# Llenguatge HTML

## Introducció

> El **llenguatge HTML (HyperText Markup Language)** és el llenguatge amb el qual s'escriuen les pàgines web.

L'any 1989 **Tim Berners-Lee** i **Anders Berglund**, dos investigadors del [CERN](https://ca.wikipedia.org/wiki/Organitzaci%C3%B3_Europea_per_a_la_Recerca_Nuclear), van crear un llenguatge  basat en etiquetes destinat a compartir informació per Internet: **HTML**.

Les pàgines web són vistes pels usuaris mitjançant un tipus d'aplicació anomenat **navegador**.

El llenguatge HTML està pensat per compartir documents de manera que es vegin de forma semblant en diferents navegadors.

Conseqüentment, el **llenguatge HTML** serveix al navegador per mostrar les pàgines a l'usuari.

**HTML** ha sofert molts canvis al llarg del temps.
  * La versió actual del llenguatge HTML és **HTML5**.

![logo html5](uf1_images/html5.png)

### Què és una pàgina web?

> Una **pàgina web** és un arxiu de text amb extensió *.html* o *.htm*

Pot ser creada amb el bloc de notes o programes Editors de codi HTML.

**HTML** és únicament text pla.

### Sintaxis HTML

El **llenguatge HTML** base la seva sintaxis en un element de base que anomenem **etiqueta**.

Una obertura de forma general `<etiqueta>` Un tancament de tipus `</etiqueta>` .

Tot el que estigui dintre d'aquesta etiqueta tindrà les modificacions que caracteritzen aquesta etiqueta.

```html
<b> Hola a tots. </b>
```

El resultat serà:

![](uf1_images/hola.png)

Però tot i que funciona, no és el que busquem, falta especificar molt millor les parts de la pàgina i la sintaxi de les etiquetes.

El llenguatge HTML té **número d'etiquetes limitat**.
* Cada etiqueta està pensada per representar documents d'una forma determinada o per marcar-ne l'estructura.

* Aquí hi trobaràs una llista d'**etiquetes vàlides**:

  * **HTML Element Reference:** [https://www.w3schools.com/TAGS/default.asp](https://www.w3schools.com/TAGS/default.asp)


## Creació de documents HTML

### L'etiqueta DOCTYPE

> Tot document **HTML5** ha de començar definint el **DOCTYPE**.

> L'etiqueta **DOCTYPE** serveix per indica al programa client (navegador) amb quina sintaxi s'ha creat la pàgina, és una sentencia que es posa al principi de tot de la pàgina.

El **DOCTYPE** s'ha de posar a la primera línia.

#### DOCTYPE en HTML4

**Estricte**:

`<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "<http://www.w3.org/TR/html4/strict.dtd>"> `

**Transicional**:

`<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "<http://www.w3.org/TR/html4/loose.dtd>">`

**Frames**:

`<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "<http://www.w3.org/TR/html4/frameset.dtd>">`

<!--
DOCTYPE XHTML 1.0

Estricte:

`<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "<http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd>">`

Transitional:
 
 `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "<http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd>">`
 -->

#### DOCTYPE HTML5

`<!DOCTYPE html>`

### L'etiqueta html

Un document HTML ha d'estar delimitat per l'etiqueta `<html>` i `</html>`.

Pot incloure l'atribut **lang**:
* **lang** ens permet definir l'idioma en el que està la pàgina
* Aquesta informació és important pels motors de cerca i els programes de síntesis de veu.

```html
<!DOCTYPE html>
<html lang="ca">

     ... 

</html>
```

### Parts d'un document HTML

Dins la pàgina HTML podem distingir-hi **dues parts**:

**L'encapçalament** 
* Flanquejat per les etiquetes `<head>` i `</head>` 
* Dóna informació sobre la pàgina.
* Col·locarem etiquetes de tipus informatiu, com per exemple el títol de la pàgina, autor, paraules clau.
* **No es mostra en el navegador.**

**El cos**
* Flanquejat per les etiquetes `<body>` i `</body>` 
* Col·locarem el nostre contingut de la pàgina.
* **És el que es veu realment.**

## Les metadades

L'etiqueta `<meta>` serveix per afegir informació sobre la pàgina i es posen dins el `<head>`.

Els buscadors consultes l'informació d'aquesta etiqueta per millorar la seva cerca i indexació.

Conté els atributs *name* i *content*

```html
<head>
  <meta charset="UTF-8">
  <meta name="description" content="Free Web tutorials">
  <meta name="keywords" content="HTML,CSS,XML,JavaScript">
  <meta name="author" content="John Doe">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

> És important definir el joc de caràcters utilitzat.

* El **joc de caràcters** determina la forma en què els caràcters es converteixen en bytes (i viceversa).
* El W3C recomana el charset **UTF-8**.

<!--
## Caràcters especials

En anglès entities, en català no se sol fer servir "entitats"
Una pàgina web es veu en diferents països que tenen diferents codificacions.

Exemples

* &nbsp; -> espai
* &gt; -> &gt;
* &lt; -> &lt;

```html
h&nbsp;o&nbsp;&nbsp;l&nbsp;&nbsp;a
```

 Tipus d'atributs

**Atributs bàsics**

La major part d'etiquetes tenen atributs ben vàlids, útils i de vegades imprescindibles.

**Atributs d'events**

S'utilitzen a les pàgines web dinàmiques, fetes amb *Javascript*, 

Per exemple: onclick, ondblclick, onmousedown, onmouseup, ...

**Atributs pels elements que poden obtenir el focus**

Per exemple `tabindex=3`, estableix la posició en l'ordre de tabulació de la pàgina

-->

### Pàgina HTML bàsica

```html
<!DOCTYPE html>
<html lang="ca">
     <head>
         <title>HTLM5</title>
         <meta charset="UTF-8">
     </head>
     <body>
          ...
     </body>
</html>

```

## Títols

HTML defineix **6 nivells de capçaleres o títols**.

```html
<h1>Títol 1</h1>
<h2>Títol 2</h2>
<h3>Títol 3</h3>
<h4>Títol 4</h4>
<h5>Títol 5</h5>
<h6>Títol 6</h6>
```

**Més informació**: w3schools HTML Headings [https://www.w3schools.com/html/html_headings.asp](https://www.w3schools.com/html/html_headings.asp)

## Paràgrafs

Per definir els **paràgrafs** utilitzem l'etiqueta `<p>`, la qual introdueix una línia en blanc després del paràgraf.

L'etiqueta `<br>` la qual no té tancament, ens serveix per fer un salt de línia, dins dels paràgrafs.

**Pregunta:** A dins de l'etiqueta `<p>` podem definir atributs a fi de justificar el text del paràgraf?

Aquí comencem amb els perills de les **coses mal fetes** però que sembla que funcionin...

![Forbidden](uf1_images/forbidden.jpg)

**Què no s'ha de fer**

Llegireu que hi ha atributs per alinear els paràgrafs, com `align`

* Text alineat a l'esquerre: `<p align="left"> Text left.</p>`

* Text alineat al centre: `<p align="center"> Text center </p>`

* Text alineat a la dreta: `<p align="right"> Text right </p>`

Antigament es feia servir però ara **no és correcte**, a vegades el camí més ràpid no és el millor.

**Coneixeu el CSS?**

Mireu l'exemple de l'*abadia del crimen*, per entendre que una cosa ben feta dura més, és més fàcil de mantenir i es pot millorar amb facilitat.

> Si comencem a fer codi brut, "espaguetti" o altres defectes, les pàgines esdevenen totalment **inmantenibles**.

En voleu més exemples? (en MAJÚSCULES EL QUE HEM D'EVITAR)

Podíem definir el **color**, **tamany** i **tipus** de lletra de diferents formes:

Mitjançant l'etiqueta `<FONT>` teníem els atributs:

* FACE: Defineix el tipus de lletra.
* SIZE: Defineix el tamany de la lletra.
* COLOR: Defineix el color del text de la lletra.

Amb Es definien dins de l'etiqueta `<body>`;

* ATRIBUTS
* BGCOLOR: Especifica el color de fons de la pàgina
* BACKGROUND: Serveix per indicar la col·locació d'una imatge com a fons de pàgina.
* COLOR DEL TEXT
* TEXT: Serveix per definir el color del text de la pàgina.
* LINK: El color del enllaços que no han estat visitats ( per defecte, és blau ) VLINK: El color dels enllaços visitats.

... i un llarg etcètera...

### L'etiqueta pre

> L'etiqueta `<pre>` defineix un paràgraf que respecte els codis propis del text pla (intros, número d'espais, etc.).

Adequat per fer textos literals, per exemple els poemes amb els seus salts de línia sense `<br>`.

[Exemple](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_pre)

## Etiquetes de text

Serveixen per indicar que un text concret té un significat especial.


* `<b></b>` (bold) o `<strong></strong>`: Text important (es mostra en negreta): 
* `<i></i>` (italic): es mostra en cursiva
* `<u></u>` (underlined): es mostra subratllat
* `<sub></sub>`: Subindex
* `<sup></sup>`: Superindex
* `<blockquote></blockquote>`: per cites (es mostra tabulat). [Exemple](https://www.w3schools.com/html/html_quotation_elements.asp)

> No són per donar format sinò per donar significat especial al text.
> **Sempre** hem de formatar el contingut mitjançant les **fulles d'estil (CSS)**.

> **MAI** fer servir *&lt;u&gt;* per subratllar. Dóna lloc a equivocacions per l'usuari, que es pot pensar que és un link (enllaç).

## Llistes

> Les **llistes** serveixen per enumerar i definir elements. 

Podem distingir **tres tipus** de llistes:

* Llistes desordenades
* Llistes ordenades
* Llistes de definició

**Més informació**: [w3schools.com: HTML Lists](https://www.w3schools.com/html/html_lists.asp)

### Llistes sense ordre (Unordered Lists)

Definides per les etiquetes `<ul>` i `</ul>` (**u**nordered **l**ist). 

Cada element de la llista queda enmarcat per l'etiqueta `<li>` (**l**ist **i**tem).

```html
<p> Països del mon </p>
<ul>
    <li> Argentina </li>
    <li> Perú </li>
</ul>
```

[Exemple de llista sense ordre](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_unordered)


![Forbidden](uf1_images/forbidden.jpg)

L'atribut `type` ens serveix per definir el tipus de vinyeta. 

`<ul TYPE="tipus vinyeta">`

On ***tipus vinyeta*** pot ser: `circle`, `disc`, `square` o `none`.

> Recordeu que això s'ha de fer **CSS**.


### Llistes ordenades (Ordered Lists)


Definides per les etiquetes `<ol>` i `</ol>` (**o**rdered **l**ist).
Cada element de la llista queda enmarcat per l'etiqueta `<li>` (**l**ist **i**tem)

```html
<p> Països del mon </p>
<ol>
    <li> Argentina </li>
    <li> Perú </li>
</ol>
```

[Exemple de llista ordenada](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_ordered)

![Forbidden](uf1_images/forbidden.jpg)

L'atribut **TYPE** ens serveix per definir el tipus de numeració que utilitzarem.

* `1` per ordenar amb nombres
* `a` per lletra de l'alfabet
* `A` per lletres majúscules de l'alfabet
* `i` per ordenar amb xifres romanes
* `I` per ordenar amb xifres romanes majúscules

### Llistes de definició (Definition Lists)

> Cada element és presentat juntament amb la seva definició.
  
* Definides per les etiquetes `<dl>` i `</dl>`   (**d**efinition **l**ist).
* Les etiquetes de cada element són `<dt>` (**d**efinition **t**erm) i la seva definició `<dd>` (**d**efinition **d**efinition).

```html
<dl>
      <dt>Casa</dt>
      <dd>Lloc on habitar</dd>

      <dt>Llar</dt>
      <dd>Lloc on viure</dd>
</dl>
```

[Exemple de llista de definició](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_description)

### Aniuar les llistes

Podem **aniuar** llistes, fins i tot de diferents tipus de llista:

```html
<p>Ciutats del mon</p>
<ul>
    <li>
    Argentina
        <ol>
           <li>Buenos Aires</li>
           <li>Bariloche</li>
        </ol>
    </li>
    <li>
    Uruguay
    <ol>
       <li>Montevideo</li>
       <li>Punta del Este</li>
    </ol>
    </li>
</ul>
```

[Exemple de llista aniuada](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_nested)

## Enllaços

> Els **enllaços** sorgeixen de la necessitat de que les pàgines HTML estiguin interconnectades (hypertext).

* Per col·locar un enllaç utlitzarem les etiquetes `<a>` i `</a>` .
* L'atribut `href`, ens indica el destí d'aquest enllaç.

```html
<a href="destí"> contingut </a>
```

Essent *contingut* un text o una imatge i destí un arxiu, un correu electrònic o una pàgina.

Els enllaços es poden classificar de la següent manera:

* **Enllaços interns:** els que es dirigeixen a diferents llocs de la mateixa pàgina.
* **Enllaços locals:** els dirigeixen a un altre pàgina dintre de la mateixa web.
* **Enllaços remots:** els dirigits cap a altres pàgines web.
* **Enllaços amb direccions de correu:** per crear un missatge de correu dirigit a una direcció.
* **Enllaços amb arxius:** perquè els usuaris puguin descarregar arxius.

### Enllaços interns

> Són **enllaços** que apunten a un lloc diferent dins de la mateixa pàgina.

Per crear un enllaç d'aquest tipus és necessari a part de l'enllaç de l'origen, col·locar un **enllaç al destí**.

**Exemple**:

```html
Enllaç origen: <a href="#avall"> Anar al final </a>

Enllaç destí: <a id="avall"> </a>
```

[Exemple d'enllaç intern](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_links_bookmark)

**No utilitzar-los molt**, és millor fer pàgines més petites ja que llavors tarden menys a carregar-se i són més fàcils de llegir.

### Enllaços locals

Un lloc web està constituit de pàgines interconnectades.

```html
<a href="arxiu.html"> Arxiu </a>
```

Per regla general, un lloc web ha d'estar ordenat per directoris.
S'ha d'utilitzar la "/" per especificar on es troben les coses. 

* Els **enllaços locals** també poden apuntar a una secció en concret dintre d'un altre pàgina.

   ```html
   <a href="arxiu.html#seccio"> Arxiu </a>
   ```

* La pàgina **arxiu.html** ha de contenir la marca referent a la secció.

   ```html
   <a id"seccio"> </a>
   ```

### Enllaços externs

> Són enllaços dirigits cap a **altres llocs web**.

A l'atribut `href` i col·loquem la **URL** o direcció de la pàgina amb la que es vol enllaçar.

Totes les direccions van precedides de `http://`

```html
<a href="http://www.elmundodeportivo.es"> Anar a El Mundo deportivo </a>
```

### Enllaços a direccions de correu

Ens obren una nova finestra de correu electrònic per enviar a una direcció de correu determinat.

A l'atribut `href` i col·loquem la paraula `mailto:` seguit de la direcció de correu.

```html
<a href="mailto:pep@hotmail.com"> Contactar amb en Pep </a>
```

* Per tal de configurar altres paràmetres del correu electrònic s'afegeix un interrogant després de la direcció de correu.
* No és recomenable posar enllaços a correus, pel tema dels robots i l'SPAM.

### Enllaços a arxius


El mecanisme és el mateix que hem vist en els enllaços remots i locals.

En comptes d'indicar la direcció web el que hem de fer és indicar el **nom del fitxer** (i en cas que sigui necessari la **ruta**).

```html
<a href="fitxer.pdf"> Descarregar el fitxer </a>
```

## Imatges

> L'aspecte més vistós i atractiu d'una pàgina web és el grafisme. 

Les **imatges** són emmagatzemades en forma d'arxius, principalment **GIF/PNG** (per imatges) i **JPG** (per fotos).

L'etiqueta que utilitzem per insertar una imatge és `<img>`, **no cal fer el tancament**.

Mitjançant l'atribut `src`  (***source***), especifiquem el lloc (URL) on es troba la imatge.

```html
<img src="img_girl.jpg" alt="Girl in a jacket">
``` 

Si la imatge es troba en una carpeta diferents que la pàgina HTML:

```html
<img src="/images/img_girl.jpg" alt="Girl in a jacket">
``` 

[Exemple d'imatge](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_images_girl)

### Atributs de l'etiqueta `<img>`

* **Alt:** Breu descripció de l'imatge. És **obligatori** per tal que el document HTLM sigui validat correctament.

* **Height** i **Width**: Defineixen l'altura i amplada de les imatges en pixels.

Altres **coses mal fetes**:

![Forbidden](uf1_images/forbidden.jpg)

* **BORDER**: Defineix el tamany en pixels del quadrat que rodeja l'imatge.
* **LOWSRC**: Quant tenim activada aquesta opció primer es descarrega la imatge amb una baixa resolució i va millorant a mesura que es va descarregant.

### Tipus d'arxius per les imatges

PNG ( per dibuixos ) JPG ( per fotos ).

Els dos formats comprimeixen les imatges per guardar-les.

**GIF** - Arxiu ideal per imatges que estan dibuixades.

* **Compresió**: És molt bona per dibuixos.
* **Transparència**: És una utilitat per definir algunes parts de la imatge com a transparents.
* **Colors**: Es poden utilitzar paletes, conjunts de 256 o menys. Quant menys colors utilitzem menys tamany ocuparà l'imatge.

Actualment s'està utilitzant un format **PNG** que té les mateixes prestacions que el GIF (transparència i animació) i a més a més incorpora **color real**, 48 bits per píxel i compresió sense pèrdua.

**JPG**

* **Compresió**: El seu algorisme de compressió és ideal per guardar fotos.
* **Transparència**: Aquest format no té possiblitats de crear arees transparents.
* **Colors**: Treballa sempre amb 16 milions de colors.

### Optimitzar els fitxers d'imatge

Hem de procurar de no posar imatges de tamany més gran que el que s'ha de visualitzar
* Per exemple si té 200x200 la imatge màxima no  té sentit posar-hi una imatge a descarregar de més de 1000x1000 píxels!

**Arxius GIF**

* Reduïm el numero de colors de la paleta.

**Arxius JPG**

* Ajustem la qualitat i la mida de l'arxiu quant l'estem guardant.
* És impresindible disposar d'un bon editor fotogràfic a fi d'optimitzar una imatge: **GIMP**

## Taules

> Una **taula** és un conjunt de cel·les organitzades dintre de les quals podem col·locar diferents continguts.

L'etiqueta per definir les taules és: `<table>` `</table>`

Les taules són descrites per línies d'esquerra a dreta, mitjançant
*&lt;tr&gt; &lt;/tr&gt;*

```html
<table>
    <tr>
        <td> Cel.la1-fila1 </td>
        <td> Cel.la2-fila1 </td>
        <td> Cel.la3-fila1 </td>
    </tr>
    <tr>
        <td> Cel.la1-fila2 </td>
        <td> Cel.la2-fila2 </td>
        <td> Cel.la3-fila2 </td>        
    </tr>
</table>
```

![](uf1_images/taula1.png)

Com es pot veure així no es veu massa clar que hi hagi una taula...

si afegim un atribut `border="1"` ho veurem més clar:

```html
<table border="1">
    ...
</table>
```

![Forbidden](uf1_images/forbidden.jpg)

**ATRIBUTS PER FILES I CEL·LES no vàlids**

* **Align**: Justifica el text de la cel·la
* **Valign**: Podem escollir si el text apareix a dalt (top), a baix  (bottom) o al mig (middle) de la cel.la.
* **Bgcolor**: Donar color a la cel·la o la fila escollida.
* **Bordercolor**: Defineix el color del marc.

**ATRIBUTS PER CEL.LES no vàlids**

* **Background**: Ens permet col·locar de fons una imatge en una cel·la.
* **Height**: Defineix l'altura de la cel·la en pixels o percentatge.
* **Width**: Defineix l'amplada de la cel·la en pixels o percentatge.
* **Align**: Alinea la taula respecte al seu entorn
* **Background**: Ens permet col·locar un fons per la taula a partir d'una imatge.
* **Bgcolor**: Color de fons de la taula.
* **Border**: Defineix el tamany del marc.
* **Bordercolor**: Defineix el color del marc.
* **Cellpadding**: Defineix en pixels l'espai entre les cel·les dela taula i el seu contingut.
* **Cellspacing**: Defineix l'espai entre els marcs (en pixels)
* **Height**: Defineix l'altura de la taula en pixels o percentatge.
* **Width**: Defineix l'amplada de la taula en pixels o percentatge.

**Atributs de taula vàlids**

* **Colspan:**: Expandeix una cel·la horitzontalment.
* **Rowspan:**: Expandeix una cel·la verticalment.

També es poden utilitzar taules anidades.

## Frames

### Atribut target

Atribut `target` a enllaços:   s'utilitza per decidir on es s'obrirà l'enllaç, pot ser:

* **\_blank**: nova finestra.
* **\_top**: finestra.
* **\_self**:(per defecte) en el frame actual.
* **\_parent**: es carrega al frame "pare", el que era havia cridat l'actual.
* **\-** o també un nom de **frame** (definit amb l'atribut name).

```html
<a href="nom-pagina-a-carregar.html" target="nom-del-marc-a-carregar">
```
![Forbidden](uf1_images/forbidden.jpg)

* Estan **obsolets** per l'HTML5, però eren vàlids per altres versions.
* Té l'interès "històric" de saber com es feien abans les pàgines web, el CSS actualment les millora molt.
* Antigament els ***layouts*** una mica complexes es feien o bé amb taules o bé amb frames. Les dues coses estan en desús avui en dia.
*  Podria interessar saber-los fer per actualitzar alguna pàgina web antiga.

**Doctypes de 4.01 o de XHTML, amb FRAMESET**

* Html 4.01:
  ```html
  <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "<http://www.w3.org/TR/html4/frameset.dtd>">
  ```

* Xhtml:
  ```html
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "<http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd>">
  ```

L'**estructura de la pàgina** també es veu modificada. No té `<body>`, té `<frameset>`

```html
<HTML>
<HEAD>
    <TITLE> Mi titulo ></TITLE>
</HEAD>

    <FRAMESET>
        <NOFRAMES>
            <BODY>
                Su visualizador no soporta frames. Pulse 
                <A HREF="indice.htm">aquí</A> para volver.
            </BODY>
        </NOFRAMES>

        <FRAME SRC="pagina1.htm" >
        <FRAME SRC="pagina2.htm" >
    </FRAMESET>

</HTML>
```

### Per què no s'utilitzen els frames


* Els **motors de cerca** tenen problemes per indexar-los.
* Ocupen **espai** a la pantalla.
* No es poden utilitzar les funcionalitats d'anar endavant o endarrere a l'**historial** de navegació.
* Tenen problemes d'**usabilitat i accessibilitat** web per persones invidents.

### Etiquetes

**frameset**: l'atribut `cols` o `rows` defineix el percentatge total de la pantalla que ocuparà cada secció. 
  * És interessant que alguna secció tingui \*     perquè el navegador calculi de forma automática l'ampada o l'alçada que ha de tenir.

**frame**: hi ha tants frames com blocs s'hagin indicat a l'etiqueta frameset.
* L'atribut `<src>` fa referència a la url de la pàgina volem que es carregui. 
* L'atribut `<name>` indica el nom del frame per ser utilitzat amb *targets*

### Exemples

Anem a veure diferents dissenys de frames

**3 àrees verticals**


![image](uf1_images/frames1.png)

```html
<FRAMESET COLS=30%,20%,50%>
   <FRAME SRC="a.htm">
   <FRAME SRC="b.htm">
   <FRAME SRC="c.htm">
</FRAMESET>
```

**3 àrees horitzontals**

![image](uf1_images/frames2.png)

```html
<FRAMESET ROWS=25%,25%,50%>
   <FRAME SRC="a.htm">
   <FRAME SRC="b.htm">
   <FRAME SRC="c.htm">
</FRAMESET>
```

<!--

**combinat 2 àrees vertical amb 2 horitzontals**


![image](frames3.png)

```html
<FRAMESET COLS=20%,*>
     <FRAME SRC="a.htm">
         <FRAMESET ROWS=40%,*>
              <FRAME SRC="b.htm">
              <FRAME SRC="c.htm">
        </FRAMESET>
</FRAMESET>
```

**combinat 2 àrees horitzontals amb 2 verticals**

![image](frames4.png)

```html
<FRAMESET ROWS=50%,*>
   <FRAME SRC="a.htm">
   <FRAMESET COLS=50%,*>
       <FRAME SRC="b.htm">
               <FRAME SRC="c.htm">  
       </FRAMESET>
    </FRAMESET>
```
-->

<!--
### Xuletes ràpides de frames

![image](xuleta-html-framesets.png)
-->

## Iframes

> El frame que ha sobreviscut a l'HTML5 és l'**iframe**.

Un `iframe` s'utilitza per mostrar una web dins una altra pàgina web.

```html
<iframe src="index.htm" 
     width="300" height="100" 
     frameborder="1" 
     scrolling="Auto">
 </iframe> 
```
<!--
Es poden veure coses que semblarins pròpies del CSS, però que en el cas
dels *iframe* podrem utilitzar.
-->

Apareixen **barres d'scroll** en el frame si la pàgina és més gran que l'espai dissenyat.

[Exemple de iFrame](https://www.w3schools.com/html/html_iframe.asp)

## Formularis

* [Creació de formularis](https://docs.google.com/presentation/d/1fZ1F4p_dvXShnL7GVNHEygFBxDvgslEW9AuTi4rE5f4/edit?usp=sharing) 
  

* Validació de camps:
<https://lenguajehtml.com/p/html/formularios/validaciones-html5>


## Accesibilitat

* [HTML: Una buena base para la accesibilidad](https://developer.mozilla.org/es/docs/Learn/Accessibility/HTML)


## Documentació i recursos

* [Vídeo Història d'Internet](https://www.youtube.com/watch?v=h8K49dD52WA)