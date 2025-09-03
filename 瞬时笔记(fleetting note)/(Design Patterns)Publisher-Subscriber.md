---
create date: 2024-03-26
tags:
  - review
  - CS
  - CS/DesignPattern
  - 程序员
modification date: 
type: LearningNote
sr-due: 2024-03-29
sr-interval: 3
sr-ease: 250
---

# Background & Materials
[Publisher-Subscriber](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/Publisher.htm)

---
# Problem
An object that fires an event is called a publisher. Examples of events include state changes, time-outs, and user inputs. Other objects, called subscribers, may need to be informed when such events occur. For example, when the value of a spreadsheet cell changes, other cells may need to update their values. In this example cells are both publishers and subscribers. But we want to be able to add and remove subscribers without having to modify the publisher's code and we want to avoid forcing the subscribers from having to constantly poll the publisher for events.
# Solution
Introduce a reusable Subscriber interface with an abstract update method and a reusable Publisher class that maintains a list of subscribers. Provide the publisher with a notify method that calls the update method of each subscriber. Concrete publishers, like the cells in a spreadsheet can inherit this notification machinery from Publisher, and concrete subscribers can implement the Subscriber interface any way they see fit.
![[Pasted image 20240310221106.png|600]]
Here is the typical interaction:
![[Pasted image 20240310221137.png|600]]
---
# Flash Cards
