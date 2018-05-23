## Linked Lists

Optimization of Unsorted lists:
We can remove an item from an array and put the last element in that place instead so that we don't have to shift every element in the array to fill that empty space up.

What is a linked list?
  * A linked list is a dynamic data structure that consists of nodes linked together.
  * A node is a data structure that contains
  	* Data
  	* The location of the next node
  	* (The location of the previous node)

  * A node contains the address of the next node in the list
  	* In c/C++ this is recorded as a pointer to a node
  * Nodes are created in dynamic memory
  	* And their memory locations are not in sequence
