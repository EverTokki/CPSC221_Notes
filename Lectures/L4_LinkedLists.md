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

Visualization
  * A linked list is a chain of nodes where each node stores the address of the next node
  [!Graphic]

Implementation
```cpp
class Node 
{
public:
	int data;
	Node* next;
};
```

  * Attributes / members of a particular node can be accessed using the '.' (dot) operator, or the '->' (arrow) operator as a shorthand for pointer types
   * Equivalent to dereferencing and using dot operator

Building a linked list
```cpp
Node* a = new Node(7, null);
a->next = new Node(3, null);
Node* p =a; // Last two lines are equal to Node* p = a->next
p = p->next; //go to next node

p=p->next; // this will become a loop.
```
  [!Graphic]

  Q: Should we delete at the end?
  We don't need to delete the p, and we'll delete everything else when we're done using the data.

  Q: How do we stop the loop? (Line 42)
  As soon as we get that null.

Insertion
  * Insertion in a singly-linked list requires only updating the next node reference of the preceding position
  [!Graphic - slide "Insertion"]

Delet

