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

We use the string conversion specifier `%s` since a string in C is actually an array of chars. Making strings is so common that nobody writes strings using array syntax! Instead we have special syntax for strings, which lets us use double quotes `"Help"` rather than the clunky array syntax `{ 'H', 'e', 'l', 'p' }`.

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
We can make a variable that holds an "address number" to a block of memory. We call variables that hodl a memeory address "pointers" or address variables.

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

We change the "hello" variable to be a *pointer* by putting a star after the type, namely `char*`. The star symbol `*` just signifies it is a "pointer" (aka *address* variable). An address variable is just a number telling us which "byte" some piece of data starts out at. Sometimes this is the beginning of an array, and sometimes it is just a single item.

We will use the `hello` pointer to access the first item in the word "Hello" (and ignore the rest) by "going to" the address in the `hello` pointer (since an address points to the beginning of some peice of data).

To "go to" the address of our `hello` pointer (and access the first item) we tell C to "go to" that address by putting a star symbol `*` in front of the `hello` variable, like this `*hello`.

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int* hello = "Hello";

	// access what is at the address
	printf("%c \n", *hello);
}
```

This is called "de-referencing" a pointer ("accessing" what is at a pointers address (since "pointer" is just another name for a variable the holds an address and not the data itself)).

The above code also changes to use the conversion specifier for `char` type `%c` (in `printf`), rather than the string conversion specifer `%s`.

This code will print out the letter "H" (obviously). Compile the above code with make, then run it (using the shell).

Using the square brackets `[]` is a useful shortcut for offsetting from an address or pointer. 

When we make an array we have to know the type of the array for C to be able to offset correctly. Hence `char*` is an address, which offsets by 1 byte when we use the square brackets iterator `[]`. If we had an array of `int` we would offset by 4 bytes to get the next item.

![array ints offsetting](./Assets/array_ints_offsetting.png)

C won't stop us from offsetting outside of the array though! If you do happen to offset outside of an array and access memory that is not part of the array then you will probably get a `null` value.

"null" means we are accessing memory that has not been set to anything. You can still read that memory in C, but we can't know what the 0s and 1s will be. Often this is called a "garbage value" when accessing unkown 0s and 1s.

Try offsetting outside of the "Hello" array. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int* hello = "Hello";

	// access what is at the address
	printf("%c \n", hello[6]);
}
```
Compile this code with make. Then run it using the shell.

This will print out `\0`, which as your remember, is something C adds to our string for us so that it can know when to stop offsetting in memory. Although we want to break things and get a null value!

Change your code ot the following.

```c
#include <stdio.h>

int main(void) 
{
	int* hello = "Hello";

	// access what is at the address
	printf("%c \n", hello[100]);
}
```

This will definitally either lead to an error when we try to compile (since the compiler is trying to correct us), or, if you manage to get this code to run, you will see "null" get printed (or another type of error called a "segmentation fault", often shortened to "seg fault").

# Loops + Arrays
We can also use a `for` loop on an array. This is pretty cool. Lets iterate over the word hello and print out each character.

Make a new file called 

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

TODO
- average all the numbers together in an array? using a for loop?

# Void
Since a pointer (aka address) simply points to the first byte of an array (or just the first byte to an `int`) we don't have to tell the type!

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

This code makes a pointer with an unknown type! Void is used as an unkown type, but it also stands for "no input" in a function. By using `void` for the pointer type we can point to any type of array!

To use the information in an array of unknown type (aka `void*`) we have to tell C how to treat the information, otherwise we wouldn't know how much to offset in memory to get the next item! As well as not knowing how many bytes after the address are part of the data (if say we had a singel `int` which takes up 4 bytes). So we cast the type (aka convert the type) in this line of code `(char*) hello` (inside of `printf`).

Now compile and run the above code using the shell.

# Getting Input from Main
The main function actually has parameters with input from the shell! So far we haven't used this functionality. 

Make a new file using the touch command called "input.c"

```
touch input.c
```

Write the following code into "input.c".

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	
}
```

What is `const char * argv[]`? Well the first part `const` is a keyword, it is telling us that we are not allowed to change the variables values (stuff inside the variable) and that they are "constant" (you can add this to your own functions to).

The `char * argv[]` is weird. It is an array of addresses `char *` to an array of strings `argv[]`... Another way of writing this would be to use two stars `char ** argv` without the square brackets (since the square brackets are the same as writing a star).

Change your code to use this syntax.

```c
#include <stdio.h>

int main(int argc, const char ** argv)
{
	// do something with the input
}
```

If we visualize an array of addresses to an array of strings, in memory it would look something like this.

![argv in c](/Assets/argv.png)

Not to complicated (it probably sounded complicated). The word `argv` stands for "argument vector" (honestly this name is just a tradition).

Lets use `argv` for a simple a program that gets our name, then prints it out along with a "hello" message.

Change your code to the following.

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	printf("Hello, %s! \n", argv[0]);
}
```

