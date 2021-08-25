In C we don't have the idea of "lists" instead we have "arrays".

Make a new repl. Select the C programming language. Call the project "arrays".

In the shell make a new file called `array.c` using the `touch`.

(command)
```
touch array.c
```

Remove the "main.c" file using `rm main.c` since we won't be using it.

Open `array.c` using Replits files window and write the following code.

```c
int main(void) {
  int integers[] = { 2, 3, 6, 1 };
}
```

We put square brackets `[]` next to the variables name to show that is is an "array" variable.

We then "fill" the array by putting curly brackets `{}` around all the items, and we separate each item using a comma `,`.

Our integers variable is an address to the first item in the array. You should think of addresses as being a ***number to a specific byte***. A "byte" is 8 bits (a `0` or `1`).

![memory continous linear](/Assets/memory_continuous_linear.png)

Although we often represent memory as a grid since that is more space efficient.

![memory grid](/Assets/memory_grid.png)

Even though we think of memory as a "grid", addresses are still a number to a specific byte.

![memory wrap around](/Assets/memory_wrap_around.png)

The `integers` variable in the above code is an *address* to the first item in our array.

![array ints](/Assets/array_ints.png)

To access an item in an array we "go to" the first item in the array + an offset.

Change your code to the below to print out the second item in the list by using an offset of 1 (Make sure to add a `\n` and `#include stdio.h>`)

```c
#include <stdio.h>

int main(void) {
  int integers[] = { 2, 3, 6, 1 };

  printf("%i\n", integers[1]);
}
```

The "offset" is what goes into the square brackets `[]`.

When we offset using the square brackets `[]` the number of bytes (blocks) we offset depend on the *size of the type*. Currently we are using an `int` type which is 4 bytes (4 blocks) so the above code offsets by `1 * 4` bytes to get the second item in the array.

![array ints offsetting](/Assets/array_ints_offsetting.png)

Compile "array.c" using make.

(command)
```
make array
```

Then run it using.

(command)
```
./array
```

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

The size of a type is measured using a unsigned (non negative, no "sign") `long` type, so when printing the size of a type we use an unsigned long specifier `%lu`.

Compile the code with `make array`, then run it using `./array`

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
It turns out that *strings* (words and phrases enclosed in double quotes `""`) are an array. More specifically an array of `char`'s. 

Make a new file.

```
touch string.c
```

Write the following code into "string.c".

```c
#include <stdio.h>

int main(void) {
	char hello[] = { 'H', 'e', 'l', 'l', 'o' };

	printf("%s \n", hello);
}
```

The `char` type is litterally an ASCII type.

In the array we enclose each individual letter with a single quote `'`. C requires that we use a single quote `'` and not a double quote `"` to represent a single char.

Run make to compile the "string.c" code

(command)
```
make string
```

Then run it using 

(command)
```
./string
```

you will see "Hello" get printed.

We use the string conversion specifier `%s` since a string in C is actually an array of chars. Makings strings is so common that nobody writes strings as an array! Instead we have special syntax for strings, which lets us use double quotes `"Help"` rather than the clunky array syntax `{ 'H', 'e', 'l', 'p' }`.

Change your code to use the double quotes `""` syntax.

```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	printf("%s \n", hello);
}
```

Now compile and run the above code using the shell (see above commands).

You may ask yourself "how does printf know when to stop offsetting in a char array (aka string)"? Every "string" in C by default ends with a special *null terminating character*, namely `\0`.

Even though we didn't add a `\0` to the end of our string, C added it for us (or C checked the the value was not a "null" value, we'll see what null is in a second).

# Addresses
We can make a variable that holds an address number to some piece of memory.

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	// array, address
	char* hello = "Hello";

	printf("%s \n", hello);
}
```

We change the "hello" variable to be a pointer (aka, address) of the type "char" by putting a star symbol afterwards, namely `char*`. The star symbol `*` just signifies it is a "pointer" (aka address number) variable. An address variable is just a number telling us which "byte" is the beginning of the array (or what byte is the beginning of our data, sometime just a single item, and not an array).

We don't have to use the square brackets to access stuff in an array. A "pointer" (address variable) just points to the first item in an array (or a singel item), so we can access the first item and ignore the rest in our array, by "going to" the address.

To "go to" the address of our variable and access the first item we have to tell C to "go to" that address. We do this by putting a star symbol `*` in front of the variable.

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
    // array (using pointer (address variable))
	int* hello = "Hello";

	printf("%c \n", *hello);
}
```

