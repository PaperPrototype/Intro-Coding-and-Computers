# Arrays
C doesn't have "lists". In C we have "arrays". 

An *array* is blocks of memory one after the other. 

![memory array](/Assets/memory_array.png)

Memory is really just a long line of swithes. Each switch is refered to as a bit.To make accessing memory faster we store bits in blocks of 8. Each block is called a byte. 

We can think of memory as a grid of bytes.

![memory grid](/Assets/memory_grid.png)

Each block having 8 bits (1 byte) of data in it.

Make a new repl. Call it "arrays". Select the C programming language. Make a new file called `array.c` using the `touch` command in the shell.

```
touch array.c
```

(use `rm` to delete the file if you named it incorrectly).

Open `array.c` using the files window and paste the following.

```c
int main(void) {
  int integers[] = { 2, 3, 6, 1 };
}
```

We put square brackets `[]` next to the variables name to show that is is an array variable.

When we set the array variables items we use curly brackets `{}` around each item.

In C, an array variable is an *address*. Addresses are a number telling us what block of memory something is in. 

![memory continous linear](/Assets/memory_continuous_linear.png)

The `integers` variable in the aboove code is an *address* to the first item in the array.

![memory array address](/Assets/memory_array_address.png)

To access an item in the array we "go to" the first element in the array + an offset.

Change your code to the below to print out the second item in the list (Make sure to add a `\n`)

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("%i\n", integers[1]);
}
```

This code accesses the second item in the array by using an offset of 1. The "offset" is what goes into the square brackets `[]` when we use the variable.

But how much do we offset exactly? The offset uses the *size of the type*. Currently we are using an `int` type which is 4 bytes (4 "blocks") so we offset by `1 * 4`. You can test the size of a type by using the builtin `sizeof` function.

Change the code to print out the size of the `int` type. (Make sure to add a `\n`)

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  // printing size of an int
  printf("sizeof int: %lu\n", sizeof(int));

  printf("%i\n", integers[1]);
}
```

The size of a type is measured using a non negative `long` type, so when printing the size of a type we use an unsigned long specifier `%lu`. 

To access the first element we don't need an offset so its just `[0]`

(example)
```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("sizeof int: %lu\n", sizeof(int));

  printf("%i", integers[0]);
}
```

# Strings
It turns out that *strings* are an array of the type `char`. Edit the above code so that we have a `char` array that spells the word "Hello".

```c

```

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

# Getting Input 
The main function gets input from the shell.


# Loops + Arrays
Now we can use a `for` loop on an array. This is pretty cool.

TODO (maybe in below section)
- `break` keyword
- `return` keyword
- `continue` keyword

# Do while and Scope and Return
- getting input until it is correct (from Getting inout section)

Any code after return will not get ran. SO if we did .... EXPLAIN