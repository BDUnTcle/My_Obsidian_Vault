---
create date: 2024-04-14
tags:
  - review
  - 程序员
  - CS
  - CS/Algorithm
modification date: 
type: LearningNote
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[Introduction to Dynamic Programming]]
- [Vedio: Dynamic Programming: Subset Sum](https://www.youtube.com/watch?v=C0xiOGhS_js&list=PLSVu1-lON6LwaLkn1J4slNQEp2oEjWCqX&index=3)

---
# Subset Sum Definition
- Given: a set $S[1,..., n]$ of positive integers, and positive integer $K$
- Answer: *true* if there exists a subset of *S* that sums to K
>[!example]
>S = {17,22,6,4,2,4}
>>- For K=45, True (17+22+2+4=45)
>>- For K=46, False

>[!Tip] Recursive Ideas 
>>If $S[i]$ is in the subset, solve $S - S[i], K - S[i]$
>>Try for all possible I

---
# Flash Cards & Review List
