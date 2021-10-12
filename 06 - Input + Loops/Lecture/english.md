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

# Do while and Scope and Return?
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

Now, how can we check if the person typed "yes" or "no" and not some gibberish? There is a special function that can compare if a string matches another string called `strcmp`, standing for "string compare". To get access to `strcmp` we need to include "string.h".

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

`strcmp` takes in two strings, compares them and returns (gives back) a number. If the words were equal it gives back `0`, so in the if statement we check if the result is `0` (meaning that the strings matched).

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

Our program behaves perfectly! Lets put all this code into a function we can use whenever we want.

![] TODO gif of editing the code by turng main into a "yes" function that returns a bool, then making a new main function above the yes function.

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

The `yes` function returns (aka gives back) a `bool` type ("true" or "false"), so we put `bool` in front of the functions name.

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
	else // the user typed "no"
	{
		return false;
	}
}
```

Now we can use the `yes` function whenever we want! 

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
		printf("Thank goodness! XD")
	}
	else
	{
		printf("That's kinda... weird");
	}
}

// ... snip ...
```

I used `// ... snip ...` to show that I am focusing on the `main` function, I did NOT delete `yes()`! I am simply focusing on the relevant parts of the code, without having to show you everything (plus you already know what the `yes` function looks like/does, so theres no need to repeat myself!)

This is often called "abstraction", which is where we write some code to do something for us once, and then don't have to worry about how it works, but just use it later.

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

And thats it for today!