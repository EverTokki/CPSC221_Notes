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
