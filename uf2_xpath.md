# XPATH


## Introducció

-   XPath és una forma d'especificar parts d'un document XML

-   XPath s'assembla molt als llenguatges de programació: Té
    expressions, funcions, ...

-   XPath és un estàndard del W3C: http://www.w3.org/TR/xpath

-   XPath no fa servir XML

-   Fa servir expressions de camí per identificar les parts del document

-   El resultat de l'avaluació d'una expressió XPath serà:

    -   Un grup de nodes
    -   Un booleà: cert / fals
    -   Un número
    -   Una cadena de caràcters

-   Totes les expressions s'avaluen en un context concret

-   XPath és un component bàsic per altres components XML:

.. image:: tecnologiesXml.png

## Arbre XPath

-   Des d'un punt de vista de les dades XPath tracta les dades d'un XML
    com si estesin representades en un arbre

-   En aquest arbre hi ha dades de 7 tipus:

    -   Arrel
    -   Elements
    -   Nodes de text
    -   Nodes atribut
    -   Nodes de comentaris
    -   Nodes d'instruccions de procés
    -   Nodes d'espai de noms

## Arbre XPath

Si tenim aquest document:

.. code-block:: xml

    <?xml version=”1.0” ?>
    <classe>
     <assignatura>XML</assignatura>
     <professor Especialitat=”507”>
     <nom>Xavier</nom>
     <cognoms>Sala</cognoms>
     </professor>
     <alumnes>
     <alumne>
     <nom>Federicu</nom>
     <cognoms>Pi</cognoms>
     </alumne>
     <alumne>
     <nom>Filomenu</nom>
     <cognoms>Garcia</cognoms>
     </alumne>
     </alumnes>
    </classe>

.. image:: arbreXpath.png

## Navegació

-   Amb XPath podem navegar a través de la seva estructura com en un
    directori Unix

.. code-block:: bash

    /classe/alumnes/alumne/nom

.. image:: arbreXpath2.png

### Navegació absoluta i relativa

De la mateixa forma que en Unix podem fer servir la navegació amb:

-   Camins absoluts:
    -   Sempre començaran des de l'arrel
-   Camins relatius
    -   Començaran des del que es coneix com a "Context node"

    -   Per defecte el "context node" és l'arrel

    -   A mesura que es van avaluant les expressions el "Context node"
        va movent-se per l'arbre

    -   Com en Unix el "context node" es representa amb un punt "."
-   Per tant podem fer referència a qualsevol dels elements
    especificant-ne el camí

## Exemple Navegació

.. image:: navegacioXpath.png

### Pregunta

.. code-block:: bash

    /classe/professor/nom

### Resultat

.. code-block:: xml

    <nom>
     Xavier
    </nom>

### Pregunta

.. code-block:: bash

    /professor/nom

### Resultat

.. code-block:: bash

    CAP

## Expressió de camí

.. image:: expressioCami.png

## Operador Qualsevol lloc ( // )

-   També podem fer servir "//"

-   Per indicar "qualsevol lloc"

### Pregunta

.. code-block:: bash

    //nom

.. image:: arbreXpath.png

### Resultat

.. code-block:: xml

    <nom>Xavier</nom>
    <nom>Federicu</nom>
    <nom>Filomenu</nom>

### Pregunta

.. code-block:: bash

    /classe//nom

.. image:: arbreXpath.png

### Resultat

.. code-block:: xml

    <nom>Xavier</nom>
    <nom>Federicu</nom>
    <nom>Filomenu</nom>

## Nodes específics ( \[n\] )

-   Podem seleccionar nodes específics amb els corxets i la seva posició

### Pregunta

.. code-block:: bash

    /classe/alumnes/alumne[1]

Resultat

.. code-block:: xml

    <alumne>
        <nom>Federicu</nom>
        <cognoms>Pi</cognoms>
    </alumne>

### Pregunta

.. code-block:: bash

    /classe/alumnes/alumne[2]/nom

.. image:: arbreXpath.png

### Resultat

    <nom>Filomenu</nom>

## Posicions

-   Podem accedir als índexs dels nodes finals amb **last()** o
    **first()**

.. code-block:: bash

    /classe/alumnes/alumne[last()]

.. code-block:: xml

    <alumne>
        <nom>Filomenu</nom>
        <cognoms>Garcia</cognoms>
    </alumne>

-   També podem obtenir la posició relativa amb **position()**

.. code-block:: bash

    /classe/alumnes/alumne[position()=1]

## Tots els elements ( \* )

-   L'asterisc es fa servir per indicar tots els elements d'un
    determinat nivell

.. code-block:: bash

    /classe/alumnes/alumne[2]/*

.. code-block:: xml

    <nom>Filomenu</nom>
    <cognoms>Garcia</cognoms>

.. code-block:: xml

    /classe/alumnes/\*/nom

.. code-block:: xml

    <nom>Federicu</nom>
    <nom>Filomenu</nom>

