# Lecture 1: Overview and Asymptotic Analysis

#### 1. Definitions

  * Algorithm: A sequence of steps to produce a solution to a problem, given a set of inputs

  * Data Structure: A representation of data in the computer's main memory (so that it can be used efficiently)

  * Abstract Data Type (ADT): A collection of data and a set of operations that can be performed on the collection so that the data behave in a well-defined way

#### 2. Suppose we have a collection of people at a concert. 
#### How are we going to find a specific person, given their name?

```
T(n) = Running time
n = input size

* The input size is indicated with the number n; sometimes there can be multiple inputs.
```

  * Ask them to stand up and wave: T(n) = 60

  * Ask everyone in the audience, one at a time, if their name is the same as the given: T(n) = 7n+4

#### 3. Asymptotic Analysis

There are different metrics of algorithms:

  * Time complexity: How long does it take to complete the given task?

  * Space complexicity: How much memory does it take to execute the task?

Running time is a function of *n* such as:
  
  * T(n) = 4n + 5
  * T(n) = 0.5nlogn - 2n + 7
  * T(n) = 2^n + n^3 + 3n
