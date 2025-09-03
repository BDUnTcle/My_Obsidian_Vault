---
create date: 2024-06-18
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - flashcards/CS
modification date: 
type: CourseNotes
---
# Before the Class
## Lectures and Materials
- [[SQL_Intro.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. What is [[#DDL and DML]]？
>	1. How to create/select/delete a database and table
>	2. How to insert data into table
>2. MySQL shortcuts
>3. SQL Query
>	1. Know [[#General SQL Evaluation Strategy]]
>	2. Know how to use "order by" [[#Ordering the results]]
>	3. Know how to **join tables** and do **cross product**
>	4. Know how to [[#Use LIKE to do pattern matching]]
>	5. Know how to [[#Use AS to label/rename]]
>4. Examples
>	1. [[#do some simple queries]]
>	2. [[#Set Operators]]
>	3. [[#Correlated Queries demo]]

---
# In-Class Problems
## DDL and DML
- DDL is **Data Definition Language**
	- Show tables and databases
	- Create/alter/delete tables and their attributes
```mysql
SHOW databases;
CREATE database name;
SELECT database_name;
DROP databases name;

CREATE TABLE IF NOT EXISTS College(cname varchar(30) PRIMARY KEY, state VARCHAR(2), enrollment INT);
CREATE TABLE IF NOT EXISTS Student(sID INT, sName VARCHAR(30), gpa FLOAT(3,2),sizeHS INT, PRIMARY KEY(sID));
CREATE TABLE IF NOT EXISTS Apply(sID INT, cName VARCHAR(30),major VARCHAR(30), decision TEXT, PRIMARY KEY (sID,cName,major));

```
- DML is  **Data Manipulate Language**
	- Query one or more tables
	- Insert/delete/modify tuples in tables
```mysql
//Insertion
INSERT INTO NewCollege(name,state) VALUES('A','CA');
INSERT INTO NewCollege(name,state) VALUES('B','CA');
```
- Translate Weak Entities
- Translate partial constrain and key constrain
- Representing Composite Attribute
## Basic SQL Query
![[Pasted image 20240709034809.png]]
- **Every SQL Query must have: SELECT and FROM clause, but do not have to have WHERE clause**
### General SQL Evaluation Strategy
![[Pasted image 20240709035051.png]]
- Type casting clause: `CAST (S.sid AS VARCHAR (255))`
>[!note] The LIKE operator
>> ![[Pasted image 20240709035618.png|1000]]
### Ordering the results
`ORDER BY` clause
- default ascending
- ties are broken by the second attribute on the list
### Handle Expressions and Strings
#### Use AS to label/rename
![[SQL_Intro.pdf#page=45&rect=25,345,538,427|SQL_Intro, p.45]]
#### Use LIKE to do pattern matching
![[SQL_Intro.pdf#page=45&rect=36,180,537,318|SQL_Intro, p.45]]

---


## Example
>3 tables will be used: Student, College and Apply
```mysql
CREATE TABLE IF NOT EXISTS College (cname varchar (30) PRIMARY KEY, state VARCHAR (2), enrollment INT);
CREATE TABLE IF NOT EXISTS Student (sID INT, sName VARCHAR (30), gpa FLOAT (3,2), sizeHS INT, PRIMARY KEY (sID));
CREATE TABLE IF NOT EXISTS Apply (sID INT, cName VARCHAR (30), major VARCHAR (30), decision TEXT, PRIMARY KEY (sID, cName, major));
```

### do some simple queries
```mysql
# find student whoes gpa is greater than 3.5
SELECT sName,GPA FROM Student WHERE GPA > 3.5;

#Natural joint
SELECT (DISTINCT) sName,major 
FROM Student,Apply 
WHERE student.sID = Apply.sID;
#Cross Product
SELECT *
FROM Student,College;

#order the results
SELECT
FROM
WHERE
ORDER BY GPA (ASCE/DESC)

#Pattern Matching
SELECT sID, major
FROM Apply
WHERE major like '%bio%';

#Do Arithmetic
SELECT sID, Sname, gpa*(sizeHS/1000.0) as new name
FROM Student;
```

### Set Operators
```mysql
# use Union
SELECT cName FROM College
UNION (all)
SELECT sName FROM Student;

# Intersection to find id of student who apply to CS and EE
SELECT sID FROM Apply WHERE major = 'CS'
INTERSECT
SELECT sID FROM Apply WHERE major = 'EE'

# Except to find id of student who apply to CS but not EE
SELECT sID FROM Apply WHERE major = 'CS'
EXCEPT
SELECT sID FROM Apply WHERE major = 'EE'
```
- @ we can get the same result not using set operators by joining tables. However, we need to care about the duplicates
```mysql
find id of student who apply to CS and EE
SELECT DISTINCt A1.sID
FROM Apply A1,Apply A2
WHERE A1.sID = A2.sID and A1.major = 'CS' and A2.major = 'EE'; 

select distinct A1.sID
from Apply A1, Apply A2
where A1.sID = A2.sID and A1.major = 'CS' and A2.major <> 'EE';
```
### Correlated Queries demo
```mysql
# student who apply cs but not apply EE
SELECT sID, Name
FROM Student
WHERE sID in (select sID FROM Apply where major='CS') 
and not sID in (select sID FROM Apply where major='EE')

# find the college who has max enrollment
select cName
from College C1
where not exists (select * from College C2 where C2.enrollment > C1.enrollment)

# find student who has highest GPA
slect sID
From Student S1
where not exists (select * from Student S2 where S2.gpa > S1.gpa)
```
>Find the k-th largest value for enrollment (k=1 here)
`select distinct enrollment from College A where 1=(select count(distinct enrollment) from College B where A.enrollment <= B.enrollment)`

---
# Flash Cards
What is **DDL** and **DML** ? ---> Data Definition Language and Data Manipulate Language

