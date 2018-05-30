# ADT - Stacks and Queues

Programming Assignment 1 
In PA1, you are asked to implement a linked list where each node stores a Block object (our linked list class is named Chain but suppose our class is called LinkedList)

```cpp
class LinkedList {
private:
	class Node {
		...		
	};
	...
public: 
	LinkedList();
	...
	void insertFront (Block & ndata);
	// finish this notes

	}
``` 

What is a data structure?
	*  A storage structure for data
	* A way of storing, accessing, organizion, and manipulating data using well-defined operations



An Abstract Data Type (ADT) is :
	* Mathematical description of an object and the set of operations on the object
		* Describes *what* data are stored but not *how* they are stored
		* Describes precisely *what* effect the operations have on the data, but not *how* the operations are carried out


Example: Dictionary ADT
	* Stores a pair of strings: (word, definition)
	* Operations:
		* Insert (word, definition)
		* Delete (word)
		* Find (word)

	* We use a data structiore to implement an ADT.

Client vs Programmer
	* Clients want to know how to use something
		* *What* operations are available, and *what* do they do
	* Programmers must decide *how* to implement the operations
	* Their choice may be influenced by a number of things:
		* Execution speed
		* Memory requirements
		* Maintenance (debussing, extending, etc)

### ADT: Queue

Queue operations:
	* Create 
	* Destroy
	* Enqueue: inswert an item at back of the queue
	* Dequeue: remove the item at the front of the queue
	* Peek: look at the item at the front of the queue (but do not remove)
	* isEmpty

Queue property:
	* If x is enqueued before y is enqueued, then x will be dequeued before y is dequeued
	* **FIFO: First In First Out**
	* Any item inserted in queue before will be the first one to be removed

Applications:
	* Any line-up where service is ordered by arrival: coffee at starbucks, job in a printer, etc.

	