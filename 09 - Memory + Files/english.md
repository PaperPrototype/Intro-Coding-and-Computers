# Swap
Make a new file using touch called "swap.c".

(command)
```
touch swap.c
```

Open it using the files window.

Lets say we have 2 variables `a` and `b`. We want to swap the numbers they hold.

(change your code to the following)
```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);
}
```

In the above code we have 2 variables and we print them out. 

If we just tried to "swap" them by doing this...

```c
#include <stdio.h>

int main(void) {
	int a = 100;
	int b = 3;

	printf("a is: %i, b is: %i \n", a, b);

	a = b;
	b = a;
}
```

...it wouldn't work. I'll show you why.

Lets imagine each variable is a cup holding its contents.

![swap cups](/Assets/swap_cups.png)

To be able to swap the "water" (stuff inside `a` and `b`) we need a second cup called "c".

![swap cups need c](/Assets/swap_cups_need_c.png)

Then we can put the stuff from `a` into `c`.

![swap cups a into c](/Assets/swap_cups_a_into_c.png)

Then we can pour `b` into `a`.

![swap cups b into a](/Assets/swap_cups_b_into_a.png)

And finally we can put `c` into `b`.

![swap cups final](/Assets/swap_cups_c_into_b.png)

Yay! We have successfully swapped the contents of `a` and `b`.

Lets turn this into real code.

> Warning: The following is a purposefully over-engineered solution that may cause untold damage to your brain. It was designed for for the sole purpose of teaching you about addresses.

> THE KNOWLEDGE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF UNLEASHING INDESCRIBABLE HORRORS THAT SHATTER YOUR PSYCHE AND SET YOUR MIND ADRIFT IN THE UNKNOWABLY INFINITE COSMOS.
-- [Rustomonicon](https://doc.rust-lang.org/nomicon/)

...for those of you who have trouble detecting sarcasm (like me), we are just kidding.

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

You'll notice how the adea of an address is like an arrow "pointing" to something in memory. This is why we call a "address variables" "pointers". 

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

# Simple swap
...in the end of all this pointer craze, we could have just done this...

```c
#include <stdio.h>

// function hint (prototype)
void swap(int* swap1, int* swap2);

int main(void) {
	int a = 100;
	int b = 3;
	
	printf("a is: %i, b is: %i \n", a, b);

	int c = a;
	a = b;
	b = c;
	
	printf("a is: %i, b is: %i \n", a, b);
}
```

And we would have successfully swapped both numbers.
