# Quicksort

### 1. Introduction

* Quicksort is a more efficient sorting algorithm than either selection or insertion sort
	* It sorts an array by repeatedly partitioning it
* Partitioning is the process of dividing an array into sections (partitions), based on some criteria
	* Big and small values
	* Negative and positive numbers
	* Names that begin with a-m, names that begin with n-z
	* Darker and lighter pixels

-----

### 2. Partitioning

* The Quicksort algorithm works by repeatedly partitioning an array
* Each time a sub-array is partitioned there is
	* A sequence of small values,
	* A sequence of big values, and
	* A pivot value which is in the correct position
* Partition the small values, and the big values
	* Repeat the process until each sub-array being partitioned consists of just one element
* Ideally, partitions would be halved in size
	* This doesn’t always happen… what is the worst case?

