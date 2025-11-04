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
- [https://www.youtube.com/watch?v=GFQaEYEc8_8&t=10s](https://www.youtube.com/watch?v=GFQaEYEc8_8&t=10s)
---
# Review List
>[! abstract] Main Topics
>1. Know why we need normalized tables and how to make table to be normalized
>2. Know the 1 st-5 th normal form rules and its examples

---
# In-Class Problems
- database should handle bad designs and prevent them from occurring
>Database design should prevent failure of data integrity
>Example: it does not make sense for a person to have 2 different birthdays

>[!abstract] Normalized tables need to have such properties
>- Easier to understand
>- Easier to enhance and extend
>- Have protected from:
>	- insertion anomalies
>	- update anomalies
>	- deletion anomalies

A good DB is anologous to Safety assessment on a bridge
- Level 1: safe to walk
- Level 2: safe for cars
- Level 3: safe for trucks
- ...
## 1 st Normal form rules
1. Using row order to convey information is not permitted
2. Mixing data types within the same column is not permitted
3. Having a table without a **primary key** is not permitted
4. Repeating groups are not permitted
>[!question] What is transitive dependency？
## 2nd Normal Form
Each non-key attribute in the table must be dependent on the entire primary key
## 3rd Normal Form
Every non key attribute in a table should depend on the key, the whole key and nothing but the key

## Boyce Codd normal form
Every attribute in a table should depend on the key, the whole key and nothing but the key

## 4th Normal Form
Multivalued dependencies in a table must be multivalued dependencies on the key
> [!question] What is multivalued dependency?

## 5th Normal Form
The table (which must be in 4nf) cannot be describable as the logical result of joining some other tables together

---

# Flash Cards
