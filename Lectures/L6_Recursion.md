### The Fibonacci Series

  *  The nth number in the Fibonacci series, fib(n), is: 
  	* 0 if n=0, 1 if n=1
  	* fib(n-1) + fib(n-2) for any n>1
  * e.g. what is fib(23)
  	* Easy if we know fib(22) and fib(21)
  	* Hard if we do not know what fib(22) and fib(21) is

  * The Fibonacci function is recursive
  	* A recursive function calls itself
  	* Each call to a recursive method results in a separate call to the method, with its own input

  * Recursive functions are just like other functions
  	* The invocation (e.g. parameters, etc.) is pushed onto the call stack
  	* It is removed from the call stack when the end of a method or a reutnr statement is reached
  	* Execution returns to the previous method call

	* Recursive functions do not use loops to repeat instructions
		* But use recursive calls in if statments

	* Recursive functions consist of two or more cases, there must be at least one of each:
	 * //!!!

### Recursion cases
	* The base case is a smaller problem with a known solution


what is the invariant of the for-loop?
anything before the i is sorted

thoroughly test your code!