---
create date: 2024-09-10
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - "#flashcards"
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[Math163_Lecture02.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. [[#Set Theory]]
>2. [[#De Morgan's Laws with Proof]]
>3. [[#Axioms of Probability]]

---
# In-Class Problems
## Set Theory
### Union, Intersection, Compliment, ...   and Venn Diagrams
### De Morgan's Laws with Proof
![[Math163_Lecture02.pdf#page=2&rect=69,590,441,704|Math163_Lecture02, p.2]]
## Axioms of Probability
![[Math163_Lecture02.pdf#page=2&rect=67,69,513,245|Math163_Lecture02, p.2]]
### Propositions
#### Addition Rule & General Addition Rule
![[Math163_Lecture02.pdf#page=3&rect=68,377,463,497|Math163_Lecture02, p.3]]

### Example Questions
> [!PDF|red] [[Math163_Lecture02.pdf#page=3&selection=166,0,170,69&color=red|Math163_Lecture02, p.3]]
> >[!faq] Write out the general addition rule explicitly for three events E, F, G and convince yourself that it is true with the help of a Venn Diagram


> [!PDF|red] [[Math163_Lecture02.pdf#page=3&selection=174,0,175,42&color=red|Math163_Lecture02, p.3]]
> >[!faq] Four married couples are arranged in a row. What is the probability that no husband will sit next to his wife?
> 

---

# Flash Cards
#flashcards/Math 
What is the DeMorgan's Laws
???
$$
(\cap_{i=1}^n E_{i})^c=\cup_{i=1}^nE_{i}^c
$$
$$
(\cup_{i=1}^n E_{i})^c=\cap_{i=1}^nE_{i}^c
$$

What is the general addition rule of probability
???
$$
P(E_{1}\cup E_{2}\cup \dots \cup E_{n})=\sum\limits_{r=1}^{n}(-1)^{r+1}\sum\limits_{i_{1}<\dots<i_{r}}P(E_{i_{1}}E_{i_{2}}\dots E_{i_{i}})
$$