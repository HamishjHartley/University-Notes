*1.a)*

*b)(i)* 
```
create table Product(
	Pid int,
	Pname varchar,
	Constraint pkPid PRIMARY KEY (Pid)
);
```
*(ii)* 
```
insert into Product(Pid, Pname)
values (1, "Washing liquid");
```
*(iii)* 
```
SELECT ratio, Iname
FROM Prod_Ingred, Ingredient
WHERE Prod_Ingred.lid = Ingredient.lid AND Prod_Ingred.Pid=1
```
*2.a)* 
```<xml>
<?xml version="1.0"?>
<Prod_IngredTB>
	<prod_ingred>
		<Pid>1</Pid>
		<lid>1</lid>
		<ratio>60%</ratio>
	</prod_ingred>
</Prod_IngredTB>
```
*b)iii)*  
```
//book[author="John Burrowes"]/@isbn
```
*iv)* 
```
for $x in //book
where $x/price<=9
return count($x)
```
*3.c)*  
```
<owl:Class>
	<owl:intersectionOf rdf:parseType="Collection">
	 <owl:Class>
	  <owl:oneOf rdf:parseType="Collection">
		  <owl:Thing rdf:about="#On"/>
		  <owl:Thing rdf:about="#Off"/>
		  <owl:Thing rdf:about="#Hibernate"/>
		  <owl:oneOf rdf:parseType="Sleep">
		  <owl:Thing rdf:about="#Sleep"/>
		  <owl:Thing rdf:about="#LogOff"/>
	</owl:oneOf>
	</owl:Class>
	</owl:intersectionOf>
</owl:Class>
```
*5.a)* 
```
SELECT ?s ?p ?o
WHERE {?s ?p ?o.}
```
*b)* 
```
@prefix ex: <http://example.org/> .
@prefix dc: <http://knowledge.org/> .

ex:John dc:type "Author" ;
        dc:given "John" ;
        dc:family "Smith" ;
        dc:hasAge 32 ;
        dc:wrote ex: TSV .

ex:TSV dc:type "Book" ;
        dc:author ex:John ;
        dc:title "The Seven Factor" ;
        dc:year 1990 ;
        dc:isbn "101010101010" ;
        dc:price 29 .
```
``
```
SELECT ?s
WHERE {?s dc:given ins:John.}
```