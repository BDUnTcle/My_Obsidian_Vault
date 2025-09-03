#CS #CS/DataStructure  #CS/DataStructure/B-Trees #程序员 

# Materials
- [[{CS146}-Class 10 B-Trees,2-3 Trees,3-4 Trees]]
# Review List
>[!tldr] List
>>[!note] Binary Search Tree
>>1. Property
>>2. 3 operation
# What is a binary search tree?
Binary search tree is a binary tree that satisfy the *binary-searc-tree property*：
for a node x in the tree
1. the left subtree value is not big than it
2. the right subtree value is not small than it
---
# Important Operations
- Find: find a value x in the tree
- [[#Insertion]]
- [[#Deletion]]
- [[#inorder tree walk & preorder tree walk]]
## inorder tree walk & preorder tree walk

```java
inorderTreeWalk(x)
{
	if(x!=NIL)
	{
		inorderTreeWalk(x.left);
		print x.key;
		inorderTreeWalk(y.left);
	}
}
```

## Search
### Time&Space complexity
Runtime: 
Space:

- From the root，follow the property loop down until you found the correct position

```java
int search(int value)
{
	while(value != A[i].value)
	{
		int i = 0;
		if(value > Tree[i].value) i = right(i);
		else i = left(i)
	}
	return i;
}
```

## Insertion
### Time&Space complexity
Runtime:
Space:
- Keep compairing until to the node which has no proper subtree

```java
insertion(value)
{
	int i=0;
	Node n = root();
	while(null != n)
	{
		if(value > Tree[i].value)
		{
			i = right(i)
			n = getNode(i);
		}
		else
		{
			i = left(i);
			n = getNode(i);
		}
	}
}

```

## Deletion
### Time&Space complexity
Runtime:
Space:

1. search for the node N
	1. if it is a leaf, delete, done
	2.  if it just have one subtree, point the parent node to it subtree then delete it. done
	3. if it has two children
		- Find the smallest value that is bigger than N in its right subtree 
			1. Found y, it is a leaf, just switch the position y and N and delete N. done
			2. Found y, it only has a right subtree. switch N and y, then let y point to N's subtree, delete N. done

```java
delete(value)
{
	index = search(value);
	if(Tree[index].isleaf()) remove(index);
	else if(Tree[index].right()==null || Tree[index].left()==null)
	{
		Tree[index].parent().subtree = Tree[index].subtree();
		delete Tree[index];
	}
	else
	{
		Node n = Tree[index].right();
		while(n.left())
		{
			n = n.left();
		}
		if(n.right())
		{
			swap(n,n.parent());
			n.right() point to n.right().right();
			delete(n.right);
		}
		else
			delete(n);
	}
}
```


---
# Advanced
## To make the B-Tree more balanced when insertion

what is the *rotation* ?
![[2024-02-23#^area=svWMIX-5AcaAsosjuFtJs]]

## 2-3, 2-3-4 Trees
2-3 tree build tree following these rules:
- each non-leaf node could have 2 or 3 children
- each node could have 1 or 2 value
- all the leaf at the same level

2-3-4 tree build tree following these rules:
- each non-leaf node could have 2 or 3 or 4 children
- each node could have 1 or 2 or 3 keys
- all the leaf at the same level

### Top-donw and Bottom-up 2-3-4 Tree
The difference between top-down and bottom-up is the strategy of when you should split a node：
TOP-Down：
- immediately split the first node which is going to be no room for a new value（already  contains 3 value）when goes down to the leaf
Bottom-Up：
- goes down until leaf，and if the leaf has no room（already  contains 3 value），then split
> Why Top-Down is better？Efficiency？Memory？Multiple Threads？
