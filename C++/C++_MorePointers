# More Pointers

**double_pointer.cpp**
```cpp
int main() {
	int a = 4;
	int b = 7;
	int& c = a;
	int* x = &a;
	int** y = &x;
	int* z = &a;

	c = 2;
	x = &b;
	**y = 8;
	y = &z;
	**y = 5;
}
```

Variable values after execution of line numbers:
(assume `&a = 0x1000`, `&b = 0x2000`, and `&x = 0x3000`)


[!one graphic that shows all steps - including 5 mini-graphics]

||`a`|`b`|`c`|`x`|`y`|`*x`|`*y`|`**y`|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Line 7|4|7|4|0x1000|0x3000|4|0x1000|4|
|Line 9|2|7|2|0x1000|0x3000|2|0x1000|2|
|Line 10|2|7|2|0x2000|0x3000|7|0x2000|7|
|Line 11|2|8|2|0x2000|0x3000|8|0x2000|8|
|Line 13|5|7|5|0x2000|Address of z|5|0x2000|5|

**parameter_passing.cpp**
```cpp
void sum(int* x, int* y) {
	*x = *x + *y; // Potentially unsafe, because changes the value of a
}
void subtract(int x, int y) {
	x = x - y;
}
void multiply(int& x, int& y) {
	x = x * y;
}

int main() {
	int a = 5;
	int b = 6;
	int* p = &a;
	int* q = &b;

	std::cout << a << " " << b << std::endl;
	// Output: 5 6

	sum(p, q);
	std::cout << a << " " << b << std::endl;
	// Output: 11 6

	subtract(a, b);
	std::cout << a << " " << b << std::endl;
	// Output: 11 6

	multiply(a, b);
	std::cout << a << " " << b << std::endl;
	// Output: 66 6 
}
```

#### Parameter passing

We need to look closely at our function calls and our function signatures

*What are we passing?*
  * Pass by value: Passing ints in java, subtract, copy values
  * Pass by reference: Alias to calling object, multiply
  * Pass by pointers: Address of an object in memory, sum


#### Calling Functions

||By Value|By Pointer|By Reference|
|:---|:---:|:---:|:---:|
|Exactly what is copied when the function is invoked?|Copy of the object|Address|Address (alias to the variable sharing the same memory address with what we're calling the function with)|
|Does modification of the passed in object modify the caller's object?|No|Yes|Yes|
|Is there always a valid object passed into the function?|Yes|No (NULL)|Yes (Because when we create an alias, we will always refer to a value to something that already exists)|
|Speed|Slow. Needs to copy ALL the memory. e.g.) Big arrays|Fast. Only thing we're passing over is just an address.|Fast.|
|Safety|Safe - Can't do damage to the original object.|Not safe: Follows the address and changes the data which can corrupt the original data.|Not safe.|