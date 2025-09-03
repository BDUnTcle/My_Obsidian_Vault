---
create date: 2024-03-26
tags:
  - review
  - CS
  - CS/DesignPattern
  - 程序员
modification date: 2024-03-26T19:48:00
type: LearningNote
sr-due: 2024-03-29
sr-interval: 3
sr-ease: 250
---

# Background & Materials
[Types as Objects](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/TypesAsObjects.htm)

---
# Problem
An object may have multiple types. 
For example, a film might have a rating (G, PG, R, ...) and a genre (Sci Fi, Romance, Mystery, ...). Representing types as classes can lead to complex class hierarchies with dozens of classes. Such hierarchies are difficult to maintain. In the example above not only will we need a GRated class and a SciFi class, but also a GRatedSciFi class, an RRatedMystery class, etc. Now imagine how difficult it would be to add a new genre to the system.

# Solution
When **types don’t affect behavior** (methods), consider representing them as objects rather than classes:
![[Pasted image 20240326195326.png|600]]

---
# Flash Cards
