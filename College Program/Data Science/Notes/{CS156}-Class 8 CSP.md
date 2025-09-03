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
- 
---
# Review List
>[! abstract] Main Topics
>1. Know How to define CSPs
>	1. What is the [[#3 components of CSP]]
>	2. Know different [[#Assignment types]]
>	3. know what is “constrain graph”
>2. Be able to express constraints in various types problems
>3. [[#Variations on the CSP]]
>
>4. Search in the context of CSP
>5. Back tracking search
>6. MRV, degree heuristics, LCV, forward checking
>7. Arc consistency
>8. Tree structured CSPs

---
# In-Class Problem

## Defining CSP
### 3 components of CSP
1. **X**: is a set of **variables**, $\{X_{1,}X_{2}\dots,X_{n}\}$
2. **D**: is a set of **domains**, $\{D_{1,}D_{2}\dots,D_{n}\}$
3. **C**: is a set of **constrains**
>[!example]
> $x_{1}$ =color
> $D_{1}={red,blue,green,\dots}$
### Assignment types
Each state in a CSP is defined by a assignment of values to some or all of the variables
- **consistent assignment**: doesn't violate any constrains
- **complete assignment**: every variable is assigned and a solution to a CSP is a consistent, complete assignment
- **partial assignment**: only partial variable are assigned
- **partial solution**: a partial assignment that is consistent

Constrain to make all variables distinct: Alldiff $\{x_{1}, x_{2}, x_{3},...\}$
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=223&rect=123,453,527,704&color=important|Artificial Intelligence - A Modern Approach (3rd Edition), p.204]]

## Variations on the CSP 
- Discrete/continuous
- Finite/infinite
- Unary constraint: only 1 value for a single variable
- Binary constraint: constraint that relates 2 variables
- Global constraint: constraint involving an arbitrary number of variables
### Linear Programming Problem
### Cryptarithmetic Problem
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=226&rect=147,456,552,705&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.207]]
Choose the different value for each letters so that it satisfy the constraint of the diagram (TWO+TWO=FOUR)
X means carry, so 
Var = {FTUWRO} Carry={X_1, X_2, X_3}
O+O = R + 10* X_1
W+W = U+ 10* X_2
T+T = O + 10* x_3

---

# Flash Cards
