# XQUERY

.. footer:: ASIX --- LMISGI --- Curs 2018-19

# Index

.. contents:: Table of Contents

# Introducció

-   La gran quantitat de dades emmagatzemades en documents XML obliga a
    tenir alguna forma de poder recuperar-ne les dades

-   Un dels problemes és obtenir dades que estan en múltiples documents

-   Per això el W3C va definir XQuery: http://www.w3.org/TR/xquery/

-   XQuery és un llenguatge funcional i declaratiu (com SQL)

    -   En comptes d'executar una llista de comandes es passa una
        expressió que s'avalua i dóna un resultat
    -   Es poden combinar expressions amb d'altres expressions per
        obtenir resultats més complexes

-   No només serveix per consultar fitxers XML sinó qualsevol cosa que
    es pugui mostrar com XML (fins i tot BDD Relacionals)

    -   Les consultes i resultats donaran resultats XML

-   Amb XQuery:

    -   Podem **seleccionar** informació segons criteris
    -   **Filtrar** la informació que ens interessa d'un flux de dades
    -   **Buscar** informació en un document o un grup de documents
    -   **Unir** dades de múltiples documents
    -   **Ordenar**, **agrupar** i **afegir** dades als resultats
    -   **Transformar** i **reestructurar** XML
    -   Fer operacions aritmètiques i **manipular** cadenes de caràcters

# XQuery / SQL

.. image:: xquery-sql.png

-   XQuery expandeix XPath i el converteix en un llenguatge de consultes
    semblant a SQL

-   XQuery és un llenguatge de consulta dissenyat per escriure consultes
    sobre col·leccions de dades expressades en XML

-   Es pot fer servir en fitxers XML o en bases de dades amb capacitats
    XML

-   Suporta la combinació de resultats que provinguin de diferents fonts

-   Suporta DTD i XML Schemas a més d'espais de noms

-   Intenta convertir-se en el llenguatge estàndard de consulta de dades
    XML en les Bases de Dades

# Llenguatge d'expressions

-   XQuery és un llenguatge d'expressions

-   Totes les expressions avaluen a un valor determinat

-   No té perquè limitar-se a recerca ja que té suport per operacions i
    treball amb cadenes

.. code-block:: bash

    let $x := 5
    let $y:=4
    return $x+$y 

retorna 9

.. code-block:: bash

    let $x := 'Hola'
    return $x 

retorna Hola

# Expressions XQuery

-   Les expressions XQuery poden estar contingudes en fitxers de text

-   Estan formades per dues parts:

    -   **Pròleg:** És opcional i pot contenir diverses expressions
        separades per punt i coma que afectaran a com s'avalua
        l'expressió (declaracions d'espais de noms, variables, funcions,
        ...)

    -   **Cos:** Una expressió que pot contenir-ne d'altres a dins

-   Per exemple en aquesta expressió

**Pròleg**

.. code-block:: xml

    declare boundary-space preserve;
    declare namespace cen = "http://iescendrassos.net/alum";
    declare variable $alum := doc("catalog.xml")//alumnes;

**Cos**

.. code-block:: xml

    <alumnes>{count($alum/nom)}<alumnes>,
    <cen:llista>{$catalog/nom}</cen:llista>

# Comentaris

-   Com en tots els llenguatges, en Xquery també podem fer comentaris

-   Els comentaris es fan posant-los dins d'un interval (: i :)

-   Els comentaris en format XML no es poden fer servir en XQuery

.. code-block:: bash

    (: Això és un comentari :)
    (: També pot ser
    De múltiples línies
    :)

# Variables

-   XQuery pot fer servir variables

-   Les variables s'identifiquen perquè comencen amb el símbol '\$'

.. code-block:: bash

    let $x := 5
    let $y := //alumnes

-   Les variables poden tenir qualsevol valor: literals, seqüències de
    nodes, seqüències buides, etc...

# Funcions

-   XQuery fa servir funcions per extreure dades dels fitxers XML

