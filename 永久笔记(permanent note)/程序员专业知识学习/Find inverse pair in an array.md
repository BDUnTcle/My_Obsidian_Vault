#程序员 #CS/Algorithm 
# Prompt
Give a Array A[n]，find how many inverse pair the array has？
PS：Define a inverse pair is the first element > the second element，which are chosen from the array

Ex：
A={5，8，6，4，7}，
*{5，4}，{8，7}* is all inverse pairs。
The total number of inverse pair in A is *5*：{5，4}，{8，6}，{8，4}，{8，7}，{6，4}

---
# Intuition
> We can use a simple double loop to solve this problem
```java
int findIversePair(int[] A)
{
	int total=0;
	for(int i = 0; i < A.length; i++)
	{
		for(int j = i+1; j< A.length; j++)
		{
			if(A[i] > A[j])
			{
				total++;
			}
		}
	}
	return total;
}
```
**the runtime of this algorithm is O($n^2$) and if we want to improve the efficiency**
**How could we do？**
### Some hints to solve this problem
- the key point is how to determine a pair to be a inverse pair？
It looks simple：
> if(first element > second element), then this pair is inverse pair
- So basically, we are compairing each elements in the array and find the summation which let us condition agrees.
*Does it sounds familiar?* 
> Yes, we do almost the same thing when we sorting a random array but we just don't count how many times our comparison condition if statement agrees or not.

Then we maybe could use those sorting algorithm to help us, for instance：insertion sort，merge sort ... etc.

---
# How insertion sort solve this problem?
let us write a insertion sort, and think how it works in every iteration
```Java
public void swap(int[] nums,int index_a,int index_b)  
{  
	int tmp = nums[index_a];  
	nums[index_a] = nums[index_b];  
	nums[index_b] = tmp;  
}  
public int[] sortArray(int[] nums) 
{  
	int total=0;
	//insertion sort  
	for(int i = 1; i< nums.length; i++)  
	{  
		int j = i-1;  
		while (j>=0 && nums[j+1]< nums[j])  
		{  
			swap(nums,j+1,j);  
			j--;  
			total++;//count the inverse pair
		}  
	}  
return nums;  
}
```
In the insertion progress，in each iteration，we can easyly know how many inverse pair we could found（*because in the if statement，we can count the time of out inverse pair condition agrees*）。
Also，since we already counted the sum of inverse pairs，the order of the part of the array has been changed doesn't influence the next iteration（*if you are told that you can't change the original array, you can just copy it to a new array and do all the operation in the new array. It's not a big deal*）.

## Time complexityuntime
Since the runtime of insertion sort is **O(n+k)** in which k is the inverse pair in the array.
So if the total number of the array's elements is small, is a pretty good algorithm to this problem 

---
# How Merge Sort solve this problem？
like the insertion sort，in merge sort，at the phase of merge steps，if two elements is inverse pair，then they will be hold in the original list to wait next comparison。
We could also count and get the total number of inverse pair after the whole sorting process go over

## Time complexity

**O(nlgn)**

---
> As you see，we could use all kinds of sorting algorithm to solve this problem with just a little modification
# How to use Binary tree structure to try to solve this？
We can built the B-tree ：
- 