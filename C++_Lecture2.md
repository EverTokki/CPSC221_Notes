# C++ Programming Basics
[https://repl.it/@aestey/cpsc221-sphere]

### 1. More C++
**main.cpp**
```cpp
#include "sphere.h"
#include <iostream>

int main() {
	Sphere s;
	std::cout << "Radius: " << s.getRadius() << std::endl;
	return 0;
}
```

Several things about C++ are revealed by our first program:

  1. always start at main 
    `main.cpp :4`
  2. declare an object of type Sphere 
    `main.cpp :5, main.cpp :1`
  3. print out radius of S 
    `main.cpp :6, main.cpp :2`
  4. However, our program is unreliable. Why?
    * No constructor - s could be not instantiated
    * in C++, every variable has some defauly value but we haven't set that.


Default Constructor:
  
  Automatic; assign "random" (junk) values to variables if you dont initialize them ourselves.

 
#### Custom Default Constructor

**sphere.h**
```cpp
#ifndef SPHERE_H_
#define SPHERE_H_

class Sphere {
public:
	Sphere();
	Sphere(double r);

	double getRadius();
	void setRadius(double r);

private:
	double r;
};

#endif
```

**sphere.cpp**
```cpp
#include "sphere.h"

Sphere::Sphere() {
	r = 0;
}

Sphere::Sphere(double r) {
	this->r = r;
}

double Sphere::getRadius() {
	return radius;
}

void Sphere::setRadius(double r) {
	radius = r;
}
```

#### Custom, Non-Default Constructors

A look ay memory

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