The above code gets the first string from the array of strings (in `argv`). 

Compile this code using `make` and run it using `./input` along with an argument, like the following command.

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

(change your code to the following)
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

If you happen to run the "input" program without any "arguments" afterward (like we did with "Mikey") you will see the word "null" get printed instead! This is because we are trying to access memory from our `argv` array that has not been set to anything (because we didn't type in "Mikey" after "./input"). 

Go ahead and try running input without any arguments.

(command)
```
./input
```

In C "null" usually means we are accessing memory that has not been set to anything.

It is generally not a good idea to read memory that has not been set, as it probably has random 0s and 1s from something else. 

In C we have to manually check how long our array is so that we don't accidentally offset outside of the array. 

Thankfully of the parameters (inputs) from main is called `argc` which stands for "argument count", `argc` is an int. You can use `argc` to prevent yourself from offsetting outside of the arrays bounds. You can also use `argc` see how many arguments were given.

Change our program to detect if it was run with an argument by using `argc`'s number.

(possible answer, DO NOT COPY PASTE)
```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	// if less than 2 arguments given
	if (argc < 2) 
	{
		// print an error
		printf("Error, expected input! `./input <argument>` \n");
		// return an error code, and don't read any more code
		return 1;
	}

	// else
	// print a welcome message
	printf("Hello, %s! \n", argv[1]);

	// return no error (aka 0)
	return 0;

	// anything after "return" keyword will not get run
}
```

Just so you know, `argc` doesn't start counting at 0 (so if your using `argc` to stop yourself from offsetting outside of an array you will need to subtract 1 from `argc`, since offsets for arrays start counting from 0 and not 1). If we put 2 arguments (including the command to run the program) then `argc` will be 2 .

In the above code we print an error message and "return" an error code of 1 if no argument was given. 

Any code after a `return` keyword won't get run (to an extend). This prevents us from running the greeting message "Hello, mikey", since the word "mikey" wouldn't exist (or any other word you put)!

If we do put 2 arguments, then print the greeting message, and return an error code of 0 (0 meaning nothing went wrong).

Compile the above code (or your variation), and see if it prints the error message when you don't put "Mikey" (or some other word) after "./input".

# Get Address
A normal variable also has an address in memory. We can get the address of a non-pointer variable by using the ampersan symbol `&` in front.

(example)
```c
int my_number = 12;

void* my_address = &my_number;
```

In the above code we make anormal variable called `my_number`. Then we make a pointer (aka address variable) called `my_address` and set it to the address of `my_number`.

Now we can use `my_address` to access the same number that `my_number` holds.

In memory this would look something like this.

![] TODO

# Getting Input
We can get input much like Python by using C's `scanf` function.

Make a new C file using touch.

(command)
```
touch input.c
```

Now open it and write the following code.

```c
#include <stdio.h>

int main(void)
{
	int my_number;
	printf("Type an integer: ");

	scanf("%i", &my_number);
}
```

The above code makes an empty variable called "my_number". We then print a prompt "Type a number: ", directly after the `printf` we run the `scanf` function. The `scanf` function waits for us to type something, except you'll notice it is expecting a `%i` which is an `int` conversion specifer!

Once we type a number and click enter `scanf` saves the number we typed into an address! The address we give `scanf` is the address to our `my_number` variable!

Finally we will print out `my_number`.

Edit your code to the following.

```c
#include <stdio.h>

int main(void)
{
	int my_number;
	printf("Type an integer: ");

	scanf("%i", &my_number);

	// print out `muy_number`
	printf("Number = %i \n", my_number);
}
```

Compile this code with `make input`, then run it using `./input` , you should have the following.

(shell)
```
~/arrays-2$ ./input
Type an integer: 
```

Type in a number, then hit enter. Yous shoudl then see something like this.

(shell)
```
~/arrays-2$ ./input
Type an integer: 1678
Number = 1678
~/arrays-2$ 
```

You can use `scanf` to get input from other types to! If you use the conversion specifier for a `float` then `scanf` will store the result you put into the address you give it.

Although if the user types just a word instead of a number, then `scanf` will probably not put anything into the address you gave it.

Go ahead and try typing random things into your program to see what will happen.

# Do while and Scope and Return?
TODO
- make program that asks for input from scanf until it is wanted input
- getting input until it is correct (from Getting input section!)

Any code after return will not get ran. SO if we did .... EXPLAIN

TODO
- all variables are technically an address. To view the address that a variable holds you can use the `&` to get access to the address