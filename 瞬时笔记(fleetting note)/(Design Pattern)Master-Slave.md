---
create date: 2024-04-01
tags:
  - review
  - CS/DesignPattern
  - 程序员
  - CS
modification date: 
type: LearningNote
sr-due: 2024-04-04
sr-interval: 3
sr-ease: 250
---

[[#Flash Cards & Review List]]
# Background & Materials
---
# Problem
Calling a function blocks the entire application and the user until the function terminates. If the function doesn't terminate, then there is no opportunity for the user to suspend the runaway function. In the context of client-server applications, clients must wait for the server until the current client finishes.
# Solution
Use multithreading to divide the application into a foreground master thread that manages a number of background slave threads that do the actual computational work:
![[Pasted image 20240401184017.png|600]]
## Note
- The master manages a collection of active slave objects.
- The master has the ability to *start*, *stop*, *suspend* or *resume* some or all of the slaves.
- The master also provides services to the slaves. For this reason each slave has a pointer to the master.
- One type of service is message passing—providing a mechanism for slaves to pass messages to each other.
- The master might allow slaves to broadcast messages to all of the slaves.
- Another type of service is discovery. A slave can ask the master to pair it with another slave.
- The master might also provide a shared environment consisting of resources to be shared by the slaves.
# Example
In a desktop application the master listens for user inputs, then launches slaves to execute user commands.

In a client-server application the master listens for client requests. When a request is received the master creates a slave to serve the client.

A master trying to solve the Travelling Salesman Problem creates a slave for each path through the graph. The slave computes the length of its path (in O(n) time) and reports it back to the master, which keeps track of the shortest path.

---
# Flash Cards & Review List
