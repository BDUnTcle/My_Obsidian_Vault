---
create date: 2024-03-06
tags:
  - 我的研究生
  - DataSince
  - SJSU
modification date: 
type: CourseNotes
---
[[CS-151 Sec 04 - Object-Oriented Design]]
# Before the Class
## Lectures and Materials
[CS 151 Object-Oriented Design-Lectures](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/index.htm)

---
# In-Class Problems
About late homework policy:
- Few minutes late, ok. 10 hours? No, you can't get credit for that

## About the next assignment
[CALab](https://www.cs.sjsu.edu/faculty/pearce/modules/projects/ood/CALab/index.htm)
- In the MVC, should not appear any "solid things", like stoplight simulator or CAlab 
### CALab Design
In Cell class:
- Observe (): cal the "ambience" [[#^ab]]
- Interact (): check whether change the status according specific rules
- Update: update the cell status
- Reset ()/getStatus ()
- NextState ()

In Grid class:
- MakeCell: an abstract factory 
- UpdateLoop: look at *The CA Update Loop*
- Repopulate: set all cell to its initial status
### GridView
CellView is a JButton but also ActionListener and Subscriber, when its clicked, it call other cell and it also listen to another cellview

Look at [Grid.java](https://www.cs.sjsu.edu/faculty/pearce/modules/projects/ood/CALab/src/Grid.java).

### About "life"
Each cell has 
- 2 status: 0(dead),1(life)
- Ambience: the number of living neighbors ^ab
### LifeLab
(https://www.cs.sjsu.edu/faculty/pearce/modules/projects/ood/CALab/life.htm)
In society class:
- PercentAlive: 
- Rebirth:
- Death:
### Some examples
1. The Conway Universe
2. Votting pattern
---