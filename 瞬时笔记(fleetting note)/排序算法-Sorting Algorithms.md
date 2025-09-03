---
tags:
  - CS
  - CS/Algorithm/Sorting
  - CS/Algorithm
  - 程序员
---

---
# Insertion Sort
The steps of the **insertion sort** algorithm:

1. Insertion sort iterates, consuming one input element each repetition and growing a sorted output list.
2. At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list and inserts it there.
3. It repeats until no input elements remain.
![[Insertion-sort-example-300px.gif|500]]

```Java
class Solution {  
    public void swap(int[] nums,int index_a,int index_b)  
    {  
        int tmp = nums[index_a];  
        nums[index_a] = nums[index_b];  
        nums[index_b] = tmp;  
    }  
    public int[] sortArray(int[] nums) {  
	    //insertion sort  
	    for(int i = 1; i< nums.length; i++)  
	    {  
	        int j = i-1;  
	        while (j>=0 && nums[j+1]< nums[j])  
	        {  
	            swap(nums,j+1,j);  
	            j--;  
	        }  
	    }  
    return nums;  
}
}
```

---
# Merge Sort
[[CS-146 Sec 05 - Data Structures and Algorithms#Class 7 - Master Method，Merge Sort#Merge-Sort]]
## Runtime & Space Requirement
---
## Optimization
## Top-Down
```Java
public void mergeSortTopDown(int[] A,int[] B,int start,int end)  
    {  
        if (start >= end) {  
            return;  
        }  
        int mid = (start + end) / 2;  
        int start1 = start;  
        int start2 = mid + 1;  
        mergeSortTopDown(A, B, start, mid);  
        mergeSortTopDown(A, B, start2, end);  
        int k = start;  
        //merge  
        while (start1 <= mid && start2 <= end) {  
            B[k++] = A[start1] > A[start2] ? A[start2++] : A[start1++];  
        }  
        while (start1 <= mid) {  
	        //involve boundary case
            B[k++] = A[start1++];  
        }  
        while (start2 <= end) {  
	        //involve boundary case
            B[k++] = A[start2++];  
        }  
        for (k = 0; k <= end; k++) {  
            A[k] = B[k];  
        }  
    }
```


# Counting Sort
## Time and Spece Complexity
Runtime：Θ(n+k) 
Space：Θ(n+k)
For k=O(n)，takesΘ(n) time and space

---
Input from a small range of k integers，0 ~ k-1
1. New array to count how many of each key
2. New array for sorted order
*Only can sort array whose element is key values（int，float）*

## improvement
1. Loop through items，increamenting appropriate counter for each
2. Loop through count，adding previous value，to get summation of counts
3. Loop through items in reverse，For each item：
	1. Use item key to index the count array 
	2. Decreament that count array value
	3. Use decremented value as array index to copy item into sorted array
---
# Radix Sort
## Time and Spece Complexity

---
## MSDF(Most Significant Digit First)

---
## LSDF(Most Significant Digit First)

---
# Bucket Sort
 
## Worst Case
all elements fall into the same bucket。then if you use insertion sort，the runtime is Θ($n^2$)