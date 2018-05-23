### 1. Recap:

Pass by value ...

Why do we use the keyword const?
We want to create a copy of the object:
```
void changeRadius (const Sphere& s1)
```
We want to create a new Sphere to copy over the values

Course webpage >> Resources : C++ Videos; Memory, pointers, constructors, deconstructors
Do exercises! Watch the videos and follow along with them.

### 2. The Big Three in C++
The rule of thumb in C++ is that if a class defines any of the three functions constructtor, destructor, and copy assignment operator - then it should explicitly define all three and not rely on their default implementation.

  * Constructor: Any time we create an instance of an object
  * Destructor: Any time an object memory is being de-allocated
    * Stack: When the function returns
    * Heap: When we delete. (When you use `new`, you should use `delete`. Don't use `delete` when you haven't used `new`.)


Q: Can you use the delete keyword in another function?

```cpp
makeSphere() {
Sphere* s1 = new Sphere(4);
// This is returning a pointer to where sphere data is stored in memory.

return s1;
// We are returning the value, or 0x3000 of s1.
}
// !!! Graphic on handout
``` 

```cpp
Sphere *mySphere = makeSphere();

delete mySphere;
// This deletes the original Sphere data.
```

Copy assignment operator: `=` Clearing memory and then updating state

**CustomArray.h**

```cpp
class Array {
	private:
		int size; // This is the size of the memory
		int* vals; // Pointing to where the array is stored

	public:
		~Array(); // Destructor in C++
		Array (int s, int* v);
}
```

**Implementation:**
```cpp
Array::Array ( int s, int* v ) {
	size = s;
	vals = new int[size];
	// Copy values from v into vals
	// ...
}

Array::~Array() {
	delete vals;
	vals = NULL;
}

int main() {
	int vals[4] = {1, 2, 3, 4};

	Array a1(4, vals);
	Array a2(a1);
	return 0;
}
```

Q: This program crashes when run. Why?

[!Graphics]
When the function returns, the destructor is going to be called.
This sets the values of a1's array to null.
The destructor goes to `a1` and clears all the data for a1. However, if the destructor is called for a2, the program cannot clear a memory that already has been deleted.

The code crashes because a1 and a2 both have `vals` which is a pointer to an array on the heap. Both the pointer vales are holding the same address value. Hence when we delete a1, we can no longer delete that in a2. What we want is for a2 to be pointing to something else which has its own values of {1, 2, 3, 4}. What we did was a shallow copy, what we want is a deep copy.


const will allow us to limit modifying the constructor that is given to an argument.

[!Graphic .vs->]

. notation: i am at the right place
-> notation: i am not at the right place i am supposed to be, so i want to dereference what I need

`a1.size`
offset to local variable

`a2->size`
follow the pointer and then offset to local variable

Explicitly defining a custom copy constructor:

**Implementation**

```cpp
Array::Array( int s, int* v) {
	 // ...
}

Array::Array(const Array& a) {
	size = a.size;
	vals = new int[size];

	for(int i=0; i<size; i++) {
		vals[i] = a.vals[i];
	}
}

Array::~Array() {
	// ...
}
```

