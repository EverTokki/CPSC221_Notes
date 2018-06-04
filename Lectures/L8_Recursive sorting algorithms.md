# Recursive sorting algorithms

### 1. Definitions revisited

* Stability: 2 objects with equal keys in input list are in the same order when sorted.
* In-place: Something is in-place if it doesn't need auxilary data structures to implement (like an array).

------

### 2. Analysis of recurrence relations

**How to calculate the running time of the following code:**

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
|∴ T(n) ∈ O(n)|

```
c * k = constant operations
n - k = we always get rid of an element every recursive step
```



