---
create date: 2024-03-18
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
- [Multithreading in Java](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood4/threads/JavaThreads.htm)
- [Synchronizing Threads in Java](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/j2se/multithreading/synch1.htm)
[[Drawing 2024-03-18 15.41.38.excalidraw]]

---
# In-Class Problems
## About CALab
what rebirth and death is used for
Rebirth is the set of all ambiences that bring a dead agent back to life (i.e., T01). Death is the set of all ambiences that cause a living agent to die. You need use the rebirth and dead to judge whether the state is going to life or dead
## Multithread in Java
1. use Thread.sleep() to make cooperative agent
2. Thread.join() : wait  until thread finish
3. Thread.currentThread (): static reference to currently executing thread
When use which strategy to create an agent (blue or red?)
1. If there is a legacy class implements the Runnable, use red one (`Thread thread = new Thread(new LegacyAgent())`)
2. Else use blue one (extends Thread and overwrite run method)

Lifecycle of a thread:
...
## Synchronizing Threads in Java
### 1. Solution 1: Locks
synchronization block
Notify () and wait ()
### 2. Solution 2: Monitors
**synchronized** in Java

---
# Review List
>[! abstract] Main Topics
>1. Sleep (), join (), currentThread ()
>2. Why there are 2 ways to implement thread (one of them is used when you could find another great lib of agent you want to use)
>3. How to synchronize threads in Java

---
# Flash Cards
