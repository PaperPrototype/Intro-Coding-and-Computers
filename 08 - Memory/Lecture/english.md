So far (without) realizing it all the code we have written and all the variables we have made have been stored in memory in a certian way.

# The Stack
There is a section of memory called the "stack". 

![] stack memory

Whenever we make a variable, we have "stacked" it onto this piece of memory.

(example)
```c
int main(void)
{
	int variable = 12;
}
```

![] my_variable "stacked"

And when we make another variable it also gets "pushed onto" the stack.

(example, 2 variables)
```c
int main(void)
{	
	// push `12` and `32` onto the stack
	int variable = 12;
	int random_number = 34;
}
```

![] 2 variables on the stack

When we are done with our variables they get "popped off" the stack.

(example)
```c
int main(void)
{
	int variable = 12;
	int random_number = 34;
} // pop `12` and `34` off of the stack
```

When our code enters a curly bracket `{` we "push" some variables onto the stack. When we find the ending curly bracket `}` we "pop" those variables off the stack. This is called a variables "scope", and it is important to know when a variable exists and when it doesn't (which is what the curly brackets are for).

When you call a function, its variables will get added to the stack, but once the function is done, the variables get poppped off again.

```c
int add(int a, int b) {
	return a + b;
}

int main(void) {
	int variable = 12;
	int random_number = 34;

	// push `add` and its variables onto the stack
	int result = add(12, 34);
}	// pop `add` off the stack
```

![]

You can even see evidence of the "stack" in assembly as "pop" and "push" instructions!

(assembly instructions)
```x86_64 gcc 11.2
.LC0:
        .string "Hello world"
main:
        push    rbp
        mov     rbp, rsp
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        mov     eax, 0
        pop     rbp
        ret
```

# Stack variables
The size of something on the stack must always be known, at compile time (when we compile the code) and before the program runs.

Remember this code?
```c
char* names[] = {"Charlie", "Bill"};
```
The reason we couldn't do `char**`...
```c
char** names = {"Charlie", "Bill"};
```
...is because the size of an array that will be on the stack, must be known when we compile! And when we do...
```c
char* names[] = {"Charlie", "Bill"};
```
...C automatically changes this to...
```c
char* names[2] = {"Charlie", "Bill"};
```
...which is an array where the exact size is known, at compile time. We also know the size of each array of char's, since we literrally wrote out each name (and C can figure out the size).

This would look something like this on the stack.

TODO ![] names address array on the stack, also each name array

So we had to do `char* names[]` which makes an array `names[]` of addresses `char*`. The square brackets allow C to automatically fill in the size to be 3 `names[3]`.

# Recursion
Imagine the following code.

(example)
```c
int add_until_3(int number)
{
	add_until_3(number + 1);
}
```

Whenever we use this function, our code will say "hey, get me a copy of the `add_until_3` function,put it on the stack, then "execute" (AKA "do") the function". 

When we start "doing" the function, we find "oh, hey, get me another copy of the `add_until_3` function, put it on the stack, then execute it".

![]

Each new copy of this function will get a larger `number` variable, since we increase the number variable `add_until_3(number + 1)` of the next `add_until_3` function.

But this function will endlessly make us stack copies of it! And we would get what is called a "stack overflow" error! Because we literrally used up all the memory on the stack!

A newer (and really cool programming language called "go" will automatically make a new larger stack, copy everything onto the new stack, and continue with that new stack, thus preventing a stck overflow!

We can put a simple `if` at the beginning of the function to stop it from making more copies of itself once its `number` variable reaches a certain point.

(example)
```c
int add_until_3(int number)
{
	if (number >= 3)
	{
		return number;
	}

	add_until_3(number + 1);
}
```

We basically are saying "if, this copy of the function, the number 3 has been increased to be larger than or equal to 3, return and give back whatever the `number` variable is currently". By `return`ing we stop ourselves from putting another copy of the `add_until_3` function on the stack.

We need to "pass" the result from the final `add_until_3` function back through all of the copies of `add_until_3`!

(example)
```c
int add_until_3(int number)
{
	if (number >= 3)
	{
		return number;
	}

	// (1)
	return add_until_3(number + 1);
}
```

(1) We "pass" the resulting value "back through" all the copies of `add_until_3` by `return`ing the number that the next `add_until_3` function will give us back (since the the function returns an `int` as you can see `int add_until_3`).

Make a new repl. Select the C language. Name the repl "recursion".

If we go ahead and use this function, we can see the "stack" in replits debugger window!

Write the following code.

```c
#include <stdio.h>

int add_until_3(int number)
{
	if (number >= 3)
	{
		return number;
	}

	return add_until_3(number + 1);
}

int main(void) {
	// (1)
	int result = add_until_3(0);

	printf("result is: %i", result);

}
```

If you run this function you will see that this code does indeed print out the number 3.

The idea of stacking the same function over and over is called "recursion".

# Memcpy
Whenever we "set" one variable to another variable we are literally copying the variable on the right, into the variable on the left.

(example)
```c
int main(void)
{
	int poop = 12;
	int random_number = 34;

	// copy "poop" into "random_number"
	random_number = variable;
}
```

There is even a function called "memcpy" (which stands for memory copy)!
(example)
```c
// get access to `memcpy`
#include <stdlib.h>

int main(void)
{
	int poop = 12;
	int random_number = 34;

	// copy "poop" into "random_number"
	memcpy(&random_number, &poop, sizeof(int));
}
```

The "=" in C almost always translates to the "memcpy" function!

As you can see we give `memcpy` the address to our variables by using the ampersan symbol `&`. Then `memcpy` also has to know "how many bytes" after the address to copy (since an address just points to the first byte of memory). The `sizeof(int)` function gives us back the size of a type in bytes (the `int` type is 4 bytes).

You can use `memcpy` to copy structs.

(example)
```c
// get access to `memcpy`
#include <stdlib.h>

typedef struct person {
	int age;
	char name[20];
};

int main(void)
{
	person poop = {12, "Bob"};
	person random_person = (34, "Bill");

	// copy "poop" into "random_person"
	memcpy(&random_person, &poop, sizeof(person));
}
```

Everything on the stack is always a copy, but what if we want a piece of memory that isn't a copy? What if we want something that can be accessed by its address `char*`, using stack based "address variables" (called "pointers"), but can remain on its own, separate from the stack.

# The heap
Heap memory lives in the same space as the stack (at least in C), but grows from the opposite side.

![] stack and heap memory

Heap memory has to be kept track of, like where memory is available, and where there is already memory being used for something.

There exists many "allocators" that have different algorithms and methods of "book keeping", which means keeping track of where memory is available and where it isn't.

We are going to use `malloc` which is a standard allocator that all Operatring System's have (Windows, MacOS, iOS, Android, and Linux are operating systems).

You can make your own allocator! But we're not gonna do that (at least not in this course).
 

# Globals

# where are the Global's + Functions? in our progrAM?

STILL WRITING THIS LECTURE...

Stack vs Heap

- Stack is copies of stuff (always)

- "swap.c"
	- function parameters are a **copy** of the variable
	- to get a reference we need to use an address to the data (a pointer) <- will need to know for "sorting algorithms"

- Call stack
	- calling a function inside of itself

Variables that are an address
	- Pointers (already covered in week 2)

Defining custom types and structures (grouping two types together "Person{name, age}")
- heap allocate
- pass copies of an address around
- memcpy is the same a `=`
- memcpy a struct (or anything)

Dynamic memory allocation
