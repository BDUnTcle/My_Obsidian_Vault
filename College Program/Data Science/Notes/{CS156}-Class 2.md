---
create date: 2024-06-27
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - review
modification date: 
type: CourseNotes
---

# Before the Class
## Lectures and Materials
- [[CS156-Lecture 2_1.pdf]]
- [[CS156-Lecture 2_2.pdf]]
---
# Review List
>[! abstract] Main Topics
>1. What is "[[#Agent]]"?
>2. Know [[#The concept of rationality]]
>5. What is [[#PEAS]] (Performance measure, Environment, Actuators, Sensors)
>6. Know the [[#Properties of task environments]]
>	1. Can describe the task environment using those terms
>7. Basic Agent types
>	1. [[#1. Simple Reflex Agents]]
>	2. [[#2. Model-based Reflex Agents]]
>	3. [[#3. Goal-based Agents]]
>	4. [[#4. Utility-based Agents]]

---
# In-Class Problems
## Introduction
> [!PDF|red] [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=53&selection=19,0,29,57&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.34]]
> >[!tip] Introduction
> > We begin by examining agents, environments, and the coupling between them. The observation that some agents behave better than others leads naturally to the idea of a rational agent—one that behaves as well as possible. How well an agent can behave depends on the nature of the environment; some environments are more difficult than others. We give a crude categorization of environments and show how properties of an environment influence the design of suitable agents for that environment. We describe a number of basic “skeleton” agent designs, which we flesh out in the rest of the book.
## The concept of rationality
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=56&rect=147,174,461,276|Artificial Intelligence - A Modern Approach (3rd Edition), p.37]]
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=56&rect=147,106,542,175|Artificial Intelligence - A Modern Approach (3rd Edition), p.37]]
## PEAS
- **P**erformance Measure
- **E**nvironment
- **A**ctuators
- **S**ensors
## Properties of task environments
- Fully observable vs. partially observable
- single agent vs. multiagent
- Competitive vs. Cooperative
- Deterministic vs. stochastic
- static vs.dynamic
- Episodic vs. sequential
- Discrete vs. continuous
## Agent
- @ An **agent** is anything that can be viewed as perceiving **environment** through sensors and acting upon that environment through **actuators**

### 1. Simple Reflex Agents
- ! these agents select actions on the basis of current percept, ignoring the rest of the percept history
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=68&rect=148,374,554,704|Artificial Intelligence - A Modern Approach (3rd Edition), p.49]]
- Agents that directly map states to actions
- Agents that select actions on the basis of current percepts, ignoring the rest of the percept history
- Rule Matcher: Condition-Action Rule
- Advantages: Speed, Simplicity
- Limitations: Lack of memory, No future planning
### 2. Model-based Reflex Agents
- ! Agent maintain some sort of internal state that depends on the percept history and thereby reflects at least some of the unobserved aspects of the current state
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=70&rect=149,344,554,705|Artificial Intelligence - A Modern Approach (3rd Edition), p.51]]
- Agents that use a model of the world to make decisions
- Agent that use memory or an internal state
### 3. Goal-based Agents
- Agents that act to achieve specific goals
### 4. Utility-based Agents
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=73&rect=123,517,530,703|Artificial Intelligence - A Modern Approach (3rd Edition), p.54]]
- Agents that act to maximize a predefined utility
### Learning Agents
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=74&rect=149,499,553,705|Artificial Intelligence - A Modern Approach (3rd Edition), p.55]]
4 components of learning agents:
- **Critic**
	- to check performance standards and provide feedback, interacts with performance standards, sensors and Learning element
- **Learning element**: responsible for making improvement
- **Problem generator**: responsible for suggesting actions that will lead to new and informative experiences
- **Performance element**: responsible for selecting external actions, [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=74&selection=54,26,55,66&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.55]]



---

# Flash Cards
