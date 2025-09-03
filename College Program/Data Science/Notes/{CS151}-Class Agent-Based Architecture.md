---
create date: 2024-05-18
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---
[[#Review List]]
# Before the Class
## Lectures and Materials
- [MVC](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/mvc/mvc.htm)
- [Agent-Based Systems](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/agents/index.htm)
- [[(Design Pattern)Master-Slave]]

---
# In-Class Problems
## MVC & CALab
1. Talk structure and implementations in the MVC framework
```java
public AppPanel(AppFactory factory)
{
	//use factory to initialize view
	view = factory.makeView(model)
}
```

How to design "edit" in different customization of the MVC
A: use factory to create a Command object, then execute () it
## Agent-Based Architecture
> An agent is a goal-oriented object. It perpetually attempts to update itself and its environment until its goal has been reached or until it is killed by another agent:
```Java
abstract class Agent extends Thread {  
   Facilitator facilitator;  
   abstract boolean done();  
   abstract void update();  
   void run() {  
      while(!done()) {  
         update();  
         yield();  
      }  
   }  
}
```

---
# Review List
>[!Abstract] Topics
>1. What is Agent-Based System 
>	- An agent-based system instantiates the [Master-Slave Pattern](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/masterslave.htm): slaves are called agents and the master is a dispatcher or facilitator that creates, manages, and runs agents. 

---
# Flash Cards
