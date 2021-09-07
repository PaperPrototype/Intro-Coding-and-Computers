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
	char* hello = "Hello";

	// access what is at the address
	printf("%c \n", *hello);
}
```

This is called "de-referencing" a pointer ("accessing" what is at a pointers address (since "pointer" is just another name for a variable the holds an address and not the data itself)).

The above code also changes to use the conversion specifier for `char` type `%c` (in `printf`), rather than the string conversion specifer `%s`.

This code will print out the letter "H" (obviously). Compile the above code with make, then run it (using the shell).

Using the square brackets `[]` is a useful shortcut for offsetting from an address or pointer. 

When we make an array we have to know the type of the array for C to be able to offset correctly. Hence `char*` is an address, which offsets by 1 byte when we use the square brackets iterator `[]`. If we had an array of `int` we would offset by 4 bytes to get the next item.

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

Change your code ot the following.

```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// access what is at the address
	printf("%c \n", hello[100]);
}
```

Compile this code with `make string` then run it using `./string`. You will see "null" get printed (or another type of error called a "segmentation fault", often shortened to "seg fault").

# Loops + Arrays
We can also use a `for` loop on an array. This is pretty cool. Lets iterate over the word hello and print out each character, one by one.

We use a simple for loop to go over each item.

(change your code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	for (int index = 0; index < 5; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

The `index` variable is the number that gets increased each loop. We loop a total of 5 times since there is only 5 letters. Its very useful to start counting at zero since the memory offsets start at the first item.

Inside the loop we use the `index` variable to access each item in the array, and print it as a character `%c`.

Although having to manually set the number of times the loop loops is kind of bad. 

So instead we can check "while the current character isn't `\0`" since C automatically puts a null character at the end. The sentence translates to the following example code.

(example)
```c
while hello[index] != '\0`
```

Which will stop the loop once it finds the null character `\0`.

Translated to a for loop in our code it would look like the following.

(change your code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	for (int index = 0; hello[index] != '\0'; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

We coudl also "count" the number of characters in our string and then use the number we get from that to loop a certain number of times.

It turns out there is a function that does this for us called `strlen`, which stands for "string length" (aka the number of characters in the array/string).

To get access to `strlen` we have to include `string.h`.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	for (int index = 0; hello[index] != '\0'; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Now we can replace the condition (aka check for true or false) in the loop with `index < strlen(hello)`.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	for (int index = 0; index < strlen(hello); index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Although this code is NOT efficient. Every single loop we count all the characters in `hello` using the `strlen` function!

We can quickly fix the terrible design by making a variable to hold the result from `strlen`, then use the variable each loop.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	int length = strlen(hello);

	for (int index = 0; index < length; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Compile and run this code using the shell.

Since the `length` variable shouldn't ever change (since there will only ever be 5 letters in the word "Hello") we can make sure other programmers don't accidentally change the `length` variable by making it a "constant".

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// make variable a "const"
	const int length = strlen(hello);

	for (int index = 0; index < length; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

We put the `const` keyword in front of the length variable. If someone makes some code to try to change `length`, then C won't even let the code compile! It will through an error message.

Also it is a tradition to uppercase a `const` variable to help programmers know it is a `const` (without having to go and look at the code that made the variable).

(change your code to be more traditional)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char* hello = "Hello";

	// make variable a "const"
	const int LENGTH = strlen(hello);

	for (int index = 0; index < LENGTH; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Now compile and run this code using the shell.

# Void
Since a pointer (aka variable with address) simply points to the first byte of an array (or just the first byte to an `int`) we don't have to tell C the type! We can jsut point to the first byte of data!

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

This code makes a pointer with an unknown type! `void` is used as an unkown type, but it also stands for "no input" in a function. By using `void` for the pointer's type we can point to any array, without having to tell the type (this is also true of non-array values).

C has to know how to treat the 0s and 1s of a variable to "use" the value. In the code above we tell C the "type" by *casting* (treating the 0s and 1s as if it was that type) the pointer to a `char` pointer, hence `(char*)`. 

If we skipped casting, C, by default, would offset by 1 byte to access items in the array (in this case a single `char` is 1 byte anyways, so it would still work).

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

The rest of it `char * argv[]` is weird. It is an array of addresses `char *` to an array of strings `argv[]`... Another way of writing this would be to use two stars `char ** argv` without the square brackets (since the square brackets are the same as writing a star).

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
	printf("Hello, %s! \n", argv[1]);
}
```

