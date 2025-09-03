---
create date: 2024-09-11
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
- [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf]]
---
# Review List
>[! abstract] Main Topics
>1. Know what is the [[#Game Theory]]
>	1. What is Zero-Sum Games? [[#^zerosumgame]]
>2. What is [[#MinMax]]
>	1. Alpha-beta pruning

---
# In-Class Problems
## Game Theory
> [!PDF|note] [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=180&selection=23,21,34,5&color=note|Artificial Intelligence - A Modern Approach (3rd Edition), p.161]]
>>[!tip] In this chapter we cover competitive environments, in which the agents’ goals are in conflict, giving rise to adversarial search problems—often known as games

> [!PDF|red] [[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=180&selection=46,1,54,19&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.161]]
>>[!tip] What is "Zero-Sum Games" ^zerosumgame
>>In AI, the most common games are of a rather specialized kind—what game theorists call **deterministic**, **turn-taking**, **two-player**, **zero-sum** games of perfect information

>[!question] Why we do researches on games？
>> ![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=180&rect=143,205,557,249&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.161]]

### Types of Games

### Game Tree

## Optimal Decisions in Games
### MinMax
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=183&rect=121,502,529,704|Artificial Intelligence - A Modern Approach (3rd Edition), p.164]]
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=185&rect=123,400,527,697&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.166]]
#### α-β pruning
![[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=187&rect=122,240,529,705&color=yellow|Artificial Intelligence - A Modern Approach (3rd Edition), p.168]]
- @ Max only update α, and prune β
- @ Min only update β, and prune α
>[!note] Properties of α-β pruning
>> ([[Artificial Intelligence - A Modern Approach (3rd Edition).pdf#page=188&selection=109,0,119,1&color=red|Artificial Intelligence - A Modern Approach (3rd Edition), p.169]])
> If this can be done, 2 then it turns out that alpha–beta needs to examine only $O (bm/2)$


---

# Flash Cards
