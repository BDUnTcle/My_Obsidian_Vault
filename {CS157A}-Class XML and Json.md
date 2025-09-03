---
create date: 2024-09-11
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
---
# Review List
>[! abstract] Main Topics
>1. Know what XML is and compare it to relational model
>2. 

---
# In-Class Problems
## XML
>[!question] What is XML?
>XML means "**extensible markup language**"
- Standard for data representation and exchange
- Designed initially for exchanging information on the internet
```xml
<?xml version="1.0" ?>
<!--Bookstore with no DTD-->
<Bookstore>
   <Book ISBN="ISBN-0-13-713526-2" Price="85" Edition="3rd">
      <Title>A First Course in Database Systems</Title>
      <Authors>
         <Author>
            <First_Name>Jeffrey</First_Name>
            <Last_Name>Ullman</Last_Name>
         </Author>
         <Author>
            <First_Name>Jennifer</First_Name>
            <Last_Name>Widom</Last_Name>
         </Author>
      </Authors>
   </Book>
   <Book ISBN="ISBN-0-13-815504-6" Price="100">
      <Remark>
      Buy this book bundled with "A First Course" - a great deal!
      </Remark>
      <Title>Database Systems: The Complete Book</Title>
      <Authors>
         <Author>
            <First_Name>Hector</First_Name>
            <Last_Name>Garcia-Molina</Last_Name>
         </Author>
         <Author>
            <First_Name>Jeffrey</First_Name>
            <Last_Name>Ullman</Last_Name>
         </Author>
         <Author>
            <First_Name>Jennifer</First_Name>
            <Last_Name>Widom</Last_Name>
         </Author>
      </Authors>
   </Book>
```

### SAX, Display XML and XSL for displaying XML
- SAX: stream model for XML, ways in which program would access XML document when it comes out of parser
How to display xml?
Use rule based language to translate XML (like CSS or XSL) to HTML
- CSS: cascading style sheets
- XSL: extensible stylesheet language
![[Pasted image 20241022222441.png|800]]
### DTD (Document Type Descriptors) and XSD for XML validation
Valid XML adheres to basic structural requirements as well formed XML, also adheres to content specific description
- DTD
- XML Schema (XSD)
![[Pasted image 20241022222650.png|800]]

DTD/XSD use grammar like language for specifying elements, attributes, nesting, ordering, number occurrences, it also specify attribute types ID and IDREF (s), specify pointers within a document
Use xmllint to validate xml
## JSON
>[!question] What is JSON?
>JSON means "**Java Script Object Notation**"

Json is good at:
- Serializing data objects
- Take objects in a program and write them to files
- Human readable
- Data interchange
- Useful for storing data where structure is not rigid

Basic construct of JSON:
- Base values
- Composite values: objects and arrays
- Objects: key-value pairs
- Arrays
![[Pasted image 20241023084235.png|800]]
![[Pasted image 20241023084253.png|800]]
## Comparison between Relational model ,XML and JSON

|                | Relational                                     | Json                                                 |
| -------------- | ---------------------------------------------- | ---------------------------------------------------- |
| Structure      | Tables                                         | Sets of label value pairs, arrays                    |
| Schema         | Fixed in Advance                               | Self describing data                                 |
| Queries        | Simple expressive language <br>for querying db | Nothing used widely                                  |
| Ordering       | -                                              | Arrays                                               |
| Implementation | Native Systems                                 | Coupled with programming languages,<br>NoSQL systems |
|                |                                                |                                                      |

|                                                                                                        | XML                 | JSON              |
| ------------------------------------------------------------------------------------------------------ | ------------------- | ----------------- |
| Verbosity                                                                                              | More                | Less              |
| Complexity                                                                                             | More                | Less              |
| Validity - <br>ability to specify constraints, <br>restrictions or <br>schema on the structure of data | DTD, XSD            | JSON schema       |
| Programming interface                                                                                  | Clunky              | More direct       |
| Querying                                                                                               | XPath, XQuery, XSLT | JSON Path, JQuery |

---

# Flash Cards
