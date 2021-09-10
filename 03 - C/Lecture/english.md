Last week we talked about how computers represent data and instructions using only two symbols 0 and 1, representing the millions and millions of bits in our computer.

We are now going to learn a new language called C. This language is a *compiled* language (whereas Python was *interpreted*). This just means our code is written as text that gets "compiled" into a program file of 0 and 1 instructions for the CPU.

Remember how functions work in Python?

```py
# define "main"
def main():
	print("hello world")

main() # run "main"
```

In C there is a function that gets called automatically, except it is the only function that gets called! Any code that we want to run, including our own functions, have to go inside of a "main" function. This gives all computers a unifide way to have a "starting point" for where to run your program.

Lets write this "main" function. Go to https://replit.com/ and make a new replit.

This time select C as the programming language. Name the the project "hello c", then click "create repl".

There should already be a file called "main.c". In it you should see the following code.

```c
#include <stdio.h>

int main(void) {
	printf("Hello World\n");
	return 0;
}
```

Change the code so that the it looks like this. 

```c
// "main" function, only function that gets called
int main(void) {
	// code goes here
}
```

Don't run this code yet, as it won't do anything! The above code is the "main" function, and is the program *starting point* that computers use.

The word "int" in front of the function, tells C that `main` gives back an "integer" number (integers don't gave decimal places). This is different from Python where we use "def" for defining a function. Don't worry you'll get used to it.

You will see the word "void" inside of the functions input (in the parenthesis). In C we have to tell the computer that the function *doesn't* take any input, which is what the `void` keyword is for. `void` stands for "nothing" (literrally).

When using we were using Python, the Python interpreter automatically assumed you didn't want input if you don't put anything in the parenthesis "()".

You will notice the curly brackets "{}". This is what C uses instead of Python's colon ":".

```c
int main(void) {
	// code goes here
}
```

We can change the position of the curly brackets too.

(example)
```c
int main(void)
{
	// code goes here
}
```

C doesn't care where you put the curly brackets. You can even write all your code in one line!

(example)
```c
int main(void) { // code goes here }
```

Now lets make our own function, it will add 2 numbers together. Make a function under `main` so that the code looks like this.

```c
int main(void) {

}

int add(int a, int b) {
	return a + b
}
```

We take as input two "integers". In C we have to always know the *type*. A *type* tells C how to treat the 0s and 1s. "Is this a number? Is this a Unicode character?".

We tell the computer this is an integer (aka number) by putting the `int` *type* in front of the function's input parameters (parameters means variables for a function).

We tell C that the `add` function *returns* (aka gives back) an `int` by putting `int` in front of the functions name.

### Variables
Inside of `main`, make a variable called "result" that holds onto what the `add` function returns.

```c
int main(void) {
	int result = add(12, 12)
}

int add(int a, int b) {
	return a + b
}
```

The `result` variable has to have a type of `int` as well. C doesn't automatically figure out that the `result` variable should be an `int`. This is because C lets us work at the binary (0s and 1s) level, so we have to know how many bytes a variable holds, as well as how to treat each `0` and `1`.

(it could figure iout that the `result` is an `int`, but the makers of C wanted to make it more *clear* as to what exactly a variables type was)

This code still won't run though!

In C, whenever we type a line of code we have to end it with a semicolon ";". This is how C tells one line of code apart from another.

Change your code to the following.

```c
int main(void) {
	int result = add(12, 12);
}

int add(int a, int b) {
	return a + b;
}
```

You can't just say "get the next line of code". This is because "the next line of code" is stored as a "newline" symbol `\n`. So our code actually looks like this in the file.

`int main(void) {\n  int result = add(12, 12);\n  int result2 = add(12, 12);\n}\n\nint add(int a, int b) {\n  return a + b;\n}`

(Most "text editors" (Microsoft Word) don't show you the newline symbol "\n", they just make a newline)

So yeah, C makes us use a semicolon ";" so it can tell lines of code apart.

Although when making a function we don't have to add a semicolon at the end

(example)
```c
int add(int a, int b) {
	return a + b;
}; // semicolon not needed!
```

...since it is easy to tell when the function ends by just using the ending curly bracket "}". 

Sadly, our code (still!) won't work because C reads code from top to bottom. So when C reads the code inside of the `main` function it doesn't know that the `add` function exists!

(example)
```c
int main(void) {
	int result = add(12, 12); // where did `add` come from?
}
```

and honestly we wouldn't know where `add` was unless we kept scrolling down to find it.

Again Python took care of this for us, while C won't.

So we just have to put the `add` function above `main`. Change the code so that `add` is above `main`.

```c
int add(int a, int b) {
	return a + b;
}

int main(void) {
	int variable = add(12, 12);
}
```

Now you can run this code! (Although it won't print anything... yet)

There is a way to put a function below main. You just have to put a function "hint" above main.

```c
int add(int a, int b); // function hint

int main(void) {
	int variable = add(12, 12);
}

int add(int a, int b) {
	return a + b;
}
```

"function hints" are called "prototypes". 

We have to put a semicolon ";" at the end of the function *prototype* because there are no curly brackets in a prototype, just its name and parameters (function variables).

# Main returns an int?
Main returns (gives back) a number right?

(example)
```c
// function hint
int add(int a, int b);

int main(void) {
	int variable = add(12, 12);

	return 0; // main returns 0
}

int add(int a, int b) {
	return a + b;
}
```

The number `main` returns is an integer `int` (obviously). It represents an "error code". returning `0` means success (aka no error). Returning `1` means there was an error! But since we don't *have to* return an error code we won't bother with it.

Nothing gets printed to the console! Lets work on that.

# Printing + including
The `print` function doesn't come builtin in C. So we have to "include" code written by someone else that figures out the specific 0 and 1 instructions.

Change the code to the following.

```c
#include <stdio.h>

int add(int a, int b) {
	return a + b;
}

int main(void) {
	int result = add(12, 12);
}
```

We use a hash symbol "#" followed by "include". "include" is called a "compiler directive".

Compiler directives after the hash "#" are things the compiler "pre-processes", which means when we *include* this file, the compiler literally replaces `#include <stdio.h>` with the code from the "stdio.h" file.

(We will get to what a compiler is later, just know it converts text based code into `0`s and `1`s instructions for the computers processor)

"std" is short for "standard", and "io" is short for "input output", so we get "include standard input output code". 

The ".h" means it is a C "header" file. Headers files are normal C code except the code has already been turned into 0s and 1s! (This way the compiler doesn't have to compile all the *headers* we include and can just "link" them all to together in a stage called "linking"). The code in a header file is just a bunch of "function hints" to functions that are in the binary (0s and 1s) code file.

Where is the "stdio.h" code in the computer? The "stdio.h" code is used so often it comes builtin with the compiler (aka when you download a compiler it also downloads the stdio.h file).

(You can also include `.c` files by using double quotes around the name of the file like this `#include "mycode.c"`)

Now that we've included the standard input output *header* code, we can send output to the console using its `printf` function (`printf` meaning "print formatted").

```c
#include <stdio.h>

int add(int a, int b) {
	return a + b;
}

int main(void) {
	int result = add(12, 12);
	printf("Hello, world");
}
```

Now run this code. You will see "Hello world" get printed.

![replit print hello world](/Assets/replit_print_hello_world.png)

But the console didn't make a newline after "Hello world"! So we have to add this manually ourselves. (Again, Python added "\n" for us in its `print` function).

```c
#include <stdio.h>

int add(int a, int b) {
	return a + b;
}

int main(void) {
	int variable = add(12, 12);
	printf("Hello, world\n");
}
```

Now a newline will be added after the "Hello, world" string (remember, we call words or phrases enclosed with double quotes `""` *strings*).

![replit print hello world with newline](/Assets/replit_print_hello_world_2.png)

# Errors?
If you get a whole bunch of errors when running code... Just scroll up to the first error at the top in the console, since the rest of the errors are the *compiler* (aka program that converts code to binary instructions) getting confused from the first error.

# Printing variables
How can we print a variable? In Python it was easy.

```py
name = "Jafly"
print(name)
```

To print variables using `printf` we have to tell it the *type* of the variable.

In `printf` you use the percent symbol `%` followed by a letter for the type. In this case our variable is an `int`, so in `printf` we write `%i`. "%i" stands for the `int` type.

Change the code to the following.

```c
#include <stdio.h>

int add(int a, int b) {
	return a + b;
}

int main(void) {
	int result = add(12, 12);

	printf("%i \n", result);
}
```

The `%i` is a placeholder, and will get replaced by the `result` variable.

Run this code. You will see that the `%i` in the string gets replaced by 24 (we also make sure to add a newline `\n`).

We refer to the percent sign "%" *placeholders / types* for `printf` as "conversion specifiers". These *conversion specifiers* tell `printf` *how* to treat the 0s and 1s of a variable. 

Here is a list of *conversion specifiers*.

```
commonly used conversion specifiers
  %d    int (signed decimal integer) 
  %u    unsigned decimal integer 
  %f    floating point values (fixed notation) - float, double 
  %e    floating point values ("exponential notation" (aka 11.4e+10)) 
  %s    string 
  %c    character  
```

We can use the "%c" conversion specifier to tell `printf` to treat 24 like an ASCII character. Delete the add function and change the code to this.

```c
#include <stdio.h>

int main(void) {
	int variable = 24;

	printf("Hello %c\n", variable);
}
```

Run this code.

It will print out "Hello " with nothing afterwards. This is because the number 24 maps to a character that is apparently invisible? (Go back to Week 0's notes to see what 24 maps to).

Change `variable` to hold 77 instead.

```c
#include <stdio.h>

int main(void) {
	int variable = 77;

	printf("Hello %c\n", variable);
}
```

Run the new code and you will see an uppercase "M" get printed like this `Hello M`.

The "f" in `printf` just means print a "formatted" string. standing for the fact we can replace placeholders (aka *converson specifiers*) with a variable.

We can also have multiple *conversion specifiers*. Change the code to this.

```c
#include <stdio.h>

int main(void) {
	int variable = 77;
    
	char character = 'B';

	printf("Hello %c %c\n", variable, character);
}
```

The `character` variable has a type of `char`. We use single quotes `''` around single characters, and double quotes `""` around *strings* of characters (aka words / phrases).

The type for characters (ASCII strings) is `char`.

# Comments
In Python we can make programmer comments.

In C you use two slashes "//" for comments.

```c
#include <stdio.h>

int main(void) {
	int variable = 77;
  
	char character = 'B';

	// Treat 77 like ASCII character
	printf("Hello %c %c\n", variable, character);
}
```

notice the `// Treat 77 like ASCII character`, this comment will be ignored by the compiler.

# Conditions
Delete all your previous code (or if you don't want to then make a new repl). Now write this code.

```c
#include <stdio.h>

int main(void) {
	int a = 2;
	int b = 3;

	if (a < b) 
	{
		printf("%i is less than %i! \n Wow! thats surprising...\n", a, b);
	}
}
```

The condition for an if statement in C goes inside of parenthesis "()". I think you can figure out what this code is doing by now.

Here are some example of if statements in C.

(example)
```c
	// true
	if (2 <= 3)
	{
		printf("2 is less than or equal to 3 \n");
	}
	else if (2 > 3)
	{
		printf ("2 is greater than 3? Really?! \n");
	}
	else
	{
		printf("At this point... I don't know what your thinking. \n");
	}
```

In C we don't use the "elif" keyword like Python does, we just write "else if".

# Loops
A loop in C runs *while* something is true. The "for" loop in C doesn't "loop over a list" like python. Instead a C `for` loop is a shortcut version of a while loop.

## While loop
```c
#include <stdio.h>

int main(void) 
{
	while (true) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");
	}
}
```

The `true` and `false` types are lowercase in C, whereas in Python they are uppercase, `True` and `False`.

This code won't actually work though! Because C doesn't come with *booleans* (`true` or `false` types) by default! We have to include them! This is because "false" in C is treated as the number zero, while true is any number above zero. The `true` and `false` types in C are actually an "alias" for the number 0 (false), and the number 1 (true).

Include the `stdbool.h` file at the top so we can use the `true` type.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) 
{
	while (true) 
	{
		printf("Hello. Yes, its me again... No, I did not bring pizza. \n \n");
	}
}
```

This will infinitely print the phrase "Hello. Yes, its me again... No, I did not bring pizza."

Although this code does that really fast! Lets make the code wait about 2 seconds every loop.

We need to include a *library* called "unistd.h" (the word "library" just means lots of code written by other people provided through a header file).

```c
#include <stdio.h>
#include <stdbool.h>
#include <unistd.h>

int main(void) 
{
	while (true) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");
		
		sleep(2);
	}
}
```

And lets make the conversation more interesting by adding some questions.

```c
#include <stdio.h>
#include <stdbool.h>
#include <unistd.h>

int main(void) 
{
	printf("Hey! Did you bring pizza?\n");

	while (true) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");
		
		sleep(2);

		printf("Hey! Did you bring pizza?\n");
	}
}
```

Run this code. Pretty cool right? The sleep function makes our code wait 2 seconds.

Now lets prevent the above loop from running forever and limit it to 10 rounds of annoying jabber. We will make a variable called counter and increase it every loop.

```c
#include <stdio.h>
#include <stdbool.h>
#include <unistd.h>

int main(void) 
{
	printf("Hey! Did you bring pizza?\n");

	// counter variable
	int counter = 0;

	// loop only if counter is less than 10
	while (counter < 10) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");

		sleep(2);

		printf("Hey! Did you bring pizza?\n");

		// increase counter
		counter = counter + 1;
	}
}
```

...then check each loop if counter is less than 10. If `counter` becomes bigger than 10 then the loop will stop running.

Run this code. 

# Syntax sugar
It turns out that increasing a number is so common we have "syntax sugar" (aka a shortcut) for doing this!

(example)
```c
counter += 1;
```

The above will increase the counter variable by 1. The above code is identical to our previous method of increasing a variable.

(previous method)
```c
counter = counter + 1;
```

Increasing a number by 1 is soooooo common that we have an even sugarier method.

(sugariest method to increase a number by 1)
```c
counter++;
```

Change your code to use the super sugary way of increasing a variable by 1.

(answer)
```c
#include <stdio.h>
#include <stdbool.h>
#include <unistd.h>

int main(void) 
{
	printf("Hey! Did you bring pizza?\n");

	int counter = 0;

	while (counter < 10) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");

		sleep(2);

		printf("Hey! Did you bring pizza?\n");

		// super sugary way of increasing a variable by 1
		counter++;
	}
}
```

# For loops
Using a while loop to loop a certain number of times can get annoying so we have the "for loop", which is a shortcut for the while loop.

(example)
```c
for (int counter = 0; counter < 10; counter++)
{
	// code goes here
}
```

The above is identical to using a while loop.

(example)
```c
int counter = 0;
while (counter < 10) 
{
	// code goes here

	counter++;
}
```

The only difference between these two pieces of code is that we do all the variable stuff in one line. We also use a semicolon `;` to separate each part.

Change our pizza begging program to use a for loop.

(answer)
```c
#include <stdio.h>
#include <stdbool.h>
#include <unistd.h>

int main(void) 
{
	printf("Hey! Did you bring pizza?\n");

	for (int counter = 0; counter < 10; counter++)
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");

		sleep(2);

		printf("Hey! Did you bring pizza?\n");
	}
}
```

# Casting
Delete all of our old code. Or if you don't like that, you can make a new repl called "casting" (select the C language) and continue by using the new repl.

What will happen if we divide to `int`'s? Since an `int` doesn't support decimal places they will literally just cut off any fractions! So if we did `2 / 3` we won't get `0.6666...` instead we will just get `0`! 

The only types (`int` and `char` are "types") that support decimal places are the `float` and `double` types. A float uses 32 bits, while a double uses 64 bits (obviously with a double we get twice as big numbers).

Lets learn how to deal with dividing two `int`s. Paste in the following code.

```c
#include <stdio.h>

