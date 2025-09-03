---
create date: 2024-03-13
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
  - CS
modification date: 2024-03-13T14:54:00
type: CourseNotes
sr-due: 2024-03-16
sr-interval: 3
sr-ease: 250
---

[[#Review List]]
# Before the Class
## Lectures and Materials
[Multithreading Concepts](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/threads/Multithreading.htm)
[Multithreading in Java](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/threads/JavaThreads.htm)

---
# In-Class Problems
Difference between Status & state in life
Status: the ambiance
State: 0 or 1

### Introduction to memory map
Code zone, heap zone, stack zone, static zone
![[multithread.excalidraw]]
*memory leak*
*Stack overflow*: run out of stack

### Thread concept：
1. Thread only has stack zone
2. 4 state of a thread: ready, running, suspended, stopped
![[Pasted image 20240313203458.png|1000]]
Application of threads:
1. User interface thread
2. Server threads

>UML notation of a active Class：
>Active objects (called an active class) has double borders on its sides

### Thread and Runnable in Java,
```Java
interface Runnable {  
   public void run();  
}
class Thread implements Runnable {  
   private Runnable runner;  
   public void start() {  
      if (runner!= null) runner.run();  
      else run();  
   }  
   public void run() { /* no-op */ } // overridable  
   // etc.  
}
```
>2 ways to implement multi-thread
1. Agent implement Runnable, use Agent variable to initialize Thread
```Java
class Agent implements Runnable {  
  State state, goal;  
  void run() {  
     while(state != goal) {  
        state = update(state);  
     }  
  }  
  State update(State state) { ... }  
}
Thread thread = new Thread(new Agent());  
thread.start();
```
2. Agent extends Thread and overwrite Thread. Run () 
```Java
class Agent extends Thread {  
  State state, goal;  
  void run() {  
     while(state != goal) {  
        update();  
     }  
  }  
  void update() { ... }  
}
```

---
# Review List
>[! abstract] Main Topics
>1. Basic concept of thread
>	1. How the underling processor work to run multiple program in parallel
>	2. What is thread of a problem? 
>	3. The 4 states of thread 
>2. Applications of threads
>3. Threads in Java
>	1. Runable interface
>	2. 2 ways to implement a thread class

---
# Flash Cards

