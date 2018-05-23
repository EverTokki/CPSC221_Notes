### C++ Linked Lists

**Node.h**

```cpp
class Node {
public:
	int data;
	Node* next;
}
```
**Node.cpp**
```cpp
class Node {
public:
	int data;
	Node* next;
	Node(int d, Node* nd) {
		data = d;
		next = nd;
	}
}
```

**Print all values in a linked list:**
```cpp
void printList (Node* head) {
	while(head != null) {
		cout << head->data << endl;
		head = head->next;
	}
}
```
Q: What is the problem of this code?
We're moving the head itself which should be keeping track of the first item in the list. So we cannot keep track of the first item in the list anymore.

[!Graphic of ll]

**Fixed code:**
```cpp
void printList (Node* head) {
	Node* cur = head;

	while(cur != null) {
		cout << head->data << endl;
		cur = cur->next;
	}
}
```

**LList.cpp**
```cpp
void LList::insertBack(int val) {
	Node* newN = new Node(val, null);

	tail->next = newN;
	tail = newN;

	length++;
}
```

**Base case:**
Consider the case where we're working with an empty list.

**LList.cpp**
```cpp
void LList::insertBack(int val) {
	Node* newN = new Node(val, null);

	if (head == null) {
		head = newN;
	} // if tail == null, we can't do tail -> next
	else {
		tail->next = newN;
	}
	
	tail = newN;
	length++;
}
```


/// Why not cur -> next 
and then
cur -> next -> prev?

because by that time we're already pointing to 7 in the example
which we already reset the pointer to
so it wont work