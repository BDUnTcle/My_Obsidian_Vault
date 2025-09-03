---
create date: 2024-04-08
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
- [[Introduction to Dynamic Programming]]
- [Videos: Dynamic Programming](https://www.youtube.com/playlist?list=PLSVu1-lON6LwaLkn1J4slNQEp2oEjWCqX)
- [[Floyd-Warshall All-Pairs Shortest Paths]]
- [[Drawing 2024-04-08 10.38.51.excalidraw]]

---
# Review List
>[! abstract] Main Topics
>1. Why iterated version is normally faster than memoized version?
>	1. There are too many method call during memoized version

---
# In-Class Problems
>[!question] Find the length of the longest common subsequence of 2 given sequence
```
//basic recursive
LCS(X[],Y[],X_len,Y_len)
{
	if(X_len==0 || Y_len==0) return 0;
	if(X[X_len-1]==Y[Y_len-1])
		return 1+LCS(X,Y,X_len-1,Y_len-1)
	else
		return Max(LCS(X,Y,X_len-1,Y_len),LCS(X,Y,X_len,Y_len-1))
}
//after memoize
Initia(T)
{
	T[X_len,Y_len] = -1;
	T[0,anything] = 0;
	T[anything,0] = 0;
}
LCS(X[],Y[],X_len,Y_len,T[])
{
	if(T[X_len,Y_len]>=0) return T[X_len,y_len];
	if(X[X_len-1]==Y[Y_len-1])
		return T[x_len,y_len]=1+LCS(X,Y,X_len-1,Y_len-1)
	else
		return T[x_len,y_len]=Max(LCS(X,Y,X_len-1,Y_len),LCS(X,Y,X_len,Y_len-1))
}
//iterate version
LCS(X[],Y[],X_len,Y_len,T[])
{
	for(i=1 to x_length)
		for(j=1 to y_length)
			if(X[x_len-1]==Y[y_len-1])
				T[i,j]=1+T[i-1,y-1];
			else
				T[i,j]=Max(T[i-1,j],T[i,j-1])
}
```
---
# Flash Cards
