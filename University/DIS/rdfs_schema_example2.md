```rdfs
<?xml version="1.0"?>
<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/
22-rdf-syntax-ns#"
xmlns:rdfs="http://www.w3.org/2000/01
/rdf-schema#"xml:base="http://www.book.bok/books#
">

<rdfs:Class rdf:ID="book" />

<rdfs:Class rdf:ID="math_book">
	<rdfs:subClassOf
rdf:resource="#book"/>
</rdfs:Class>

</rdf:RDF>
```