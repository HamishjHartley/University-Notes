[Data Models](Data%20Models.md)
#### Definition
XML stands for Extensible Markup Language, designed to carry data. It can describe data.

#### Example

| Title  | Author | year |
| ------ | ------ | ---- |
| Java   | John   | 1999 |
| Pascal | Sara   | 1980 |
| Basic  | Mary   | 1975 |
| Oracle | Emad   | 1999 |
| .....  | .....  | .... |
`<Books>`
	`<Book>`
		`<Title>Java</Title>`
		`<Author>John</Author>`
		`<Year>1999</Year>`
	`</Book>`
`....`
`....`
	`<Book>`
		`<Title>Oracle</Title>`
		`<Author>Emad</Author>`
		`<Year>1999</Year>`
	`</Book>`
`....`
`</Books>`

#### Anatomy of XML Document
XML documents start with an XML declaration and Processing instruction as shown below:
`<?xml version:”1.0”?>`
`<?xml-stylesheet type="text/xsl" href=“template.xsl"?>`
this is then followed by comments:
`<!-- File name: Bibliography.xml -->`
Then Root/Document element, with elements nested within the root element):
`<Book ISBN=“1-111-122”>`
`<Title> Java </Title>`
`<Author> John </Author>`
`<Year> 1998 </Year>`
`</Book>`
`.`
`<Book>`
`<Title> Oracle </Title>`
`<Author> Emad </Author>`
`<Year> 1999 </Year>`
`</Book>`

#### Components of an XML document
Elements and attributes. Elements have a beginning and ending tag, and attributes are used to describe an element, furthermore they can only appear on the beginning tag.
##### Elements
XML elements are everything from start tag to end tag, they are extensible and have the relationship parent, child and sibling. They have the following naming rules: Names can contain letters, number or other characters. They cannot start with a number or punctuation character or the letters xml, and they cannot contain spaces.

##### Attributes
stores data about elements, however they cannot store multiple values like a child element can, and they are not easily expandable. 

#### Well-Formed XML rules
1. Begins with XML declaration
2. Has one unique root element
3. All start tags must match end-tags
4. XML tags are case sensitive
5. All elements must be closed
6. All elements must be properly nested
7. All attribute values must be quoted
8. XML entities must be used for special characters.

#### XML DTD: Data Type Definition
A DTD(Data type definition) defines the legal elements of an XML document, an alternative to this being an XML Schema which

DTDs are used so independent groups of people can agree on a common DTD for data exchange. It can be used to verify received data is valid, and also to verify own data.
##### Example DTD implementation

###### XML Document
`<novel><foreword>`
`<paragraph> This is a great novel </paragraph>`
`</foreword>`
`<chapter number="1">`
`<paragraph>It was a dark and stormy night.</paragraph>`
`<paragraph>Suddenly, a shot rang out!</paragraph>`
`</chapter>`
`</novel>`

##### Equivalent DTD
`<!DOCTYPE novel [`
`<!ELEMENT novel (foreword, chapter+)>`
`<!ELEMENT foreword (paragraph+)>`
`<!ELEMENT chapter (paragraph+)>`
`<!ELEMENT paragraph (#PCDATA)>`
`<!ATTRIBUTE chapter number CDATA #REQUIRED>`
`]>`

#### XML Schema
##### XML document
`<?xml version="1.0"?>`
`<note>`
`<to>Tove</to>`
`<from>Jani</from>`
`<heading>Reminder</heading>`
`<body> Don't forget me this weekend!</body>`
`</note>`

##### Equivalent XML Schema
`<?xml version="1.0"?>`
`<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"`
`targetNamespace="http://www.w3schools.com"`
`xmlns="http://www.w3schools.com" elementFormDefault="qualified">`
`<xs:element name="note">`
`<xs:complexType>`
`<xs:sequence>`
`<xs:element name="to" type="xs:string"/>`
`<xs:element name="from" type="xs:string"/>`
`<xs:element name="heading" type="xs:string"/>`
`<xs:element name="body" type="xs:string"/>`
`</xs:sequence>`
`</xs:complexType>`
`</xs:element>`
`</xs:schema>`
#### Parser
An XML parser is an API that reads the contents of an XML document.

#### Information Retrieval using XPath and XQuery

##### XPath
`doc("books.xml")/bookstore/book[price>30]/title`

##### XQuery equivalent
`for $x in doc("books.xml")/bookstore/book`
`where $x/price>30`
`return $x/title`
##### XPath
Syntax used for selecting parts of an XML Document

##### XQuery
Built on XPath expressions
###### XQuery FLWOR Expression
FLWOR stands for "For, Let, Where, Order by, Return"

`for $x in doc("books.xml")/bookstore/book`
`where $x/price>30`
`order by $x/title`
`return $x/title`

In the above XQuery, the for clause selects all book elements under the bookstore element into a variable called $x. The let clause allows to define variable and assign it to a sequence. The where clause selects only book elements with a price element with a value greater than 30. The order by sorts the results according to the specified element. The order by sorts the results according to the specified element. The return clause specifies what should be returned. 

