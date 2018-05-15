# C++ Programming Basics

### 1. How to

  * To compile: `g++ -o name FirstProgram.cpp`
  * To run: `./name`

 #### FirstProgram.cpp
 ```cpp
#include <iostream> //allows for printing

 int main() {
 	int max = 0;

  //declare an array below:
 	int arr[] = {6, 1, 3, 7, 5};

  //find highest value in array:
 	for (int = 0; i < 5; i++){
 		if (arr[i] > max) {
 			max = arr[i];
 		}
 	}

 	std::cout << "max number in the array is: " << max << "\n";
 	return 0;
 }
 ```

 ### 2. Variables and Classes in C++

 Every variable is defined by four properties:
   1. type
   2. name
   3. value
   4. memory location

 And every variable is one of two types:

 | Primitive | Complex(Object) |
 | :--- | :--- |
 |int myFavoriteInt;|Sphere myFavoriteSphere;|
 |char grade = 'A';|Cube rubix;|
 |double gamma = 0.653;|Grade courseGrade;|

#### **Creating New Types**
 In data structures, we will be learning and creating new types of structures to store data.

#### Big Idea: Encapsulation
When we create a class in c++ we want to separate 2 things:
  * the API: **WHAT** is the class supposed to do?
  * the Implementation: **HOW** does it do it?

#### Encapsulation principles: C++ Convention
  * sphere.h
    APIin.h
    Define what other programmers will be able to use
  * sphere.cpp
  	implementation
  	The implementation of the code

### 3. Our first class

**sphere.h**
```cpp
#ifndef SPHERE_H_
#define SPHERE_H_

class Sphere {
public:
	// this is accessible from other classes.
	double getRadius();
	void setRadius(double r);
	double getVolume();

private:
	// this is not accessible from other classes.
	double radius;
};

#endif
```

**sphere.cpp**
```cpp
#include "sphere.h"

double Sphere::getRadius() {
	return radius;
}

void Sphere::setRadius(double r) {
	radius = r;
}

double Sphere::getVolume() {
	return = (4/3) * 3.14 * radius^3;
}
```

```
Note: 
ifndef = if not defined 
(this acts like an if for the compiler)

Has this already been defined(aka. included in a cpp file)? If not, include it
```

### 4. Key Concepts in C++ Classes:
Every class will be made up of common key pieces:

  1. Inclusion guards
  `sphere.h :1 :2 and :17`
  2. class definition (ends with ;)
  `sphere.h :4 ... :15`

  3. including header file
  `sphere.cpp :1`
  4. double colon is scope resolution operator
  `sphere.cpp :3`
  
   ⇒ This signifies that the method belongs to the class specified before the double colon

