# XSLT

.. footer:: ASIX --- LMISGI --- Curs 2018-19

# Index

.. contents:: Table of Contents

# Introducció

**XML** a pesar de que és un format llegible

-   Relativament

-   Aquest no és el seu principal objectiu

XML està pensat per:

Emmagatzemar i intercanviar informació

-   Pot fer falta transformar els XML per intercanviar dades entre
    programes diferents

-   Dos programes que treballin de forma similar però generin XML
    diferents

.. image:: plataformes-xml.png

-   O mostrar la informació d'una forma més "amigable"

Però:

-   XML no incorpora cap forma de presentar la informació

-   Col·locar informació de com es presentaran les dades trencaria amb
    l'ideal XML

"Separar les dades de la forma com es visualitzaran"

-   Per presentar les dades tinc vàries possibilitats:

1)  Es podria desenvolupar un programa

         És molta feina per una cosa que pot ser trivial

2)  Puc fer servir CSS

         De la mateixa forma que es fa amb HTML

3)  Puc transformar el document en un format pensat per ser visualitzat

         Hi ha molts formats que només estan pensats per això: PDF, HTML, ... 

# XML+CSS

-   Es pot solucionar amb: CSS

amb el següent **XML**:

.. code-block:: xml

    <professor>
     <nom>Xavier</nom>
     <cognom>Sala</cognom>
     <departament>
     Informàtica
     </departament>
     <carrecs>
    <carrec>
     Cap de Departament
     </carrec>
    <carrec>
     Tutor 2n ASI
     </carrec>
     </carrecs>
    </professor>

i el corresponent **CSS**:

.. code-block:: css

    nom, cognom {
     font-size:30px;
    }
    departament {
     display:block;
     font-weight: bold;
    }
    carrec {
     font-style: italic;
     padding-left:10px;
    }
    carrec:after { content: ","; }

Podem obtenir:

.. image:: resultat-xml-css.png

## Limitacions css

Però fer servir CSS té moltes limitacions:

-   La informació no pot ser reordenada

-   La informació dels atributs es pot mostrar però té moltes
    limitacions

-   No es poden afegir estructures noves

# XML+XSL

Per tant es va definir una forma de solucionar tots aquests problemes

-   Al principi aquest era l'únic objectiu i per això es va definir el
    XSL-FO

    -   Serveix per definir el disseny del text que es mostrarà
    -   Es fa servir bastant en la indústria

-   Els navegadors encara no el suporten

          No està pensat per pàgines web

## XSLT

-   Però ja que fem les transformacions

-   Perquè quedar-nos només en transformacions a documents
    visualitzables

-   També ens pot servir per transformar documents XML en altres
    documents XML

-   Així XSL va canviar i en va sorgir XSLT

## XSL

-   XSL està dividit en tres llenguatges:

**XSL Transformations (XSLT)** Un llenguatge per transformar documents
XML

**XSL Formatting Objects (XSL-FO)** Per definir com un document ha de
ser visualitzat

**XPath** Llenguatge per navegar en un document XML

.. image:: arbre-xsl.png

# XSLT

.. image:: xslt-esquema.png

-   XSLT és un llenguatge XML que permet convertir l'estructura dels
    elements XML
    -   Permet definir la forma com es transformaran les dades per
        poder-les representar o usar
    -   Permet fer canvis radicals en l'estructura del document
-   Està pensat per XML
    -   És més potent que CSS
    -   CSS no pot transformar el document només donar forma a la
        visualització
    -   En CSS la informació no es pot reordenar
    -   No es poden afegir estructures noves

## Funcions

-   Transformar documents XML en altres documents XML
-   La plantilla XSLT definirà com s'ha de fer per transformar un
    document XML en un altre

de:

.. code-block:: xml

    <professor>
     <nom>Xavier</nom>
     <cognom>Sala</cognom>
     <departament>
     Informàtica
     </departament>
     <carrecs>
    <carrec>
     Cap de Departament
     </carrec>
    <carrec>
     Tutor 2n ASI
     </carrec>
     </carrecs>
    </professor>

a:

.. code-block:: xml

    <professor>
     <nom>Xavier Sala</nom>
     <departament carrec=”Cap”>
     Informàtica
     </departament>
    <tutor>
     2n ASI
     </tutor>
    </professor>