The above code gets the second string from the array of strings (in `argv`).

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

Thankfully one of the parameters (inputs) from main is called `argc` which stands for "argument count", `argc` is an int. You can use `argc` to prevent yourself from offsetting outside of the arrays bounds. You can also use `argc` see how many arguments were given.

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

		// return an error code of 1
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

Just so you know, `argc` doesn't start counting at 0. If we put 2 arguments (including the *command to run* the program) then `argc` will be 2.

In the above code we print an error message and "return" an error code of 1, if no argument was given (the command to run the program "./input" counts as an argument).

Any code after a `return` keyword won't get run. So we use "return" inside of the `if (argc < 2)` to prevent us from running the code afterwards (the greating message "Hello, Mikey", since "Mikey" woudln't exist).

Compile the above code (or your variation), and see if it prints the error message when you don't put "Mikey".

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

![memory address from variable](/Assets/memory_address_from_variable.png)

# Getting Input using Scanf
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

We make an empty variable called "my_number". We then print "Type a number: ". 

Directly after the `printf` we run the `scanf` function. The `scanf` function will wait for us to type something (you'll notice that `scanf` is expecting a `%i` which is an `int` conversion specifer!).

Once we type a number and click enter `scanf` saves the number we typed into an address! The address we give `scanf` is the address to our `my_number` variable!

Finally we will print out `my_number`.

(Edit your code to the following to print out `my_number`)
```c
#include <stdio.h>

int main(void)
{
	int my_number;
	printf("Type an integer: ");

	scanf("%i", &my_number);

	// print out `my_number`
	printf("Number = %i \n", my_number);
}
```

Compile this code with `make input`, then run it using `./input` , you should have the following.

(shell example)
```
~/arrays-2$ ./input
Type an integer: 
```

Type in a number, then hit enter. You should then see something like this.

(shell example)
```
~/arrays-2$ ./input
Type an integer: 1678
Number = 1678
~/arrays-2$ 
```

You can use `scanf` with other conversion specifiers, and even multiple conversion specifiers! You just have to make sure that the input you type in is consisitent with the conversion specifiers in the `scanf`.

If the user (you) types just a word instead of a number, then `scanf` will probably not put anything into the address you gave it.

Go ahead and try typing random things into your program to see what will happen.

# Do while and Scope and Return?
There may be an instance where you want the user to type something specific, like a "yes" or "no", but they type gibberish instead. How can we solve that?

Make a new file using touch.

(command)
```
touch do_while.c
```

This makes a new fiel called "do_while.c".

In the code we will first ask the user to type "yes" or "no".

(write the following code into "do_while.c")
```c
#include <stdio.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");
}
```

Then make a variable to hold the answer (from the user).

(change your code to the following)
```c
#include <stdio.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	char answer[10];
	scanf("%s", answer);
}
```

We make an "answer" array, but we don't use the star symbol `*`. Instead we make the array of size 10, otherwise it woudl be an empty array! And `scanf` can't *put* data into an empty array!

Since the `answer` variable is already an address (aka pointer), we don't have to put an ampersan `&` in front of it in `scanf` to get its address. 

Also, we use the string conversion specifier (`%s`) in `scanf`.

Now, how can we check if the person typed "yes" or "no" and not some gibberish? There is a special funciton that can compare if a string matches another string called `strcmp`, standing for "string compare". To get access to `strcmp` we need to include "string.h".

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	char* answer;
	scanf("%s", answer);
}
```

Now we can use `strcmp` to check "if strcmp(answer is "yes")".

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	char answer[10];
	scanf("%s", answer);

	if (strcmp(answer, "yes") == 0)
	{
		printf("yes!");
	}
}
```

