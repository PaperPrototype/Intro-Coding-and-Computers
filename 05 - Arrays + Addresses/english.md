In C we don't have the idea of "lists" instead we have "arrays". 

Arrays are different than Python lists because once we set their size, we can't change that size!

Make a new repl. Select the C programming language. Call the project "arrays".

In the shell make a new file called "array.c" using `touch`.

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

The `num` variable is the number that gets increased each loop. We loop a total of 5 times, and use the `num` variable to offset into the `hello` array (and access each item)! You'll notice it is very convenient that out `for` loop starts counting at zero, atarting the first memory offset at 0 will get us the first itme (if we had started counting at 1 then we would have skipped the first item).

Traditionally the `num` variable would have been called `index` (or just `i`). This is partly connected to the terminology. Most programmers would say that we are "indexing into the array", and that `num` is the "index".

This is essentially yhe same thing as saying "offsettig into the array", and that `num` os the offset number we use each loop.

For the sake of tradition (and that fact that many programmers are already using this terminology), lets change our code to reflect this traditional way of naming things.

(change `num` to be called `index`)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// loop 5 times
	for (int index = 0; index < 5; index++)
	{
		// print single item in hello array at offset
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Compile the above code using `make string`, and run it using `./string`.

# Design
Having to manually set the number of times to loop (which is currently 5) is kind of a bad design. Say we accidentally set the number of times to loop to 10 (instead of 5)! At some point you might start having "buffer overflow" errors. "buffer overflow" Basically we have "overflowed" and accessed memory outside of the "buffer"/array of memory we are allowed to access.

Instead of manually setting the loop to loop 5 times we can check "while the current character isn't `\0`" (since C automatically puts a null termintating character `\0` at the end of a string).

(example)
```c
// while current character isn't '\0'
while hello[index] != '\0'
```

Which will stop the loop once it finds the null character `\0`.

(change your code to the following)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	int index = 0;
	while (hello[index] != '\0')
	{
		printf("%c", hello[index]);

		// increase index
		index++;
	}

	printf("\n");
}
```

Challenge time! Try to change the above `while` loop to a `for` loop! The answer is below if you get stuck, but try and do it without looking at the answer below!

(answer)
```c
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	for (int index = 0; hello[index] != '\0'; index++)
	{
		printf("%c", hello[index]);
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

	for (int index = 0; hello[index] != '\0'; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Now we can replace the condition (aka check for true or false) in the loop with `while index < strlen(hello)`.

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// loop "strlen" times
	for (int index = 0; index < strlen(hello); index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Which says "loop "string length" amount of times".

Every time we loop we use the `strlen` function to check "if current index is less than length of hello".

# Design 3
You might realize at some point that he strlen function has to count all the stuff inside of the `hello` variable, every single loop, just to check `while index is less than strlen of hello`! This is not efficient!

We can quickly fix the terrible design of this by making a variable that will hold the "length" number from `strlen`, then use that variable in the check each loop (instead of recalculating `strlen` every loop, we run it once, and then use the resulting number as many times as we want).

(change your code to the following)
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Hello";

	// create length variable
	int length = strlen(hello);

	for (int index = 0; index < length; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Tada! 

Now go ahead an change the word inside of the `hello` array! And the loop will automatically loop the correct number of times and print out each character!

(change your code to the following (or write a sentence of your own in the `hello` array))
```c
#include <string.h>
#include <stdio.h>

int main(void) 
{
	char hello[] = "Helloooo everyyybody! I really shoudln't be running with these massive golden scissors in my hands! -- Cloudy with a Chance of Meatballs";

	// create length variable
	int length = strlen(hello);

	for (int index = 0; index < length; index++)
	{
		printf("%c", hello[index]);
	}

	printf("\n");
}
```

Compile and run this code using the shell!

(command)
```
make string
```

(command)
```
./string
```

# Constants
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

Also it is a tradition to uppercase a `const` variable to help programmers *know* it is a `const` (without having to go and look at the code that "made" the variable).

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

It might feel a bit odd that we UPPERCASE the entire word... you should've seen BASIC (BASIC was an old programming language).

(simple BASIC program)
```basic
ARRAY c
c[1] = "red"
c[2] = "blue"
c[3] = "yellow"
c[4] = "cyan"
c[5] = "blue"
c[6] = "magenta"
REM start draw loop
a = rand(50) - 1
b = rand(50) - 1
PLOT a, b, c[rand(6)]
PAUSE 10
GOTO 9
```

Anyhow...

Compile our code usign `make string` and run it using `./string` in the shell.

Now stare at this marvelous beautiful, fantastic yet... pointless, program.

# Addresses
An array "variable" is technically an address to the first byte of memory in the array (if you've forgotten, go back to section 05). What if we only want an address to a single item? In that case we can use a star symbol `*` after the type.

(example)
```c
#include <stdio.h>

int main(void) {
	int* my_address = 12;
}
```

Here we have made a variable of the type `int*` that is an *address to* 12.

If we want to print out `12` then we need to "go to" the address. To "go to" an address type we put (again) the star symbol in front of the address variable `*my_address`. This is the same as going to a specific item in an array `my_array[0]`.

(example)
```c
#include <stdio.h>

int main(void) {
	int* my_address = 12;

	printf("%i", *my_address);
}
```

The above would print out the number 12.

# Void
Since an address variable simply "points" to the first byte of memory of something we don't have to tell C the type! We can just make a plain old address to the first byte!

Make a new file using touch called "pointer.c".

(command)
```
touch pointer.c
```

Open pointer.c using the files window.

(change the code in pointer.c to the following)
```c
#include <stdio.h>

int main(void) 
{
	// "void" address
	void* hello = "Hello";

	//             convert to a char array using "char*"
	printf("%s \n", (char*) hello);
}
```

This code makes a plain address without needing to know the type! You will also notice that making an array variable using two brackets `myArray[] = "Hello"` is (in some ways) no different than just using an address `void* myArray = "Hello"` since internally both are just addresses to the first byte of the array. In fact you could do just that if you wanted and it would work just as well.

If your thinking just doing `* myAddress = "Hello"` to make an address variable then your intuition is right. Although that code makes sense it wouldn't be valid C code, since C's "grammer" requires that we put `void` to represent "no type".

C has to know how to treat the 0s and 1s of something at an address to "use" the value. In the code above we tell C the "type" at the address by *casting* (treating the 0s and 1s) at the address, to a `char*` address, hence `(char*)`.

If we skipped *casting* the address to a `char*` then C would offset by 1 byte (by default) when we use the square brackets `[]` (by default C offsets by 1 byte (8 bits) since that is the smallest individual piece of memory we can access. In this case a `char` uses 1 byte anyways, so it would still work fine).

Types also tell us how many bytes *after the first byte* are part of the value. This is necessary since an address just points to the first byte, and we don't want to access bytes outside of the type.

Types also help later when compiling to Assembly, since there are special `add` instructions for float's (SIMD (Single Instruction Multiple Data) is one example, which can add up to 8 numbers in a single instruction, giving us up to 8x speed ups!).