### Week 1 - Relational Databases
1. Draw an Entity Relationship diagram(ERD) for a give scenario
2. Write the required SQL statements to implement your ERD
3. Write the suitable SQL SELECT statements to retrieve information based on some requirements
### Week 2 - XML
##### 1. Write an XML file that is equivalent to a relational table
###### Relational Table

People

| Name  | Tel         | email           | Dob        |
| ----- | ----------- | --------------- | ---------- |
| Peter | 07598772665 | peter@gmail.com | 26/4/1934  |
| Robin | 07598262665 | robin@gmail.com | 18/12/2001 |
| Simon | 07389632678 | simon@gmail.com | 21/12/1968 |

Job

| Role       | Dob        |
| ---------- | ---------- |
| Retired    | 26/4/1934  |
| Bar_tender | 18/12/2001 |
| Finance    | 21/12/1968 |
###### XML equivalent
```xml
<?xml version="1.0"?>
<people_jobs>
    <people>
        <person dob="26/4/1934">
            <name>"Peter"</name>
            <tel>07598772665</tel>
            <emai>"peter@gmail.com"</emai>
        </person>
        <person dob="18/12/2001">
            <name>"Robin"</name>
            <tel>07598262665</tel>
            <email>"robin@gmail.com"</email>
        </person>
        <person dob="21/12/1968">
            <name>"Simon</name>
            <tel>07389632678</tel>
            <email>"simon@gmail.com</email>
        </person>
    </people>
    <jobs>
        <job dob="26/4/1934">
            <role>"Retired"</role>
        </job>
        <job dob="18/12/2001">
            <role>"Bar_tender"</role>
        </job>
        <job dob="21/12/1968">
            <role>"Finance</role>
        </job>
    </jobs>
</people_jobs>
```
##### 2. Draw an XML tree


###### XML file
```xml
<?xml version="1.0" ?>
<library>
    <book>
        <chapter></chapter>
        <chapter>
            <section>
                <paragraph>A</paragraph>
                <paragraph>B</paragraph>
            </section>
        </chapter>
    </book>
</library>
```

###### Tree equivalent

![](_attachments/Pasted%20image%2020240403115114.png)
##### 3. Write an XML Schema or DTD for a given XML file
###### 1. XML
```xml
<?xml version="1.0" ?>
<novel>
	<foreword>
		<paragraph>This is a great novel</paragraph>
	</foreword>
		<chapter number="1">
			<paragraph>It was a dark and stormy night.</paragraph>
			<paragraph>Suddenly, a short rang out!</paragraph>
		</chapter>
</novel>
```
###### 1. DTD equivalent
```dtd
<!DOCTYPE novel [
<!ELEMENT novel (foreword, chapter+)>
<!ELEMENT foreword (paragraph+)>
<!ELEMENT chapter (paragraph+)>
<!ELEMENT paragraph (#PCDATA)>
<!ATTRIBUTE chapter number CDATA #REQUIRED>
]>
```
###### 2. XML
```xml
<weatherReport>
    <date>05/29/2002</date>
    <location>
        <city>Philadelphia</city>
        <state>PA</state>
        <country>USA</country>
    </location>
    <temperature-range>
        <high scale="F">84</high>
        <low scale="F">51</low>
    </temperature-range>
</weatherReport>
```
###### 2. DTD equivalent
```dtd
<!DOCTYPE weatherReport[
    <!ELEMENT weatherReport (date, location, temperature-range)>
    <!ELEMENT date (#PCDATA)>
    <!ELEMENT location (city, state, country)>
    <!ELEMENT city (#PCDATA)>
    <!ELEMENT state (#PCDATA)>
    <!ELEMENT country (#PCDATA)>
    <!ELEMENT temperature-range ((low, high)|(high, low))>
    <!ELEMENT low (#PCDATA)>
    <!ELEMENT high (#PCDATA)>
    <!ATTLIST low scale (C|F) #REQUIRED>
    <!ATTLIST high scale (C|F) #REQUIRED>
]>
```

##### 4. Use XPath to find answers from an XML file
###### XML file
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mondial SYSTEM "mondial.dtd">
<mondial>
<river id="river-Clyde" country="GB" island="island-GreatBritain">
   <name>Clyde</name>
   <located country="GB"/>
   <to watertype="sea" water="sea-Irische_See"/>
   <length>176</length>
   <source country="GB">
      <latitude>55.41</latitude>
      <longitude>-3.65</longitude>
      <elevation>278</elevation>
   </source>
