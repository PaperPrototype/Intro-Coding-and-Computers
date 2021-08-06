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

To access an item in an array we "go to" the first element in the array + an offset.

Change your code to the below to print out the second item in the list (Make sure to add a `\n`)

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("%i\n", integers[1]);
}
```

This code accesses the second item in the array by using an offset of 1. The "offset" is what goes into the square brackets `[]` when we use the variable to access its items.

When we offset using the curly brackets `[]` the offset uses the *size of the type* to know how many bytes to offset in memory. Currently we are using an `int` type which is 4 bytes (4 "blocks") so we offset by `1 * 4` to get to the second item in the array. You can test the size of a type by using the builtin `sizeof` function.

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

The size of a type is measured using a unsigned (non negative) `long` type, so when printing the size of a type we use an unsigned long specifier `%lu`. 

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
#include <stdio.h>

int main(void) {
	char hello[] = { 'H', 'e', 'l', 'l', 'o' };

	printf("%s \n", hello);
}
```

Now run the make command to compile the "array.c" code

```
make array
```

Then run it using 

```
./array
```

you will see "Hello" get printed.

We use the string conversion specifier `%s`. Makings strings is so common that nobody writes strings this way. Instead we have special syntax for strings. 

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	printf("%s \n", hello);
}
```

Now compile and run it using the shell (see above commands).

TODO `\0` symbol

# Pointers (aka address variables)
In C, we call variables that hold an address "pointers". It turns out that using the square brackets `[]` after a variables name is also a shortcut.

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
    // pointer
	char* hello = "Hello";

	printf("%s \n", hello);
}
```

We change variable to be a pointer of the type char which gives us `char*`. The star symbol `*` means it is a pointer!

# Void
Since a pointer (aka address) simply points to the first byte of an array we don't have to tell the type!

Change the code to the following.

```c
#include <stdio.h>

int main(void) 
{
    // address to first byte
	void* hello = "Hello";

    //             convert to a char pointer "char*"
	printf("%s \n", (char*) hello);
}
```

Now compile and run the code using the shell.

Void is an unkown type (but it also stands for "no input" in functions). By using `void` for the pointer type we can point to any array in memory! 

When we use the void pointer `void*`, we have to know the type though. Otherwise we wouldn't know how much to offset in memory to get the next element in an array! So we cast the type (aka convert the type) with this line of code `(char*)`.

If we hold onto an `int` using a void pointer we will reference the first byte of the 4 bytes in an `int`.

# Getting Input 
The main function gets input from the shell. Except so far we haven't used this functionality. 

Make a new file using the touch command called "input.c"

```
touch input.c
```

Write the following into "input.c".

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	
}
```

Wow! What is `const char * argv[]`? Well the first part `const` just means we can't change the variables values (stuff inside the variable).

The `char * argv[]` is weird. It is an array of addresses `char *` to an array of strings `argv[]`. Another way of writing this line of code would be.

```c
#include <stdio.h>

int main(int argc, const char ** argv)
{
	
}
```

If we visualize an array of addresses to an array of strings in memory it would look like this.

![]



# Loops + Arrays
Now we can use a `for` loop on an array. This is pretty cool.

TODO
- `break` keyword
- `return` keyword
- `continue` keyword

# Do while and Scope and Return
- getting input until it is correct (from Getting inout section)

Any code after return will not get ran. SO if we did .... EXPLAIN