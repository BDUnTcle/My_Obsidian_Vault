---
create date: 2024-06-27
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
- [[Drawing 2024-09-16 15.19.01.excalidraw]]
- [[RelationalAlgebra.pdf]]
- [[SQL_Triggers.pdf]]
- [[SQL_Functions.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. What is relational algebra [[#Definition]]
>2. Know Unary operation
>	1. [[#Selection $ rho(R)$]]
>	2. [[#Projection $ pi_{ alpha}(R)$]]
>		1. Know how to combine selection and projection
>	3. How to do cartesian product [[#Product $R1 X R2$]]
>3. Know joint operations
>	1. [[#Theta Join]]
>	2. [[#Natural Join]]
>	3. [[#Left Outer Join]]
>	4. [[#Right Outer Join]]

---
# In-Class Problems
## Definition
- Relational Algebra is **a set of mathematical operators** that *compose, modify, and combine tuples within different relations*
- Relational algebra operations operate on relations and produce relations
- The Relational Algebra is used to define the ways in which relations (tables) can be operated to manipulate their data
- It is used as the basis of SQL for relational databases, and illustrates the basic operations required of any DML
## Basic Unary Operations
### Projection  $\pi_{\alpha}(R)$
![[RelationalAlgebra.pdf#page=7&rect=34,260,692,422|RelationalAlgebra, p.7]]
### Selection $\rho(R)$
![[RelationalAlgebra.pdf#page=6&rect=27,254,694,415|RelationalAlgebra, p.6]]
#### Combination of selection and projection
![[RelationalAlgebra.pdf#page=8&rect=30,123,606,408|RelationalAlgebra, p.8]]
### Product $R1 X R2$
### Rename $\rho_{\alpha \to \beta}(R)$
>[!abstract] The rename operator can be expressed several ways:
>>[!note] 1. Takes the relation with schema a returns a relation with the attribute list b
## Joint operations
### Cross product (cartesian product)
$R_{1}*R_{2}$
### Theta Join
![[RelationalAlgebra.pdf#page=13&rect=58,269,609,378|RelationalAlgebra, p.13]]
### Natural Join
![[RelationalAlgebra.pdf#page=17&rect=17,63,616,309|RelationalAlgebra, p.17]]
### Outer Join
#### Left Outer Join
![[RelationalAlgebra.pdf#page=19&rect=57,208,640,307|RelationalAlgebra, p.19]]
#### Right Outer Join
![[RelationalAlgebra.pdf#page=19&rect=58,79,642,172|RelationalAlgebra, p.19]]

## Set Operations
### Union $R_{1} \cup R_{2}$
- Takes the set of rows in each table and combines them, eliminating duplicates
- Participating relations must be compatible
### Intersection $R_{1}\cap R_{2}$
- Takes the set of rows that are common to each relation
- Participating relations must be compatible
### Difference $R1 - R2$
- Takes the set of rows in the first relation but not the second
- Participating relations must be compatible
---

# Flash Cards