int main(void) 
{
	int a = 2;
	int b = 3;

	float result = a / b;

	printf("%f", result);
}
```

We use the `%f` conversion specifier for printing a float.

Run this code.

Even though the `result` variable is a float it will get a `0.0` from the ints `a` and `b`. This is because when we divide `a` and `b` they give an `int` (and `int`'s don;\'t support decimals!). 

The solution is to convert `a` and `b` to a `float` before we divide them.

Change the code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int a = 2;
	int b = 3;

	float result = (float) a / (float) b;

	printf("%f", result);
}
```

We use two parenthesis around the `float` type in front of the variables `(float) a`. This converts the `a` variable to float. We call this "casting". I can probably think of reasons why they called it "casting", but hey, anyone can come up with an excuse! When we "cast" something `(float) a` we are telling C to treat one type like it was the type we are casting it too.

If you run the new code it will print out.

```
0.666667
```

(We also forgot to add a `\n`, but whatever!)

## Imprecision
You will also notice that our number gets rounded to the 6th place (or 6th column). We can tell `printf` to print out even more numbers after the decimal place to see how "precise" a float can be (eg. how many numbers after the decimal place it can represent using only 32 bits).

Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int a = 2;
	int b = 3;

	float result = (float) a / (float) b;

	printf("%.15f", result);
}
```

Inside of `printf` we change the cpnversion specifer syntax to `%.15f`. The `.15` tells `printf` to print out 15 places after the decimal point, then we put the `f` at the end to tell `printf` it is a `float`.

Run this code. It will print out `0.666666686534882`! "86534882" is definitely not part of `2 / 3`! This is actually a very common problem, and is why games have trouble simulating massive worlds! After a certain point using only 32 bits we can't represetn super precise numbers! So you'll start having precision problems and things... start breaking, or physics don't work! A common solution is to move everything around the player to be in the center of the world constantly, keeping the floats relatively small.

With only 32 bits we can have about 7 (??? is this correct?) columns of numbers. The decimal point slides around between these 7 columns of numbers. 

We can use a `double` to *double* the precision of our number is we want.

Change your code to use a `double` instead of a `float.

