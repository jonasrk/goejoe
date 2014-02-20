#Eigene

####Alle Spiele von Herstellern in Tokyo

´´´
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?game ?dev WHERE {
    ?dev <http://dbpedia.org/ontology/location> <http://dbpedia.org/resource/Tokyo> .
    ?game rdf:type <http://dbpedia.org/ontology/VideoGame> .
    ?game <http://dbpedia.org/ontology/developer> ?dev .
}
ORDER BY ?dev
´´´


#Aufgabenblatt 4

##Aufgabe 2:

http://dbpedia.org/snorql/

###a)

####Ausgabe der Artikelzusammenfassung zum deutschen Physiker "Max Planck" in deutscher Sprache.

```
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

####Wer waren die Doktoranden Max Plancks?

```
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?student WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name.
     FILTER regex(?name, "Max Planck") 
    ?person <http://dbpedia.org/ontology/doctoralStudent> ?student
}
ORDER BY ?name
```

####Welche Personen haben dieselbe Hochschule besucht wie Max Planck

```
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

####Wer von diesen Personen hat einen Nobelpreis erhalten?

```
PREFIX dbo: <http://dbpedia.org/ontology/>

SELECT ?person2 WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name .
     FILTER regex(?name, "Max Planck")
     ?person <http://dbpedia.org/ontology/almaMater> ?uni .
     ?person2 <http://dbpedia.org/ontology/almaMater> ?uni .
     ?person2 rdf:type <http://dbpedia.org/class/yago/Laureate110249011> .
}
ORDER BY ?name
``` 

####Wie könnte man die DBpedia-Ontologie verbessern, um diese Anfrage zu vereinfachen?

#?

###b)

####Finden Sie alle Indiana-Jones-Filme.
```
SELECT ?person2 WHERE {
     ?person rdf:type dbpedia-owl:Person .
     ?person dbpprop:name ?name .
     FILTER regex(?name, "Max Planck")
     ?person <http://dbpedia.org/ontology/almaMater> ?uni .
     ?person2 <http://dbpedia.org/ontology/almaMater> ?uni .
     ?person2 rdf:type <http://dbpedia.org/class/yago/Laureate110249011> .
}
ORDER BY ?name
``` 