## Atributs

Amb @ es poden seleccionar elements que:

-   Tinguin un atribut determinat

.. code-block:: bash

    /classe/professor[@Especialitat]

-   No tinguin un atribut concret

.. code-block:: bash

    /classe/professor[not(@Especialitat)]

-   Els atributs tinguin un determinat valor

.. code-block:: bash

    /classe/professor[@Especialitat=”507”]

-   Elements que tinguin atributs o no en tinguin

.. code-block:: bash

    /classe/professor[(@*)]
    /classe/professor[not(@*)]

## Text

-   El contingut de text d'un node es pot obtenir amb la funció:
    **text()**

### Pregunta

.. code-block:: bash

    /classe/alumnes/alumne[2]/nom/text()

### Resultat

Filomenu

-   Sempre que el node tingui text el podem obtenir

### Pregunta

.. code-block:: bash

    //assignatura/text()

.. image:: arbreXpath.png

### Resultat

.. code-block:: xml

    XML

## Eixos XPath

.. image:: eixos.png

-   En XPath sempre podem fer referència a les direccions:

**self::** Apunta al node en que estem

**child::** Fill del node en el que estem

**parent::** Pare del node en el que estem

**descendant::** Tots els descendents del node

**descendant-or-self::** Els descendents incloent el node actual

**ancestor::** Ascendents del node

**ancestor-or-self::** Ascendents del node incloent l'actual

**preceding::** Elements precedents al node actual

**preceding-sibling::** Germans precedents

**following::** Elements que segueixen el node actual

**following-sibling::** Germans posteriors

## Eixos especials

-   També en tenim que fan referència a altres eixos:

**attribute::** Apunta al node en que estem ( @ )

**namespace::** Fill del node en el que estem

.. code-block:: bash

        //alumnes/child::alumne

-   Alguns d'aquests eixos tenen forma abreujada i d'altres no.

.. code-block:: xml

    <alumne>
     <nom>Federicu</nom>
     <cognoms>Pi</cognoms>
     </alumne>
    <alumne>
     <nom>Filomenu</nom>
     <cognoms>Garcia</cognoms>
     </alumne>

### Seqüències

-   Una seqüència és una expressió XPath retorna més d'un element

-   Les seqüències són semblants a les llistes dels altres llenguatges

-   Tenen ordre i poden tenir duplicats

-   Poden contenir valors de tipus diferents excepte llistes de valors

-   Podem crear seqüències amb parèntesis i els valors separats per
    comes

.. code-block:: xml

    (33, 34, 35)

-   En XPath 2.0 si separem dues expressió amb una coma tindrem una
    seqüència dels resultats

