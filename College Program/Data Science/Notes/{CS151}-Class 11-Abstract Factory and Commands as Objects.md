---
create date: 2024-03-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - CS
  - "#CS/DesignPattern"
  - "#review"
modification date: 
type: CourseNotes
sr-due: 2024-04-11
sr-interval: 21
sr-ease: 250
---
[[#Review Lists]]
# Before the Class
## Lectures and Materials
[Abstract Factories](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/factories/index.htm)
[Commands as Objects](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/patterns/Commands/index.htm)

---
# In-Class Problems
## Abstract Factory
> [! Question] Why we need Abstract Factory?
>> Some times, we know how to construct an assembly, but we don't know how to construct its components
>>>[!note] An example in cross-platform GUI design
>>> One of the biggest problems programmers of the 1990s faced was porting applications to new platforms. Often the majority of the code was the user interface, a complex tree-like structure of windows and controls. Unfortunately, these components were not exactly the same on Windows, Mac, and Linux. This meant that the GUI had to be recoded for each port.

>[!tip] Seperate the construction of the assembly from the construction of its components by providing the assembly with abstract component classes for each type of component needed and an abstract factory that "makes" these components

- An abstract factory is a class (or interface) containing abstract factory methods for each type of abstract component.
- A factory method is a normal method that creates and returns some type of object.
![[Pasted image 20240309165039.png|1100]]

```Java
public interface Component1 {}

public interface Component2 {}

public interface AbstractFactory {
    public Component1 makeComponent1();
    public Component2 makeComponent2();
}

public class Assembly {
    private Component1 a, b, c;
    private Component2 d, e;
    public Assembly(AbstractFactory factory) {
        a = factory.makeComponent1();
        b = factory.makeComponent1();
        c = factory.makeComponent1();
        d = factory.makeComponent2();
        e = factory.makeComponent2();
    }
    // etc.
}
;=========================

public class ConcreteComponent1 {}

public class ConcreteComponent2 {}

public class Adapter1 implements Component1 {
	ConcreteComponent1 adaptee = new ConcreteComponent1();
}

public class Adapter2 implements Component2 {
	ConcreteComponent2 adaptee = new ConcreteComponent2();
}
public class ConcreteFactory implements AbstractFactory {
    @Override
    public Component1 makeComponent1() {
        return new Adapter1();
    }

    @Override
    public Component2 makeComponent2() {
        return new Adapter2();
    }
}

class TestAssembly {
   public static void main(String[] args) {
        ConcreteFactory factory = new ConcreteFactory();
        Assembly assembly = new Assembly(factory);
        // etc.
    }
}
```

### Example
Using this idea we could define abstract GUI component classes for windows, buttons, text fields, etc. We provide the GUI constructor with an abstract factory for making these components. On a Mac we create adapters that adapt the corresponding Mac GUI components to our abstract components and a concrete factor that makes these components.
![[Pasted image 20240309165610.png]]

---
## Commands as Objects
> [! Question] Why we need Commands as Objects?
>> 1. Most applications offer users several ways to issue a command—menu item, button, and keyboard. This can lead to multiple occurrences of the same command execution code.
>> 2. How can we provide an undo/redo mechanism for applications?

> Instead of triggering execution code when a control is activated, the control listener creates an object representing the command and sends it to a command processor for execution.
> Selecting a menu item, clicking a button, or pressing a combination of keys may all issue the same command.

#### Undo/Redo design
- The command processor executes the command, then pushes it onto an undo stack.
- The undo command causes the command processor to pop the topmost command from the undo stack, undo the command, then push it onto the redo stack.
- The redo command causes the command processor to pop the topmost command off of the redo stack, execute it, then push it onto the undo stack.
An example may look like this:
![[Pasted image 20240309170153.png]]

---
# Review Lists
>[! Question] What convenience does Factory pattern brings ?
>> When you have designed and implemented a concreted system (maybe a GUI)
>> And you want to design an another one which has similar framework, but its components different (maybe because in different platform, Windows, Mac etc.) It could save time for you if you have a abstract factory on the top layer of framework. Otherwise, you will need to re-code the GUI design 

>[! Question] What convenience does Command pattern brings ?
>> Let you easily handle the situation when a command need to be used in multiple places instead of writing the implement code again and again