</river>
<river id="river-Rhein" country="F D CH FL A NL">
   <name>Rhein</name>
   <located country="D"/>
   <located country="F"/>
   <located country="A"/>
   <located country="CH"/>
   <located country="NL"/>
   <to watertype="sea" water="sea-Nordsee"/>
   <length>1324</length>
   <source country="CH">
      <latitude>46.6</latitude>
      <longitude>8.7</longitude>
      <elevation>2345</elevation>
   </source>
</river>
<river id="river-Ruhr" country="D">
   <name>Ruhr</name>
   <located country="D" province="prov-Germany-11"/>
   <to watertype="river" water="river-Rhein"/>
   <length>219</length>
</river>
</mondial>
```
###### XPath

|     | Question                                                                        | XPath                                                 | Output                                |
| --- | ------------------------------------------------------------------------------- | ----------------------------------------------------- | ------------------------------------- |
| A   | What are the lengths of the rivers                                              | `//river/length`                                      | length:176, length: 1324, length: 219 |
| B   | What are the latitiudes of the sources of rivers?                               | `//river/source/latitude`                             | 55.41, 46.6                           |
| C   | What is the name of the river that is located in the country "GB"               | `//river[@country="GB"]/name`                         | Clyde                                 |
| D   | What is the elevation of the source of rivers that start in Switzerland         | `//river/[source@country="CH"]/elevation`             | 2345                                  |
| E   | What is the river name that empties into see-Nordsee                            | `//river/to@water="sea-Nordsee"/../name`              | Rhein                                 |
| F   | How many rivers have lengths greater than 500?                                  | `count(//river[length>500])`                          | 1                                     |
| G   | What is the total length in the data structure?                                 | `sum(//river/length)`                                 | 1719                                  |
| H   | How long is the river before the river is before the Ruhr in the data structre? | `//river[name="Ruhr"]/preceding-sibling::*[2]/length` | 176                                   |
| I   | What is the name of the next river to the river 'Clyde' in the data set?        | `//river[name="Clyde"]/following-sibling::*[1]/name`  | Rhein                                 |

##### 5. Use XQuery to find answers from an XML file
###### XML file
(same as pt .
4)
###### XQuery

|     | Question                                                                                   | XPath                                                                                            | Output        |
| --- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ------------- |
| A   | What are the lengths of the rivers                                                         | `For $x in //river` `return $x//length`                                                          | 175, 1324,219 |
| B   | What are the latitudes of the sources of rivers?                                           | `for $x in //river/source`<br>`return $x//latitude`                                              | 55.41, 46.6   |
| C   | What is the name of the river that is located in the country "GB"                          | `for $x in //river`<br>`where $x/@country="GB"`<br>`return $x/name`                              | Clyde         |
| D   | What is the elevation of the source of rivers that start in Switzerland (denoted by "CH")? | `for $x in //river/source`<br>`where $x/@country="CH"`<br>`return $x/elevation`                  | 2345          |
| E   | What is the river name that empties into see-Nordsee                                       | `for $x in //river` `where $x/to/@water="see-Nordsee"` `return $x/name`                          | Rhein         |
| F   | How many rivers are included?                                                              | `let $x := //river/name` `return count ($x[length>500]`                                          | 1             |
| G   | What is the name of the next river to the river 'Clyde' in the data set?                   | `for $x in //river`<br>`where $x/name = "Clyde"`<br>`return $x/following-<br>sibling::*[1]/name` | Rhein         |


### Week 3 - Web 3.0
This lecture in exam!
Based on the forthcoming lectures, to work and
exercise some elements of semantic web stack that
are explained in this lecture
### Week 4 - RDF
##### 1. Describe RDF triples in English giving their meaning

