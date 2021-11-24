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

(change your code to the following (or write a sentence of your own in the `hello` array))
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
Array variables are an address to the first byte of memory in an array. But what if we only want an address to a single item? In that case we can use a star symbol `*` after the type.

(example)
```c
#include <stdio.h>

int main(void) {
	int* my_address = 12;
}
```

In this case we have made a variable of the type `int*` that holds an *address* to 12.

# Swap
Make a new file using touch called "swap.c".

(command)
```
touch swap.c
```

Open it using the files window.

Lets say we have to variables `a` and `b`. We want to swap the numbers they hold.

(change your code to the following)
```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);
}
```

Ok, so we have 2 variables, and we print them out. Lets imagine each variable is a cup holding its contents.

![swap cups](/Assets/swap_cups.png)

To be able to swap the "water" (stuff inside `a` and `b`) we need a second cup called "c".

![swap cups need c](/Assets/swap_cups_need_c.png)

Then we can put the stuff from `a` into `c`.

![swap cups a into c](/Assets/swap_cups_a_into_c.png)

Then we can pour `b` into `a`.

![swap cups b into a](/Assets/swap_cups_b_into_a.png)

And finally we can put `c` into `b`.

![swap cups final](/Assets/swap_cups_c_into_b.png)

Yay! We hav e now successfully swapped the contents of `a` and `b`.

Lets turn this into real code.

