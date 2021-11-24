So far (without) realizing it all the code we have written and all the variables we have made have been stored in memory in a certian way.

# The Stack
There is a section of memory called the "stack". 

![memory stack](/Assets/memory_stack.png)

Whenever we make a variable, we stack it onto this piece of memory.

(example)
```c
int main(void)
{
	int variable = 12;
}
```

![memory stack 1](/Assets/memory_stack_1.png)

And when we make another variable it also gets "pushed" (stacked) onto the stack.

(example, 2 variables)
```c
int main(void)
{	
	// push `12` and `32` onto the stack
	int variable = 12;
	int random_number = 34;
}
```

![memory stack 2](/Assets/memory_stack_2.png)

Although what is really being held in memory are the *values* (numbers) in the 2 variables...

![memory stack values](/Assets/memory_stack_values.png)

And we are just using the word `variable` and `random_number` to refer to those values/0s and 1s.

The stack "grows upwards". The stack is not infinite! You can get a "stack overflow" error if you use up to much memory!... Although it would take a lot of memory to actually achieve a stack overflow error.

When we are done with our variables they get removed or "popped off" the stack.

(example)
```c
int main(void)
{
	int variable = 12;
	int random_number = 34;
} // pop `12` and `34` off of the stack
```

![memory stack cricket noises](/Assets/memory_stack_cricket_noises.png) 

When our code enters a curly bracket `{` we "push" variables onto the stack. 

(example)
```
int main(void) 
{ 	// push variables onto the stack
	int variable = 12;
}
```

When we find the ending curly bracket `}` we "pop" those variables off the stack. 

(example)
```
int main(void) 
{
	int variable = 12;
} 	// pop variables off the stack
```

This is called a variables "scope". "scope" tells us when a variable exists (on the stack)and when it doesn't (which is what the curly brackets are for!).

You can even see evidence of the "stack" in assembly as "pop" and "push" instructions!

(assembly instructions)
```x86_64 gcc 11.2
.LC0:
        .string "Hello world"
main:
        push    rbp    <- here
        mov     rbp, rsp
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        mov     eax, 0
        pop     rbp    <- here 
        ret
```

When you call/use a function, it's variables and instructions get pushed to the stack, and once the function is done, it's instructions and variables get taken off of the stack!

```c
int add(int a, int b) {
	return a + b;
}

int main(void) 
{
	// push `add` onto the stack
	add(12, 34);
	// pop `add` off the stack
}
```

# Stack variables + Array confusion
The size of a variable on the stack must always be known, at compile time (when we compile the code into a program file of 0s and 1s) and before the program ever runs.

When making an array you may get confused as to the difference between using the curly brackets `[]` and using an address `char*`

(example)
```c
char name[] = "Billy";
char* name = "Billy";
```

The size of an array that will be on the stack, must be known when we compile! And when we do...

```c
char name[] = "Billy";
// or
char* name = "Billy";
```

...C automatically changes this to...

```c
char name[5] = "Billy";
```

...which is an array of char's where the exact size is known, at compile time!

You'll notice there are only 4 letters in "Billy" but remember that C automatically adds the null terminating character `\0` for us!

This would look something like this on the stack.

TODO ![] name array on the stack

# Recursion
Imagine the following code.

(example)
```c
int add_until_3(int number)
{
	add_until_3(number + 1);
}
```

Whenever we use this function, our code will say "hey, get me a copy of the `add_until_3` function, put it on the stack, then "execute" (AKA "do") the function.

When we start "doing" the function, we find "oh, hey, get me another copy of the `add_until_3` function, put it on the stack, then execute it".

![memory stack recursion](/Assets/memory_stack_recursion.png)

Each new copy of this function will get a larger `number` variable, since we increase the number `(number + 1)` that we give the next `add_until_3` function.

This will endlessly stack copies of the `add_until_3` function! Over and over! And we would get a "stack overflow" error! Because we literrally used up all the memory on the stack!

A side note: A newer (and really cool) programming language called "go" will automatically make a new (larger) stack, copy everything onto the new stack, (remove the old stack) and continue with that new stack! Thus preventing a stack overflow!

To prevent a stack overflow, we can put a simple `if` condition, before making a new `add_until_3` function, to stop us from making more copies of `add_until_3`.

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

We basically are saying "if, this copy of the function, the `number` variable is larger than or equal to 3, return (exit) and give back whatever the `number` variable is currently".

Remember that anything after a `return` will not run, so we we stop ourselves from calling/pushing a new `add_until_3` function onto the stack.

There is one problem still. We need to get access to whatever the next `add_until_3` function will give back!

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

(1) We "pass" the resulting value "back through" all the copies of `add_until_3` as they get removed from the stack we pass the number it gives back, by `return`ing the number.

TODO LEFT OFF HERE:...

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

Everything on the stack is always a copy, but what if we want a piece of memory that isn't a copy? What if we want something that can be accessed by its address `char*`, using stack based pointers, but that can remain on their own, separate from the stack? That takes us to a new area of memeory we haven't even touched yet...

# The heap
Heap memory lives in the same space as the stack (at least in C), but grows from the opposite side.

![] stack and heap memory

Heap memory has to be kept track of, like where memory is available, and where there is already memory being used for something.

There exists many "allocators" that have different algorithms and methods of "book keeping", which means keeping track of where memory is available and where it isn't.

We are going to use `malloc` which is a standard allocator that all Operating System's have (Windows, MacOS, iOS, Android, and Linux are operating systems).

You can even make your own allocator! But we are NOT gonna do that.

TODO

# Globals

# where are the Global's + Functions? in our program?

STILL WRITING THIS LECTURE...

Stack vs Heap

- Stack is copies of stuff (always)

- "swap.c"
	- function parameters are a **copy** of the variable
	- to get a reference we need to use an address to the data (a pointer) <- will need to know for "sorting algorithms"

- Call stack
	- calling a function inside of itself

Variables that are an address
	- Pointers (already covered in week 5)

- structures + addresses
- heap allocate, dynamic memory allocation

- pass copies of an address around

- memcpy is the same a `=`
- memcpy a struct (or anything)