This is called "de-referencing" a pointer (address variable).

The above code aslo changes to use the conversion specifier for `char` type in `printf`, rather than the string conversion specifer `%s`.

This code will print out the letter "H". Compile the above code with make, then run it in the shell.

Using the square brackets `[]` is a useful shortcut for offsetting from the address.

We have to know the type in an array if we want to properly use offsetting shortcut. Hence `char*` is an address, which offsets by 1 byte when we use the square brackets iterator `[]`. (If we had an array of `int` we would offset by 4 byts to get the next item).

C won't stop us from offsetting outside of the array though! If you do happen to offset outside of the array and access that memory you will get a `null` value.

"null" means we are accessing memory that has not been set to anything. You can still read that memory in C, but we can't know what the 0s and 1s will be. Often this is called a "garbage value" when accessing unkown 0s and 1s.

# Void
Since a pointer (aka address) simply points to the first byte of an array (or type) we don't have to tell the type!

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

Void is an unkown type (but it also stands for "no input" in functions). By using `void` for the pointer type we can point to any type of array!

When we use the void pointer `void*` to an array, we do have to know the type to be able to print it, otherwise we wouldn't know how much to offset in memory to get the next element in the array! So we cast the type (aka convert the type) with this line of code `(char*)`, inside of `printf`.

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

The `char * argv[]` is weird. It is an array of addresses `char *` to an array of strings `argv[]`... Another way of writing this would be to use two stars `char ** argv`.

Change your code to use this method.

```c
#include <stdio.h>

int main(int argc, const char ** argv)
{
	// do something with the input
}
```

If we visualize an array of addresses to an array of strings, in memory it would look something like this.

![argv in c](/Assets/argv.png)

Not to complicated (it probably sounded complicated). The word `argv` stands for "argument vector" (honestly this name is jsut traditional).

Lets use `argv`! Lets make simple a program that gets our name, then prints it out along with a "hello" message.

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

It is generally not a good idea to read memory that has not been set, as it proably has random 0s and 1s from something else. 

In C we have to manually check how long our array is so that we don't accidentally offset outside of the array. 

One of the parameters (inputs) from main is called `argc` which stands for "argument count", `argc` is an int. You can use `argc` to prevent yourself from offsetting outside of the arrays bounds. Yiu can also use `argc` see how many arguments were given.

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

Just so you know, `argc` doesn't start counting at 0. If we put 2 arguments (including the command to run the program) then `argc` will be 2 (so if your using `argc` to stop yourself from offsetting outside of an array you will need to subtract 1 from `argc`, since offsets start counting from 0 and not 1).

In the above code we print an error message and "return" an error code of 1 if no argument was given. 

Any code after a `return` keyword won't get run (to an extend). This prevents us from running the greeting message "Hello, mikey", since the word "mikey" wouldn't exist (or any other word you put)!

If we do put 2 arguments, then print the greeting message, and return an error code of 0 (0 meaning nothing went wrong).

Run the above code (or your variation), and see if it prints an error message when you don't put "mikey" (or some other word) after "./input".


# Loops + Arrays
Now we can use a `for` loop on an array. This is pretty cool.

TODO (not in order presented)
make sure to introduce gradually and explain the for loop
- avarage a bunch of numbers

- const keyword, protects to make sure no one is allowed to change the number (very useful to prevent people from making mistakes)
    - prevents you from going through all your code and changing all the numbers you typed, just store the number in a variable and use the const variable!

- then move everything into an "average" function


TODO
- `break` keyword
- `return` keyword
- `continue` keyword


(example)
```c
TODO
```

TODO (for pointer offsetting manually without the square brackets `[]`)
- show example code?
- find place to put this in lecture


TODO
- average all the numbers together in an array? using a for loop?

# Do while and Scope and Return?
- getting input until it is correct (from Getting input section)

Any code after return will not get ran. SO if we did .... EXPLAIN

TODO
- all variables are technically an address. To view the address that a variable holds you can use the `&` to get access to the address