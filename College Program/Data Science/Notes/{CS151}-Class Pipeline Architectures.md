---
create date: 2024-04-15
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
- [Pipeline Architectures](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood3/distributed/Pipelines.htm)
- [Client-Server Architectures](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood3/distributed/ClientServer.htm)
- [Peer-to-Peer(P2P) Architectures](https://www.cs.sjsu.edu/faculty/pearce/modules/lectures/ood3/distributed/P2P.htm)
---
# In-Class Problems
A distributed architectures contains multiple (environment)computers for some same purples
# Pipeline Architectures
A **pipeline** consists of a sequence of filters connected by message queues called pipes.
![[Pasted image 20240415151009.png|600]]
There are *four types* of filters:
- **Producers** are at the start of the pipeline. They perpetually produce messages and write them to an output pipe.
- **Consumers** are at the end of the pipeline. They perpetually read messages from their input pipe and consume them.
- **Transformers** perpetually read messages from their input pipes, transform them into different messages, then write the transformed message to their output pipe.
- **Testers** perpetually read messages from their input pipe, test the message, and if it passes, write them to their output pipe.

Demand-driven and
Demand-driven: start from consumer read ()
-driven: start from producer produce()

Transformers are called maps and consumers are called reducers.
# Client-Server Architectures
Protocols can be stateless or stateful
# Peer-to-Peer(P2P) Architectures

# The Echo framework
The echo **client** is a simple console user interface that perpetually prompts its user for a request, forwards the request to a remote server, then displays the server's response.
Upon receiving a request, the **remote server** spawns a request handler thread connected to the client, then resumes listening for more requests.
Responses are created by the request handler's response method. (override by subclass for particular purples)
## The decorator Pattern
[[The decorator Pattern.excalidraw]]

---
# Review List
>[! abstract] Main Topics
>1. 

---
# Flash Cards
