Open up https://replit.com. Make a new repl using the plus button. Select the C programming language. Name the repl "input".

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

The word `argv` stands for "argument vector" (this name is just traditional, we could have named it anything we wanted).

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

Compile this code using `make`.

(command)
```
make input
```

and run it using `./input` along with an argument, like the following command.

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

You might ask "what is the string at `argv[0]`"? Well lets change the code to access the first string in `argv[0]`.

(answer)
```c
#include <stdio.h>

int main(int argc, const char * argv[])
{
	printf("Hello, %s! \n", argv[0]);
}
```

Now compile this using `make`.

(command)
```
make input
```

And now run it using the shell.

(command)
```
./input Mikey
```

This should print out "hello ./input", which was litterally the command for running the `input` program! So `argv[0]` stores the literal command we used for running a program, in this case the string "./input".

## Out of bounds
In C we have to manually check how long our array is so that we don't accidentally offset outside of the array. We call this the "bounds" of an array.

Thankfully one of the parameters (inputs) from main is called `argc` which stands for "argument count", `argc` is an int, which tells us how many "arguments" are in `argv` (including the command for running the program).

Individual "arguements" are determined by a space separating each (`./hello how are you` would equal 4 arguments).

You can use `argc` to prevent yourself from offsetting outside of the `argv` array bounds.

Change our program to detect if it was run with any arguments (besides the first one for running it) by using `argc`'s number.

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

	// anything after "return" will not get run!
	printf("This code will never run!");
}
```

In the above code we print an error message and "return" an error code of 1, if no argument was given. Since the command to run the program `./input` counts as an argument we have to check `if argument_count less than 2` and not `if argument_count less than 1`.

Any code after a `return` keyword won't get run. So we use "return" inside of the `if (argc < 2)` to prevent us from running the code afterwards for printing out `argv[1]`.

I also put an extra `printf` at the end just to illustrate that code after a `return` will not get run (that `printf` will never happen).

Compile the above code uisng make (or your variation).

(command)
```
make input
```

Now see if it prints the error message when you don't put "Mikey".

(command, without "Mikey")
```
./input
```

# Getting Input using Scanf
We can get input much like Python's builtin `input` function by using C's `scanf` function.

Make a new C file using touch in the shell.

(command)
```
touch scan.c
```

Now open the "scan.c" file using the files window in Replit and write the following code.

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

Compile this code with `make scan`, then run it using `./scan` , you should have the following.

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
There may be an instance where you want the user to type something specific, like a "yes" or "no", but they type gibberish instead. How can we make them have to say "yes" or "no" and get an answer?

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

Then use `scanf` to get the answer from the user (you in this case).

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

We make an "answer" array, but we don't use the star symbol `*`. Instead we make the array of size 10, otherwise it would be an empty array! And `scanf` can't *put* data into an empty array! We make this array of size 10, so at the max we can only hold up to 10 `char`'s.

Since the `answer` variable is already a pointer (address to the first byte), we don't have to put an ampersan `&` in front to gets its address in `scanf`.

We use the `string` conversion specifier (`%s`) in `scanf`.

Now, how can we tell if the person typed "yes" or "no", and not some gibberish?

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

But can't compare two arrays (since `answer` is an array of ASCII characters and so is "yes")! So instead we would have to go through every single ASCII character, and check if they match eachother!

There is actually a special function that does just that (although we could easily make one ourselves). It is called `strcmp`, standing for "string compare". To get access to `strcmp` we need to include "string.h".

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

Now we can use `strcmp` to check `if strcmp(answer vs "yes")`.

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
		printf("Yay!");
	}
	else {
		printf("Why not?");
	}
}
```

(1) `strcmp` takes in two strings, compares them and returns (gives back) a number. If the words were equal it gives back `0`, so in the `if` statement we check if `strcmp` gave back `0` (meaning that the strings matched).

Compile this code using `make do_while`, then run it using `./do_while`

When the program asks you to type "yes" or "no", if you typed "yes" then the response will have been "Yay!". Otherwise it will have been "Why not?".

