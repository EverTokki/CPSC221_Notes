# Pointers and References 

### 1. Introduction
A major component of C++ that will be used throughout all of CS221 is the use of references and pointers. 
References and pointers both:
  * Are extremely powerful, but extremely dangerous
  * Are a **level of indirection** via memory to the data.

 As a level of indirection via memory to the data: 
   1. `*`: pointer to where data is in memory
   2. `&`: address to where data is being stored

### 2. Pointers and References

Often, we will have direct access to our object:
```cpp
Sphere s1; // A variable of type Sphere
```

Occasionally, we have a reference or pointer to our data:
```cpp
Sphere &s1; // A reference variable of type Sphere
Sphere *s1; // A pointer that points to a Sphere
```
#### Pointers
Unlike reference variables, which alias another variable's memory, pointers are variabes with their own memory. Pointers store the memory address of the contents they are "pointing to".

Here are things to remember on pointers and reference variables:

| Pointers `(*v)` | Reference Variables `(&v)` |
| :---: | :---: |
| Have their own memory | Don't have their own memory |
| Store the address of some data | Alias an existing variable |
| Don't have to be initialized immediately and can be null | Have to be initialized upon creation |

**main.cpp**
```cpp
int main() {
	Sphere s;
	std::cout << "Address storing `s`: " << &s << std::endl;
	// 0x1000

	Sphere *ptr = &s;
	std::cout << "Address storing ptr: " << &ptr << std::endl;
	// 0x2000
	std::cout << "Contents of ptr: " << ptr << std::endl;
	// 0x1000
}
```

Indirection Operators:

 1. `&v` : "Give me the address" : Refers to memory address storing data
 2. `*v` : "Give me the data" : Dereferencing (following) a pointer to where that data is pointing to
 3. `v->` : same as `(*v).getRadius` :

 Referring back to `main.cpp` above : `(*ptr).radius = s.radius;` // under the circumstances radius is a public variable


 You don't want to return the local address of local variables as the function will deallocate the following memory when the function returns, and it will be unaccessible after it goes out of scope.