# Recursive sorting algorithms

### Definitions revisited

* Stability: 2 objects with equal keys in input list are in the same order when sorted.
* In-place: Something is in-place if it doesn't need auxilary data structures to implement (like an array).

### Merge sort
* Merge sort is an efficient sorting algorithm
*  Divide and conquer
*  Divides an array in half, and merges the two sorted halves
* Sorting happens during the merge step
* One unsorted array is divided into half
* Looks at each element of the array and if one is smaller than another, put it into another array and repeat this process until both arrays are merged and sorted

But how do we get the sorted sub-arrays?
* Repeatedly divide arrays in half until each sub-array contains a single element
* an element by itself is already sorted
* merging two single-element arrays is simply a single comparison
* The merge step copies the sub-array halves into a temporary array
* and the merged elements are copied from the temporary array back to the original array

The running time of this sorting algorithm is very good, but every time we use a temporary array, we use up space which is not efficient in terms of memory

How many comparisons are made in the merge step?
* Worst case: n − 1 comparisons
(need to check every subarray index)
* Best case: n⁄2 comparisons
(reach the end of one subarray, copy the rest of the second subarray)
* Still copying n subarray items in any case

How many times can the subarray be divided?
log_2 (n) divisions to reach 1-element subarrays(proof coming up)

### Analysis of recurrence relations

How to calculate the running time of the following code

```
double arrMax(double arr[], int size, int start) {
	if (start == size – 1)
	return arr[start];
	else
	return max( arr[start], arrMax(arr, size, start + 1) );
}
```

| Equations | Steps |
| :---: | :---: |
|`T(1) ≤ b`| Base case|
|`T(n) ≤ c + T(n - 1)`| General equation|
|||
|`T(n) ≤ c + c + T(n − 2)` |By substitution|
|`T(n) ≤ c + c + c + T(n − 3)` |By substitution, again|
|`T(n) ≤ k * 2 T(n - k)` |Extrapolating, `0 < k ≤ n`|
|`T(n) ≤ (n - 1) * c + T(n - (n − 1)` |For `k = n − 1`|
|`≤ (n − 1) * c+ T(1) = (n - 1) * c + b`| Because `T(1) ≤ b`|

```
c * k = constant operations
n - k = we always get rid of an element every recursive step
```

∴ T(n) ∈ O(n)

