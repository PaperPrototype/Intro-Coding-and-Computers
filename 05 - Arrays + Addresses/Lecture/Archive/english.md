# Addresses
We can make a variable that holds an "address number" to a single piece of memory. We call variables that hold a memory address "pointers".

(change your string.c code to the following)
```c
#include <stdio.h>

int main(void) 
{
	// array, address
	char* hello = "Hello";

	printf("%s \n", hello);
}
```

We change the "hello" variable to be a *pointer* (aka address) by putting a star symbol after the type `char*`. The star symbol `*` just signifies it is a "pointer" (aka *address* variable).

Using the star symbol `*` has been no different than when we made an array variable, since they are both technically addresses!

(example)
```c
#include <stdio.h>

int main(void) 
{	
	// address
	char* hello = "Hello";
	
	// also address!
	char hello[] = "Hello";

	// ...
}
```

We will use the `hello` "pointer" to access the first character in the word "Hello" (Yes we did this previously using ssquare brackets `[0]`) by "going to" the address in the `hello` pointer (since an address points to the first byte).

To "go to" the address of our `hello` pointer (and access the first item) we tell C to "go to" that address by putting a star symbol `*` in front of the `hello` variable, like this `*hello`.

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// access what is at the address
	printf("%c \n", *hello);
}
```

This is called "de-referencing" a pointer ("accessing" what is at a pointers address ("pointer" is just another name for a variable that holds an address number)).

The above code also changes to use the conversion specifier for the `char` type `%c` (in `printf`), rather than the string conversion specifer `%s`. This is because we are only printing the first single item in the array.

This code will print out the letter "H" (obviously). Compile the above code with make, then run it (using the shell).

Using the square brackets `[]` is a useful shortcut for offsetting from a pointer/address variable. 

When we make an array we have to know the type of the array for C to be able to offset correctly. Hence `char*` is an address, which offsets by 1 byte (since a `char` uses only 8 bits = 1 byte). 

If we had an array of `int` we would offset by 4 bytes to get the next item.

![array ints offsetting](/Assets/array_ints_offsetting.png)

C won't stop us from offsetting outside of the array though! If you do happen to offset outside of an array and access memory that is not part of the array then you will probably get a `null` value.

"null" means we are accessing memory that has not been set to anything. You can still read that memory in C, but we can't know what the 0s and 1s will be. Often this is called a "garbage value" when accessing unkown 0s and 1s.

Try offsetting outside of the "Hello" array. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// access what is at the address
	printf("%c \n", hello[6]);
}
```
Compile this code with make. Then run it using the shell.

This will print out `\0`, which as your remember, is something C adds to our string for us so that it can know when to stop offsetting in memory. Although we want to break things and get a null value!

(edit your code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// access what is at the address
	printf("%c \n", hello[100]);
}
```

Compile this code with `make string` then run it using `./string`. You will see "null" get printed! It is possible you may get a different type of error.
