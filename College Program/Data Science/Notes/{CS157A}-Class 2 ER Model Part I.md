---
create date: 2024-06-06
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
- [[ER.pdf]]
- [[ER-Model.pdf]]
- [[20240606-CS157A-class2_note.excalidraw]]
---
# Review List
>[! abstract] Main Topics
>1. The E-R (Entity-Relationship) Model

---
# In-Class Problems
## Main topics
A database requires:
- Massive Storage
- Reliable
- Efficient
- Multi-User
- Convenient
- Safe

1. Data Model: relational model
2. Schema (not change) V.S. Data (can change)
3. DDL (Data Definition Language)
4. DML (Data Manipulation Language)
5. Data Administrators
## Homework (due on Sep 4 th):
Write a java program, which 
1. Read csv file
2. Create a database
3. Create table
4. Insert records
5. Do Queries

>[!note] Process of Designing a DB System
>1. Requirement Analysis
>2. Conceptual DB Design(Using ER Model)
>3. Logical DB Design(Transform E-R diagram into relation tables)
## The E-R Model
The E-R model views the real world as a set of basic objects and relationships among these objects.
### Entity and Entity Sets
- An **entity** is an object that exists and is distinguishable from other objects. For instance, Michelle Lee with S.S.N. 890 12 3456 is an entity, as she can be uniquely identified as one particular person in the universe.
- An entity may be concrete (a person or a book, for example) or abstract (like a holiday or a disease).
- An **entity set** is a set of entities of the same type (e. all persons having an account at a bank).
- Entity sets need not be **disjoint** . For example, the entity set Student (all students in a university) and the entity set professor (all professors in a university) may have members in common. (i.e a computer science professor might take a class in anthropology).
## E-R Diagrams
- *Rectangles*: representing **entity sets**
- *Ellipses*: representing **attributes**
- *Diamonds*: representing **attributes**
- *Lines*: linking attributes to entity sets and entity sets to relationship sets
- *Arrows* (key constraints): if A->B (B is at most one, A could be multiple)
- *Bold Arrow*(participation constraints)
- *Bold Rectangles*: weak entity set
- *Underline*: primary key
- *Dashed underline*: partial key
what is "**primary key**": a special attribute (underlined in the diagram, S.S.N and PI. D in below)
What is "**descriptive attribute**": "since" in below
![[Pasted image 20240608100457.png|1000]]
### 4 kinds of Key Constraints
1. 1-to-1
2. 1-to-many
3. Many-to-one
4. Many-to-many
#### Participation Constraints
Total participation and partial participation
- Total: not include entity which may not have a relationship
- Partial: opposite of total, which means every entity must have a partner related to it
We Can use **bold lines** (to indicate participation constraints), and arrow lines (to indicate key constraints) independently of each other to create an Expressive language of possibilities.
![[Pasted image 20240608101501.png|500]]
>Here, every man must have a wife and every women must have a husband

#### Entity vs. Attribute

### Keys
For each entity set, we choose a key.
- Superkey and candidate key
	- A **superkey** is a set of one or more attributes which, taken collectively, allow us to identify uniquely an entity in the entity set.
	- A superkey for which no subset is a superkey is called a **candidate key**
- Strong entity and weak entity 
	- An entity that has a primary key is called a **strong entity**
	- An entity set that does not possess sufficient attributes to form a primary key is called a **weak entity set**
- Partial key (dashed underline)
In order to be able to uniquely refer to an item in a weak entity set we must consider some (or all) of its attributes in conjunction with some strong entities Primary key. The entity whose primary key is being used is called the **identifying owner**
![[Pasted image 20240608103349.png|1000]]
>Another weak entity sets example
![[Pasted image 20240608103412.png|1000]]
#### Ternary Relationships

---

# Flash Cards
