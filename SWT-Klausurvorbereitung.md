##Was ist Semantic Web Fragen

####Was ist das Semantic Web?

Eine **Erweiterung des aktuellen Netzes** in der Informationen wohl-definierte Bedeutungen gegeben werden. Hierdurch wird es Computern und Menschen ermöglicht kooperativ zusammen zu arbeiten.

Die Bedeutung einer Information wird durch formale, strukturierte und standardisierte Beschreibungen (Ontologien) explizit gemacht.

Das Semantic Web ist eine Art globale Datenbank, welche ein universelles Netzwerk semantischer Aussagen enthält.

####Welche Ziele sollen mit dem Semantic Web erreicht werden?

* Die Bedeutung von Informationen automatisiert verarbeiten
* Heterogene Daten automatisiert zu integrieren und zu verknüpfen
* Implizite (nicht evidente) Informationen aus existierenden (evidenten) Informationen automatisiert abzuleiten

####Wie unterscheidet sich das Semantic Web vom World Wide Web?

Bisher ist das WWW für den Menschen strukturiert und nicht für Maschinen. Bisher wurden im WWW vornehmlich Markup-Sprachen verwendet, die lediglich Informationen zur Darstellung und nicht zur Bedeutung enthalten.


##RDF(S) Fragen

####Warum gibt es in RDF(S) nicht wirklich die Möglichkeit, semantische Inkonsistenzen zu erzeugen?

Es gibt keine explizite Negation.

####Was ist hier die Ausnahme? 

XML Clash, e.g. spitze Klammern in XMLLiteral

Es kann auch Inkonsistenzen bzgl. der Datentypen geben Int <-> float

####Welche Konsequenz ergibt sich daraus für die Wissensrepräsentation?

Es ist schwer Inkonsistenz herzuleiten, mit der man sagen kann, dass es keine Interpretation gibt, mit der ein Graph wahr werden kann.

XML Clash ist Inkonsistenz in Tripel. Aus falschen Aussagen lassen sich beliebige Aussagen herleiten. Deswegen muss RDFS Herleitbarkeit erweitert werden. I.e. entweder ein Graph lässt sich aus einem anderen herleiten, wenn er sich einfach herleiten lässt oder wenn ein XML Clash vorliegt.

Es gibt außerdem noch eine Lücke für den Fall, das blank nodes als property benutzt werden.

Die Semantik der Datentypen wird von RDFS nicht wirklich betrachtet. Daher fügt man noch Deduktionsregeln hinzu: Wenn beide den selben Wert haben, lassen sich Datentypen ersetzen. Ein Datentyp kann außerdem Subklasse eines anderen sein. 

Das waren nur zwei von mehreren Ausnahmeregeln.

####Erklären Sie die Grenzen von RDF(S) und nehmen Sie dabei Bezug auf die beiden Aufgabenteile (a) und (b)

* Keine explizite Negation

* Locality of global properties

* Disjunctive classes

* Class combinations

* Cardinality Restrictions

* Special Property Constraints

Aufgaben a und b:

    (a) Eine Herren-Basketballschaft besteht aus genau einem Center, genau zwei Forwards und genau zwei Guards. Modellieren Sie solch eine Mannschaft in RDF(S) Turtle.
    (b) Beschreiben Sie die Instanz ”ex:Flipper“ anhand der in Abb. 1 angegebenen Ontologie in natürlicher Sprache.

##Reifikation Fragen

####Erklären Sie den Begriff der Reifikation und geben Sie dazu ein Beispiel an (in natürlicher Sprache und RDF/Turtle).

Sherlock Holmes supposes that the gardener has killed the butler.

exv:SherlockHolmes exv:supposes exv:StatementOnGardener .
exv:StatementOnGardener a rdf:Statement;
    rdf:subject exv:Gardener;
    rdf:predicate exv:hasKilled;
    rdf:obect exv:Butler .

rdf:statement
rdf:subject
rdf:predicate
rdf:obect

####Warum ist die Reifikation im Semantic Web von großer Bedeutung?

Um Aussagen über Aussagen machen zu können.

Aussagen darüber machen, wer etwas gesagt hat oder wo etwas steht. (Provenienzangaben) Man kan darauf aufbauen Aussage trauen oder nicht trauen. (Reliability & Trust)

####Warum ist die Umsetzung/Verwendung von Reifikation problematisch?

Wenn man als Objekt wieder Statement angibt: Schachteln und Circular Dependencies/Rekursion.