.. code-block:: bash

    (//nom,//cognom)

.. code-block:: xml

        <nom>Xavier</nom>
    <nom>Federicu</nom>
    <nom>Filomenu</nom>
    <cognom>Sala</cognom>
    <cognom>Pi</cognom>
    <cognom>Garcia</cognom>

## Predicats

-   Ens permetran avaluar els nodes resultat basant-nos en condicions

-   S'especifiquen posant la condició entre corxets

.. code-block:: bash

    //alumne[nom/text()=”Filomenu”]

.. code-block:: xml

    <alumne>
     <nom>Filomenu</nom>
     <cognoms>Garcia</cognoms>
     </alumne>

-   Els predicats s'avaluen després de fer la selecció

-   Del conjunt de nodes es seleccionen els que compleixen la condició

.. code-block:: bash

    //professor[@Especialitat=”507”]

-   Però això no impedeix preguntar per etiquetes de fora de la selecció

.. code-block:: bash

    //professor/nom[../@Especialitat=”507”]

.. code-block:: xml

    <nom>Xavier</nom>

## Operadors

.. image:: operadors-xpath.png

### Comparació

and or not()

### Operadors lògics

## Operador d'unió

-   L'operador d'unió ens permetrà mesclar els resultats

.. code-block:: bash

    //alumne/nom | //alumne/cognoms

.. code-block:: xml

    <nom>Federicu</nom><cognoms>Pi</cognoms>
    <nom>Filomenu</nom><cognoms>Garcia</cognoms>
    <nom>Manolito</nom><cognoms>Puig</cognoms>

-   Que podem comprovar que és diferent de fer:

.. code-block:: bash

    //alumne/nom
    //alumne/cognoms

## Operadors de conjunts

-   Però l'operador d'unió no és l'únic operador de conjunts. En 2.0
    s'han afegit:

### Intersecció

.. code-block:: bash

    (//alumne/nom) intersect (//professor/nom)

### Disjunció

.. code-block:: bash

    (//alumne/nom) except (//professor/nom)

## Funcions XPath

-   Xpath ofereix una gran quantitat de funcions que ens permetran
    manipular els resultats

-   Cada una de les versions d'XPath ha afegit noves funcions

-   Les funcions es poden dividir

-   Funcions per conjunts de nodes

-   Funcions de cadenes de caràcters

-   Funcions numèriques

-   Funcions booleanes

-   Hi ha moltes funcions XPath predefinides:
    http://www.w3.org/TR/xpath-functions/

.. image:: funcions-xpath.png

-   Amb les funcions podem aconseguir resultats diferents

-   Quants alumnes tenim

.. code-block:: bash

    count(//alumne)

-   Mostrar les etiquetes de tres lletres

.. code-block:: bash

    //\*[string-length(name())=3]

-   També les podem fer servir per comparar

.. code-block:: bash

    //alumne[contains(nom,”PI”)]

## Rendiment XPath

-   Quan s'escriu una expressió XPath s'està especificant què es vol i
    no com recuperar-ho

-   S'executarà diferent en diferents eines

.. code-block:: bash

    /alumnes/alumne[starts-with(nom,'F') and cognom='Garcia' ]

Podem resseguir el fitxer mirant si un nom comença per 'F' i si
coincideix mirem si el cognom és 'Garcia' L'eina pot crear un índex per
cognom i accedir directament als 'Garcia' i després mirar si comencen
per 'F' ...

-   Això vol dir que el rendiment dependrà de:

-   Com es facin les expressions

-   quina eina fem servir

-   Com que sovint no es sap amb què s'executarà l'expressió

-   La millor expressió és la més simple...

-   Fer el possible per evitar duplicats en expressions llargues

**Millor** /alumne/nom

**Pitjor** //nom

## Xpath 2.0

-   En XPath 2.0 s'ha afegit una sèrie de característiques que ens
    permetran fer coses més complexes

-   Molts d'aquests operadors els veurem amb **XQuery**

## Avaluació XPath

Llibreries

-   Podem fer servir molts programes per comprovar el funcionament de
    les expressions XPath

-   Les llibreries més habituals són les llibreries de Java, .NET, o C:

    -   Saxon
    -   Xalan
    -   MSXML

Però la majoria dels llenguatges d'scripts tenen alguna forma d'avaluar
expressions XPath - Perl, Python, Ruby, PHP ...

### xmllint

-   Xmllint també permet fer avaluacions Xpath de forma interactiva

-   Està pensat per avaluar les expressions abans de posar-les en una
    transformació

.. code-block:: bash

    $ xmllint --shell classes.xml

    / > xpath //nom
    Object is a Node Set :
    Set contains 3 nodes:
    1 ELEMENT nom
    2 ELEMENT nom
    3 ELEMENT nom
    / > 

### Saxon-B

-   Amb Ubuntu podem avaluar expressions XPath fent servir la línia de
    comandes amb Saxon:

-   **XQuery** suporta les expressions XPath i per tant podem fer servir
    la comanda per avaluar les expressions

.. code-block:: bash

    $ echo //alumne/nom | saxonb-xquery -s classes.xml -

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <nom>Federicu</nom>
    <nom>Filomenu</nom>

### Perl: xpath

-   Els llenguatges d'scripts ofereixen utilitats per avaluar
    expressions XPath

-   La llibreria libxml-xpath-perl ens instal·la la comanda xpath:

-   Però n'hi ha moltes més...

.. code-block:: bash

    $ xpath -q -e //alumne/nom classes.xml -

.. code-block:: xml

    <nom>Federicu</nom>
    <nom>Filomenu</nom>

### xmlstarlet

-   Podem instal·lar el paquet 'xmlstarlet' que ens permetrà fer
    consultes més complexes.

.. code-block:: bash

    $ xmlstarlet sel -t -m "//nom" -v "." -n classes.xml

    Xavier
    Federicu
    Filomenu

-   Xmlstarlet permet fer múltiples peticions i obtenir múltiples
    resultats a partir de cada una de les peticions

### XMLCopyEditor

-   La majoria dels editors gràfics XML també suporten avaluació XPath

.. image:: xmlcopyeditor-xpath.png

### Editors propietaris

-   La majoria dels editors XML de pagament també tenen alguna forma de
    fer consultes Xpath dins de l'editor

    -   oXigen XML Editor
    -   Microsoft Visual Studio
    -   Altova XMLSpy
    -   Liquid XML Studio
    -   Stylus Studio 6 XML
    -   XMLPad

## Extensions de navegadors

-   També tenim extensions del navegador per avaluar Xpath:

.. image:: extensions-xpath.png

Exemples: - XPath Checker (Firefox) XPather (Firefox) - Internet
Explorer - Developer Bar (IE)

## Avaluació Online

-   El fet de que moltes llibreries siguin en llenguatge Java afavoreix
    la creació de pàgines web per fer proves:

http://emdin-here.ru/r/xpath_checker/

http://www.bit-101.com/xpath/

http://www.futurelab.ch/xmlkurs/xpath.en.html

.. image:: online-xpath.png