## Funcions

-   Transformar un document XML en un altre per ser visualitzat
-   HTML, PDF, ...

.. code-block:: xml

    <professor>
     <nom>Xavier</nom>
     <cognom>Sala</cognom>
     <departament>
     Informàtica
     </departament>
     <carrecs>
    <carrec>
     Cap de Departament
     </carrec>
    <carrec>
     Tutor 2n ASI
     </carrec>
     </carrecs>
    </professor>

a:

.. image:: transformar-html.png

# XSLT

-   XSLT és un llenguatge que permet reestructurar radicalment el
    document XML original

-   Les transformacions XSLT cada vegada es fan servir més per generar
    vistes per diferents destins

.. image:: tranformar-mitjans.png

# Processadors XSLT

-   Per fer una transformació XSLT necessitem tres coses:
    -   El document XML que volem transformar
    -   La fulla d'estil XSLT que transformarà el XML en una altra cosa
    -   Un processador XSLT que faci la transformació
-   El processador agafarà els dos documents anteriors i els
    transformarà aplicant les regles de la plantilla

# El processador XSLT

-   La transformació la faran els processadors XSLT:

.. image:: processador-xslt.png

# Transformació de documents

-   La transformació de documents consisteix en:
    -   Crear un arbre de nodes a partir de l'XML
    -   Aplicar les regles als nodes que quadren
    -   S'escriu de nou l'arbre a XML

.. image:: transformacio.png

# XSLT: xsltproc

.. image:: xslt-xsltproc.png

-   xsltproc és una utilitat per processar XSLT que forma part de la
    llibreria libxslt de GNOME

-   S'invoca des de la línia de comandes especificant el nom del XSLT a
    aplicar i el document XML (o el document XML sol si té la
    referència)

.. code-block:: bash

    $ xsltproc fitxer.xml fitxer.xsl -o sortida

# XLST: Xalan

.. image:: xslt-xalan.png

