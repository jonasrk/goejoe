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