-   Hi ha més de 100 funcions en XQuery que cobreixen un gran ventall de
    tasques diverses

-   A més permet que definim les nostres pròpies funcions

-   D'entre les funcions a destacar començarem amb:

.. code-block:: bash

    - doc()
    - document()
    - collection()

## doc()

-   Les expressions més senzilles simplement seleccionen elements i
    atributs d'un document

.. code-block:: xml

    doc(“classes.xml”)/classe/alumnes/alumne

-   La funció document ens permet carregar documents XML i crear-ne els
    nodes

-   També podem fer servir variables i posteriorment interrogar-les

-   A partir d'aquest moment podrem fer recerques dins de la variable de
    la mateixa forma que en el fitxer

.. code-block:: xml

    let $classe = doc(“classes.xml”)

## Funció collection()

-   Retorna una seqüència de nodes referenciats per una adreça.

    -   No necessita que hi hagi cap node arrel

-   Aquesta és la funció més corrent en accessos a Bases de dades XML

-   Es pot usar per fer *querys* a tots els xml's d'una carpeta

.. code-block:: xml

    let $classe = collection(“ruta/nom-carpeta”)

-   Però podem fer una col·lecció nosaltres:

fer un fitxer **totesclasses.xml**

.. code-block:: xml

    <collection>
     <doc href=”classes.xml”>
     <doc href=”classes2.xml”>
     <doc href=”classes3.xml”>
    </collection>

i ara fer l'assignació a una variable de tots els xmls continguts

.. code-block:: xml

    let $classe = collection(“totesclasses.xml”)

# Xquery - XPath

.. image:: xquery-superset.png

-   XQuery fa servir XPath

    -   Estrictament XQuery és un superconjunt d'XPath 2.0
    -   Totes les expressions XPath 2.0 són consultes
    -   Però a més del que permet XPath permet unir informació de
        diferents fonts i generar nous fragments d'XML

.. code-block:: bash

    let $profe := doc(“classes.xml”)//professor
    return $profe/nom

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <nom>Xavier</nom>

# Expressions avaluables

-   En XQuery es poden fer servir els corxets { } per marcar el
    contingut que ha de ser calculat quan s'executa la consulta

.. code-block:: xml

    <resultat>
    {
     doc(“alumnes.xml”)/classe/professor
    }
    </resultat>

-   Si barregem XQuery amb alguna altra cosa hem de fer servir els
    corxets { } o no serà avaluat

-   Les expressions avaluables són la forma més senzilla de crear nous
    elements o fins

