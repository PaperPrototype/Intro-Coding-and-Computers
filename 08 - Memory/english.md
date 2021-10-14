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


# Stack variables
The size of something on the stack must always be known, at compile time (when we compile the code) and before the program ever runs.

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

So we had to do `char* names[]` which makes an array `names[]` (with the square brackets so C could tell the size `names[3]`) of addresses `char*`, each address to a name.
