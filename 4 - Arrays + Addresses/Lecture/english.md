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

TODO
- currently the picture below is incorrect since an `int` uses 4 bytes, not 2.

![memory array address](/Assets/memory_array_address.png)

To access an item in an array we "go to" the first element in the array + an offset. 

Change your code to the below to print out the second item in the list by using an offset of 1 (Make sure to add a `\n`)

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("%i\n", integers[1]);
}
```

The "offset" is what goes into the square brackets `[]`.

When we offset using the square brackets `[]` the number of bytes (blocks) we offset depend on the *size of the type*. Currently we are using an `int` type which is 4 bytes (4 blocks) so we offset by `1 * 4` to get to the second item in the array. 

TODO
- show picture of offsetting

You can test the size of a type by using the builtin `sizeof` function.

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

What is `const char * argv[]`? Well the first part `const` is a keyword, it is telling us that we are not allowed to change the variables values (stuff inside the variable) and they are "constant".

The `char * argv[]` is weird. It is an array of addresses `char *` to an array of strings `argv[]`... Another way of writing this would be.

(example, don't change your code)
```c
#include <stdio.h>

int main(int argc, const char ** argv)
{
	// do something with the input
}
```

If we visualize an array of addresses to an array of strings, in memory it would look something like this.

![argv in c](/Assets/argv.png)

Not to complicated (it probably sounded complicated). The word `argv` stands for "argument vector".

Lets use `argv`! Lets make a program that gets our name, then prints it out along with a "hello" message.

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	printf("Hello, %s! \n", argv[0]);
}
```

The above code gets the first string from the array of strings (in `argv`). Compile this code using `make` and run it using `./input` along with an argument, like the following command.

```
./input Mikey
```

It runs the input program with an argument (the word "Mikey"). You should see the following get printed.

```
~/arrays$ ./input Mikey
Hello, ./input!
~/arrays$ 
```

What? So getting the first argument from `argv` (by using an offset of 0) gave us "./input", which was the command for running the input program! Instead lets access the second string in `argv` by using an offset of 1.

(answer)
```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	printf("Hello, %s! \n", argv[1]);
}
```

Run `make input` then run the input program using...

```
./input Mikey
```

Yay! You should see the phrase "Hello, Mikey!" get printed!

If you happen to run the "input" program without giving it an argument (like the word Mikey) you will see the word "null" get printed instead! This is because we are offsetting in our array to a spot in memory that has not been set to anything (because we didn't type in "mikey" after "./input"). 

In C "null" usually means we are accessing memory that has not been set to anything.

It is generally not a good idea to read memory outside the "bounds" (boundaries) of an array! So, in C we have to manually check how long our array is. One of the parameters (inputs) from main is called `argc` which stands for "argument count", and funny enough `argc` is an int! You can use `argc` to see how many arguments were given!

Change our program to detect if it was run with an argument by using `argc`'s number.

(possible answer)
```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	if (argc < 2) {
		printf("Error, expected input! `./input <argument>` \n");
		return 1;
	}

	printf("Hello, %s! \n", argv[1]);

	return 0;
}
```

Just so you know, argc doesn't start counting at 0. If we put 2 arguments (including the command to run the program) then argc will be 2.

In the above code we print an error message and "return" an error code of 1 if no argument was given. 

Any code after a `return` keyword won't get run (to an extend). This prevents us from running the greeting message "Hello, mikey", since the word "mikey" wouldn't exist (or any other word you put)!

If we do put 2 arguments, then print the greeting message, and return an error code of 0 (0 meaning nothing went wrong).

Run the above code (or your variation that you made), and see if it prints an error message when you don't put "mikey" (or some other word) after "./input".

# Loops + Arrays
Now we can use a `for` loop on an array. This is pretty cool.

TODO
- `break` keyword
- `return` keyword
- `continue` keyword

# Do while and Scope and Return
- getting input until it is correct (from Getting input section)

Any code after return will not get ran. SO if we did .... EXPLAIN

TODO
- all variables are technically an address. To view the address that a variable holds you can use the `&` to get access to the address