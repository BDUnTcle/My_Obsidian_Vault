#程序员 #CS/Algorithm/QuickSort 

-  [[CS-146 Sec 05 - Data Structures and Algorithms]]
- [[{CS146}-Class 8 Quick Sort]]
Related resources：

---
# Basic Concept
1. Separate elements into two groups: *small keys* and *large keys*
2. Recursively sort the group with small keys and large keys
3. Use one element(called **pivot** or **bound**) to separate small and large groups (the approach of finding the *pivot* is called **Partition**)

>[!note] The Basic Pseudocode for quick sort
```java
def QuickSort(A[],start,end)
	if(start >= end) return;
	pivotIndex = Partition(A,start,end); //Partition returns an index
	QuickSort(A,start,pivotIndex-1);
	QuickSort(A,pivoIndex,end);
```
---
# The Partitioning Algorithms
## 1. Nico Lomuto Version, Used in CLRS
- Choose the *last element*  as **Pivot**
- Compare pivot against elements, left to right
	- If the element is larger than our pivot, keep it in the same position (we need to keep tracking the index of the first element in the larger group)
	- If the element is smaller than our pivot, swap it with the first element of the larger group (this makes the respective order in the larger group would change through the algorithm running)
- *Unstable sort：elements with equal keys might switch order*
>[!tip] The Worst Case (bad pivot)
>> If the list are already sorted, then the pivot will be the largest value.
>> The Runtime will takes $θ(n^2)$

```python
def Partition(A[],start,end)
	int i =start, j=start;
	while(j < end-1)
	{
		if(A[end] >= A[j])
		{
			int tmp = A[i];
			A[i] = A[j];
			A[j] = tmp;
			i++;
		}
		j++;
	}
	int tmp = A[end];
	A[end] = A[j];
	A[j] = tmp;
```
## 2. Hoare's Partition
- Using pivot from the middle
- Partition of small elements on left extend this partition until you run into a large element
- Partition of large elements on right extend this partition until you run into a small element
- when both partitions are blocked, swap those elements and continue 
> Pivot get included in one partition.
> Values equal to pivot can be split between partitions, no special block needed for duplicated
> Random pivot on distinct values requires n/6 expected swaps(Lomuto expects about n/2)

**Although the Hoare‘s Partition use fewer swap，and run faster in duplicated case，but its harder to code，teach，debug，prove correct**

---
# Runtime and Performance Analysis
> If all the elements are randomly sorted and not have too much duplicate valur, the quick sort is good
## Worst Case
### If use the last element as pivot
- If the list are sorted, then you need to compare all element aganist the pivot in each recurence
> Runtime:  $T(n) = T(n-1)+n=Θ(n^2)$ ， because after each loop，the index of pivot just from n to n-1
> 
> Space: Θ(1) of total room to store elements, Θ($lgn$) each excluding program stack but the program stack grows to Θ(n) depth

**How to avoid the worst-case space requirement ?** 
- *Make first recursive call on group with fewer elements*
worst case ：Θ($lgn$) program stack depth
```java
//Avoid Worst Case Stack Usage with Optimized Tail Recursion
QuickSort(A[],start,end)
{
	if(start>=end) return;
	pivotIndex = Partition(A,start,end);
	if(pivotIndex - start < end - pivoIndex)
	{
		QuickSort(A,start,pivotIndex-1);
		QuickSort(A,pivotIndex,end);
	}
	else
	{
		QuickSort(A,pivotIndex+1,end);
		QuickSort(A,start,pivoIndex-1);
	}
}
```
### if there are many duplicated elements
very close to the worst case above
> Expected Θ($n^2$) runtime and
> Expected Θ(n) stack depth
## Average (Expected) Performance
- Assumtiion：no（or few）duplicate values
### If pick a random element from the partition as a pivot（Randomized Version）
> Expected runtime：$nlgn$
> Expected stack depth：$O(lgn)$

---
# Optimizations
## 1. Pivot Picking
> we want to pick a pivot to let each side of items seperated by the pivot do not have too much gaps
- try to avoid "bad" pivot for large n:
	- 2% chance of picking a pivot in top or bottom 1%
	- 20% chance of picking a pivot in top or bottom 10%
- If you pick 3 elements and take median as pivot:
	- 0.596% chance of picking a pivot in top or bottom 1%
	- 5.6% chance of picking a pivot in top or bottom 10%
For non-randomized version, consider using the median of  the first, last and middle items from a block

## 2. Insertion sort on Small Subproblems
> Insertion Sort runs faster than Quick Sort on small inputs

## 3. Multiple Pivot

## 4. Naive Parallelization
# "Selection" through quick sort
- Find the Maximum element
- Find the Minimum element
- Find the k-th smallest element
use quick sort, break when get a pivot index which is biger than the k-th during the recurrence

# Analysis
## QuickSelect Analysis
**T(n) = Θ(n)**

## QuickSort Analysis
**T(n) = Θ(nlgn)**
### nomal analysis
### new approach
try to find the number of comparisons in once sort
- find the probability of 1 pair get comparied
- inductively find over all case