(make a `void` function under main called "swap" (`void` means it doesn't give anything back))
```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);
}

// swap function
void swap(int* swap1, int* swap2) {
	// code for swapping
}
```

`swap` takes in 2 addresses (of the type `int`) code named `swap1` and `swap2`. We haven't filled in the code for `swap` just yet. But lets pretend to use it in the "main" function.

(change your code to the following)
```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);

	// use swap
	swap(a, b);

	// print out "a" and "b" after swap
	printf("a is: %i, b is: %i \n", a, b);
}

void swap(int* swap1, int* swap2) {
	// code for swapping
}
```

We use `swap` in main, and give it our two variables `a` and `b`, then print out `a` and `b` after calling (using) the `swap` function... except there is a problem. `a` and `b` are *NOT* address variables (the type `int*` is an address to an integer), and the `swap` function is expecting 2 `int*`.

To get an address out of a normal variable we have to put the ampersan symbol `&` in front of it. This changes our code to the following.

(edit your code to the following)
```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);

	// get addresses of "a" and "b"
	swap(&a, &b);

	printf("a is: %i, b is: %i \n", a, b);
}

// ... snip ...
```

(I put the comment `// ... snip ...` this does NOT mean you should delete the `swap` function, I am just showing the relevant parts of the code that actually need to change)

Now we are giving `swap` what it is expecting, 2 addresses to 2 numbers.

One last thing is that we need to put a function hint for `swap` above `main`.

(add a function hint above main)
```c
#include <stdio.h>

void swap(int* swap1, int* swap2);

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);

	// get addresses of "a" and "b"
	swap(&a, &b);

	printf("a is: %i, b is: %i \n", a, b);
}

// ... snip ...
```

Now lets focus on the `swap` function.

(the currently empty swap function)
```c
// ... snip ...

void swap(int* swap1, int* swap2) {
	// code for swapping
}
```

`swap` has 2 address variables to 2 numbers. You can visualize the addresses like this.

![swap function](/Assets/swap_function.png)

You'll notice how the adea of an address is like an arrow "pointing" to something in memory. In C we call a "address variables" "pointers". 

I have neglected using the correct terminology so far to make it easier on you, but if you start talking to a C developer and say "I have this address variable..." he might laugh at you (or worse have no idea what you are talking about). From now on we're going to use the word "pointer" instead of "address variable".

(remember an address is really just a number representing a memory offset to the first byte (8 bits) of something)

Now we need a 3rd variable that can act as the 3rd cup. We will call it "c" (you see where I'm going with this?).

(edit the code inside of swap)
```c
// ... snip ...

void swap(int* swap1, int* swap2) {
	int c;
}
```

You can visualize this as the following.

![swap function need c](/Assets/swap_function_need_c.png)

Currently the variable `c` is not set to anything so it is `null` (null means the 0s and 1s are probably some random 0s and 1s "garbage value").

From the cups example we need to set `c` to a copy of what is at the `swap1` variable (which is the `a` variables *value*).

![swap function c copy a](/Assets/swap_function_c_copy_a.png)

To "go to" the address of `swap1` (a "pointer") we put a star symbol `*` in front of it.

(edit swap to the following)
```c
// ... snip ...

void swap(int* swap1, int* swap2) {
	int c = *swap1;
}
```

This puts a copy of `a` into `c` (much like the cups example).

"Going to" the address of a pointer is called "de-referencing" because a pointer gives us a "reference" to something, rather than a copy (a normal variable always gets a copy of it and NOT a reference).

From the cups example the next step is to set `a` (which is at `swap1`) to a copy of what is at the `swap2` variable (which is the `b` variables *value*).

![](/Assets/swap_function_a_copy_b.png)

(edit swap to the following)
```c
// ... snip ...

void swap(int* swap1, int* swap2) {
	int c = *swap1;
	*swap1 = *swap2;
}
```

And now we can set `b` to a copy of `c`.

![swap function b copy c](/Assets/swap_function_b_copy_c.png)

And we have successfully swapped `a` and `b` in the `main` function!

```c
// .. snip ..

int main(void) {
	int a = 100;
	int b = 3;
	
	printf("a is: %i, b is: %i \n", a, b);

	swap(&a, &b);
	
	printf("a is: %i, b is: %i \n", a, b);
}

// .. snip ..
```

Here is the final code.

```c
#include <stdio.h>

// function hint (prototype)
void swap(int* swap1, int* swap2);

int main(void) {
	int a = 100;
	int b = 3;
	
	printf("a is: %i, b is: %i \n", a, b);

	swap(&a, &b);
	
	printf("a is: %i, b is: %i \n", a, b);
}

// swap 2 numbers
void swap(int* swap1, int* swap2) {
	int c = *swap1;
	*swap1 = *swap2;
	*swap2 = c;
}
```

Run this code using `make swap`, and run it using `./swap`.

# Void
Since a pointer simply points to the first byte of memory we don't have to tell C the type! We can just make a plain old address to the first byte of the value!

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
	// "void" pointer
	void* hello = "Hello";

	//             convert to a char array using "char*"
	printf("%s \n", (char*) hello);
}
```

This code makes a plain old pointer (address) without needing to know the type! You will also notice that making an array variable using two brackets `myArray[] = "Hello"` is (in some ways) no different than just using a pointer `void* myArray = "Hello"` since internally both are just pointers (address variables) to the first byte of the array.

If your thinking just doing `* myAddress = "Hello"` to make a pointer (address variable) then your intuition is right. Even if that makes sense it wouldn't be valid C code, since C's "grammer" requires that we put `void` to represent "no type".

C has to know how to treat the 0s and 1s of something at an address to "use" the value. In the code above we tell C the "type" at the address by *casting* (hinting / converting) the pointer to a `char*` pointer, hence `(char*)`.

If we skipped *casting* pointer to a `char*` then C would offset by 1 byte (by default) when we use the square brackets `[]` (by default C offsets by 1 byte (8 bits) since that is the smallest individual piece of memory we can access. In this case a `char` uses 1 byte anyways, so it would still work fine).

Types also tell us how many bytes *after the first byte* are part of the value. This is necessary since an address just points to the first byte, and we don't want to access bytes outside of the type.

Types also help later when compiling to Assembly, since there are special `add` instructions for int's and float's (not to mention SIMD (Single Instruction Multiple Data) which can add up to 8 numbers (of a particular type) in one single instruction, giving us up to 8x speed ups!).