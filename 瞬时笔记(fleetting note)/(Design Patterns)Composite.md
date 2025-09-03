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
[Composite](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/Composite.htm)

---
# Problem
We often encounter tree-like structures in design. Examples include assemblies (GUIs, computers) and hierarchies (command chains, org charts). For example, a corporate organizational chart might include subsidiaries, subsidiaries of subsidiaries, and so on. We want to avoid introducing special classes for each level in the tree as this will require recoding each time the tree is modified. This might happen, for example, when a new CEO wants to restructure his company.

# Solution
Introduce an abstract Component class (or interface) representing nodes in the tree. Introduce concrete subclasses representing the leaf nodes of the tree (SimpleComponent) and the parent nodes (CompositeComponent). The CompositeComponent class maintains a collection of sub-components.
![[Pasted image 20240326200833.png|600]]
Because CompositeComponent **is a** Component and **has a** list of Component, it's sub-components can include a mixture of simple and composite components.

---
# Flash Cards
