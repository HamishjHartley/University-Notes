1. 
a) 6
b) i) Partially wrong 2
```<sql>
create table Player {
	int PN NOT NULL,
	varchar Pname NOT NULL,
	Assert Pname as primary key
}
```
ii)  Partially wrong 2
```<sql>
INSERT INTO player(01,"FFA","FFB","01/01/2000")
```
iii) wrong 1
```<sql>
select $PN from Player_Match(MN=3) 
select from Player($PN)
```

2. a) Partially wrong 2
```<xml>
<?xml version="1.0"?>
<match>
	<MN>01</MN>
	<MFT>FFA</MFT>
	<MST>FFB</MST>
	<MD>01/01/2000</MD>
</match>
```
b) i)

ii) partially wrong 1
```<XPATH>
//matchtb/mft select=["FFA"] .. /match mn
```
iii)  partially wrong 0
```<XQuery>
for $s in //matchtb/match/mst 
where $s equals "FFA"
do total $s
```

3.a) Know how to do that 3

b)  0
```<turtle>
@prefix ex <http://knowledge.db/> .
ex:mn01 ex:played_by ex:john_smith .
ex:John_Smith ex:player_class ex:a .
ex:John_Smith ex:plays_in ex:FFA .
ex:FFA ex:has_player ex:John_Smith .
```

c) 0
```<OWL>
<owl:Class rdf:about="#Rectangle">
			<rdfs:subClassOf rdf:resource="#Shape"/>
	<owl:equialentClass>
		<owl:Restriction>
			<owl:onProperty rdf:resource="#hasAngles"/>
			<owl:qualifiedCardinality rdf:datatype="XMLSchema#nonNegativeInteger">
			4
			</owl:qualifiedCardinality>
			<owl:onClass rdf:resource="#Angle"/>
		</owl:Restriction>
	</owl:equivalentClass>
</owl:Class>
```

4.

a)
Partially Correct 5

| Classes/Instances      | Modifiers | Relations    | Definables |
| ---------------------- | --------- | ------------ | ---------- |
| **Person**             | has_name  | Plays_for    |            |
| &nbsp; Player          |           | Works_for    |            |
| &nbsp; Coach           |           | Has_position |            |
| **Club**               |           |              |            |
| &nbsp; Football club   |           |              |            |
| &nbsp; Basketball club |           |              |            |
| Liverpool FC*          |           |              |            |
| Mo Salah*              |           |              |            |
| Jurgen Klopp*          |           |              |            |
| Chicago Bulls*         |           |              |            |
| MJordan*               |           |              |            |
| Position               |           |              |            |
| Forward                |           |              |            |
b) 
1

| Domain | Relation     | Range | Object Property | Data property | Symmetric | Transistive | Functional | Inverse | Functional Reflexive |
| ------ | ------------ | ----- | --------------- | ------------- | --------- | ----------- | ---------- | ------- | -------------------- |
|        | Plays_for    |       |                 |               |           |             |            |         |                      |
|        | Works_for    |       |                 |               |           |             |            |         |                      |
|        | Has_position |       |                 |               |           |             |            |         |                      |

c)
Player, Coach are subclasses of Person 2

d) ![[Ontology_club.png]] 7

5. a)0

b)
0

total: 32/70 = 45% not good enough 


Once I have revised OWL, SPARQL and turtle my marks will be boosted substantially 



---
## Retry
1 a) 6

b) i) 3
```<sql>
create table Player(
	PN int,
	Pname varchar,
	Constraint pk primary key (PN)
);
```
ii) 3
```
insert into Match(01,"FFA", "FFB", "01/01/2000");
```
iii) 1
```
SELECT Pnames from player, player_match
WHERE (player.pn = player_match.pn) and (player_match.mn=3);
```

2 a) 3
```
<?xml version="1.0" ?>
<matchtb>
	<match MN="01">
		<MFT>FFA</MFT>
		<MST>FFB</MST>
		<MD>01/01/2000</MD>
	</match>
</matchtb>
```

b) i) 3
![[Pasted image 20240415155143.png]]
ii) 4
```
//match[mn="FFA"]@mn
```
iii) 0
```
let $X:=//match return count ($x[mst="FFB"])
```
3 a)![[Pasted image 20240415155726.png]]
3
b) 2
```
@prefix ex <http://knowledge.db/> .
ex:mn01 ex:played_by ex:John_Smith .
ex:John_Smith ex:player_class ex:A . 
ex:John_Smith ex:plays_in ex:FFA .
ex:FFA ex:has_player ex:John_Smith .
```
c) 0
```
<owl:ClassAbout="#Rectangle">
	
```


4 a) 5
b) 1 
c) 2
d) 7


Retry marks (not including Q5 as havent revised that yet)

43/60 = 71% Big difference. 

##### Weak Areas(Target these):
- OWL
- SPARQL
- SQuery
- XPath
- SQuery
- Ontology Relation Properties (Symmetric, Transistive, Functional, Inverse, Function Reflexive)

[[DIS-549 Module Overview]]