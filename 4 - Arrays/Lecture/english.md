
PASTED FROM WEEK 1

# Arrays
C doesn't have "lists". In C we have "arrays". 

An *array* is blocks of memory one after the other, each of the same size.

TODO 
- move pictures into one large folder
![memory array](/Assets/Week_1/memory_array.png)

Memory is really just a long line of swithes. But to make accessing memeory faster it is stored in blocks of 8 bits (called a byte).

We can visualize memory as a grid of blocks.

![memory grid](/Assets/Week_1/memory_grid.png)

Each block has 8 bits (1 byte) of data in it.

Make a new file called `array.c` using `touch` (use `rm` to delete the file if you named it incorrectly).

Open `array.c` and paste the following.

```c
int main(void) {
  int integers[] = { 2, 3, 6, 1 };
}
```

We use curly brackets `{}` for making an array (that's just how C's syntax works).

We put square brackets `[]` next to the variables name to show that is is an array variable.

In C, array variables "point" to the first item in the array.

![memory array address](/Assets/Week_1/memory_array_address.png)

The `integers` variable is an *address* to the first piece of memory in the array. Addresses are a number telling us what block of memory something is in.

![memory continous linear](/Assets/Week_1/memory_continous_linear.png)

We put memory in a grid so that it fits in our computer. This doesn't affect the memory address.

![memory grid linear](/Assets/Week_1/memory_grid_linear.png)

Memory addresses are called "pointers" in C.

When we access an item in the array we are "going to" the first element in the array + an offset.

TODO ![memory array offset](/Assets/Week_1/TODO)

Change the code to access the second item (by using an offest of 1), then print the second item.

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("%i\n", integers[1]);
}
```

(Make sure to add a `\n`)

The "offset" is what goes into the square brackets `[]`.

How much does C offset? It uses the *size of the type*. Currently we are using an `int` type which is 4 bytes. You can test the size of a type by using the builtin `sizeof()` function.

Change the code to print out the size of an `int` type.

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("sizeof int: %lu\n", sizeof(int));

  printf("%i\n", integers[1]);
}
```

(Make sure to add a `\n`)

So an offest of 1 moves us by 4 bytes.

TODO ![memory offset by 1]()

Computers store everything in blocks of memory, each block holding 1 byte (8 bits). As a result the smallest size possible for a type is 8 bits. As a result the `bool` (true or false type) is stored as 1 byte (8 bits), even though it only stores 2 possible values.

If we want to access the first element we don't need an offset so its just `[0]`

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("sizeof int: %lu\n", sizeof(int));

  printf("%i", integers[0]);
}
```

# Strings
It turns out that strings are an array of the type `char`.

# Pointers (aka address variables)
Addresses 
We call variables that hold an address "pointers".

# Void
void is an unkown type https://www.c-programming-simple-steps.com/what-is-void.html

We can use void with a pointer to hold onto an unknown type. This is because addresses are per byte.

![] picture of address to a byte

A pointer using void will give you the address of the first byte of a type. If we hold onto an `int` using a void pointer we will reference the first byte of the 4 bytes in an `int`.

![] picture of pointer to first byte (but int takes up more space)

An int is 4 bytes, but the void pointer doesn't *how much* after the address is part of the type. So when we use the void pointer to access the data we have to "cast" it to the type it represents (so that we know how much after the address is part of the `int`)

```c
void* pointer;

int number = 10;

// we know the type of number
pointer = &number; // get the memeory address of the number variable

// cast pointer to an int pointer
int finalNumber = (int *)pointer;
```

TODO MAYBE? We can give back a void from a function.

# Loops + Arrays
Now we can use a `for` loop on an array. This is pretty cool.

TODO
- `break` keyword
- `return` keyword
- `continue` keyword

# Getting Input 
- main gets input from shell


# Do while and Scope and Return
- getting input until it is correct (from Getting inout section)

Any code after return will not get ran. SO if we did .... EXPLAIN