##### 2. Draw RDF graph of a given RDF file
###### 2.1
```rdf
<?xml version="1.0"?>

<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
xmlns:ds="https://www.example.com/rdf/">

<rdf:Description rdf:about="https://www.strathclyde.ac.uk">
    <ds:title>University of Strathclyde</ds:title>
    <ds:location>Glasgow </ds:location>
</rdf:Description>

</rdf:RDF>
```
![](_attachments/Pasted%20image%2020240404085219.png)
###### 2.2
```rdf
<rdf:Description rdf:about
="http://sw.edu/#capital_of">
    <rdf:type rdf:resource="http://www.w3.org/1999/02/22-rdf-syntax-ns#Property"/>
    <rdfs:domain rdf:resource="http://sw.edu/#city" />
    <rdfs:range rdf:resource="http://sw.edu/#country" />

</rdf:Description>
```
![](_attachments/Pasted%20image%2020240404101525.png)
##### 3. Write RDF file from a given RDF graph
![](_attachments/Pasted%20image%2020240404103317.png)
```rdf
?xml version="1.0"?>
<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
xmlns:dscr="https://www.rfc-editor.org/rfc/rfc3187/">

<rdf:Description rdf:about="https://www.Macbeth.bok">
	<dscr:title>Macbeth</dscr:title>
	<dscr:author rdf:resource"https://www.amazon.co.uk/William-Shakespeare/" />
	<dscr:isbn>978-1841461168</dscr:isbn>
</rdf:Description>

</rdf:RDF>
```

##### 4. Construct RDF schema of a given RDF graph

| RDF                     | RDFS                    |
| ----------------------- | ----------------------- |
| [rdf_schema_example1](rdf_schema_example1.md) | [rdfs_schema_example2](rdfs_schema_example2.md) |


##### 5. Integrate relational tables using RDF graph
###### Db1
**Table Book**

| ISBN           | Author | Title                  | Publisher | Year |
| -------------- | ------ | ---------------------- | --------- | ---- |
| 777-1838648072 | A100   | C++ Game Programming   | P10       | 2019 |
| 777-1838648888 | A101   | Python Game programing | P20       | 2020 |

**Table Author**

| ID   | Name       | Genre       |
| ---- | ---------- | ----------- |
| A100 | John Smith | Programming |
| A101 | Xiang Lui  | Programming |

**Table Publisher**

| ID  | Name   | website        |
| --- | ------ | -------------- |
| P10 | Landar | www.landar.pub |
| P20 | Diwan  | www.diwan.pub  |

**RDF graph**
![](_attachments/Pasted%20image%2020240404114442.png)
###### Db2
**Table bookDetails**

| ISBN           | Language | Paperback | Dimensions         |
| -------------- | -------- | --------- | ------------------ |
| 777-1838648072 | English  | 600 pages | 19.05x3.02x23.5 cm |
| 777-1838648888 | English  | 750 pages | 20.05x2.50x23.5 cm |

**RDF graph**
![](_attachments/Pasted%20image%2020240404114755.png)
###### Combining Db1 and Db2 into one RDF graph
![](_attachments/Pasted%20image%2020240404114842.png)

### Week 5 - Designing Ontologies
**Design an ontology of a given scenario that can answer a given competency question(s). Then draw this ontology diagram.**
##### Example 1.
*"Pizza, Vegetarian Pizza and Pizza Topping are well known concepts. Each
Pizza has Pizza Topping. A Vegetable Topping is a type of Pizza topping. An example of Vegetable Topping is a Tomato Topping. Pizza Topping can also have Spiciness . A Vegetarian Pizza is a Pizza that has only Vegetable
Topping."*
###### Competency questions (Knowledge to be entailed in the ontology):
- How spicy is a tomato topping?
- Can a vegetarian pizza have a tomato topping?


| Classes/Instances                                                                      | Modifiers | Relation                      | Definable        |
| -------------------------------------------------------------------------------------- | --------- | ----------------------------- | ---------------- |
| Pizza <br> Pizza topping <br>     Vegetable topping <br>     Tomato topping (instance) | Spiciness | has_topping <br>has_spiciness | Vegetarian_Pizza |

![](_attachments/Pasted%20image%2020240404174103.png)
##### Example 2.
*"Students study at universities however workers work in workplaces. Both
worker and student have first names and surnames while universities and
workplaces have names and locations. Naturally, there are students who
work as well, let’s call them StuWorker. John Smith is a student who works
in SupStore and studies at the university of Strathclyde"*
###### Competency questions:
-Can a StuWorker study in a university?


| Classes/Instances                                                                           | Modifiers                                      | Relation                 | Definable                            |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------- | ------------------------ | ------------------------------------ |
| Person <br>    Student <br>    Worker <br> Place <br>     Workplace <br>     University<br> | firstName <br> surname <br> name <br> location | works_in <br> Studies_at | StuWorker <br> John_Smith (instance) |

![](_attachments/Pasted%20image%2020240404175541.png)
##### Example 3.
*"Animals and plants are both a living thing. Nothing can be an animal and a plant at the same time. Trees are a type of plant, both branches and leaves are parts of plants. Herbivores are animals that only eat parts of plants. However, carnivores are animals that eat animals. Giraffes are herbivores, and they eat acacia leaves. Lions are animals that eat only herbivores."*
###### Competency questions:
- Can a lion eat a giraffe?

