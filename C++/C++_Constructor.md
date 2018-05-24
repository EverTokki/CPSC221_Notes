# Constructors
Code used in this lecture can be found [here.](https://repl.it/@aestey/cpsc221-sphere)

------

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

  1. Always start at main 
    `main.cpp :4`
  2. Declare an object of type Sphere 
    `main.cpp :5, main.cpp :1`
  3. print out radius of S 
    `main.cpp :6, main.cpp :2`

However, our program is unreliable. Why?
  * No constructor - There is a possibility that s could be not instantiated
  * In C++, every variable has some default value but we haven't set that.

------
 
### Custom Default Constructor, Custom Non-Default Constructor

Default Constructor:
  * Automatic; assign "random" (junk) values to variables if you dont initialize them ourselves.

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
------
