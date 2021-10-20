Last week we talked about how computers represent data and instructions using only two symbols 0 and 1, representing the millions and millions of bits in our computer.

We are now going to learn a new language called C. This language is a *compiled* language (whereas Python was *interpreted*). 

Previously, in Python, our text based code was getting read by a program called an "interpreter", that interpreter "interprets" our text written code and runs it as instructions for your computers processor. So Python doesn't have to directly deal with memory addresses (the interpreter takes care of that for us), instead it's more like a "scripting language", which means it is much easier and simpler to code in.

C is still an ASCII text based programming language, but C code gets converted into 0s and 1s instructions (into a "program file") for our processor (by a program called a "compiler"), which makes C VERY fast.

C is actually what the Python "interpreter" program was made with!

Remember how functions work in Python?

```py
# define "main"
def main():
	print("hello world")
	print("This is some code inside of the 'main' function")

main() # run code inside of "main"
```

In C there is a function that gets run automatically, but it is the only function that will get called ("called" means "the code was *called upon* so it **did** its instructions). This function is called the "main" function.

Any code that we want to run (including our own functions) have to happen inside of the "main" function. This gives all computers a unifide way to have a "starting point" for programs.

Lets write a real program in C, that will run directly on a processor! Go to https://replit.com/ and make a new replit.

This time select C as the programming language and name the the project "hello c", then click "create repl".

There should already be a file called "main.c" with the following code.

(example)
```c
#include <stdio.h>

int main(void) {
	printf("Hello World\n");
	return 0;
}
```

Delete some of the code so that the it looks like this. 

(answer)
```c
int main(void) {
	
}
```

Don't run this code yet, as it won't do anything! The above code is the "main" function (in C), and is the program *starting point* that almost all computers will use.

The word `int` in front of the function, tells C that `main` gives back an "integer" number ("integers" don't have decimal places). This is different from Python where we use "def" for defining a function. You'll get used to it.

You will see the word `void` in the functions input (in the parenthesis). In C we have to tell the computer that the function *doesn't* take any input, which is what the `void` keyword is for. `void` stands for "nothing". From what I can tell the word `void` exists thanks to C's weird grammer/syntax (literrally! New languages (especially interpreted ones) don't even have the `void` keyword).

Python automatically assumed you didn't want input if you don't put anything in the parenthesis "()".

You will notice the curly brackets "{}". This is what C uses instead of Python's colon ":" symbol.

(example)
```c
int main(void) {
	// code goes here
}
```
The brackets tell us what is "inside of" a function. In Python we had to use TAB to move code over, telling us what code was inside of a function or loop, or if statement.

C doesn't care where you put the curly brackets. You can even write all your code in one line! (As long the code is inside of the curly brackets)

(example)
```c
int main(void) { /* code goes here */ }
```

Programmer comments in C use 2 slashes `//`. Although to make a comment with a start and end we use `/*` to start the comment and we use `*/` to end the comment (as you see in the above code).

Now lets make our own function in C. It will add 2 numbers together. Make the following function under `main`.

(add the following code)
```c
// ... main function (excluded for shortness of reading)

int add(int a, int b) {
	return a + b
}
```

We make a function called `add`. We tell C that the `add` function *returns* (aka gives back) an `int` (integer) by putting `int` in front of `add` (the functions name). We take as input two `int` variables, `a` and `b`.

In C we have to always know the *type*. A *type* tells C how to treat the 0s and 1s. "Is this a number? Is this a Unicode or ASCII character?". A type also tells C how many bytes of memory the "type" uses. For example the `int` type takes exactly 4 bytes (32 bits) of memory.

We tell the computer this is an integer (aka number) by putting the `int` *type* in front of the function's `a` and `b` parameters ("parameter" means "variable for a function").

### Variables
Inside of `main` we will use the `add` function to add 2 numbers together.

(edit your code to the following)
```c
int main(void) {
	// add 2 umbers together
	add(12, 12)
}

int add(int a, int b) {
	return a + b
}
```

... and store what `add` returns (gives back) in a variable called "result"...

(edit your code to the following)
```c
int main(void) {
	int result = add(12, 12)
}

int add(int a, int b) {
	return a + b
}
```

You'll notice the `result` variable has a "type" of `int` as well. C won't automatically figure out that the `result` variable should be an `int` (since the `add` function gives back an `int`, C *could* figure it out).

There is one last thing we have to do before we can run this code.

In C, whenever we write a line of code we have to end it with a semicolon `;` <- This is how C tells one line of code apart from another.

(edit your code to the following)
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

Most "text editors" (Microsoft Word, Google Docs) don't show you the newline symbol `\n`, they just make a newline.

So yeah, C makes us use a semicolon `;` so it can tell lines of code apart.

Although for functions we don't have to add a semicolon at the end

(example, uneccessary semicolon)
```c
int add(int a, int b) {
	return a + b;
}; // semicolon not needed!
```

...since it is easy to tell when the function ends by just looking at the ending curly bracket "}". 

Sadly, our code (still!) won't work because C reads code from top to bottom. So when C reads the code inside of the `main` function it doesn't know that the `add` function exists!

(example)
```c
int main(void) {
	int result = add(12, 12); // what is `add`?
}
```

...and honestly we wouldn't know where or what `add` was unless we kept scrolling down to find it.

Python took care of this for us, while C won't.

So we just have to put the `add` function above `main`. Change the code so that `add` is above `main`.

(change your code to the following)
```c
int add(int a, int b) {
	return a + b;
}

int main(void) {
	int variable = add(12, 12);
}
```

Now you can run this code! (Although it won't print anything to the console... yet)

There is a way to put a function below main. You just have to put a function "hint" above main.

(example)
```c
int add(int a, int b); // function hint

int main(void) {
	int variable = add(12, 12);
}

// actual function
int add(int a, int b) {
	return a + b;
}
```

"function hints" are called "prototypes" (don't ask me who came up with that name)

We have to put a semicolon `;` at the end of the functions *prototype* because there are no curly brackets in a prototype, just a function name and its parameters (function variables).

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

The number `main` returns is an integer `int` (you already know this). The number represents an "error code". Returning `0` means success (aka no error). Returning `1` (or any number besides `0`) means there was an error! But since we don't *have to* return an error code we won't bother with it.

Why does `0` represent no error? Well there are a million things that things could go wrong in a program, but there is only 1 way that the program will succeed, so we just designated `0` as the number for success.

Nothing gets printed to the console! Lets work on that.

# Printing + including
The `print` function doesn't come builtin in C. So we have to "include" code written by someone else that figures out the specific Operating SYstem instructions to get our computer to print something (an Operating System is a Filesystem program, and a bunch of other code for managing apps (eg. Windows, Android, iOS, Linux)).

(edit your code to include `stdio.h`)
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

Compiler directives after the hash "#" are things the compiler "pre-processes", which means when we *include* this file, the "compiler" program (which will convert our C code into 0s and 1s instructions for the processor) somehow will "include" the code from the "stdio.h" file.

We surround the `stdio.h` file with greater than symbol `>` and the less than symbol `<`, because... well the father/original maker of C just designed C that way.

"std" is short for "standard", and "io" is short for "input output", so we get "include standard input output code".

The ".h" means it is a C "header" file. Headers files are normal C code except the code has already been turned into 0s and 1s! (This way the compiler doesn't have to also compile/convert all the *headers* we include into 0s and 1s, and can just "link" the already compiled code with ours in the end). The code in a "header" file is just a bunch of "function hints" to functions that are in the binary (already compiled/converted to 0s and 1s) code file.

Where is the "stdio.h" code in the computer? The "stdio.h" code is used so often it comes builtin with most computers's. The compiler for your computer will usually set itself up to find the "stdio.h" file. By default Replit already has a compiler set up for us for converting our C code into 0s and 1s instructions.

(You can also include regular `.c` files by using double quotes around the name of the file like this `#include "mycode.c"`)

Now that we've included the standard input output *header* code, we can send output to the console using its `printf` function (`printf` meaning "print formatted").

(edit your code to use `printf`)
```c
// ... irrelevant code (not showing code for "include" or add function to make this snippet faster to read)

int main(void) {
	int result = add(12, 12);

	// print something
	printf("Hello, world");
}
```

You notice we put a comment above the `main` function `// ... irrelevant code` <- this does not mean you should delete the `add` function that we put above main (or the `#include <stdio.h>` code)! Instead we are just showing you the code that has changed so you can edit your code (rather than showing you all the code again, and you having to figure what parts of the code have changed).

Now run your edited code. You will see "Hello world" get printed.

![replit print hello world](/Assets/replit_print_hello_world.png)

But the console didn't make a newline after "Hello world"! So we have to add this manually ourselves. (Again, Python added "\n" for us in its `print` function).

(edit your `printf` to have a `\n` symbol at the end)
```c
// ... irrelevant code

int main(void) {
	int variable = add(12, 12);

	printf("Hello, world\n");
}
```

Now a newline will be added after the "Hello, world" string (remember, we call words or phrases enclosed with double quotes `""` *strings*).

![replit print hello world with newline](/Assets/replit_print_hello_world_2.png)

# Errors?
If you get a whole bunch of errors when running some code... Just scroll up to the first error at the top in the console, since the rest of the errors are the *compiler* (aka program that converts code to binary instructions) getting confused from the first error.

# Printing variables
How can we print a variable? In Python it was easy.

(example, python)
```py
name = "Jafly"
print(name)
```

To print variables in C using `printf` we have to tell it the *type* of the variable to print.

In a `printf` you use the percent symbol `%` followed by a letter for the type. In this case our variable is an `int`, so in `printf` we write `%i`. "%i" stands for the `int` type.

(edit your `printf` to look like the following)
```c
// ... irrelevant code (DON'T delete the add function!)

int main(void) {
	int result = add(12, 12);

	printf("the number is: %i \n", result);
}
```

The `%i` is a placeholder, and will get replaced by the `result` variable.

Run this code. You will see that the `%i` in the string gets replaced by 24 (we also make sure to add a newline `\n`).

We refer to the percent sign "%" *placeholders / types* for `printf` as "conversion specifiers". These *conversion specifiers* tell `printf` *how* to treat the 0s and 1s of a variable, as well as how many bytes that variable uses in memory.

Here is a list of *conversion specifiers*.

```
commonly used conversion specifiers:

  %d    int (signed (positive and negative) decimal integer) 
  %u    unsigned (only positive) decimal integer 
  %f    floating point values (fixed notation) - float, double 
  %e    floating point values ("exponential notation" (aka 11.4e+10)) 
  %s    string 
  %c    single ASCII character  
```

We can use the "%c" conversion specifier to tell `printf` to treat 24 like an ASCII character. 

(delete the add function and change the code to this)
```c
#include <stdio.h>

int main(void) {
	int variable = 24;

	printf("Hello %c\n", variable);
}
```

Run this code.

It will print out "Hello " with nothing afterwards! This is because the number 24 maps to a character that represent the "Cancel" key! The Cancel key on your keyboard doesn't really have a symbol! (Go back to Fundamentals Notes to see what 24 maps to in the ASCII mappings).

(change `variable` to hold 77 instead)
```c
#include <stdio.h>

int main(void) {
	int variable = 77;

	printf("Hello %c\n", variable);
}
```

Run the new code and you will see an uppercase "M" get printed like this `Hello M`.

The "f" in `printf` just means print a "formatted" string. standing for the fact we can replace placeholders (aka *converson specifiers*) with a variable.

We can also have multiple *conversion specifiers*. 

(edit your code to have a new variable called "character", then also print the "character" variable)
```c
#include <stdio.h>

int main(void) {
	int variable = 77;
    
	char character = 'B';

	printf("Hello %c %c\n", variable, character);
}
```

The `character` variable has a type of `char` which is the ASCII type. We use single quotes `''` around ASCII characters (whereas we use double quotes `""` around *strings* of ASCII characters).

Run this code to see what it prints.

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

The condition for an if statement in C goes inside of parenthesis "()". Here we are saying `if a < b then { /* do code */ }`. 

We then print the `a` and `b` variables inside of a phrase using conversion specifiers.

Here are some example of "if logic" in C.

(example)
```c
	// true
	if (2 <= 3)
	{
		printf("2 is less than or equal to 3 \n");
	}
	// false
	else if (2 > 3)
	{
		printf ("2 is greater than 3? Really?! \n");
	}
	// default to this if nothing else worked
	else
	{
		printf("At this point... I don't know what your thinking. \n");
	}
```

In C we don't use the "elif" keyword like Python does, we just write "else if" <- which makes much more sense to me.

# Loops
A loop in C runs *while* something is true. The "for" loop in C doesn't "loop over a list" like python. Instead a C `for` loop is a shortcut version of a while loop.

# While loop

(delete everything inside of main, and change your code to the following)
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

The `true` and `false` types are lowercase in C, whereas in Python they are uppercase like `True` and `False`.

This code won't actually work though! Because C doesn't come with *booleans* (`true` or `false` types) by default! We have to include them! This is because "false" in C is treated as the number zero, while true is any number above zero. The `true` and `false` types in C are actually an "alias" for the number 0 (false), and the number 1 (true).

Include the `stdbool.h` file at the top so we can use the `true` type (bool is short for "boolean". The name came from the man who invented the idea (apprently someone had to come up with the idea of "true" or "false). His name was "George Bool").

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

If you looked at the code from `stdbool.h` then you would find something like this...

(example)
```c
#define true 1

#define false 0
```

`#define` is a compiler directive as well, so it literally will replace our use of the word `true` with the number value of 1.

Code written in C runs directly on the processor so it is waaaaay faster than Python. Python code runs on an "interpreter" program so its much more flexible, yet slower, than C.

Now lets prevent the above loop from running forever and limit it to 10 rounds of annoying jabber. We will make a variable called counter and increase it every loop.

(edit your code to the following)
```c
#include <stdio.h>
#include <stdbool.h>

int main(void) 
{
	// counter variable
	int counter = 0;

	// (1) loop only if counter is less than 10
	while (counter < 10) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");

		// increase counter
		counter = counter + 1;
	}
}
```

(1) ...then check each loop if counter is less than 10. If `counter` becomes bigger than 10 (since we increase it each loop) then the loop will stop running, and our program will finish running.

Run this code. You should see the phrase "Hello. Yes, its me again... No I did not bring pizza." get printed 10 times.

# Syntax sugar
It turns out that increasing a number is so common we have "syntax sugar" (AKA a shortcut) for doing this!

(example)
```c
counter += 2;
```

The above will increase the counter variable by 2. The above code is identical to our previous method of increasing a variable.

(previous method)
```c
counter = counter + 1;
```

Although just wanting to increase a number by 1, is soooooo common that we have an even sugarier method.

(sugariest method to increase a number by 1)
```c
counter++;
```

Change your code to use the super sugary way of increasing a variable by 1.

(answer)
```c
#include <stdio.h>
#include <stdbool.h>

int main(void) 
{
	int counter = 0;

	while (counter < 10) 
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");

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

```
		  semicolon to separate
				   \
for (int counter = 0; counter < 10; counter++)
```

Change our pizza begging program to use a for loop.

(answer)
```c
#include <stdio.h>
#include <stdbool.h>

int main(void) 
{
	for (int counter = 0; counter < 10; counter++)
	{
		printf("Hello. Yes, its me again... No I did not bring pizza. \n \n");
	}
}
```

Now make sure to run our super sugary for loop!

# Casting
Delete all of our old code. Or if you don't like that, you can make a new repl called "casting" (select the C language) and continue by using the new repl.

What will happen if we divide to `int`'s? Since an `int` doesn't support decimal places we will literally just cut off any fractions! So if we did `2 / 3` we won't get `0.6666...` instead we will just get `0`! 

The only types (`int` and `char` are "types") that support decimal places are the `float` and `double` types. A float uses 32 bits, while a double uses 64 bits (obviously with a double we get twice as big numbers).

Lets learn how to deal with dividing two `int`s. Write in the following code.

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

We use the `%f` conversion specifier for printing a float (`float` supports decimal places `0.66666`)

Run this code.

Even though the `result` variable is a float it will get a `0` from the ints `a` and `b`. This is because when we divide `a` and `b` they gave us an `int` (and `int`'s don't support decimals!). The Rust programming language (a new "safer" programming language, would have wraned us, and prevented us from making this simple mistake).

The solution is to convert `a` and `b` to a `float` before we divide them.

(edit the `result` variable code to the following)
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

We use two parenthesis around the `float` type in front of the variables -> `(float) a` <- This converts the `a` variable to the `float` type. We call this "casting". Again I don't know why they called it "casting" because its just "converting" one type to another. Although in C, when we "cast" one type to another, we literally just treat the 0s and 1s as if they were the type we wanted (so it can be kinda dangerous, cause we can ignore some parts of the 0s and 1s, if say the types were different sizes, giving us wild numbers).

If you run the new code it will print out.

```
0.666667
```

(We also forgot to add a `\n`, but whatever!)

## Imprecision
You will also notice that our number gets rounded to the 6th place (or 6th column). We can tell `printf` to print out even more numbers after the decimal place to see how "precise" a float can be (eg. how many numbers after the decimal place it can represent using only 32 bits).

(edit the `printf` conversion specifier)
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

Inside of `printf` we change the conversion specifer syntax to `%.15f`. The `.15` tells `printf` to print out 15 places after the decimal point, then we put the `f` at the end to tell `printf` it is a `float`.

Run this code. It will print out `0.666666686534882`! "...86534882" is definitely not part of `2 / 3`! This is actually a very common problem, and is why games have trouble simulating massive worlds! After a certain point using only 32 bits we can't represent super precise numbers like `0.66666666666666666666666...`! So you'll start having precision problems and things... start breaking, or physics don't work.

With only 32 bits we can have about 7 (??? is this correct?) columns of numbers. The decimal point slides around between these 7 columns of numbers. 

We can use a `double` to *double* the precision of our number if we want.

Change your code to use `double`'s instead of `float`'s.

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

We cast our `int` variables to a double, as well as change the `result` variable to a `double`. 

The conversion specifier in `printf` for a `double` is the same as a floats.

Now run this code! You should see a much larger (and more "precise") number.

# Overflow
Now that we've seen the limitations of a float what will happen if we try to make a number that is really big using an `int`?...

(example)
```c
#include <stdio.h>

int main(void) 
{
	int a = 2000000000;
	int b = 2000000000;

	printf("%i", a + b);
}
```

We hold 2 billion in our `int` variables, but once we add them together we should get 4 billion, but instead we get -294967296!

THis reason for this madness is that an `int` can hold negative numbers. We use the first bit of the 32 bits to represent a negative or positive sign (0 = negative, 1 = positive). So if we have `0001` since the first bit is zero we get `-1`, but if we had `1001` we would get `+1` since the first bit (a 0 or 1) is 1 which represents positive.

When we made the number grow past its max (the max is 2147483648 or 2^31, which is 2 to the 31st power), we make the number grow so big it overrides the first bit that is being used for the sign (positive or negative). So that is why the number we got is negative. 

As to why the number became `294967296`, that is the part of our resulting number that was able to fit into the 32 bits of our integer.

So, yeah an `int` has limits. We can bypass those limits (to an extent) by using a `long` type which uses 64 bits giving us twice as large of a number.

# Debugger!
If you have a really complex program that is having problems you can use a Debugger, to *de-bug* the code. (get it? *de-bug*? Oh, right you don't get it... The term was coined by a person who found an actual bug in one of Harvards computers! The bug was short-circuiting the computers electircity causing the computer to not work properly!).

Replit has a "Debugger". Open replits debugger.

![replit debugger](/Assets/replit_debugger.png)

Now, Replace your code with the following (or make a new repl if you don't want to delete your work. Then paste this code into the new repl).

```c
#include <stdio.h>

int main(void) 
{
	int size = 4;
	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = 0; hash < size; hash++)
		{
			if (hash <= offset)
			{
				printf("#");
			}
		}

		printf("\n");
		offset++;
	}
}
```

This is the code from one of the tutorials (called "Marios Pyramid") you will do after this lecture.

Don't worry about trying to understand it. For now we'll learn to use a debugger. Add some "breakpoints" to the code by clicking next to the line numbers.

![replit set breakpoints](/Assets/replit_set_breakpoints.gif)

Now click the run button that is INSIDE of the debugger tab.

![replit run debugger](/Assets/replit_run_debugger.png)

Now you can step through your code to see what each variable is at each step!

![replit debugger step through](/Assets/replit_debugger_step_through.gif)

Use the "next step" arrow to step through each line of code.

![replit debugger next step](/Assets/replit_debugger_next_step.png)

Go directly to one of the breakpoints that you set by using the "next breakpoint" button.

![replit debugger next breakpoint](/Assets/replit_debugger_next_breakpoint.png)

And, at each step you can see what the variables are!

![replit debugger variables](/Assets/replit_debugger_variables.png)

This will help you a LOT when trying to find bugs in your code because you will be able to see what your code is doing at each step, and what the variables are at each step. A "bug" is a logic error in our code. A bug is ***not*** something that keeps us from running the code (Oh yes, bugs are very evil) they are hidden inside of code that runs when we click the run button, but the code isn't doing what we *intended* it to do.

De-buggers let us *de-bug* the logic in our code by stepping through each line of code, one at a time, and telling us what each variable is at each step.

Although... you won't even be able to click the play button if your code has a syntax error! An example of a syntax error is when you forget to put the ending curly bracket `}` after some code. 

Lets fix some fake syntax errors (in an example), to help you become more familiar with C. The following code has 3 syntax errors.

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

"The more you understand a problem, the more obvious the solutions becomes... Lol, I spend so much time analyzing everything." -- Me (Abdiel Lopez)

# The rubber duck debugger
A funny thing that apparently is very common (and I used to use it too when I first started) is called Rubber Duck debugging! (lol)

The (quite funny) idea is that you explain your code to a rubber duck (XD). And this really works! By sitting there explaining what your code is doing to someone (the joke is that you use a rubber duck) that you will find your own mistakes! It really works and even Harvard teaches their students to use it!

If you encounter any errors and can't figure them out, take some time to explain your code and what it is doing to a rubber duck (or a teddy bear). Feel free to join our discord to get help from me or other students! https://discord.gg/QhqTE4t2tR <- here is the invite link.

# Printf
We can also temporarily use the `printf` function to print out the values of variables (to find out what they are at each step). 

I found myself doing this a lot when trying to understand why my code wasn't working right (and I don't have access to a debugger to help me).

 We can insert a `printf` in some code to find out why it isn't working right.

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
            // printing current hash number
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

If we manually remove the numbers that have no corresponding hash, we could find what the hash variable is when we print the hash symbol `#`.

```
1#
2#1#
3#2#1#
4#3#2#1#
5#4#3#2#1#
```

This could prove to be very useful in understanding how the code works. You could then remove the extra `printf` once you understand what is happening.

And thats it! Have fun! Now go make Marios Pyramid!