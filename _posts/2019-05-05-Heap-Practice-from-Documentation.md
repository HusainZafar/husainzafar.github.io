---
layout: post
---

With Leetcode solution to top-k-frequent-elements

https://docs.python.org/2/library/heapq.html 

https://leetcode.com/problems/top-k-frequent-elements/

```python
>>> import heapq
```

<pre>
        5
    4      3
 1    2  8   7
</pre>


```python
# Create heap in linear time from an existing array
>>> heap = [5,4,3,1,2,8,7]
>>> heapq.heapify(heap)
>>> heap
[1, 2, 3, 4, 5, 8, 7]
```

<pre>
        1
    2      3
 4    5  8   7
</pre>


```python
# Push an element to an existing heap
>>> heapq.heappush(heap, 0)
>>> heap
[0, 1, 3, 2, 5, 8, 7, 4]
```

<pre>
         0
      1      3
   2    5  8   7
4 
</pre>


```python
# Pop the root and heapify
>>> heapq.heappop(heap)
0
```

<pre>
        1
    2      3
 4    5  8   7
</pre>


```python
# Merge 2 heaps
>>> heap2 = [10,11,12]
>>> mergedGenerator = heapq.merge(heap, heap2)
>>> list(mergedGenerator)
[1, 2, 3, 4, 5, 8, 7, 10, 11, 12]
```

<pre>
      heap                        heap2                            Iterable
        1                              10                                          1
    2      3          +          11  12       =                       2            3
 4    5  8   7                                                       4         5    8     7
                                                                     10 11  12
</pre> 


```python
# Largest and Smallest k elements
>>> k = 3
>>> heapq.nlargest(k, heap), heapq.nsmallest(k, heap)
([8, 7, 5], [1, 2, 3])
```

```python
# Leetcode 347. Top K Frequent Elements
>>> def topKFrequent(nums, k):
...     freqCount = {}
...     for num in nums:
...         freqCount[num] = freqCount.get(num, 0) + 1
...     heap = []
...     for key in freqCount:
...         heap.append((freqCount[key],key))
...     mostFrequent = heapq.nlargest(k, heap)
...     return [b for a,b in mostFrequent]

>>> assert topKFrequent([1,1,2,2,2,3,4,4,4,4], 4) == [4,2,1,3]
```