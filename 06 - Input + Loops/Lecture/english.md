TODO LEFT OFF HERE

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

TODO PASTED ABOVE FROM PREVIOUS LECTURES

# Get Address
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

# Getting Input using Scanf
We can get input much like Python's builtin `input` function by using C's `scanf` function.

Make a new repl. Select the C programming language. Name the repl "input".

Make a new C file using touch in the shell.

(command)
```
touch input.c
```

Now open "input.c" file using the files window in Replit and write the following code.

```c
#include <stdio.h>

int main(void)
{
	int my_number;
	printf("Type an integer: ");

	scanf("%i", &my_number);
}
```

We make an empty variable called "my_number". We then print the phrase "Type a number: ". 

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

Go ahead and try typing random things into your program to see what `scanf` will do!

# Do while, Scope, and Return?
There may be an instance where you want the user to type something specific, like a "yes" or "no", but they type gibberish instead. How can we solve that?

Make a new file using touch.

(command)
```
touch do_while.c
```

This makes a new file called "do_while.c".

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

Now, how can we check if the person typed "yes" or "no" and not some gibberish? 

Well we could try to compare the two words!

(example)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	char answer[10];
	scanf("%s", answer);

	if (answer == "yes")
	{
		printf("yes!");
	}
}
```

But since a "string" is just an array of ASCII numbers (which map to characters) we can't compare two arrays! So instead we would have to go through every single ASCII character, and check if they match eachother!

There is actually a special function that does just that! It can compare if a string matches another string. It is called `strcmp`, standing for "string compare". To get access to `strcmp` we need to include "string.h".

(add `#include <string.h>` to your code)
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

	// (1)
	if (strcmp(answer, "yes") == 0)
	{
		printf("yes!");
	}
}
```

(1) `strcmp` takes in two strings, compares them and returns (gives back) a number. If the words were equal it gives back `0`, so in the if statement we check if the result is `0` (meaning that the strings matched).

Compile this code using `make do_while`, then run it using `./do_while`

If you typed "yes" then the response will have been "yes!"

Now what we want is to prompt the user and ask them to give us "yes", but if the user doesn't give us "yes" then the code should repeat (and ask the user again).

Delete the code for "if strcmp(answer is "yes")"

(change your code to the following)
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

Make sure to use the tab key to put space in front of the code in the "do" block, so that it is inside of the "do" block (AKA, make sure your code looks pretty).

Now at the end of the do block, add a "while" condition.

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

The problem becomes more obvious if you realize that a `do while` loop is just a regular `while` loop...

(regular loop version, example)
```c
	while (strcmp(answer, "yes") != 0)
	{
		printf("Type 'yes' or 'no': ");

		char answer[10];
		scanf("%s", answer);
	} 
```

...with the only difference being that we *`do`* the code inside of the curly brackets at least once, *before* we do the check.

So now you can see we are trying to use the `answer` variable before it even exists!

To fix this we have to move the `answer` variable out of the `do` block and into the "main" function.

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

"Scope" is a concept that makes sure we don't use a variable before it exists.

And now the answer variable exists inside of `main`, which (thanks to "scope") also makes it valid inside of the `while` check.

Before we run this program lets also make the `while` condition check `while compare(answer, "no") != 0 and compare(answer, "yes") != 0`, basically loop again if the input is not "yes" or "no".

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
}
```

One last thing is to print out something depending on the answer.

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

Our program behaves perfectly!

Lets turn the "main" function into a function called "yes", then re-make the "main" function again.
![main into yes function](/Assets/main_into_yes_function.gif)

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

We also delete the `printf` at the end of the "yes" function.

The `yes` function returns (aka gives back) a `bool` type ("true" or "false"), so we put `bool` in front of the functions name.

Since we are using the "boolean" types `true` and `false` we add `#include <stdbool.h>` at the top, to get access to them.

The `yes` function needs to return (give back) `true` if the user put "yes" and return `false` if the user typed "no".

At the end of the `yes` function (after the user cooperates and puts "yes" or "no") we can return `true` or `false` based on the the answer variable.

(edit the `yes` function)
```c
// ... snip ...

bool yes()
{
	char answer[10];
	do
	{
		printf("Type 'yes' or 'no': ");

		scanf("%s", answer);
	} 
	while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);
	
	// answer is yes
	if (strcmp(answer, "yes") == 0)
	{
		return true;
	}
	else // answer was "no"
	{
		return false;
	}
}
```

I put the comment `// ... snip ...`, to show that I am focusing on the `yes` function, that does NOT mean you should delete the "main" function! Instead you should just edit what is already inside of the `yes` function!

Now we can use the `yes` function whenever we want, and ask the user for a `yes` or `no`!

Lets use `yes` to ask the user a question! (inside of `main`)

(edit your code)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(void)
{
	printf("Do you want nose hair? \n");

	if (yes())
	{
		printf("Thank goodness! XD")
	}
	else
	{
		printf("That's kinda... weird");
	}
}

// ... snip ...
```

Again you'll see I used `// ... snip ...` to show that I am focusing on the `main` function, I did NOT delete `yes()`! I am simply focusing on the relevant parts of the code, without having to show you everything (plus you already know what the `yes` function looks like/does, so there is no need to repeat myself!)

This is often called "abstraction", which is where we write some code to do something for us once, and then don't have to worry about how it works, but just use it later.

You'll notice that I forgot to add a function hint above main! Go ahead and add a function hint for `yes` above main.

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
		printf("That's kinda... weird");
	}
	else
	{
		printf("Thank goodness!")
	}
}

// ... snip ...
```

I also left one tiny error for you to solve in the "main" function!

Try to compile this code with make (you should see an error, go ahead and fix it)

(command)
```
make do_while
```

and run it using

(command)
```
./do_while
```

And thats it for today!

PS: the error I left for you to solve is that I didn't add a semicolon `;` at the end of `printf("Thank goodness!")`