(answer)
```c
#include <stdio.h>

int main(void) 
{
	int a = 2;
	int b = 3;

	double result = (double) a / (double) b;

	printf("%.15f", result);
}
```

We also cast our `int` variables to a double! As well as change the `result` variable to a `double`. The conversion specifier for a `double` is the same as a floats.

# Overflow
Now that we've seen the limitations of a float what will happen if we try to make a number that is really big using an `int`?...

```c
#include <stdio.h>

int main(void) 
{
	int a = 2000000000;
	int b = 2000000000;

	printf("%i", a + b);
}
```

If we run this we won't see 4 billion (which is the correct answer)! We hold 2 billion in our `int` variables, but once we add them together we get -294967296!

An `int` can hold negative numbers. We use the first bit of the 32 bits to represent a negative or positive sign, 0 = negative, 1 = positive. 

When we made the number grow past its max (the max is 2147483648 or 2^31, which is 2 to the 31st power), we make the number grow so big it overrides the first bit that is being used for the sign (positive or negative). We also (some how) manage to distord the number!

So, yeah an `int` has limits. We can bypass those limits (to an extent) by using a `long` which uses 64 bits (whereas an `int` uses 32).

# Debugger!
If you have a really complex program that is having problems you can use a Debugger, to *de-bug* the code. (get iit? *de-bug*? Oh, right you don't get it... The term was coined by a person who found a bug in one of Harvards computers. The bug was short-circuiting the computers electircity causing the computer to not work properly!).

Replit has a "Debugger". Open replits debugger.

![replit debugger](/Assets/replit_debugger.png)

Now, Replace your code with the following (or make a new repl if you don't want to delete your work. Then paste this code into the new repl).

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = size; hash > 0; hash--) 
		{
			if (hash <= offset + 1)
			{
				printf("#");
			}
		}

		offset++;

		printf("\n");
	}
}
```

This is the code from one of the tutorials (called "Marios Pyramid") you will do after this lecture.

Don't worry about trying to understand it. For now we'll learn to use adebugger. Add some "breakpoints" to the code by clicking next to the line numbers.

![replit set breakpoints](/Assets/replit_set_breakpoints.gif)

Now click the run button that is INSIDE of the debugger tab.

![replit run debugger](/Assets/replit_run_debugger.png)

Now you can step through your code to see what each variable is at each step / breakpoint! 

![replit debugger step through](/Assets/replit_debugger_step_through.gif)

Use the "next step" arrow to step through each line of code.

![replit debugger next step](/Assets/replit_debugger_next_step.png)

Go directly to one of the breakpoints that you highlighted by using the "next breakpoint" button.

![replit debugger next breakpoint](/Assets/replit_debugger_next_breakpoint.png)

And, at each step you can see what the variables are!

![replit debugger variables](/Assets/replit_debugger_variables.png)

This will help you a LOT when trying to find bugs in your code. "bug" is a logic error in our code. A bug is ***not*** something that keeps us from running the code (Oh yes, bugs are very evil) they are hidden inside of code that works, but isn't doing what we *inteded* it to do.

De-buggers let us *de-bug* the logic in our code by stepping through each line of code, one at a time, and telling us what each variable is at each step.

Although... you won't even be able to click the play button if your code has a syntax error! An example of a syntax error is when you forget to put the ending curly bracket `}` after some code. 

Lets fix some fake syntax errors, to help you become more familair with C. The following code has 3 syntax errors.

(example, 3 syntax errors)
```c
int add(int a, b) {
	return a + b

```

Can you spot them?

The first syntax error is the parameter `b` (parameters are function variables). `b` doesn't have a type! Lets fix that.

(example, 2 syntax errors)
```c
int add(int a, int b) {
	return a + b

```

Now `b` is set to the `int` type.

The second syntax error is that we forgot the ending curly bracket `}`. Lets fix that as well.

(example, 1 syntax errors)
```c
int add(int a, int b) {
	return a + b
}
```

Functions (in C) require that we enclose the code with a starting curly bracket `{`, and an ending curly bracket `}`, like this `{ my code }`. Although C doesn't care where exactly we put the curly brackets and code, as long as it follows the pattern of encolsing the code with the brackets, so the above code could also be this.

(example, different placement of curly brackets)
```c
int add(int a, int b) 
{
	return a + b
}
```

Which is perfectly legal, and won't give us any errors.

There is one final syntax error! We forgot to add a semicolon at the end of `return a + b`!

(example, no syntax errors)
```c
int add(int a, int b) {
	return a + b;
}
```

And now there are no syntax errors!

# The rubber duck debugger
A funny thing that apparently is very common (and I used to use it too when I first started) is called Rubber Duck debugging! (lol)

The (quite funny) idea is that you explain your code to a rubber duck (XD). And this really works! By sitting there explaining what your code is doing to someone (the joke is that you use a rubber duck) that you will find your own mistakes! It really works and even Harvard teaches their students to use it!

If you encounter any errors and can't figure them out feel free to join our discord to get help from me or other students! https://discord.gg/QhqTE4t2tR <- here is the invite link.

# Printf
We can also temporarily use the `printf` function to print out the values of variables (to find out what they are at each step). 

I found myself doing this a lot when trying to understand why my code wasn't working right. We can insert a `printf` in some code to find out why it isn't working right.

(example)
```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = size; hash > 0; hash--) 
		{
            // printing hash number
			printf("%i", hash);

			if (hash <= offset + 1)
			{
				printf("#");
			}
		}

		offset++;

		printf("\n");
	}
}
```

If you run the above code you will see the `hash` variables number get printed next to each hash.

```
54321#
5432#1#
543#2#1#
54#3#2#1#
5#4#3#2#1#
```

If we manually remove the numbers that have no corresponding hash we would see the following.

```
1#
2#1#
3#2#1#
4#3#2#1#
5#4#3#2#1#
```

This could prove to be very useful in understanding how the code works. You could then remove the extra `printf` once you understand what is happening.

And thats it! Have fun!