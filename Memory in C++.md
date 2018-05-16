# Memory in C++

A look at memory

### 2. Variable Scope
#### What does scope mean?

  Accessibility or lifetime of a variable

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

#### Lifetime 

  Allocated when a procedure starts, deallocated (freed) when procedure returns

  Each function has their own private copy of their own local variables

A stackframe for all data needed in fn1
 * int a is in here!

 -> fn2() -> 

Data is stacked on top of functions
After a function is returned, the memory that was used for the data is freed and deallocated. Now that memory can be used for something else, other data.

If a value of a variable is not initialized, the program might just bring the junk that was stored in *that* memory (where the new variable sits) which is the data that was used at that specific memory space right before it was deallocated.

#### Dynamic Allocation

When we use the `new` keyword we allocate memory on the heap.
	* We use this to create a new instance of the object (and call its constructor)
	* This returns a pointer to where that data is stored in the heap
	* Makes sure we have enough memory to instantiate variables
	* Let's create this memory in the heap and I'm going to keep it there unless the programmer explicitly uses the keyword `delete` which frees up the allocated space.

The only way to free heap memory is the `delete` keyword