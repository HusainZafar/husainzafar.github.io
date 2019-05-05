---
layout: post
---

Three approaches. O(n^3), O(n^2), O(n)

Approach 1: O(n^3)
Calculate sum of each subset and check for modulo

```
def divisibleSubsetCount(A, k):
	result = 0
	n = len(A)
	for start in range(0, n):
		for end in range(start, n):
			subsetSum = 0
			for index in range(start, end+1):
				subsetSum += A[index]
			if(subsetSum % k == 0):
				result += 1
	return result
			 
```

Approach 2: O(n^2):
Use prefix sum to calculate the subset sum efficiently.

```
def divisibleSubsetCount(A, k):
	result = 0
	n = len(A)
	prefixSum = []
	sum = 0
	for num in A:
		prefixSum.append(sum + num)
		sum += num
	
	for start in range(0, n):
		for end in range(start, n):
			if start == 0:
				subsetSum = prefixSum[end]
			else:
				subsetSum = prefixSum[end] - prefixSum[start-1]
			if (subsetSum % k == 0):
				result += 1
	return result
	
```