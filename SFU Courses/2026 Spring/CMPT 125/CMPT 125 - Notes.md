#### Jan 7, 2026
- Use CSIL for assignments (where it will be marked)
- Lab Exam will be in CSIL
- Course is in C
- Past exams are all posted on his site
- Grading Sceme
	- FInal - 40%
	- Midterm - 20%
	- In-lab exam - 20%
	- Homeworks - 20% (4% each)
- Prerequisites
	- CMPT 120
		- Variables
		- Data Types
		- Lists/arrays
		- Conditions
		- Loops
		- Functions
		- Develop -> Test -> Debug
#### Jan 9, 2026
- Differences between C and Python
- Compilation Process
	- Python
		- Algorithm -> program.py -> Running the program
		- Runs one instruction at a time
		- Errors only caught when trying to run
	- C/C++
		- Algorithm -> program.c -> machine code a.out -> Running the program
		- Compiled into machine language in advance
		- Some errors caught in complier
		- Faster performance
- Variables
	- In C all variables must be declared before using them
	- Type of variable must be declared
	- ```
	  int main()
	  {
	  int x = 5;
	  long y = 10;
	  
	  printf("The sum of %d abd %ld is %ld", x, y, x+y);
	  
	  return 0;
	  }
	  >> The sum of 5 and 10 is 15
	  ```
	- Type of variable cannot be changed
	- When a variable is declared a space in memory for the var is reserved
		- int - 4 bytes (sometimes 2, compiler dependent)
		- long - 8 bytes
		- double - 8 bytes
		- char - 1 byte
- How to compile then run
	- gcc {file name}
	- then run the output file
- Pointers and References
	- Each variable is stored in a unique location in memory
	- Its address is represented by a number (can be accessed using pointers and references)
	- Thus a variable has 3 main features
		- Type
		- Value
		- Address in memory
	- Address can be stored in a var explicitly
		- ```
		  int x = 5;
		  int* px = &x; // pointer to the location of x
		  printf("The address of %d is %p\n", x , px);
		  ```
	  - Use & to get address
	  - Use * to dereference/change
- Arrays 
	- Represents a list of elements
	- List is of a fixed length, once created cannot be changed
	- All elements have the same type (ints, str, etc)
	- The variable of type array of ints is really a pinter to int
		- it points to the zero'th element of the array
		- the elements are stored in the memory in a contiguous block
#### Jan 14, 2026
- Array
	- The variable of type array of ints is really a pointer to the zeroth element
	- The elements are stored in the memory in a continuous block (one after other)
	- Size of int = 4 bytes
		- This means that arr + i really increases by i*(sizeof(int))
#### Feb 4, 2026
- 