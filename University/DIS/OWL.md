### Definition
OWL (Web Ontology Language) is a Semantic Web language designed to represent rich and complex knowledge about things, groups of things and relations between things.

OWL has six types of class descriptions:
1. A class identifier (URI reference)
2. An enumeration of the instances of a class
3. A property restriction (min, max, value)
4. The intersection of classes
5. The union of classes
6. The complement of a class

##### 1. Class Identifier
A class is described through a class name (represented as a URI)

So for a class of type Person:
```
<owl:Class rdf:ID="Person"/>
```
Plant:
```
<owl:Class rdf:ID="Plant"/>
```
Cheese:
```
<owl:Class rdf:ID="Cheese"/>
```
##### 2. Enumeration of the instances of a class
A class is described through using the onOf property and a listing(enumeration) of all class instances. 

So for class of type DeviceState:
```
<owl:Class>
	<owl:oneOf rdf:parseType="Collection">
		<owl:Thing rdf:about="#On"/>
		<owl:Thing rdf:about="#Off"/>
	</owl:oneOf>
</owl:Class>
```
For class of type season:
```
<owl:Class
	<owl:oneOf rdf:parseType="Collection">
		<owl:Thing rdf:about="#Spring"/>
		<owl:Thing rdf:about="#Summer"/>
		<owl:Thing rdf:about="#Autumn"/>
		<owl:Thing rdf:about"#Winter"/>
	</owl:oneOf>
</owl:Class>
```
##### 3. Property Restriction
A class can be described through ha restriction on a property where all the instances of this class satisfy this restriction. 

To define a shape triangle which has exactly 3 angles
```
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
##### 4. Intersection of classes
A class can be described through the intersection of other classes.

The following describes a class of one instance Hibernate.
```
<owl:Class>
 <owl:intersectionOf rdf:parseType="Collection">
  <owl:Class>
   <owl:oneOf rdf:parseType="Collection">
	   <owl:Thing rdf:about="#On"/>
	   <owl:Thing rdf:about="#Off"/>
	   <owl:Thing rdf:about="#Hibernate"/>
   </owl:oneOf>
</owl:Class>
<owl:Class>
 <owl:oneOf rdf:parseType="Sleep">
  <owl:Thing rdf:about="#Hibernate"/>
  <owl:Thing rdf:about="#Restart"/>
 </owl:oneOf>
 </owl:Class>
</owl:intersectionOf>
</owl:Class>
```

##### 5. Union of Classes
A class can be described through the union of other classes.

The following describes a class of instances On, Off and Sleep.
```
<owl:Class>
 <owl:unionOf rdf:parseType="Collection">
  <owl:Class>
   <owl:oneOf rdf:parseType="Collection>
    <owl:Thing rdf:about="#On"/>
    <owl:Thing rdf:about="#Off"/>
   </owl:oneOf>
  </owl:Class>
  <owl:Class>
    <owl:oneOf rdf:parseType="Sleep">
  </owl:oneOf>
  </owl:Class>
 </owl:unionOf>
</owl:Class

```

##### 6. Complement Of
A class can be described through desribing all of the instances that don't belong to the mentioned class. 