Gefahr 1: Rekursive Strukturen aufbauen, die sich ins unendliche stapeln.
Gefahr 2: Eigentlich gibt es strikte Klassenzugehörigkeit/Typisierung, hier macht man aber aus einem Property ein Objekt, i.e. eine Ressource. So verwischt die strikte Typisierung.

####Welche Unterschiede bestehen in OWL 1 DL und OWL 2 DL bezüglich der Reifikation. Wie wird die Problematik der Reifikation in OWL 2 DL gelöst?





##SPARQL Anfragen formulieren

Gegeben sei die folgende Wissensbasis:

> @prefix ex:    > <http://example.org/> .
> @prefix foaf:  <http://xmlns.com/foaf/0.1/> .
> Klausur 21.02.2011
> ￼@prefix xsd:
> _:a  a
>      foaf:name
>      foaf:homepage
>      foaf:mbox
>      ex:worksFor
> _:b  a
>      foaf:name
>      foaf:mbox
>      foaf:homepage
>      ex:ageInYears
>      foaf:knows
> _:c  a
>      foaf:name
>      foaf:knows
>          [ a
> <http://www.w3.org/2001/XMLSchema#> .
> ex:worksFor
> foaf:homepage ].
> foaf:Person ;
> ex:examplecorp ;
> <http://work.examplecorp.com/trudy/> ;
> foaf:Person ;
> "Alice" ;
> <http://work.examplecorp.org/alice/> ;
> <mailto:alice@examplecorp.org> ;
> ex:examplecorp .
> foaf:Person ;
> "Bob"@en ;
> ""; <http://work.examplecorp.com/bob/> ; "24"ˆˆxsd:integer ;
> _:c .
> foaf:Person ;
> "Carlos"@es ;
> _:b,

Formulieren Sie SPARQL Anfragen, um die folgenden Sachverhalte aus der Wissensbasis zu ermitteln. Geben Sie fu ̈r jede Anfrage die Zahl der zuru ̈ckgelieferten Ergebnisse (Zeilen) an.
(a) Alle Personen mit jeweiligen Angaben zu Namen, Homepage, Mailboxadresse und Alter, soweit bekannt.
(b) Alle Personen, deren Name ein ’a‘ (unabha ̈ngig von der Groß-/ Kleinschreibung) entha ̈lt oder unter 18 Jahre alt sind.
(c) Alle Personen, die fu ̈r ExampleCorp arbeiten oder jemanden kennen, der fu ̈r ExampleCorp arbeitet.


2



Gegeben sei die folgende Wissensbasis:
@prefix ex:    <http://example.org/> .
@prefix skos:  <http://www.w3.org/2004/02/skos/core#> .
@prefix xsd:   <http://www.w3.org/2001/XMLSchema#> .
ex:A a skos:Concept ; skos:prefLabel "Kartenspiel"@de ; skos:narrower ex:B,ex:C,ex:D.
ex:B a               skos:Concept ;
     skos:prefLabel  "Poker"ˆˆxsd:string ;
     skos:related    ex:E .
ex:C a               skos:Concept ;
     skos:prefLabel  "Skat"@de .
Klausur 07.02.2012
12 Punkte
￼ex:D a skos:Concept ;
skos:prefLabel "Baccara" ;
skos:definition "ein Kartengl ̈ucksspiel; wird in Kasinos angeboten" .
ex:E a               skos:Concept ;
     skos:prefLabel  "Spielbank"@de ;
skos:altLabel
skos:related
"Kasino"@de ;
ex:B ,
[ a               skos:Concept ;
  skos:prefLabel  "Jeton" ;
skos:related ex:E ].
Formulieren Sie SPARQL Anfragen, um die folgenden Sachverhalte aus der Wissensbasis zu ermitteln. Geben Sie fu ̈r jede Anfrage die Zahl der zuru ̈ckgelieferten Ergebnisse (Zeilen) an.
(a) Alle Konzepte1. Geben Sie zu jedem Konzept die verfu ̈gbaren Angaben zu bevorzugtem Bezeichner, alternativem Bezeichner und Definition aus. (4 Punkte)
(b) Alle Konzepte, die mehr als ein Unterkonzept2 besitzen oder deren Vorzugsbezeichner ein ”B“ (unabha ̈ngig von der Groß-/Kleinschreibung) entha ̈lt. (4 Punkte)
(c) Alle Konzepte, die mit dem Konzept ”Kasino“ verwandt (skos:related) sind oder ein Unterkonzept besitzen, das mit dem Konzept ”Kasino“ verwandt ist. (4 Punkte)