| Classes/ instances                                                                                                       | Modifiers | Relation         | Definable                                                                   |
| ------------------------------------------------------------------------------------------------------------------------ | --------- | ---------------- | --------------------------------------------------------------------------- |
| LivingThing <br>     Animal <br>     Plant <br>          Tree <br>     PlantPart <br>          Branch <br>          Leaf |           | eat <br> part_of | Carnivore <br>     lion(instance) <br> Herbivore <br>     giraffe(instance) |

![](_attachments/Pasted%20image%2020240404182440.png)
### Week 6 - Ontologies (Cont')
##### 1. Develop an ontology, draw a table that lists object and data properties. For each property show both Domain and range, then identify relation characteristics(functional, inverse functional, symmetric, transitive, reflexive)

*"Holiday packages. The themes of holiday packages such as culture, sightseeing, safari. Inclusive holiday packages. Accommodation-only holiday packages. Hotels. The Marriott Hotel Glasgow. Hotel amenities such as bar, lounge, room service, pool, spa. Hotel star rating. A four-star hotel. Holiday package booking. Person, Customer, Salesperson."*

The produced ontology should allow the following information to be recovered:
- The names of the customers who book sightseeing holiday packages
- The names of salespersons who took bookings for safari holiday packages.
- The holiday packages that use the Marriott Hotel Glasgow

##### Step-by-step:
1. List the standalone classes, modifiers, relations and definables.
2. Distinguish between classes and instances.
3. Indicate the hierarches for classes.
4. For relations, give the range and domain and indicate whether they are symmetric, transitive, inverse functional, functional or reflexive. 
5. Give a definition of each definable, state any assumptions that you make.

| Domain          | Relation        | Range           | Symmetric | Transistive | Functional | Inverse Func | Reflexive |
| --------------- | --------------- | --------------- | --------- | ----------- | ---------- | ------------ | --------- |
| Booking         | For             | Holiday Package |           |             | X          |              |           |
| Holiday package | Booken on       | Booking         |           |             |            | X            |           |
| Booking         | Has Cust        | Customer        |           |             | X          |              |           |
| Customer        | Made Booking    | Booking         |           |             |            | X            |           |
| Booking         | Has Salesperson | SalesPerson     |           |             | X          |              |           |
| SalesPerson     | Took Booking    | Booking         |           |             |            | X            |           |
| Holiday Package | Uses            | Hotel           |           |             |            |              |           |
| Hotel           | Used on         | Holiday Package |           |             |            |              |           |
| Hotel           | Has Amenity     | Amentiy         |           |             | X          |              |           |
| Amenity         | Is Amenity of   | Hotel           |           |             |            | X            |           |
| Holiday Package | Has Theme       | Theme           |           |             |            |              |           |
| Person          | Has Name        | Name            |           |             |            |              |           |
| Hotel           | Has Rating      | Star Rating     |           |             |            |              |           |

### Week 7 - OWL
##### 1. Define a class using OWL
###### Triangle
*This class is described through a restriction on a property where all the instances of this class satisfy this restriction.*
```<owl>
<owl:Class rdf:about="#Triangle">
		<rdfs:subClassOf rdf:resource="#Shape"/>
	<owl:equivalentClass>
		<owl:Restriction>
		<owl:onProperty rdf:resource="#hasAngles"/>
		<owl:qualifiedCardinality rdf:datatype="XMLSchema#nonNegativeInteger">
		3
		</owl:qualifiedCardinality>
	<owl:onClass rdf:resource="#Angle"/>
	</owl:Restriction>
	</owl:equivalentClass>
</owl:Class>
```

###### 2. Define an object property or a data property using OWL
*"Define studies"*
![[Pasted image 20240412100755.png]]

```<owl>
<owl:ObjectProperty rdf:ID="studies">
	<rdfs:domain rdf:resource="#Student"/>
	<rdfs:range rdf:resource="#Module"/>
</owl:ObjectProperty>
```
###### 3. Explain/ describe a snippet of OWL code(For example as shown below):
	 Draw the graph corresponding to this set
	 Explain the narrative meaning of this graph