.. code-block:: xml

    <credit> {doc(“classes.xml”)//credit} </credit>

-   O i tot atributs:

-   Es poden fer servir per generar sortides en HTML a partir de les
    dades en XML

.. code-block:: xml

    <credit nom={doc(“classes.xml”)//credit/text()} />

# Expressions FLWOR

-   La expressió **FLWOR** és una forma de bucle que permet processar
    els ítems d'una connexió

**F for** Permet passar d'un element a un altre d'una col·lecció

**L** let Assigna valors a variables

**W where** Permet filtrar els resultats de la comanda segons condicions

**O order by** Permet ordenar els resultats per un camp abans de mostrar
els resultats

**R return** Retorna el resultat

.. image:: xquery-flwor2.png

## Exemple FLWOR

.. image:: xquery-flwor.png

# for

-   'for' es fa servir per avaluar cada un dels resultats d'un conjunt
    de nodes

.. code-block:: bash

    for $alumne in doc(“classes.xml”)

-   El següent s'executarà per cada node alumne

.. code-block:: bash

    for $alumne in doc(“classes.xml”)//alumne

.. code-block:: xml

    <alumne>
     <nom>
     Federicu
     </nom>
     <cognoms>
     Pi
     </cognoms>
    </alumne>

    <alumne>
     <nom>
     Filomenu
     </nom>
     <cognoms>
     Garcia
     </cognoms>
    </alumne>

    <alumne>
     <nom>
     Manolito
     </nom>
     <cognoms>
     Puig
     </cognoms>
    </alumne>

## return

-   La forma més senzilla d'expressió FLWOR és combinar el for amb el
    'return'

.. code-block:: bash

    for $alumne in doc(“classes.xml”)//alumne
    return $alumne/nom

-   El *return* es fa servir per retornar els valors obtinguts (tots o
    una part)

-   En aquest exemple a més filtrem els resultats per només recuperar el
    nom i no tot

.. code-block:: xml

    <nom>Federicu</nom>
    <nom>Filomenu</nom>
    <nom>Manolito</nom>

## for .. return

-   Podem fer servir el for per fer seqüències de números:

-   Però pot ser més complexe...

.. code-block:: bash

    for $i in (1, 2, 3)
    return $i*$i

.. code-block:: bash

    1 4 9

.. code-block:: bash

    for $i in (1, 2, 3), $j in (3 to 5)
    return $i*$j

.. code-block:: bash

    3 4 5 6 8 10 9 12 15

-   Podem afegir resultats extres al fer un return expressant el
    retornat entre corxets

.. code-block:: bash

    for $alumne in doc(“classes.xml”)//alumne
    return <persona> { $alumne/nom } </persona>

.. code-block:: xml

    <persona><nom>Federicu</nom></persona>
    <persona><nom>Filomenu</nom></persona>
    <persona><nom>Manolito</nom></persona>

-   Es pot fer més complexe si cal ...

.. code-block:: xml

    <llista>
    {
     for $alumne in doc(“classes.xml”)//alumne
     return <persona> { $alumne/nom } </persona>
    } </llista>

## Operador 'at'

-   Amb el for podem fer servir l'operador at que ens permetrà obtenir
    la posició del node

-   El valor de la variable s'aconsegueix en relació a la posició en el
    grup de nodes

.. code-block:: bash

    for $alumne at $pos in doc(“classes.xml”)//alumne
    return <alumne pos=”{$pos}”>
     {$alumne/nom}
     </alumne>

.. code-block:: xml

    <alumne pos=”1”>Federicu</alumne>
    <alumne>Filomenu</alumne>
    <alumne pos=”2”>Manolito</alumne>

## for .. return

-   I fins i tot podem treballar amb múltiples variables:

.. code-block:: xml

    <resultats>
    {
     for $alumne in doc("alumnes.xml")//alumne,
     $nom in $alumne/nom,
     $curs in $alumne/credits
     return
     <llista credits="{count($curs/assignatura)}">
     { $nom }
     </llista>
     }
    </results>

# let

-   La comanda 'let' ens permet declarar variables i assignar-los un
    valor

.. code-block:: bash

    let $i := 1
    let $nom := 'Manel'

-   Un dels usos de 'let' és guardar els resultats per usar-los
    posteriorment

-   Es poden assignar iteracions a una variable

.. code-block:: bash

    let $i := (1 to 3)

-   **ATENCIÓ**: let no és un sistema per fer loops, només per assignar
    valors a una variable

.. image:: xquery-let.png

## Diferència entre for i let

.. code-block:: bash

    for $selec in doc("classes.xml")//alumne
    return <persona>{$selec/nom}</persona>

.. code-block:: xml

    <persona> <nom>Federicu</nom> </persona>
    <persona> <nom>Filomenu</nom> </persona>
    <persona> <nom>Manolito</nom> </persona>

-   Es genera una etiqueta `<persona>`{=html} per cada iteració

.. code-block:: bash

    let $selec := doc("classes.xml")//alumne
    return <persona>{$selec/nom}</persona>

.. code-block:: xml

    <persona>
     <nom>Federicu</nom>
     <nom>Filomenu</nom>
     <nom>Manolito</nom>
    </persona>

-   Només una sola etiqueta `<persona>`{=html}, vol dir que \$selec ha
    pres el valor de tots els alumnes de cop

# where

-   where serveix per filtrar els resultats que es passaran al return

-   Es poden fer servir operadors lògics 'and' i 'or'

.. code-block:: bash

    for $alumne in doc('classes.xml')//alumne
    where $alumne/@aprovat='si'
    return $alumne/nom

.. code-block:: xml

    <nom>Federicu</nom>
    <nom>Filomenu</nom>
    for $alumne in doc('classes.xml')//alumne
    where $alumne/@aprovat='si' and nom='Federicu'
    return $alumne/nom

# Expressions quantificades

-   Les expressions quantificades serveixen per comprovar si algun dels
    nodes compleixen una determinada condició

.. code-block:: bash

    for $s in doc('classes.xml')//alumne
    satisfies ($s/cognoms='Pi')

-   Les expressions quantificades sempre s'avaluen a 'cert' o 'fals'

    -   No serveixen per seleccionar els nodes que compleixen una
        determinada condició

# Quantificadors existencials

-   També suporta varis quantificadors:

**some:** Comprovar si algun element de la llista satisfà la condició

**every:** Comprovar que tots els elements de la llista satisfan la
condició

.. code-block:: bash

    for $selec in doc('classes.xml')//alumne
    where some $s in $selec satisfies ($s/cognoms='Pi')
    return $s/nom

.. code-block:: xml

    <nom>Federicu</nom>

# Order by

-   Amb 'order by' podrem ordenar la col·lecció de resultats

-   Podem ordenar de forma ascendent (per defecte) o descendent

-   Podem ordenar per múltiples camps

.. code-block:: bash

    for $alumne in doc(“classes.xml”)//alumne
    order by $alumne/cognoms descending
    return $alumne/cognoms

.. code-block:: xml

    <cognoms>Puig</cognoms>
    <cognoms>Pi</cognoms>
    <cognoms>Garcia</cognoms>

.. code-block:: bash

    order by $alu/cognoms descending, $alu/nom ascending

# Niuar els for

-   No hi ha cap problema per niuar les comandes for

-   Això permet passar el resultat d'un *for* a un *for* fill

.. code-block:: bash

    for $selec in doc('classes.xml')//alumne
    return <persona>{ $selec/nom }
    {
     for $selec2 in $selec
     return $selec2//cognoms
    }
    </persona>

.. code-block:: xml

    <persona><nom>Federicu</nom><cognoms>Pi</cognoms></persona>
    <persona><nom>Filomenu</nom><cognoms>Garcia</cognoms></persona>
    <persona><nom>Manolito</nom><cognoms>Puig</cognoms></persona>

# if..then..else

-   Podem fer comparacions fent servir una de les estructures típiques
    de programació

.. code-block:: xml

    let $doc := doc("alumnes.xml")
    let $aprovat := 5
    for $b in $doc/alumne
     return
     if ($b/credit/nota > $aprovat) then
     <data>
     { $b/nom } està aprovat
     </data>
     else
     <data>
     { $b/nom } no està aprovat
     </data>

# Espais de noms

-   Es poden fer servir espais de noms en les consultes XQuery

    -   Es poden especificar directament
    -   Es poden declarar en la capçalera

.. code-block:: xml

    declare namespace cen= "http://iescendrassos.net/alum";
    <llista xmlns="http://iescendrassos.net/alum">
     {
     let $nom := doc('alumnes.xml')//cen:nom
     return $nom
     }
    </llista>

# Unions

-   La comanda **FLWOR** ens permet crear unions entre documents

.. code-block:: bash

    for $alum1 in doc('classe1.xml')//alumne
    let $alum2 := doc('classe2.xml')//alumne
    where $alum1 = $alum2
    return $alum1

-   Això ens permet obtenir els noms dels alumnes que es repeteixen
    entre les dues llistes

-   Però evidentment tenim moltes més possibilitats...

-   Podem fer unions amb dades de tres fonts diferents

.. code-block:: xml

    for $alum1 in doc('classe1.xml')//alumne,
     $alum2 := doc('classe2.xml')//alumne,
     $alum3 := doc('classe3.xml')//alumne
    where $alum1 = $alum2 and $alum1 = alum3
    return <resultat nom={$alum1/nom} />

# Outer joins

-   També podem fer unions i obtenir els valors encara que no tinguin
    correspondència:

Si tenim els següents xml

**alumnes.xml**

.. code-block:: xml

    <?xml version=”1.0” ?>
    <alumnes>
     <alumne num=”1”>
     <nom>Filomenu</nom>
     <cognom>Pi</cognom>
     </alumne>
     ...

**notes.xml**

.. code-block:: xml

    <?xml version=”1.0” ?>
    <notes>
     <nota id=”1”>5</nota>
     <nota id=”2”>3</nota>
     <nota id=”3”>8</nota>
     ...
    </notes>

podem ajuntar-los amb:

.. code-block:: xml

    for $alumne in doc("alumnes.xml")/alumnes/alumne
    return <resultat>{$alumne/nom,$alumne/cognom}
    {
     for $notes in doc("notes.xml")/notes/nota
     where $notes/@id = $alumne/@num
     return <nota>{$notes/text()}</nota>
     }
    </resultat>

# Agrupaments

-   Un altre aspecte important és poder fer agrupacions de dades:

.. code-block:: bash

    for $d in distinct-values( doc("alumnes.xml")//assignatura )
    let $n := doc("alumnes.xml")//alumne[assignatura = $d]
    order by $d
    return <d credit="{$d}" alumnes="{count($n/nom)}" />

-   Ens donaria un resultat com:

.. code-block:: xml

    <?xml version="1.0" encoding="UTF-8"?>
    <d alumnes="4" credit="Programació"/>
    <d alumnes="5" credit="XML"/>
    <d alumnes="5" credit="Xarxes Locals"/>

# Resultats XML

-   Hi ha una norma al fer les consultes que sempre s'ha de respectar:

Els resultats sempre han de ser resultats **XML vàlid**

-   Per tant si posem etiquetes en els resultats aquestes s'hauran de
    tancar

# Operadors de comparació

-   En XQuery hi ha 4 tipus de comparadors

-   Comparació de nodes

    -   Determinar si una seqüència de nodes compleix una determinada
        condició

.. code-block:: xml

    some every is satisfies
    doc('classes.xml')//alumne[1] is “Pere”

-   Comparació d'ordre

    \<\< \>\>

-   Tenim dos tipus d'operadors per comparar

-   Operadors de comparació general

-   Serveixen per comparar elements i arguments

    = != \< \<= \> \>=

.. code-block:: bash

    doc('classes.xml')//alumne[@aprovat='si']

-   Operadors de comparació de valors

-   Compara els valors basant-se en els tipus definits en el XML Schema

    eq ne lt gt ge le

.. code-block:: bash

    doc('classes.xml')//alumne[nom eq 'Federicu']

## Operadors booleans

-   Es poden fer servir els operadors booleans tradicionals

    and or eq not()

.. code-block:: xml

    $alumnes/nom and $notes

## Operadors de conjunts

-   Podem fer servir except per filtrar els resultats que no ens
    interessen d'una consulta:

.. code-block:: bash

    for $selec in doc("classes.xml")//alumne
    return $selec/* except $selec/nom

.. code-block:: xml

    <cognoms>Pi</cognoms>
    <cognoms>Garcia</cognoms>
    <cognoms>Puig</cognoms>

-   També la funció **distinct-values():**

.. code-block:: bash

    for $selec in
     distinct-values(doc("classes.xml")//alumne)
    return $selec/nom 

## Una bona utilitat per let: distinct-values

.. image:: xquery-distinct-values.png

-   Agafem tot el document

-   Seleccionemt tots els colors i els posem dins una variable

-   Seleccionem només els diferents

-   Però els operadors union i intersect ens proporcionen una potència
    molt interessant

.. code-block:: bash

    doc('classe1.xml')//nom intersect
    doc('classe2.xml')//nom

Els nom dels alumnes de les dues classes

-   L'operador d'unió ens pot afegir resultats als que ja teníem

.. code-block:: bash

    doc('classe1.xml')//nom union doc('classe2.xml')//nom

## Operadors i funcions

-   Podem fer servir qualsevol dels operadors i funcions de XPath. Els
    més importants són:

**Matemàtics** + - \* div() idiv() mod abs() floor() ceiling() round()
round-half()

**Seqüència** to union (\|) intersect except

**Agrupació** count() min() max() avg() sum()

**Cadena** concat() string-lenght() substring() starts-width()
ends-width() string() lowercase() uppercase()

**Altres** distinct-values() empty() exits()

# Funcions

-   Podem fer servir qualsevol de les funcions XPath al fer una consulta
    XML

-   Per exemple podem concatenar valors d'un resultat per obtenir-ne
    només un

.. code-block:: bash

    for $alu in doc(“classes.xml”)//alumne
    return <nom>
     { concat($alu/nom,” “,$alu/cognoms) }
     </nom>

.. code-block:: xml

    <nom>Federicu Pi</nom>
    <nom>Filomenu Garcia</nom>
    <nom>Manolito Puig</nom>

## Funcions d'usuari

-   Amb XQuery podem definir les nostres propies funcions

.. code-block:: bash

    declare funtion local:quadrat($num AS xs:integer) as
    xs:integer
    {
     return ($num * $num)
    };

-   També podem passar seqüències d'elements com a tipus afegint-hi
    element(...)\*

.. code-block:: bash

    declare funtion local:resum($num as element(alumne)*) as
    xs:element(aprovats)*
    {
     return ($num * $num)
    };

-   Les funcions les podem cridar de forma normal

.. code-block:: xml

    <notes>
    {
     local:quadrat($alumne/nota)
    }
    </notes>

-   Però podem cridar documents sencers com a paràmetres:

.. code-block:: xml

    <aprovats>
    {
     local:resum(fn:doc(“classes.xml”)//alumnes)
    }
    </aprovats>

# Avaluació de XQuery

-   L'avaluació d'expressions XQuery requereix que siguin passades a
    través d'un processador XQuery

.. image:: processador-xquery.png

## Saxon

-   Una de les llibreries més usades per fer consultes XQuery és Saxon.

    -   Té una versió gratuïta Saxon-HE (home edition). Abans era
        anomenada saxon-b
    -   Versions de pagament Saxon-PE (professional),

SAXON-EE (enterprise)

-   En la versió d'Ubuntu tenim la comanda saxonb-xquery
    (libsaxonb-java):

.. code-block:: bash

    $ saxonb-xquery alumnes.xquery
    <?xml version="1.0" encoding="UTF-8"?>
    <nom>Federicu</nom>

## xqilla

-   Podem fer comprovacions de Xquery amb **xqilla** (sobre la llibreria
    **Xerces-C**):

-   Generem l'arxiu

.. code-block:: bash

    $ cat helloworld.xquery
    (: Hello world :)
    $i := “Hola món”
    return $i

-   i el passem al programa **xqilla** directament

.. code-block:: bash

    $ xqilla helloworld.xquery
    Hola món

## Galax

-   Galax és una implementació de programari lliure de XQuery 1.0 que
    segueix estrictament les recomanacions del W3C

-   També està disponible en els repositoris d'Ubuntu

.. code-block:: bash

    $ galax-run alumne.xquery
    <persona><nom>Federicu</nom></persona>

.. code-block:: bash

    $ galax-run nomsencer.xquery
    <persona>Federicu Pi</persona>
    <persona>Filomenu Garcia</persona>
    <persona>Manolito Puig</persona>

## Kernow

-   Hi ha un entorn gràfic per Saxon anomenat **Kernow** que ens
    permetrà debugar consultes XQuery fàcilment

.. image:: kernow.png

## Programes propietaris

-   La majoria dels editors XML de pagament també tenen alguna forma de
    provar i depurar les consultes XQuery des de dins de l'editor

-   oXigen XML Editor

-   Microsoft Visual Studio

-   Altova XMLSpy

-   Liquid XML Studio

-   Stylus Studio 6 XML

-   XMLPad

.. image:: processadors-xquery-propietari.png

# Base de dades XML

-   Les bases de dades que tenen suport XML

-   Nativament (eXist, ... )

-   Com a extensions (Oracle, ... )

-   Normalment tenen suport XQuery per interrogar a les dades XML

.. image:: xquery-bdd.png

## XQuery

## XQueryX

-   L'objectiu de XQueryX és donar una sintaxi XML estàndard a XQuery

-   Està més pensat per ús dels ordinadors que de les persones

-   Per exemple la expressió Xquery següent:

.. code-block:: xml

    for $t in doc("alumnes.xml")/alumnes/alumne/nom
     return $t 

-   En XqueryX seria més o menys:

.. code-block:: xml

    <?xml version="1.0"?>
    <xqx:module xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xmlns:xqx="http://www.w3.org/2003/12/XQueryX"
     xsi:schemaLocation="http://www.w3.org/2003/12/XQueryX xqueryx.xsd">
     <xqx:mainModule>
     <xqx:queryBody>
     <xqx:expr xsi:type="xqx:flwrExpr">
     <xqx:forClause>
     <xqx:forClauseItem>
     <xqx:typedVariableBinding>
     <xqx:varName>t</xqx:varName>
     </xqx:typedVariableBinding>
     <xqx:forExpr>
     <xqx:expr xsi:type="xqx:pathExpr">
     <xqx:expr xsi:type="xqx:functionCallExpr">
     <xqx:functionName>doc</xqx:functionName>
     <xqx:parameters>
     <xqx:expr xsi:type="xqx:stringConstantExpr">
     <xqx:value>alumnes.xml</xqx:value>
     </xqx:expr>
     </xqx:parameters>
     </xqx:expr>
     <xqx:stepExpr>
     <xqx:xpathAxis>child</xqx:xpathAxis>
     <xqx:elementTest>
     <xqx:nodeName>
     <xqx:QName>alumnes</xqx:QName>
     </xqx:nodeName>
     </xqx:elementTest>
     </xqx:stepExpr>
     <xqx:stepExpr>
     <xqx:xpathAxis>child</xqx:xpathAxis>
     <xqx:elementTest>
     <xqx:nodeName>
     <xqx:QName>alumne</xqx:QName>
     </xqx:nodeName>
     </xqx:elementTest>
     </xqx:stepExpr>
     <xqx:stepExpr>
     <xqx:xpathAxis>child</xqx:xpathAxis>
     <xqx:elementTest>
     <xqx:nodeName>
     <xqx:QName>nom</xqx:QName>
     </xqx:nodeName>
     </xqx:elementTest>
     </xqx:stepExpr>
     </xqx:expr>
     </xqx:forExpr>
     </xqx:forClauseItem>
     </xqx:forClause>
     <xqx:returnClause>
     <xqx:expr xsi:type="xqx:variable">
     <xqx:name>b</xqx:name>
     </xqx:expr>
     </xqx:returnClause>
     </xqx:expr>
     </xqx:elementContent>
     </xqx:expr>
     </xqx:queryBody>
     </xqx:mainModule>
    </xqx:module>

# XQuery amb Kernow

-   Anar a la pestanya **Xquery Sandbox**

.. code-block:: bash

    <discos>
    {

    for $disc in doc("../discos.xml")/catalog
    return $disc

    }
    </discos>

un altre exemple ja dins de l'editor seria:

.. image:: xquery-kernow-sandbox.png

# XQuery amb Oxygen

## Carrega fitxer xquery a Oxygen

Obre l'**oxygen** i arrossega-hi a dins el fitxer **XQUERY** creat.

Clica el botó de la clau

.. image:: oxygen-icona.png

## Configura transformació

.. image:: oxygen-escenario.png

1.  Escull transformació **XQuery**

2.  Clica a New

## Escull fitxers

.. image:: oxygen-escenario-2.png

1.  Selecciona el fitxer *xml*
2.  Clica a OK

## Executa query

.. image:: oxygen-executa.png

-   Clica a un botó de PLAY vermell
