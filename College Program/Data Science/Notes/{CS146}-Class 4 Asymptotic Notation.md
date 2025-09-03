---
create date: 2024-03-09
tags:
  - 我的研究生
  - DataSince
  - SJSU
  - CS/Algorithm
  - "#review"
modification date: 2024-03-09T17:59:00
type: CourseNotes
sr-due: 2024-04-07
sr-interval: 12
sr-ease: 230
---

# Before the Class
## Lectures and Materials
- [[《2009 Introduction to Algorithms Third Ed》.pdf]]  Ch 3.1,3.2 (p.43-52)(p.53)
- [Learning Videos: Asymptotic Notation](https://www.youtube.com/watch?v=lRD35H39o_E)
- [Videos: Itrated Function and Log*](https://www.youtube.com/watch?v=Z2vprYeJ0qs)
---
# Review List
>[!Abstract] Topics
>1. Θ-Notation (tight bound)
>	1. Definition, Graph representation
>	2. Some conclusions
>2. O-Notation (upper bound)
>	1. Definition, Graph representation
>	2. Relationships between Θ and O
>	3. The abuse of O notation
>3. Ω-Notation (lower bound)
>	1. Definition, Graph representation
>	2. Important theorem between O,Θ and Ω and how to use it in practice
>4. $o$ -Notation
>	1. Definition
>	2. Difference between O and o notation
>5. Comparing functions

---
# In-Class Problems
## Note
### Asymptotic Notation: Definitions
[[2024-02-05]]
#### Θ Notation (asymptotic tight bound)
For a given function $g(n)$, $Θ(g(n))$ represents the *set of functions*: 
> $Θ(g (n))={f(n)}: \exists$  $c_{1},c_{2} > 0$  and $n_{0}$ such that
> $0\leq c_{1}*g(n)\leq f(n) \leq c_{2}*g(n)$ for all $n \geq n_{0}$
![[Pasted image 20240316083943.png|300]]

>[!tip]  Remember
>>For any polynomial $p(n)=\sum\limits_{i=0}^{d} a_in^i$, $p(n)=Θ(n^d)$

#### O Notation（asymptotic upper bound）
For a given function $g(n)$, $O(g(n))$ represents the *set of functions*: 
> $O(g (n))={f(n)}: \exists$  $c>0$  and $n_{0}$ such that
> $0\leq f(n) \leq c*g(n)$ for all $n \geq n_{0}$
![[Pasted image 20240316085733.png|300]]

- **Θ is a stronger notation than O**
- **O is usually used to describe the running time of an algorithm in overall structure**
- **O could work for every input. However Θ may change for different input**
	- For insertion sort, the worst-case Θ is $Θ(n^2)$, but if input is sorted, Θ is $Θ(n)$

>[!note] abuse
> When we say, the running time of insertion sort is $O(n^2)$, the actual running time varies, depending on the input
>> When we say "the running time is $O(n^2)$", we mean that the **worst-case running time** is $O(n^2)$

#### Ω Notation(asymptotic lower bound)
For a given function $g(n)$, $Ω(g(n))$ represents the *set of functions*: 
> $Ω(g (n))={f(n)}: \exists$  $c>0$  and $n_{0}$ such that
> $0\leq c*g(n) \leq f(n)$ for all $n \geq n_{0}$
![[Pasted image 20240316091507.png|300]]

>[!tip] important theorem
>For any $f(n)$ and $g(n)$, we have $f(n)=Θ(g(n))$ if and only if $f(n)=O(g(n))$ and $f(n)=Ω(g(n))$
>> In practice, rather than using this theorem to obtain asymptotic upper and lower bounds from tight bounds, we usually use it to prove asymptotic tight bounds from upper and lower bounds.

##### A deepper understanding 
The running time of insertion sort therefore belongs to both $Ω(n)$ and $O(n^2)$, since it falls anywhere between a linear function of n and a quadratic function of n.
Moreover, these bounds are asymptotically as tight as possible: for instance, the Running time of insertion sort is not $Ω(n^2)$, since there exists an input for which insertion sort runs in $Θ(n)$ time (e.g., when the input is already sorted). It is not contradictory, however, to say that the worst-case running time of insertion sort is $Ω(n^2)$, since **there exists** an input that causes the algorithm to take $Ω(n^2)$ time.
#### $o$ Notation
For a given function $g(n)$, $o(g(n))$ represents the *set of functions*: 
> $o(g (n))={f(n)}: \forall$  $c>0$  and $\exists n_{0}>0$ such that
> $0 \leq f(n) \leq c*g(n)$ for all $n \geq n_{0}$

The main difference is in $f(n)=O(g(n))$, the bound hold for *some* $c>0$, but in $f (n)=o(g (n))$, the bound hold for *all* constants $c$

#### $\omega$ Notation
For a given function $g(n)$, $o(g(n))$ represents the *set of functions*: 
> $o(g (n))={f(n)}: \forall$  $c>0$  and $\exists n_{0}>0$ such that
> $0 \leq c*g (n)\leq f(n)$ for all $n \geq n_{0}$

### Asymptotic Notation: Comparing Functions
#### Transitivity
![[Pasted image 20240316100450.png|900]]
#### Reflexivity
![[Pasted image 20240316100511.png|300]]
#### Symmetry & Transpose Symmetry
![[Pasted image 20240316100545.png|500]]
![[Pasted image 20240316100601.png|500]]
#### Trichotomy
![[Pasted image 20240316100659.png|800]]
#### Asymptotic smaller & larger
![[Pasted image 20240316100848.png]]

### Asymptotic Notation: Proofs, Properties and Pictures
### Asymptotic Notation: Usage

## Assignment after Class

---
