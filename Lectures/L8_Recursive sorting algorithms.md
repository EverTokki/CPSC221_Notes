Recursive sorting algorithms

Merge sort
 * Merge sort is an efficient sorting algorithm
 	*  Divide and conquer
 	*  Divides an array in half, and merges the two sorted halves
* Sorting happens during the merge step
	* One unsorted array is divided into half
	* Looks at each element of the array and if one is smaller than another, put it into another array and repeat this process until both arrays are merged and sorted

But how do we get the sorted sub=arrays?
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