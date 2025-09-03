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
[Strategy](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/Strategy.htm)

---
# Problem
An object needs to dynamically change the algorithm used by one of its methods.
For example, an object representing a list of strings may want to allow users to change the algorithm used by it's sort method. Although the fields of an object can be changed dynamically, the implementations of its methods are fixed by the compiler.
# Solution
Represent a method's algorithm as an object that can be dynamically switched:
![[Pasted image 20240326195632.png|600]]
```java
class Warrior {
   Strategy s;
   void attack() {
      s.strike();
   }
}
abstract class Strategy {
	abstract void strike();
}

class Poison extends Strategy {
	void strike() {
		// poison opponent
	}
}

class Stab extends Strategy {
	void strike() {
		// stab opponent
	}
}
class Battle {
	public static void main(String[] args) {
		Warrior sonya = new Warrior();
		sonya.strategy = new Poison();
		sonya.attack();
		sonya.strategy = new Stab();
		sonya.attack();
	}
}

```
---
# Flash Cards
