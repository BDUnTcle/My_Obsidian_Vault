---
create date: 2024-03-12
tags:
  - 我的研究生
  - DataSince
  - SJSU
modification date: 
type: CourseNotes
---
# Before the Class
## Lectures and Materials
- [Video: Recurrence Relations: 3 examples](https://www.youtube.com/watch?v=yPaEB7iVLuQ&list=PLSVu1-lON6LybCHQs8Io_EhyrEQ4b1xAF&index=4&t=12s)
- [Video: Recurrence Relations: Master Method](https://www.youtube.com/watch?v=SDnnDZgxYiI&list=PLSVu1-lON6LybCHQs8Io_EhyrEQ4b1xAF&index=5)
- [Video: Merge Sort](https://www.youtube.com/watch?v=k3oezbZgfDs)
- [[排序算法-Sorting Algorithms#Merge Sort]]
 
---
# Review List
>[!tldr]
>>[!note] Master Method
>
>>[!note] Merge Sort
>>1. Top Down Version
>>2. Bottom Up Version
>>3. Basic Runtime: $θ(nlgn)$
>>4. Space: $θ(n)$

---
# In-Class Problems
 [[2024-02-13]]
### The Master Method
> To solving recurrences of the form: $T(n)=aT(n/b)+f(n)$
#### The master  theorem
1. If $f(n) = O(n^{logb^{a-e}})$ for some constant $e > 0$. Then $T(n) = Θ(n^{logb^a})$ 
2. If $f(n) = Θ(n^{logb^a})$, then $T(n) = Θ(n^{logb^a}lgn)$
3. If $f(n) = Ω(n^{logb^{a+e}})$ for some constant $e>0$, and if $af(n/b) <= cf(n)$ for some constant $c<1$ and all sufficiently large n, then $T(n)=Θ(f(n))$

*driving function* & *watershed function*

### Merge-Sort
[[排序算法-Sorting Algorithms#Merge Sort]]
#### Optimization methods
1. Only copy the first sorted list，leave the second in place
2. Once first list is merged，the remainder of the second is already in place
3. Only allocate working space once
4. Before any copy prior to merge，test if lists already ordered
#### Top-Down & Bottom-Up version
If N is not the perfect number of power of 2，they will be different（comparisons will different）

## Algorithm  Problems
Given n chips，some are good and some are bad（let the strict majority of chips are good）
You can test chips in pairs
A good chips will tell if the other is good or bad
A bad chip might not

---
# Flash Cards
