```rdf
<?xml version="1.0"?>
<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/2
2-rdf-syntax-ns#"
xmlns:rdfs="http://www.w3.org/2000/01/r
df-schema#"xml:base="http://www.book.bok/books#"
>
<rdf:Description rdf:ID="book">
	<rdf:type
rdf:resource="http://www.w3.org/2000/01
/rdf-schema#Class"/>
</rdf:Description>

<rdf:Description rdf:ID="math_book">
	<rdf:type
rdf:resource="http://www.w3.org/2000/01
/rdf-schema#Class"/>
	<rdfs:subClassOf
rdf:resource="#book"/>
</rdf:Description>

</rdf:RDF>
```