-   Apache Xalan (http://xml.apache.org/xalan)

-   Es tractat d'un projecte per fer llibreries lliures, multiplataforma
    i amb qualitat comercial i totes les funcionalitats

-   Xalan funciona tant en Java com en C++

-   En Ubuntu tenim un programa de línia de comandes per fer les
    transformacions

.. code-block:: bash

    $ xalan -in fitxer.xml -xsl fitxer.xsl -out sortida

# XLST: Saxon

.. image:: xslt-saxon.png

-   Saxon (http://saxon.sourceforge.net)

-   Probablement Saxon és un dels més complerts de tots

-   Desenvolupat per un dels especificadors de l'estàndard. Suporta XSLT
    2.0, Xquery 1.0, Xpath 2.0

-   Versions:

    -   Saxon-HE (Home Edition): Codi obert.
    -   Saxon-PE (Professional Edition): Comercial
    -   Saxon-EE (Enterprise Edition): Comercial

-   En Ubuntu instal·lar-lo és senzill:

.. code-block:: bash

    $ sudo apt-get install libsaxon-java
    $ sudo apt-get install libsaxonb-java

-   Podem fer servir l'script per fer les transformacions que ens
    calguin:

.. code-block:: bash

    $ saxonb-xslt -o sortida fitxer.xml fitxer.xsl

# Altova XML engine

.. image:: xslt-altova.png

-   Altova XML Engine ( http://www.altova.com/altovaxml)

-   Altova és un motor XSLT que porta suport per esquemes.

-   No és programari lliure però és gratuït.

-   Només funciona sota Windows

.. code-block:: bash

    C:\> altovaxml -xslt1 fitxer.xsl -in fitxer.xsl -out sortida
    C:\> altovaxml -xslt2 fitxer.xsl -in fitxer.xsl -out sortida

# XSLT: Microsoft XML Parser

.. image:: xslt-microsoft.png

-   Microsoft XML Parser (http://www.microsoft.com/xml)

-   En el món .NET el més usat és el motor de Microsoft.

-   Es pot descarregar des de http://msdn.microsoft.com/xml

-   Necessita Microsoft XML Core Services per funcionar

.. code-block:: bash

    C:\> msxsl fitxer.xml fitxer.xsl -o sortida

# XT

.. image:: xslt-xt.png

-   Va ser un dels primers que va complir completament l'estàndard

-   Implementat en Java i per tant multiplataforma

# Navegadors web

-   Els navegadors també poden fer transformacions XSLT:

-   Firefox

-   Internet Explorer

-   Google Chrome

-   Opera

.. image:: processador-navegador.png

# Depuradors XSLT

-   Si es treballa molt amb XSLT ens pot passar que quedem aturats per
    algun error

-   Això si es treballa professionalment és un problema

-   Aquí és on apareixen els depuradors XSLT

-   Actualment hi ha molts depuradors XSLT que ens facilitaran descobrir
    en quin lloc hi ha el problema

## Editors XML

-   La majoria dels grans editors XML tenen algun tipus de depurador
    XSLT que permet avançar pas a pas, posar punts d'interrupció, ...

.. image:: xslt-debugacio.png

## Processadors XSLT

-   Els processadors XSLT també solen tenir algun tipus de forma de
    mostrar-nos què han fet

.. code-block:: bash

    $ xsltproc --debug prova.xml

    DOCUMENT
    version=1.0
    standalone=true
     ELEMENT b
     TEXT
     content=Pere
     ELEMENT b
     TEXT
     content=Joan

.. code-block:: bash

    $ xsltproc --profile prova.xml
    number match name mode Calls Tot 100us Avg
     0 alumnes 1 4 4
     Total 1 4
    <?xml version="1.0"?>
    <b>Pere</b><b>Joan</b>

## xsl:message

-   També es pot recórrer a un sistema més manual

-   Tenim les etiquetes xsl:message que ens permeten fer sortides

-   Es fa servir sobretot per mostrar errors

-   La idea és fer una depuració "manual"

-   A l'estil dels printf de C

.. code-block:: xml

    <xsl:message>

     ** INFO: Ha arribat aquí!!

    </xsl:message>

# Creació d'una fulla d'estils per fer una transformació

## Associar un XSL a un XML

-   Podem associar un XSL a un document XML posant-li la definició

.. code-block:: xml

    <?xml version=”1.0” ?>
    <?xml-stylesheet href=”fitxer.xsl” type=”text/xsl” ?>

.. image:: associacio-xslt.png

## Estructura d'un XSLT

-   Com qualsevol llenguatge XML el XSLT té un node arrel que hem de
    definir

.. code-block:: xml

    <xsl:stylesheet version=”1.0”
     xmlns:xsl=”http://www.w3.org/1999/XSL/Transform”
     >
     ...
    </xsl:stylesheet>

-   Cal definir-hi l'espai de noms de les etiquetes que farem servir

-   L'arrel del document serà stylesheet

# xsl:output

-   Es pot fer servir per informar al processador del tipus de document
    que generem

**method="xml":** Generem XML. És el valor per defecte

**method="html":** Generem HTML. Es pot detectar si l'arrel és html

**method="text":** Generem un fitxer de text

**method="xhtml":** Generem XHTML. Només funciona en versió 2.0

-   Però té més paràmetres indent (per formatar les sortides), etc...

.. code-block:: xml

    <xsl:output method=”html” indent="yes"/>

# Plantilles

-   Tota la feina de transformació es fa a partir de les plantilles
    -   Les plantilles es defineixen a partir de regles
    -   A partir de les regles es controla el processador
    -   Hi ha funcions predefinides que ens poden ajudar a obtenir els
        resultats desitjats
-   Una regla està formada per:
    -   Alguna cosa que seleccioni un node: XPath
    -   Una acció que transforma el node en un altre

# xsl:template

-   xsl:template defineix una plantilla i el selector de nodes (XPath)

-   Dintre seu hi haurà el codi que generarà la sortida

.. code-block:: xml

    <xsl:template match=”alumnes”>

.. image:: template-match.png

## Plantilles

-   El funcionament consisteix en anar agafant un a un els nodes del XML
    segons el "context"

.. code-block:: xml

    \
    <professor>Toni</professor>
    <alumnes>
     <nom>Joan</nom>
     <nom>Pere</nom>
    </alumnes>

-   S'intenta fer quadrar amb alguna de les regles
    -   Si no n'hi ha cap es segueix la política per defecte: Normalment
        escriure'n el text
    -   Si n'hi ha alguna s'aplica

## 1

.. image:: template-exemple1.png

## 2

.. image:: template-exemple2.png

## 3

.. image:: template-exemple3.png

# Plantilles predefinides

-   Tenim una sèrie de plantilles definides que ens permetran
    seleccionar els diferents elements que composen un document:

**Text** Navegarem per tots els nodes de text del XML

.. code-block:: xml

    match=”text()”

**Atributs** Amb els atributs simplement afegim @

.. code-block:: xml

    match=”@*”

**Elements** Podem navegar per tots els elements \*

.. code-block:: xml

    match="*|/"

**Comentaris** Anar seleccionant tots els comentaris del document

.. code-block:: xml

    match=”comments()”

**Instruccions de procés** Les instruccions de procés que hi hagi
definides

.. code-block:: xml

    match=”processing-instruction()”

**Espais de noms** Ens mostrarà tots els espais de noms del document

.. code-block:: xml

    match=”namespaces()”

# xsl:text

-   L'etiqueta xsl:text serveix per escriure text en la sortida

.. code-block:: xml

    <xsl:template match=”alumne”>
     <xsl:text>Alumne eliminat</xsl:text>
    </xsl:template>

-   Es pot afegir text sense fer servir xsl:text

.. code-block:: xml

    <xsl:template match=”alumne”>
     Alumne eliminat
    </xsl:template>

-   xsl:text es fa servir per:
    -   Sortides a fitxers de text
    -   Conservar els espais
    -   Afegir un espai en blanc: `<xsl:text>`{=html}
        `<xsl:text>`{=html}
-   Amb el text podem afegir etiquetes noves sense problemes

.. code-block:: xml

    <xsl:template match=”alumne”>
     <html><body>Alumne eliminat</body></html>
    </xsl:template>

-   Però s'ha de tenir en compte que si s'obren etiquetes s'han de
    tancar!

           O el document no serà ben format i fallarà!

.. code-block:: xml

    <xsl:template match=”alumne”>
     <p>Alumne eliminat
    </xsl:template>

# xsl:value-of

-   xsl:value-of genera una sortida per pantalla d'algun valor del XML

.. code-block:: xml

    <xsl:value-of select=”expressió” />

-   Avalua l'expressió i en genera una sortida en format text

-   Només s'aplica al primer que compleixi la condició

-   Sol ser una expressió XPath

.. code-block:: xml

    <xsl:template match=”alumne”>
     <p> <xsl:value-of select=”nom” /> </p>
    </xsl:template>

-   Amb la mateixa etiqueta podem mostrar els atributs

-   Només cal precedir-los del símbol '@'

-   Mostrem els atributs de l'element en el que ens trobem

.. code-block:: xml

    <xsl:template match=”alumne”>
     <persona>
     <xsl:value-of select=”nom” />
     <xsl:value-of select=”cognoms” />
     :
     <xsl:value-of select=”@aprovat” />
     </persona>
    </xsl:template>

# xsl:apply-templates

Serveix per cridar explícitament a plantilles per un grup de nodes

-   Si té atribut 'select' només s'apliquen les plantilles als que
    compleixin la condició

.. code-block:: xml

    <xsl:template match=”alumnes”
     <xsl:apply-templates select=”expressió” />
    </xsl:template>

-   Si no en té s'aplica a tots els fills del node actual

.. code-block:: xml

    <xsl:template match=”alumnes”
     <xsl:apply-templates />
    </xsl:template>

-   Es pot fer servir per determinar l'ordre en el que s'han de
    processar els fills

.. code-block:: xml

    <xsl:template match=”/”>
     <xsl:apply-templates select=”alumnes” />
     <xsl:apply-templates select=”professor” />
    </xsl:template>

-   Això ens permetria processar primer els elements 'alumne' i després
    els 'professor'

-   Independentment de com estiguin dins del document

# mode=".."

-   Les plantilles tenen un atribut "mode" que serveix per poder
    processar els nodes varies vegades

.. code-block:: xml

    <xsl:template match=”/”>
     <xsl:apply-templates select=”alumnes” mode=”A” />
     <xsl:apply-templates select=”alumnes” mode=”B” />
    </xsl:template>
    <xsl:template match=”nom” mode=”A”>
    ...
    </xsl:template>
    <xsl:template match=”nom” mode=”B”>
    ...
    </xsl:template>

# xsl:element

-   Permet crear elements nous

.. code-block:: xml

    <xsl:element name=”persones”>
    </xsl:element>

-   L'atribut name serà el valor de l'etiqueta i és l'únic que és
    obligatori

-   Podem especificar espais de noms amb namespace

.. code-block:: xml

    <xsl:element name=”persones” namespace=”insti”>
    </xsl:element>

# xsl:attribute

-   Podem definir atributs a un element amb **xsl:attribute**

.. code-block:: xml

    <xsl:attribute name=”href”>
     http://www.iescendrassos.net
    </xsl:attribute>

-   Els atributs es poden afegir a literals dins de la plantilla

-   O per elements creats per nosaltres

.. code-block:: xml

    <a>
    <xsl:attribute name=”href”>
    http://www.iescendrassos.net
    </xsl:attribute>
    </a>

# xsl:if

-   S'avalua la expressió i si compleix es segueix amb l'expressió de
    dintre

.. code-block:: xml

    <xsl:if test=”expressió”>
     ...
    </xsl:if>

-   Per exemple:

.. code-block:: xml

    <xsl:if test=”nota &gt; 5”>
     <b>Aprovat</b>
    </xsl:if>

-   A diferència del que sol passar amb els llenguatges de programació
    no hi ha else

# xsl:choose

-   Selecciona entre un grup d'alternatives

-   És l'equivalent al 'switch' d'alguns llenguatges

.. code-block:: xml

    <xsl:choose>
     <xsl:when select=”test”> ... </xsl:when>
     <xsl:when select=”test2”> ... </xsl:when>
     <xsl:otherwise> ... </xsl:otherwise>
    </xsl:choose>

-   Podem tenir tantes opcions com ens faci falta

-   Otherwise és per totes les altres opcions

# xsl:for-each

-   Processa cada un dels nodes seleccionats per XPath

.. code-block:: xml

    <xsl:for-each select=”expressió”>

si tenim el següent xml:

.. code-block:: xml

    <?xml version=”1.0” ?>
    <alumnes>
     <nom>Pere</nom>
     <nom>Joan</nom>
    </alumnes>

amb la plantailla:

.. code-block:: xml

    <xsl:stylesheet ...>
    <xsl:template match="alumnes">
     <xsl:for-each select="nom">
     <b><xsl:value-of select="."/></b>
     </xsl:for-each>
    </xsl:template>
    </xsl:stylesheet>

dóna per resultat:

.. code-block:: xml

    <b>Pere</b>
    <b>Joan</b> 

# xsl:sort

-   Si s'afegeix un xsl:sort dins d'un for-each - el resultat és ordenat
    fent servir l'especificat en el sort amb l'atribut select

.. code-block:: xml

    <xsl:for-each select=”alumne”>
     <xsl:sort select=”cognom” />
     <persona>
     <xsl:value-of select=”nom” />
     <xsl:value-of select=”cognoms” />
     </persona>
    </xsl:for-each>

dóna per resultat:

.. code-block:: xml

     <persona>FilomenuGarcia</persona>
     <persona>FedericuPi</persona>
     <persona>ManolitoPuig</persona>
     <persona>Pito Salazar</persona>

# xsl:number

-   Serveix per numerar parts dels documents o per donar format als
    números

-   Amb l'etiqueta "format" definim de quina forma volem que es numerin
    i com es veuran

    -   "1. " numèric: 1,2,3,4...
    -   "a. " abecedari: a,b,c,d...
    -   "i. " números romans: i, ii,iii,iv,v,vi, ...
    -   "w. " paraules: un, dos, tres, ... (versió 2.0)

per exemple:

.. code-block:: xml

    <xsl:for-each select=”alumne”>
     <xsl:number format=”1. “>
     <xsl:value-of select=”nom” />
    </xsl:for-each>

-   És important la etiqueta **"level"** que ens permet definir des d'on
    comencem a comptar:

**single:** només els nodes afectats

**multiple:** afectats i antecessors

**any:** Dins de tot el document

-   Però té molts més atributs: value, etc... que permeten personalitzar
    la numeració

.. code-block:: xml

     <persona>1. Pito</persona>
     <persona>2. Federicu</persona>
     <persona>3. Filomenu</persona>
     <persona>4. Manolito</persona>

# xsl:variable

-   Podem fer servir variables per emmagatzemar cadenes, grups de nodes
    o fragments

.. code-block:: xml

    <xsl:variable name=”institut”>Cendrassos”</xsl:variable>

-   Un cop se'ls hi ha assignat valor no pot ser canviat

-   Les variables desapareixen fora de l'àmbit en que s'han creat

-   També s'hi poden posar valors a través de l'atribut 'select'

.. code-block:: xml

    <xsl:variable name="color" select='"blau"' /> 

-   Podem accedir al valor de la variable afegint el símbol **\$**
    davant del nom de la variable

.. code-block:: xml

    <xsl:value-of select="$institut"/>
    <fons coloret=”{$color}” />
    </fons>

-   Però si que podem fer:

.. code-block:: xml

    <xsl:variable name="y">
     <xsl:choose>
     <xsl:when test="$x &gt; 7">
     <xsl:text>13</xsl:text>
     </xsl:when>
     <xsl:otherwise>
     <xsl:text>15</xsl:text>
     </xsl:otherwise>
     </xsl:choose>
    </xsl:variable>

# Plantilles amb paràmetres

-   Podem definir plantilles que rebin paràmetres d'entrada amb
    xsl:param

.. code-block:: xml

    <xsl:template name=”duplica”>
     <xsl:param name=”numero” />
     <xsl:value-of select=”$numero*2” />
    </xsl:template>

-   Les podem cridar amb **xsl:call-template**

.. code-block:: xml

    <xsl:call-template name=”duplica”>
     <xsl:with-param name=”numero” select=”nota” />
    </xsl:call-template>

-   Podem usar aquests paràmetres per fer el que vulguem

-   Només ens cal especificar els paràmetres de la mateixa forma que les
    variables: \$

.. code-block:: xml

    <xsl:template name=”calculaArea”>
     <xsl:param name=”costat1” />
     <xsl:param name=”costat2” />
     <xsl:value-of select=”$costat1 * $costat2” />
    </xsl:template>

-   També es poden passar paràmetres a tota la plantilla

.. code-block:: xml

    <?xml version="1.0"?>
    <xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
     <xsl:param name="un"/>
     <xsl:param name="dos"/>
    ...

-   Per cridar-la caldrà informar al processador XSLT dels paràmetres
    que té

-   Cada processador ho fa de la seva forma

# xsl:copy / xsl:copy-of

-   Serveixen per copiar els nodes en que estem en el resultat tal com
    estan actualment (sense modificacions)

**xsl:copy** Copia els elements del node actual No copia els nodes fills
ni els atributs

**xsl:copy-of** - Copia els elements del node actual, els fills i els
atributs - Té un atribut "select" obligatori on indiquem què volem
copiar

# xsl:include / xsl:import

-   Es fan servir per fer referència a altres documents XSLT.

-   Tot el contingut d'aquests altres fulls s'afegirà a l'actual.

**`<xsl:import>`{=html}** - Pot aparèixer només al principi del
document - Té menys prioritat que les definicions del nostre document. -
D'aquesta forma podem fer subclasses

**`<xsl:include>`{=html}** - Pot aparèixer on vulguem

# Funcions

-   XSLT incorpora més de 100 funcions per treballar amb les dades

-   Hi ha funcions per manipular cadenes, números, dates i hores, nodes,
    booleans, ...

-   Per defecte el prefix de les funcions és fn:

-   L'espai de noms és a http://www.w3.org/2005/xpath-functions

.. code-block:: xml

    <xs:value-of select=”fn:current-date()” />
    <xs:value-of select=”fn:count(//alumnes)"/>
    <xsl:if test="fn:contains($nom,'Xavier')">

# Altres

El que hem vist només són algunes de les etiquetes i possibilitats

N'hi ha moltes més que ens permeten controlar la transformació fins al
darrer detall