What we want is to prompt the user and ask them to give us "yes" (or "no"), but if the user doesn't give us "yes" (or "no") then the code should repeat, and ask the user again.

Delete the code for `if strcmp(answer is "yes")`

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

Make sure to use the tab key to put space in front of the code in the `do` block. Why? Because it would be hard to read if my code looked like this...


(terrible code)
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

...really hard to read.

Now at the end of the `do` block, add a "while" condition.

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

The `do` code will run at least one time, before we check the `while` condition. That is what makes this different than a regular old `while` loop.

(example, regular old while loop)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	while (strcmp(answer, "yes") != 0);
	{
		printf("Type 'yes' or 'no': ");

		char answer[10];
		scanf("%s", answer);
	} 
}
```

The above code wouldn't even work! WE would have to change it to...

(example, terrible code)
```c
#include <stdio.h>
#include <string.h>

int main(void)
{
	printf("Type 'yes' or 'no': ");

	// ask once
	char answer[10];
	scanf("%s", answer);

	// ask again if incorrect
	while (strcmp(answer, "yes") != 0);
	{	
		printf("Type 'yes' or 'no': ");
		scanf("%s", answer);
	} 
}
```

Where were we? Oh right, the `do { do this code } while(condition to check)`...

(original code)
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

If we try to run this code we will get an error. Simply that the `answer` variable does not exist in the `while` check... which is odd.

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

...with the only difference being that we *`do`* the code inside of the curly brackets at least once, *before* we check the condition.

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

And now the answer variable exists inside of `main` as well as inside of the `while` check.

Before we run this program lets also make the `while` condition also check if the input is NOT "yes" *or* "no".

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
	while (strcmp(answer, "yes") != 0 
			&& strcmp(answer, "no") != 0);
}
```

"and" in C is represented by 2 ampersan symbols `&&`. I also put the `&& strcmp(answer, "no") != 0);` on a newline, but you can put it all on the same line if you want.

(example, all in one line)
```c
// ... snip
while (strcmp(answer, "yes") != 0 && strcmp(answer, "no") != 0);
// ... snip
```

both ways are valid C code.

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

	// print out the answer
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

We delete the `printf("%s", answer);` at the end of the "yes" function.

The `yes` function returns (aka gives back) a `bool` type ("true" or "false"), so we put `bool` in front of the functions name.

Since we are using the "boolean" types `true` and `false` we need to add `#include <stdbool.h>` at the top, to get access to them.

(add `#include <stdbool.h>` at the top of the code)
```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h> // include

// ... snip (main)...

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

(I put the comment `// ... snip ...`, to show that I am focusing on the `yes` function and the `#include <stdbool.h>` that does NOT mean you should delete the "main" function!)

Now, the `yes` function needs to return (give back) `true` if the user put "yes" and return `false` if the user typed "no".

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
	
	// if answer is yes
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

(I put the comment `// ... snip ...`, to show that I am focusing on the `yes` function, that does NOT mean you should delete the "main" function! Instead just edit what is already inside of the `yes` function!)

Now we can use the `yes` function whenever we want to force a user for a `yes` or `no` answer!

Lets use `yes` to ask the user a question! (inside of `main`)

(edit your code)
```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

int main(void)
{
	printf("Do you want nose hair? \n");

	if (yes() == true)
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

(Again you'll see I used `// ... snip ...` to show that I am focusing on the `main` function, I did NOT delete `yes()`! I am simply focusing on the relevant parts of the code, without having to show you everything (plus you already know what the `yes` function looks like/does, so there is no need to repeat myself!))

We run/use the `yes` function inside of `if (yes() == true)`. This will make the code inside of `yes` run, and then give us backa `true` or `false`. I think you can figure out what the rest of the code is doing.

This is often called "abstraction", which is where we (or someone else) writes some code to do a common task, and then after that we can just use it without having to worry about how `yes` works (I am just teaching you the terminology here since someone you talk to will inevitably use it).

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