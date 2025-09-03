---
create date: 2024-06-25
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
- [[SQL_Intro.pdf]]
- [[SQL_Advanced.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Know what is [[#Nested Queries]] and [[#Correlated  Queries]]
>	1. Be able to use "in" "not", "exist" in subquery condition
>2. How to use set operators [[#UNION, INTERSECT, EXCEPT]]
>	1. Be able to write query without union operators
>3. Know how to use [[#ANY and ALL operators]]
>4. Know Joint operations
>	1. Be able to write queries using join clause and without join clause
>5. Know [[#Aggregate Functions]]
>	1. Be able to use `count()`, `max()/min()` , `sum()`, `avg()` in sql query
>6. Know [[#GROUP BY and HAVING]]
>7. [[#Examples]]

---
# In-Class Problems
### Nested Queries
#### Correlated  Queries
- @ The inner subquery depend on the outer query is called correlation
![[Pasted image 20240709041733.png]]
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

### UNION, INTERSECT, EXCEPT
- They all eliminate duplicates, using `UNION ALL` to remain duplicates
- When using INTERSECT, be careful that you are searching unique id for tuples
- UNION，EXCEPT & INTERSECT keyword
	- care about uniqueness when using INTERSECT
- Nested Queries
- difference between IN and EXSIST
- Group BY & HAVING
#### Write same queries without set operators
```mysql
find id of student who apply to CS and EE(INTERSECT)
SELECT DISTINCt A1.sID
FROM Apply A1,Apply A2
WHERE A1.sID = A2.sID and A1.major = 'CS' and A2.major = 'EE'; 
```
### ANY and ALL operators
- [[#ANY examples]]
```mysql
# find the college who has max enrollment
select cName
from College S1
where not enrollment <= any(select enrollment from College S2 where S2.cName <> S1.cName)

# student's infomation except the lowest sizeHS
select sID,sName,sizeHS
from Student
where sizeHS > any(select sizeHS from Student);
```
- [[#ALL examples]]
```mysql
# students who has higher gpa to at least 1 student
select distinct S1.sName, S1.GPA from Student S1, Student S2 where S1.GPA > S2.GPA

# find student who has highest gpa
select sName, GPA
From Student
WHere GPA >= all (select GPA from Student);

select cName
from College S1
where enrollment > all(select enrollment from College S2 where S2.cName <> S1.cName)
```
## Joint Operations
### Inner join/Theta join
```mysql
select distinct sName, major
from Student inner join Apply
on Student.sID = Apply.sID
```
### Natural join
```mysql
select distinct sName, major
from Student, Apply
where Student.sID = Apply.sID;

select distinct sName, major
from Student natural join Apply
```
### Outer join
#### Left outer join
- @ Also show tuples which doesn't match in the left table
```mysql
select sName, sID, cName, major
from Student left outer join Apply using(sID)

# if don't use the join clause
select sName, Student.sID, cName, major
from Student, Apply
where Student.sID = Apply.sID
union
select sName, sID, NULL, NULL
from Student
where sID not in (select sID from Apply)
```
#### Right outer join
- @ Also show tuples which doesn't match in the right table
```mysql
select sName, sID, cName, major
from Student right outer join Apply using(sID)
```
#### Full outer join
```mysql
select sName, sID, cName, major
from Student left outer join Apply using(sID)
union
select sName, sID, cName, major
from Student right outer join Apply using(sID)

select sName,sID,cName,major
From Student,Apply
Where Student.sID = Apply.sID
union
select sName,sID,Null NULL
from Student
Where sID not in (select sID from Apply)
union
select NULL,sID,cName,major
from Apply
where sID not in (select sID from Student);
```
## Aggregate Functions
- With the exception of `count()`, all functions must operate on sets that consist of simple values (set of numbers or strings)
Computing arithmetic expressions, such as Minimum and Maximum
5 kinds of operators supported by SQL:
1. COUNT (A): The number of values in the column A
2. SUM (A): The sum of all values in column A
3. AVG (A): The average of all values in column A
4. MIN (A): The minimum value in column A
5. MAX (A): The maximum value in column A

 >[!tip] Correct Clause when using MAX and MIN
>To Find the name and age of the oldest sailor
> `SELECT S.name, MAX(S.age) FROM Sailors S` is illegal, **if the SELECT clause uses aggregate operation, it must only use aggregate operations unless we use GROUP BY/HAVING**
> The correct form is:
>> ```SQL
>> SELECT S.name, S.age
>> FROM Sailors S
>> WHERE S.age=(SELECT MAX (S 2. Age) FROM Sailors S 2) 
>> ```

Examples:
*Count the number of different sailors*:
```sql
SELECT COUNT (DISTINCT S.sname)
FROM Sailors S
```

```mysql
# SUM(): select total amount of balance of the account in branches located in fairfax
SELECT SUM(A.balance)
FROM account A, branch B
WHERE B.branch = 'Fairfax' and B.branchID = A.branchID

# Min()
SELECT min(GPA)
FROM Student S, Apply A
WHERE S.sID = A.sID and major = 'CS'

# avg()
SELECT avg(GPA)
FROM Student S
WHERE sID in (select sID FROM Apply A where major = 'CS')

# count()
select count(*)
from College
where enrollment > 15000;

select count(distinct sID)
From Apply
where cName='Cornell'

```

## Group By and Having
Sometimes, we want to apply *aggregate operators* to each of *several groups of tuples*
For example: find the age of the youngest sailor for each rating level
![[SQL_Advanced.pdf#page=23&rect=191,256,506,404|SQL_Advanced, p.23]]
```mysql
# group by: select the college and its number of applications
select cName,count(*)
from Apply
group by cName

# having: find colleges that receive application less than 5
select cName
from Apply
group by cName
having count(*)<5

# find colleges that receive from less than 5 student 
select cName
from Apply
group by cName
having count(distinct sID)<5
```
## Examples
>We use the same tables with [[{CS157A}-Class 5 SQL Intro & simple query#Example]]

### ALL examples
```mysql
# students who has higher gpa to at least 1 student
select distinct S1.sName, S1.GPA from Student S1, Student S2 where S1.GPA > S2.GPA

# find student who has highest gpa
select sName, GPA
From Student
WHere GPA >= all (select GPA from Student);

select cName
from College S1
where enrollment > all(select enrollment from College S2 where S2.cName <> S1.cName)
```
### ANY examples
```mysql
# find the college who has max enrollment
select cName
from College S1
where not enrollment <= any(select enrollment from College S2 where S2.cName <> S1.cName)

# student's infomation except the lowest sizeHS
select sID,sName,sizeHS
from Student
where sizeHS > any(select sizeHS from Student);
```
### Joint examples 
```mysql
select sName,GPA
FROM Student join Apply 
on Student.sID = Apply.sID
and sizeHS < 1000 and major = 'CS' and cname = 'Stanford';

select sName,GPA
FROM Student join Apply 
on Student.sID = Apply.sID
where sizeHS < 1000 and major = 'CS' and cname = 'Stanford';

select Apply.sID, sName, GPA, Apply.cname, enrollment
FROM Apply join Student join College
ON Apply.sID = Student.sID and Apply.cName = College.cName;

select S1.sID,S1.sName,S1.GPA,S2.sID,S2.sName,S2.GPA
FROM Student S1 join Student S2
on S1.GPA = S2.GPA and S1.sID < S2.sID

select S1.sID,S1.sName,S1.GPA,S2.sID,S2.sName,S2.GPA
FROM Student S1 join Student S2 using(GPA)
WHERE S1.sID < S2.sID
```

### Aggregate Example
```mysql
select CS.avgGPA - NonCS.avgGPA
from 
	(select avg(GPA) as avgGPA 
	 from student where sID in
		(select sID from Apply where major='CS')) as CS,
	(select avg(GPA) as avgGPA 
	 from student where sID not in
		(select sID from Apply where major='CS')) as NonCS

select cName,major,min(GPA),max(GPA)
from Student S,Apply A
where A.sID = S.sID
group by cName,major

select Student.sID,count(distinct cname)
from Apply,Student
Where Student.sID = Apply.sID
group by Student.sID
```

---

# Flash Cards