```<owl>
<owl:Class rdf:about="#Man">
	<rdfs:subClassOf rdf:resource="#Person"/>
	<owl:disjointWith rdf:resource="#Woman"/>
</owl:Class>

<owl:Class rdf:about="#Woman">
	<rdfs:subClassOf rdf:resource="#Person"/>
	<owl:disjointWith rdf:resource="#Man"/>
</owl:Class>

<owl:ObjectProperty rdf:about="#hasMember">
	<rdfs:subPropertyOf rdf:resource="http://www.w3.org/2002/07/owl#topObjectProperty"/>
	<rdfs:domain rdf:resoruce="#SmallTeam"/>
	<rdfs:range>
		<owl:Restriction>
			<owl:onProperty rdf:resource="hasMember"/>
			<owl:maxCardinality rdf:datatype="XMLSchema#nonNegativeInteger">5</owl:maxCardinality>
			<owl:onClass rdf:resource="#Person"/>
		</owl:Restriction>
	</rdfs:range>
</owl:ObjectProperty>

<owl:Class rdf:about="#ModernTeam">
	<rdfs:subClassOf rdf:resource="#SmallTeam"/>
	<rdfs:subClassOf>
	<owl:Restriction>
		<rdfs:subClassOf rdf:resource="#hasMember"/>
		<owl:maxCardinality rdf:datatype="XMLSchema#nonNegativeInteger">4</owl:maxCardinality>
		<owl:onClass rdf:resource="#Woman"/>
	</owl:Restriction>
	</rdfs:subClassOf>
</owl:Class>
	
```
###### Solution
- This is an Ontology that describes
5 classes which are
- Person and two sub- classes of
Person: (Man and Woman)
- SmallTeam and a sub class of it:
ModernTeam
- hasMember is an object property
- SmallTeam can have a Max of five
members since the relation is
restricted with maxCardinality
constraint
- ModernTeam can have a Max of
four women since the relation is
restricted with maxCardinality
constraint
### Week 8 - SPARQL
###### 1. Write one or two SPARQL queries against a given Turtle document
```<turtle>
@prefix ex: <http://example.org/> .
@prefix ds: <http://knowledge/> .
ex:john
ds:FN "John Smith" ;
ds:Job "Professor" ;
ds:gender "Male" ;
ds:hasAge "32" ;
ds:workAt ex:Strath .
ex:strath
ds:title "Strathclyde";
ds:hasDept ex:cis;
ds:located ex:glasgow .
ex:cis
ds:title "CIS" ;
ds:belongTo ex:strath ;
ds:hasCourse ex:acs.
```
![[Pasted image 20240412102857.png]]

###### Query 1
*Write a query to list all the triples butlimit the returned solutions to three triples.*

```<SPARQL>
SELECT *
WHERE {?s ?p ?o.}
LIMIT 3
```

|         | Result    |              |
| ------- | --------- | ------------ |
| ?s      | ?o        | ?p           |
| ex:john | ds:FN     | "John Smith" |
| ex:john | ds:job    | "Professor"  |
| ex:john | ds:gender | "Male"       |
###### Query 2
*Write a query to return full names of anyone whose job is Professor.*

```<SPARQL>
SELECT ?fullname
WHERE {s? ds:FN ?fullname;
		  ds:job ?job .
	FILTER (?job="Professor").
}
```

| Result     |
| ---------- |
| ?fullname  |
| John Smith |

###### Query 3
*Write a query to return full name of anyone whose job is Professor OR has age greater than or equal to 32.*
```<SPARQL>
SELECT ?fullname
WHERE {s? ds:FN ?fullname;
		  ds:hasAge ?age;
		  ds:job ?job.
FILTER (?job="Professor" || ?age>=32).
}
```

| Result     |
| ---------- |
| ?fullname  |
| John Smith |

###### Query 4
*Write a query to return the full name of anyone who works at a work place that has a department that has a title "CIS*. Order the results in descending order.
```<SPARQL>
SELECT ?fullname
WHERE {?s ds:FN ?fullname;
		  ds:workAt ?wrk.
	   ?wrk ds:hasDept ?dpt.
	   ?dpt ds:title "CIS".}
ORDER BY DESC(?fullname)
```

| Result     |
| ---------- |
| ?fullname  |
| John Smith |

###### Query 5
*Are there any Professor in this dataset?*
```<SPARQL>
ASK{?s ds:job "Professor".}
```

| Result |
| ------ |
| "TRUE" |
|        |

### Week 9 - Description on Logic/Reasoning
###### 1. Express knowledge statements as DL axioms
*"All Mothers are Parent"*

###### 2. Deduce extra knowledge that is not stated in the statements


