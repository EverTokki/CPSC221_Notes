# Asymptotic Analysis

### 1. Definitions

  * Algorithm: A sequence of steps to produce a solution to a problem, given a set of inputs

  * Data Structure: A representation of data in the computer's main memory (so that it can be used efficiently)

  * Abstract Data Type (ADT): A collection of data and a set of operations that can be performed on the collection so that the data behave in a well-defined way

### 2. Suppose we have a collection of people at a concert. How are we going to find a specific person, given their name?

```
T(n) = Running time
n = input size

* The input size is indicated with the number n; sometimes there can be multiple inputs.
```

  * Ask them to stand up and wave: *T(n)* = 60
  * Ask everyone in the audience, one at a time, if their name is the same as the given: *T(n)* = 7*n* + 4

### 3. Asymptotic Analysis

There are different metrics of algorithms:

  * Time complexity: How long does it take to complete the given task?
  * Space complexicity: How much memory does it take to execute the task?

Running time is a function of *n* such as:
  
  * *T(n)* = 4*n* + 5
  * *T(n)* = 0.5*n*log*n* - 2*n* + 7
  * *T(n)* = 2<sup>*n*</sup> + *n*<sup>3</sup> + 3*n*

#### O-Notation (Classification for running time)

![Big-O notation graph](https://github.com/EverTokki/CPSC221_Notes/blob/master/images/big_o.png "Big-O")

  *T(n)* ∈ *O(f(n))* if there are constants *c* and *n*<sub>0</sub> such that *T(n)* ≤ *c∙f(n)* for all *n* ≥ *n*<sub>0</sub> 
  * *T(n)* is bounded from above by *c∙f(n)*
  * i.e. the growth of *T(n)* is no faster than *f(n)*

![Big-Omega notation graph](https://github.com/EverTokki/CPSC221_Notes/blob/master/images/big_omega.png "Big-Omega")

  *T(n)* ∈ Ω*(f(n))* if there are constants *d* and *n*<sub>0</sub> such that *T(n)* ≤ *d∙f(n)* for all *n* ≥ *n*<sub>0</sub> 
  * *T(n)* is bounded from below by *d∙f(n)*
  * i.e. the growth of *T(n)* is no slower than *f(n)*

![Theta notation graph](https://github.com/EverTokki/CPSC221_Notes/blob/master/images/theta.png "Theta")

  *T(n)* ∈ Θ*(f(n))* if T(n)* ∈ *O(f(n))* and T(n)* ∈ Ω*(f(n))*
  * *T(n)* is bounded from above and below by *f(n)*
  * i.e. *T(n)* grows at the same rate as *f(n)*

#### Asymptotic Analysis hacks:
*Eliminate low order terms, and then constant coefficients.*
  
  * 4*n* + 5 ⇒ 4*n* ⇒ *n*
  * 0.5*n*log*n* - 2*n* + 7 ⇒ 0.5*n*log*n*
  * 2<sup>*n*</sup> + *n*<sup>3</sup> + 3*n* ⇒ 2<sup>*n*</sup> ⇒ 2<sup>*n*</sup>
  * *n*log(*n*<sup>2</sup>) ⇒ 2*n*log*n* ⇒ *n*log*n*

Examples:
  * 10,000*n*<sup>2</sup> + 25*n* ∈ Θ(*n*<sup>2</sup>)
  * 10<sup>-10</sup>*n*<sup>2</sup> ∈ Θ(**n<sup>2</sup>)
  * *n*log*n* ∈ *O(n<sup>2</sup>)*
  * *n*log*n* ∈ Ω(*n*)
  * *n*<sup>3</sup> + 4 ∈ *O(n<sup>4</sup>)*, but not Θ(*n*<sup>4</sup>)
  * *n*<sup>3</sup> + 4 ∈ Ω(*n*<sup>2</sup>), but not Θ(*n*<sup>2</sup>)

#### Typical growth rates in order
| Name | Big-O Notation | Remarks |
|:---:|:---:|:---:|
|Constant|*O*(1)||
|Logarithmic|*O*(log*n*)|log<sub>k</sub>*n*, log(*n*<sup>2</sup>) ∈ *O*(log*n*)|
|Poly-log|*O*((log*n*)<sup>k</sup>)|
|Sublinear|*O(n<sup>c</sup>)*|*c* is a constant, 0 < *c* < 1|
|Linear|*O(n)*||
|Log-linear|*O*(*n*log*n*)||
|Superlinear|*O*(*n*<sup>1 + *c*</sup>)|*c* is a constant, 0 < *c* < 1|
|Quadratic|*O*(*n*<s>2</s>)||
|Cubic|*O*(*n*<s>3</s>)||
|Polynomial|*O*(*n*<s>*k*</s>)|*k* is a constant; "tractable"|
|Exponential|*O*(*c*<s>*n*</s>)|*c* is a constant > 0; "intractable"|

#### Dominance
We can look at the dominant term to guess at a big-O growth rate. 

e.g. *T(n)* = 2*n*<sup>2</sup> + 600*n* + 60000
  * Up to *n* = 100, the constant term dominates
  * Between *n* = 100 and *n* = 300, the linear term dominates
  * Beyond *n* = 300, the quadratic term dominates, *T(n)* ∈ *O*(*n*<sup>2</sup>)

#### Analyzing Code
*Types of analysis*

  * Bound flavour
    * Upper bound (O)
    * Lower bound (Ω)
    * Asymptotically tight (Θ)

  * Analysis case
    * Worst case (adversary)
    * Average case
    * Best case / "lucky" case
    * "common" case

  * Analysis quality
    * Loose bound (any true analysis)
    * Tight boud (no better "meaningful" bound that is asymptotically different)
