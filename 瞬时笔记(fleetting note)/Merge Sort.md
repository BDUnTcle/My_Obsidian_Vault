---
create date: 2024-05-02
tags:
  - review
  - 程序员
  - CS
  - CS/Algorithm
  - CS/Algorithm/Sorting
modification date: 
type: LearningNote
---

[[#Flash Cards & Review List]]
# Background & Materials
- [[{CS146}-Class 7 Master Method,Merge Sort]]
- The Idea of Recursion
---
# Intuition and Standard Version (Top Down)
>[!tip] Merge Sort basic Idea
>- If you have 2 lists which are both already sorted, you can merge these 2 list to a longer sorted list in linear total time 
>>[!note] Example: 2 ordered lists:{-10, 2, 4, 5, 48, 88}  {1, 2, 4, 5, 14, 18}
>>Go through both list from left to right, put the smaller one in the sorted list then go next
>>>[!question] How to get the 2 sorted list? (Using recursion)
>>> ![[Merge-sort-example-300px.gif|500]]

So, by following the idea above, we could get the **basic merge sort algorithm** without considering any optimization
```java
MergeSort_BasicIdea(Array A[])
{
	if(A.length < 2) return;
	Array B = new Array[];
	Array C = new Array[];
	copyArray(A,B,0,A.length/2);//Copy the first half of A to the new array B
	MergeSort(B);
	copyArray(A,C,A.length/2+1,A.length);//Copy the second half of A to the new array C
	MergeSort(C);
	Merge(A,B,C);//merge B and C back into A, let it be ordered
}

MergeSort_StandardVersion(Array A[], int start,int end)
{
if(end<=start) return;
int mid = (start+end)/2;
MergeSort(A,start,mid);
MergeSort(A,mid+1,end); 

copyArray(A,B,start,mid);
copyArray(A,C,mid+1,end);

merge(A,B,C);
}
```
- **Runtime Analysis**
	- $T(n)=2T(n/2)+θ(n)=θ(nlg^n)$ 
- Tie Breakers
	1. **For equal values**: the lower indexed value goes first (*make algorithm stable*)
	2. **For a odd number of n**: the left half gets the extra one
- --- 
# Optimizations
>[!note] The idea of optimization has 3 purpose
>1. Reduce the total copy times (Because the copy takes times, less copy, faster run)
>2. Reduce the comparison times (Same reason of 1)
>3. Reduce the total space we use (Space optimization)

1. Only copy the first sorted list, leave the second in place
	1. Decrease copies by about 25%
	2. Doesn't change number of comparisons
2. <mark style="background: #FFB86CA6;">Once first list is merged</mark>, the remainder of the second is already in place (no need to copy it again after compare with others) <mark style="background: #FFB8EBA6;">Because the first list is merged means there is no elements needs to be compared since the left list and the right list are already ordered, and there is no elements left in the left, thus there is no need to do anything to the elements in the right list which are already sorted.</mark>
	1. Decrease copies, amount depends on data
	2. Decrease comparisons, amount depends on data
3. Only allocate working space (Array B) once
4. When the left and the right lists are already sorted (the biggest element in the left is less than the smallest element in the right)
	1. Decrease copies and comparisons
	2. By doing this, in best case, algorithm now takes $θ(n)$ However, in the worst case, you need to *add extra n-1 comparisons* to the algorithm for each time you check the condition
---
# Bottom Up Version
>[!tip] idea
>Don't use recursion, just compare 2n values in each iteration (n=1,2,...)

The bottom up and top down could have different comparison when the n is not perfect power of 2.


---
# Flash Cards & Review List
>[!abstract]
>1. The Basic Idea of Merge Sort and its standard version
>2. 4 Optimizations methods
>3. Top Down and Bottom Up Version of merge sort