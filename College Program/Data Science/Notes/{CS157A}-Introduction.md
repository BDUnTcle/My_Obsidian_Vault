---
create date: 2024-06-04
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
- [[CS157a-intro.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. What is a Database Management System(**DMBS**)?
>2. How is a RDBMS used?

---
# In-Class Problems
## Definitions
- Database: collection of files that store the data
	- Entities: student, faculty, courses and classroom
	- Relationships: between entities (students taking courses, faculty teaching courses)
- DBMS (Database Management System): software that manages the DB, a big program that access and updates those files
	- DBMS provides *efficient*, *reliable*, *convenient*, *safe*, *multi user storage* of and access to *massive* amounts of *persistent* data
- RDBMS (Relational DBMS): DBMS that is based on a relational model
## Key People
- DBMS implementer: ones who build the system
- DB designer: establish the schema
- DB application developer: programs the operate on database
- DB administrator: loads data, keeps data running smoothly
## Terms in DB
- Database: set of relations (or tables)
- Tuple: row of data
- Schema: structural descriptions of relations in a database
- Instance: actual contents at a given point in time
- Null: special value for "unknown" or "undefined"
- Key: attribute whose value is unique in each tuple
## How is a RDBMS used?
![[Pasted image 20240606081127.png]]
## Important problem that a DBMS should care
- Different Views
- Concurrency
- Security
- Crash Recovery
---

# Flash Cards
