# C++ Programming Basics
[https://repl.it/@aestey/cpsc221-sphere]

### 1. More C++ - Constructors
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

 
### 2. Custom Default Constructor, Custom Non-Default Constructor

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

// Custom default constructor
Sphere::Sphere() {
	r = 0;
}

//Custom non-default constructor
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
```
As soon as we define custom contructor(s), we must use one of our defined constructors.
```

### 3. Pointers and References - Introduction
A major component of C++ that will be used throughout all of CS221 is the use of references and pointers. 
References and pointers both:
  * Are extremely powerful, but extremely dangerous
  * Are a **level of indirection** via memory to the data.

 As a level of indirection via memory to the data: 
   1. `*` pointer to where data is in memory
   2. `&` address to where data is being stored

### Pointers and References