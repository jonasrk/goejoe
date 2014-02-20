Aufgabenblatt 4

Aufgabe 2:

http://dbpedia.org/snorql/

Ausgabe der Artikelzusammenfassung zum deutschen Physiker "Max Planck" in deutscher Sprache.

<code>

PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?abstract WHERE {

     ?person rdf:type dbpedia-owl:Person .

     ?person dbpprop:name ?name.

     ?person dbpedia-owl:abstract ?abstract

     FILTER langMatches( lang(?abstract), "de")

     FILTER regex(?name, "Max Planck") 

}

ORDER BY ?name

</code>