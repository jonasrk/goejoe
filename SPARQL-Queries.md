Aufgabenblatt 4

Aufgabe 2:

http://dbpedia.org/snorql/

Ausgabe der Artikelzusammenfassung zum deutschen Physiker "Max Planck" in deutscher Sprache.

```sql
PREFIX dbo: <http://dbpedia.org/ontology/>
SELECT ?abstract WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name.
     ?person dbpedia-owl:abstract ?abstract
     FILTER langMatches( lang(?abstract), "de")
     FILTER regex(?name, "Max Planck") 
}
ORDER BY ?name
```

Wer waren die Doktoranden Max Plancks?

```sql
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?student WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name.
     FILTER regex(?name, "Max Planck") 
    ?person <http://dbpedia.org/ontology/doctoralStudent> ?student
}
ORDER BY ?name
```

Welche Personen haben dieselbe Hochschule besucht wie Max Planck

```sql
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?person2 WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name .
     FILTER regex(?name, "Max Planck")
     ?person <http://dbpedia.org/ontology/almaMater> ?uni .
     ?person2 <http://dbpedia.org/ontology/almaMater> ?uni .
}
ORDER BY ?name
```