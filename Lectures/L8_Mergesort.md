# Mergesort

### 1. Introduction

* Merge sort is an efficient sorting algorithm
	*  Divide and conquer
	*  Divides an array in half, and merges the two sorted halves
* Sorting happens during the merge step
	* One unsorted array is divided into half
	* Looks at each element of the array and if one is smaller than another, put it into another array and repeat this process until both arrays are merged and sorted

**But how do we get the sorted sub-arrays?**
* Repeatedly divide arrays in half until each sub-array contains a single element
	* an element by itself is already sorted
	* merging two single-element arrays is simply a single comparison
* The merge step copies the sub-array halves into a temporary array
	* and the merged elements are copied from the temporary array back to the original array

The running time of this sorting algorithm is very good, but every time we use a temporary array, we use up space which is not efficient in terms of memory

**How many comparisons are made in the merge step?**
* **Worst case:** n − 1 comparisons
(need to check every subarray index)
* **Best case:** n⁄2 comparisons
(reach the end of one subarray, copy the rest of the second subarray)
* Still copying n subarray items in any case

How many times can the subarray be divided?

log_2 (n) divisions to reach 1-element subarrays(proof coming up)

------

### 2. Algorithm

| Equations | Steps |
| :---: | :---: |
|`T(1) ≤ b`| Base case|
|`T(n) ≤ 2T(n/2) + cn`| General equation|
|`2T(n/2)`|# of operations to sort left half + # of operations to sort right half|
|`cn`|# of operations to merge the two sorted arrays|
|||
|`T(n) ≤ 2(2T(n/4) + cn/2) + cn` |By substitution|
|`T(n) ≤ 4(2T(n/8) + cn/4) + 2cn` |By substitution, again|
|`T(n) ≤ 2ᵏT(n/2ᵏ) + kcn` |General case|
|`= nT(1) + (log₂n) + cn` |For `k = log₂n`|
|`= bn +cnlog₂n`| Because `T(1) ≤ b`|
|∴ T(n) ∈ O(nlogn)||

```
In order to reach the base case, we need T(1)
In order to make T(1), we need n/2ᵏ = 1
n/2ᵏ = 1
n = 2ᵏ
∴ k = log₂n
```

-----


### 3. Characteristics

 * Stability?
	* Yes!
	* When merging left and right sub-arrays, make sure element is grabbed from left sub-array for a tie
 * In-place?
 	* No, we create temporary arrays during each recursion step to hold all n items.
 	* There is also the cost of the recursive call stack!