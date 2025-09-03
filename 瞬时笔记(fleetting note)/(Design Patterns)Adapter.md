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
[Adapter](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/Adapter.htm)

---
# Problem
A class exists that has the desired functionality, but doesn't implement the desired interface. 
For example, a calculator class might have add and mul methods, but the required interface specifies sum and times methods.
# Solution
An adapter contains a reference to a concrete provider (the class that has the desired functionality) and implements the required interface (Provider) by translating the specified methods into the methods supplied by the concrete provider:
![[Pasted image 20240326195841.png|600]]

The provider adapter can also inherit the methods of the concrete provider:
![[Pasted image 20240326195918.png|600]]
```java
class Client {
   Provider provider;
   // etc.
}

interface Provider {
	void service1();
	void serice2();
}


class ConcreteProvider {
	void serviceA() { ... }
	void serviceB() { ... }
}

class Adapter extends ConcreteProvider implements Provider {
	void service1() { serviceA(); }
	void serice2() { serviceB(); }
}

class Adapter2 implements Provider {
	ConcreteProvider s = new ConcreteProvider();
	void service1() { s.serviceA(); }
	void serice2() { s.serviceB(); }
}
```
---
# Flash Cards