`strcmp` returns (gives back) a number. If the words were equal it gives back `0`, so in the if statement we check if the result is `0`.

Compile this code using `make do_while`, then run it using `./do_while`

If you typed "yes" then the response will have been "yes!"

Now what we want is to prompt the user and ask them to give us "yes", but if the user doesn't give us "yes" then the code should repeat.

Delete the code for "if strcmp(answer is "yes")"

(change your code ot the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	char answer[10];
	scanf("%s", answer);
}
```

Then "wrap" all the code in main in a "do" block.

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	do
	{
		printf("Type 'yes' or 'no': ");

		char answer[10];
		scanf("%s", answer);
	}
}
```

Make sure to use the tab key to put space in front of the code that is inside of the "do" block (aka, make sure your code looks pretty).

Now at the end of the do block, add a "while" condition.

(change your code ot the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	do
	{
		printf("Type 'yes' or 'no': ");

		char answer[10];
		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0);
}
```

If you read this code it literrally says 

```
do
{
	// code
}
while answer is NOT 'yes'
```

And the `do` code runs once before the `while` condition.

Although if we try to run this code we will get an error. Simply that the `answer` variable does not exist in the `while` check.

This is because `answer` only exists inside of the curly brackets `{}`! This is called a variables "scope".

To fix this we have to move the `answer` variable out of the `do` block.

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0);
}
```

And now the answer variable exists inside of `main`, which (thanks to "scope") also makes it valid inside of the `do while` loop.

Before we run this program lets also make the `while` condition check if the answer `while "no" != 0 and "yes" != 0`.

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);

```

The code `while "no" != 0 and "yes" != 0` is a bit weird to read, but it asks `while the answer is NOT "yes" or "no"` then we should do the loop again.

One last thing is to print out "yes" or "no" depeneding on the answer.

(change your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);

	printf("%s", answer);
}
```

Now compile this using `make do_while` and run it using `./do_while`.

Our program behaves perfectly! Lets make this program into a function we can use to ask the user "yes" or "no" whenever we want.

(change your code to the following)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(void)
{
	
}

bool yes()
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);
}
```

We move all the code into a function called "yes".

(I recommend you copy paste, or rename "main" to "yes" to "move the code" rather than deleting it all and starting over).

The function returns (aka gives back) a `bool` type ("true" or "false"), so we put `bool` in front of the functions name.

The function will return `true` if the user put "yes" and it will return `false` if the user typed "no", so we need to include the true and false variables which are in `stdbool.h`.

Now at the end of the function (once the user cooperates and puts "yes" or "no") we can return true or false.

(change your code to the following)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(void)
{
	
}

bool yes()
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);
	
	if (strcmp(answer, "yes") == 0)
	{
		return true;
	}
	else
	{
		return false;
	}
}
```

Now we can use the `yes` function whenever we want! 

(you could honeslty name `yes` something else like "ask" or "ask_yes_or_no" if you want)

Lets use `yes` to ask the user a question! (inside of `main`)

(change your code to the following)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(void)
{
	printf("Do you want nose hair? \n");

	if (yes())
	{
		printf("Thank goodness!")
	}
	else
	{
		printf("That's kinda... weird");
	}
}

// ... snip ...
```

I used `// ... snip ...` to show that I am focusing on the `main` function, I did NOT delete `yes()`! I am simply focusing on the relevant parts of the code, without having to show you everything (plus you already know what the `yes` function looks like/does, so theres no need to repeat myself!)

This is often called "abstraction", which is where we write some code once and then don't worry about how it works, but just use it later.

You'll notice that I forgot to add a function hint above main! Go ahead and add a function hint for `ask` above main.

(answer)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

// function hint
bool yes();

int main(void)
{
	printf("Do you want nose hair? \n");

	if (yes())
	{
		printf("Thank goodness!")
	}
	else
	{
		printf("That's kinda... weird");
	}
}

// ... snip ...
```

I also left one tiny error for you to solve! (^_^)

Now compile this code with make

(command)
```
make do_while
```

and run it using

(command)
```
./do_while
```

And thats it for today! Have fun with the tutorials!