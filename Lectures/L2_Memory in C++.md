# Memory in C++

### 1. A look at memory
  * Think of memory like an array:
	* It is finite, and depends on the underlying hardware
	* Each "slot" in memory holds data
	* Each "slot" has its own unique address (large: often in hexadecimal)
	
  * Our programs take up memory: 
	* The code itself takes up memory
	* Static data (alive for the whole program)
	* Data in Stack and Heap

	* Heap grows downwards
	* Stack grows upwards
	
	------

### 2. Variable Scope
  * What does scope mean?
	* Accessibility or lifetime of a variable

  * Lifetime 
	* Allocated when a procedure starts, deallocated (freed) when procedure returns
	
  * Each function has their own private copy of their own local variables
  
  * Activation frame:
	* Each function has an activation frame, which is memory that stores data including local variables and arguments
	
```cpp
void fn1(){
	int x = 0;
	int y = x+1;
}

void fn2() {
	int z = 0;
	fn1(); 
	// at this point we will not have access to x, y anymore
}
```

  * What is the lifetime of variables x, y, and z?
    * fn2 is called: `int z = 0;`
	* fn1 is called: data of fn2 is stored in the stackframe, above the memory of fn2
	* int x and y is stored inside the stackframe
	* when fn1 is returned, the space used for fn1 is freed
	
	------

### 3. Local variables on the "Stack"

```cpp
void fn4() {
	int x, y;
}
void fn3() {
	int n;
}
void fn2() {
	fn3();
	fn4();
}
void fn1() {
	int a;
	//more code
	fn2();
}
```

  * A step-by-step breakdown:
    * A stackframe for all data needed in fn1 is created - `int a` is in here!*
	[!Graphic 1]
	* fn2 is called, and a stackframe for all data needed in fn2 is created
	[!Graphic 2]
	* fn3 is called, and a stackframe for all data needed in fn3 is created
	[!Graphic 3]
	* When fn3 returns, the stackframe is deallocated (freed) and so the `int n` space, used for fn3, is deallocated
	[!Graphic 4]
	* fn4 is called, and a stackframe for all data needed in fn4 is called on the memory space previously freed from fn3
	[!Graphic 5]
	* When fn4 returns, fn2 also returns and the space for fn2 is deallocated.
	[!Graphic 6]

After a function is returned, the memory that was used for the data is freed and deallocated. Now that memory can be used for something else, other data.

If a value of a variable is not initialized, the program might just bring the junk that was stored in *that* memory (where the new variable now sits) which is the data that was used at that specific memory space right before it was deallocated.

------

### 4. Dynamic Allocation

  * When we use the `new` keyword we allocate memory on the heap.
    * We use this to create a new instance of the object (and call its constructor)
	* This returns a pointer to where that data is stored in the heap
	* Makes sure we have enough memory to instantiate variables
	* "Let's create this memory in the heap and I'm going to keep it there unless the programmer explicitly uses the keyword `delete` which frees up the allocated space."

* Memory leaks: 
	* This happens when we don't explicitly free (delete) memory on the heap and when we can no longer access it,
	* We have no way to free up that space, which is memory that's sitting there indefinitely, unable to be freed.
	* It's important to delete *everything* we create with the keyword `new`.
	* Also - it is a good practice to set the deleted variable to `NULL`.

  * The only way to free heap memory is the `delete` keyword
    * The `delete` command calls the object's destructor (in C++)
	* This also "marks" the memory as free (usable)

------

###  5. Stack vs. Heap

Stack eventually goes back down after function calls are returned.

When we're working with the heap, we can deallocate chunks of memory that we are not using.

Now we have fragmentation- which are gaps made by freeing memory in some spaces.

  Using heaps require more complicated and thus more costly allocation and deallocation to avoid fragmentation.


Stack is a simple, cheap allocation, Why use stack over heap?
  * Lasts longer- depends on the scope we want to use in our program
  * For many programs, we need both. If we only need a variable for a function, then declare it locally (stack).

------
