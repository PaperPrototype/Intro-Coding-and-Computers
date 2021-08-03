Last week we talked about how computers represent data and instructions using only two symbols 0 and 1, representing the millions and millions of bits in our computer.

We are now going to learn a new language called C. This language is a *compiled* language (whereas Python was *interpreted*). This just means our code is written as text that gets "compiled" into a program file of 0 and 1 instructions for the CPU.

Remember how functions work in Python?

```py
def main():
	# put code here
	print("hello world")

main() # run the code
```

In C there is a function that gets called automatically, except here's the catch, it is the only function that gets called! Any code that we want to run, including our own functions, have to go inside of the "main" function. This gives all computers a unifide way to have a "starting point" for where to run your program.

Lets write this "main" function. Go to https://replit.com/ and make a new replit.

(if you don't see the "New replit" button, it is probably hidden. To find it, look in the top left corner of the website, you should see three lines, click those. Then you should see a blue button)

This time select C as the programming language. Name the the project "hello c", then click "create repl".

There should already be a file called "main.c". In it you should see the following.

```c
#include <stdio.h>

int main(void) {
	printf("Hello World\n");
	return 0;
}
```

Delete everything except for the function called "main" so that the code looks like this. 

```c
int main(void) {
	// code goes here
}
```

Don't run this code yet, as it won't do anything! (if replit did not give you this code automatically then just copy paste the above). The above code is the "main" function in C, and is the program *starting point* that most computers use.

The word "int" in front of the function, tells C that `main` gives back an integer. This is different from Python where we use "def" for defining a function. Don't worry you'll get used to it.

You will see the word "void" inside of the functions input (the parenthesis). In C we have to tell the computer that the function *doesn't* take any input, which is what the `void` keyword is for.

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

The `result` variable has to have a type of `int` as well. C doesn't automatically figure out that the `result` variable should be an `int` 

(it could figure it out since the `add` function returns an `int`, but the makers of C wanted to make it more *clear* as to what excaclty a variable is)

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

We use a hash symbol "#" followed by "include". "include" is called a "command".

Commands after the hash "#" are things the compiler "pre-processes", which means when we *include* this file, the compiler literally replaces `#include <stdio.h>` with the code from the "stdio.h" file.

(We will get to what a compiler is later, just know it converts text based code into `0`s and `1`s instructions for the computers processor)

"std" is short for "standard", and "io" is short for "input output", so we get "include standard input output code". 

The ".h" means it is a C "header" file. Headers files are normal C code except the code has already been turned into 0s and 1s! (This way the compiler doesn't have to compile all the *headers* we include and can just "link" them all to together in a stage called "linking"). The code in a header file is just a bunch of "function hints" to functions that are in the binary (0s and 1s) code file.

Where is the "stdio.h" code in the computer? The "stdio.h" code is used so often it comes builtin with the compiler (aka when you download a compiler it also downloads the stdio.h file).

(You can also include `.c` files by using double quotes around the name of the file like this `#include "mycode.c")

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

# Debugger!
But... if you have a really complex program use can use a Debugger! 

Open the debugger 

If you encounter any errors and can't figure them out feel free to join our discord to get help https://discord.gg/QhqTE4t2tR <- here is the invite link.

# Printing variables
How can we print a variable?

In C we have to declare the type a variable holds (aka `int result = 12;`). To print variabkes using `printf` we also have to tell it the *type* of the variable.

In `printf` you use the percent symbol `%` followed by a letter. In this case our variable is an `int`, so in `printf` we write `%i` which stands for the `int` type.

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

The `%i` is a placeholder (with a type), and will get replaced by the `result` variable.

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

We can use the "%c" conversion specifier to tell `printf` to treat 24 like an ASCII character. Delete the add function and change ht code to this.

```c
#include <stdio.h>

int main(void) {
  int variable = 24;

  printf("Hello %c\n", variable);
}
```

Run this code.

It will print out "Hello " with nothing afterwards. This is because the number 24 maps to a character that is apparently invisible? (Go back to Week 0's notes to see what 24 maps to).

Change `variable` to hold 77. Run the new code and you will see an uppercase "M" get printed like this `Hello M`.

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

We told `printf` to treat the `character` variable as a character, so we got `B`.

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

TODO
- numbers overflow
