In C we don't have the idea of "lists" instead we have "arrays". 

Arrays are different than Python lists because once we set their size, we can't change that size!

Make a new repl. Select the C programming language. Call the project "arrays".

In the shell make a new file called `array.c` using `touch`.

(command)
```
touch array.c
```

Remove the "main.c" file using the `rm main.c` command (since we won't be using `main.c`).

Open `array.c` using Replits files window and write the following code.

```c
int main(void) {
	int integers[] = { 2, 3, 6, 1 };
}
```

When making a variable that holds onto an array we put square brackets `[]` next to the variables name to show that it is an "array" variable.

We then "fill" the array by putting curly brackets `{}` around all the items, and we separate each item using a comma `,`.

Any variable is really an address to the first byte of the `0`s and `1`s (A "byte" is 8 bits (a bit is a single `0` or `1`)). You should think of addresses as being a ***number to a specific byte*** in memory.

You can visualize addresses and bytes like this.

![memory continous linear](/Assets/memory_continuous_linear.png)

Although we often represent memory as a grid since that helps it is more space efficient in your computer (and helps it fit on the page).

![memory grid](/Assets/memory_grid.png)

Even though we think of memory as a "grid", addresses are still a number to a specific byte.

![memory wrap around](/Assets/memory_wrap_around.png)

Now the only reason we have to have "types" (like `int` and `char`) is that we have to know how many bytes after the first byte are part of the variable!

An array is no different, you hold an address to the first byte of memory!

The `integers` variable in the above code is an *address* to the first byte in our array. This looks like the following in memory.

![array ints](/Assets/array_ints.png)

To access an item in an array we "go to" the first item in the array + an offset. THe "type" tells us how many bytes to move per offset to access sequential items.

Change your code to the below code to print out the second item in the list by using an offset of 1 (Make sure to add a `\n` and `#include stdio.h>`)

(change your code to the following)
```c
#include <stdio.h>

int main(void) {
	int integers[] = { 2, 3, 6, 1 };

	printf("%i\n", integers[1]);
}
```

The "offset" is what goes into the square brackets `[]`. Using the square brackets makes us "go to" the address with an offset, plus the size of the "type". Currently we are using an `int` type which is 4 bytes (4 blocks) so the above code offsets by `1 * 4` bytes to get the second item in the array.

![array ints offsetting](/Assets/array_ints_offsetting.png)

To get the first item we can simply "go to" the address with an offset of `0`.

(example)
```c
#include <stdio.h>

int main(void) {
	int integers[] = { 2, 3, 6, 1 };

	printf("%i", integers[0]);
}
```

Compile "array.c" using make in the shell window.

(command)
```
make array
```

Then run it using the shell.

(command)
```
./array
```

You can test the size of a type in C by using the builtin `sizeof` function.

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

The size of a type is measured using a unsigned (non negative, no "sign") `long` type, so when printing the size of a type we use the unsigned long specifier `%lu`.

Compile the code with `make array`, then run it again using `./array`

# Strings
It turns out that *strings* (words and phrases enclosed in double quotes `"like this"`) are an array! More specifically an array of `char` types. 

Make a new file uisng `touch`.

(command)
```
touch string.c
```

Use `ls` to see the new file.

(command)
```
ls
```

Write the following code into "string.c" (open string.c using the files window).

(change the code to the following)
```c
#include <stdio.h>

int main(void) {
	char hello[] = { 'H', 'e', 'l', 'l', 'o' };

	printf("%s \n", hello);
}
```

The `char` type is litterally an ASCII type.

In the array we enclose each individual letter with a single quote `'`. C requires that we use a single quote `'` and not a double quote `"` to represent a single `char` type.

Run make to compile the "string.c" code

(command)
```
make string
```

Then run it using the shell.

(command)
```
./string
```

You will see "Hello" get printed.

We use the string conversion specifier `%s` since a string in C is actually an array of `char`acters. Making a string (an array of `char`s) is so common that nobody writes strings using array syntax! Instead we have been using the special syntax for strings,double quotes `"like this"` rather than the clunky array syntax `{ 't', 'h', 'i', 's' }`.

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

You may ask yourself "how does printf know when to stop offsetting in a char array (string)"? Every "string" in C by default ends with a special *null terminating character*, which look like this `\0`.

Even though we didn't add a (backslash zero) `\0` to the end of our string, C added it for us.

# Loops + Arrays
Now we finally get to know *why* a `for` loop is useful!

(for loop, example)
```c
// loop 5 times
for (int num = 0; num < 5; num++) {

	printf("%i", num);
}
```

We can use a `for` loop to offset in an array and print all the items!

The above for loop is equivalent to the following `while` loop.

```c
// make "num" variable
int num = 0;

// loop 5 times
while (num < 5) {

	printf("%i", num);

	// increase "num" variable by 1
	num++;
}
```

The `for` loop does the same thing as the `while` loop, it just puts it all in one line `for (int num = 0; num < 5; num++)`.

(change your string.c code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// loop 5 times
	for (int num = 0; num < 5; num++)
	{
		// print single item in hello array at offset
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

The above code prints out each character (one by one) in the hello array.

The `num` variable is the number that gets increased each loop. We loop a total of 5 times, and print each item in the `hello` array. Its very useful that a `for` loop starts counting at zero, since doing so will make the memory offsets start at the first item!

Compile the above code using `make string`, and run it using `./string`.

# Design
Having to manually set the number of times to loop (which is currently 5) is kind of a bad design. Say we accidentally set the number to 10 instead of 5! At some point you might start getting "buffer overflow" errors. Basically we have "overflowed" and accessed memory outside of the "buffer"/chunk of memeory we are allowed to access.

Instead of manually setting the loop to loop 5 times we can check "while the current character isn't `\0`" (since C automatically puts a null termintating character `\0` at the end).

(example)
```c
// while current character isn't '\0'
while hello[num] != '\0'
```

Which will stop the loop once it finds the null character `\0`.

(change your code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	int num = 0;
	while (hello[num] != '\0')
	{
		printf("%c", hello[num]);

		// increase number
		num++;
	}

	printf("\n");
}
```

Challenge time! Try to change the above `while` loop to a `for` loop! The answer is below if you get stuck, but try and do it without looking at the answer!

(answer)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	for (int num = 0; hello[num] != '\0'; num++)
	{
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

# Design 2
We could also "count" the number of characters in our string and then use the number we get from that to loop a certain number of times.

It turns out there is a function that does this for us called `strlen`, which stands for "string length" (aka the number of characters in an array/string).

To get access to `strlen` we have to include `string.h`.

(edit your code accordingly)
```c
// include string.h
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	for (int num = 0; hello[num] != '\0'; num++)
	{
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

Now we can replace the condition (aka check for true or false) in the loop with `while num < strlen(hello)`.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// loop "strlen" times
	for (int num = 0; num < strlen(hello); num++)
	{
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

Which says "loop string length amount of times".

Every time we loop we use the `strlen` function to check "if num is less than length of the string"...but, the strlen function has to count all the stuff inside of the `hello` variable, every single loop, just to do that check! This is not efficient!

We can quickly fix the terrible design of this by making a variable that will hold onto the "length" number from `strlen`, then use that variable in the check each loop.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// create length variable
	int length = strlen(hello);

	for (int num = 0; num < length; num++)
	{
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

Tada! Now go ahead an change the word inside of the `hello` array! And the loop will automatically loop the correct number of times!

(change your code to the following (or wrtie a sentence of your own))
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Helloooo everyyybody! I ammmm soooo smart, running with these massive golden scissors in my hands!";

	// create length variable
	int length = strlen(hello);

	for (int num = 0; num < length; num++)
	{
		printf("%c", hello[num]);
	}

	printf("\n");
}
```

Compile and run this code using the shell!

We can make sure other programmers don't accidentally change the `length` variable (once we "set" it) by making it a "constant".

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// make variable a "const"
	const int length = strlen(hello);

	for (int index = 0; index < length; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

We put the `const` keyword in front of the length variable. If someone makes some code to try to change `length`, then C won't even let the code compile! It will through an error message saying "hey, you can't change that, the other programmer made it a constant."

Also it is a tradition to uppercase a `const` variable to help programmers know it is a `const` (without having to go and look at the code that "made" the variable).

(change your code to be more traditional)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// traditional const uppercasing
	const int LENGTH = strlen(hello);

	for (int index = 0; index < LENGTH; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Compile this code usign `make string` and run it using `./string` using the shell.

Now stare at this marvelous beautiful... pointless, program.

# Addresses
Array variables are an address to the first byte of memory in the array. But what if we only want an address to a single item? In that case we can use a star symbol `*` in front of the variable.

(example)
```c
#include <stdio.h>

int main(void) {
	int *my_address = 12;
}
```

In this case we have made a variable that holds an address to 12.

# Swap
TODO
- swap the numbers in 2 variables

# Get Address (TODO combine knowledge form thsi into "swap" code)
A normal variable also has an address in memory. We can get the address of a non-pointer variable by using the ampersan symbol `&` in front.

(example)
```c
int my_number = 12;

void* my_address = &my_number;
```

In the above code we make a normal variable called `my_number`. Then we make a pointer (aka address variable) called `my_address` and set it to the address of `my_number`.

Now we can use `my_address` to access the same number that `my_number` holds.

In memory this would look something like this.

![memory address from variable](/Assets/memory_address_from_variable.png)


# Void
Since a pointer (aka variable with an address) simply points to the first byte of an array (or just the first byte to an `int`) we don't have to tell C the type! We can just make a plain old address to the first byte (of the data)!

Change the code to the following.

```c
#include <stdio.h>

int main(void) 
{
	// void pointer
	void* hello = "Hello";

	//             convert to a char pointer "char*"
	printf("%s \n", (char*) hello);
}
```

This code makes a plain old pointer (address) without needing to know the type! C's "grammer" requires that we put `void` in front of the variables name.

C has to know how to treat the 0s and 1s of something at an address to "use" the value. In the code above we tell C the "type" at the address by *casting* (treating the 0s and 1s) to a `char` address, hence `(char*)`.

If we skipped *casting* the address then C would offset by 1 byte (by default) to access items in the array when we use the square brackets `[]` (in this case a single `char` is 1 byte anyways, so it would still work fine).

Types also tell us how many bytes *after the first byte* are *part of* the value at the address. This is necessary since an address just points to the first byte. 

Types also help later when compiling to Assembly code, since there are special `add` instructions for int's and float's (as well as other "special" math instructions specialized for speed).

# Getting Input from Main
The "main" function actually gets special input parameters (function variables) from the shell! So far we haven't used this functionality!

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

What is `const char * argv[]`? 

Well the first part `const` is a keyword, it is telling us that we are not allowed to change the variable's value (stuff inside the variable) and that it is "constant".

The rest of it `char * argv[]` is an array `argv[]` of addresses `char *`. Another way we could write it could be to use two stars `char ** argv` without the square brackets.

(change your code to use two stars)
```c
#include <stdio.h>

int main(int argc, const char ** argv)
{
	
}
```

If we visualize an array of addresses (the addresses each going to a separate string/word/phrase), in memory it would look something like this.

![argv in c](/Assets/argv.png)

The word `argv` stands for "argument vector" (honestly this name is just a tradition).

Lets use `argv` for a simple a program that gets our name, then prints it out along with a "hello" message.

Change your code to the following.

```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	printf("Hello, %s! \n", argv[1]);
}
```

The above code gets the second string from the array of addresses (in `argv`).

Compile this code using `make` and run it using `./input` along with an argument, like the following command.

(command)
```
./input Mikey
```

It runs the input program with an argument (the word "Mikey"). You should see the following get printed.

(shell)
```
~/arrays$ ./input Mikey
Hello, Mikey!
~/arrays$ 
```

If you happen to run the "input" program without any "arguments" afterward you will see the word "null" get printed instead! 

Go ahead and try running input without any arguments.

(command)
```
./input
```

We are trying to access memory from our `argv` array that has not been set to anything (because we didn't type in "Mikey" after "./input"). 

In C "null" usually means we are accessing memory that has not been set to anything.

You might ask "what is the string at `argv[0]`"? Well if you change your code to access the first string in `argv[0]` then you will get "./input", which was litterally the command for running the `input` program!

# Out of bounds
In C we have to manually check how long our array is so that we don't accidentally offset outside of the array. We call this the "bounds" of an array.

Thankfully one of the parameters (inputs) from main is called `argc` which stands for "argument count", `argc` is an int, which tells us how many "arguemnts" the program got (includeing the command to run the program). Individual "arguements" are determined by a space separating each ("./hello how are you" would equal 4 arguments).

You can use `argc` to prevent yourself from offsetting outside of the `argv` arrays bounds.

Change our program to detect if it was run with an argument by using `argc`'s number.

(possible answer, DO NOT COPY PASTE)
```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	// if argument count is less than 2
	if (argc < 2) 
	{
		// print an error
		printf("Error, expected input! `./input <argument>` \n");

		// return an error code of 1 and don't run any of the code after this
		return 1;
	}

	// else
	// print a great message
	printf("Hello, %s!", argv[1]);

	// return no error (0 means no error)
	return 0;

	// anything after "return" will not get run
	printf("This code will never run!");
}
```

In the above code we print an error message and "return" an error code of 1, if no argument was given (the command to run the program "./input" counts as an argument, so we check `if argument_count less than 2`).

Any code after a `return` keyword won't get run. So we use "return" inside of the `if (argc < 2)` to prevent us from running the code afterwards (the greating message "Hello, Mikey", since "Mikey" woudln't exist).

Compile the above code (or your variation), and see if it prints the error message when you don't put "Mikey".

See you next section!
