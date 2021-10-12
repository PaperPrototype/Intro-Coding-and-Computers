Searching is a difficult problem for computers. They can't just take a glance at everything and find what they are looking for. Nope.

This is partly due to that fact a computer is just a glorified Turing Machine.

# The Turing Machine
The idea behind a Turing Machine is first imagine an infinitely long tape, split into cells of symbols (For a computer it is 0s and 1s, AKA the many switches in our computers memory).

![tape of memory](/Assets/tape_of_memory.png)

Then imagine a "head" that move along the tape, and can read and write symbols (0s and 1s) to the tape.

![head reading memory tape](/Assets/head_reading_memory_tape.png)

Then there is a "state register" which you can think of as a number telling us "where" we are at in our code (what line of code we are at). Then there is some instructions for this "head" that specify what instruction to move to next, based on the symbol in the tape the head is currently looking at.

![head state register](/Assets/head_state_register.png)

Without realizing it our C code is getting converted to Assembly Instructions, and then into Machine Code for this glorified dumb Turing Machine!

When we load a program file to run it, we are loading it into the "RAM" (Random Access Memory, which is a faster piece of memory than our hard drive (the hard drive is where our files are stored)) and our processor loads the machine code instructions from this RAM and "does" them.

When we "search" something in a computers memory, we have to remember that this Turing Machine of ours has to send its "head" to some position in memory and look at each item individually.

# Searching
Open this link to go to Replit https://replit.com. Make a new Repl. Select the C language. Name the project "searching".

By default Replit will give you the "hello world" program (remember the famous phrase? -> "Hello World"). 

(default C program)
```c
#include <stdio.h>

int main(void) {
  printf("Hello World\n");
  return 0;
}
```

Delete everything inside of main.

(answer)
```c
#include <stdio.h>

int main(void) {
  
}
```

Now add an array of names for us to search.

(add an array of names to your code)
```c
#include <stdio.h>

int main(void) {
	// names to search
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};
}
```

The "names" variable is an array of addresses, each to an array of `char`'s (AKA, a name is an array of characters).

You can visualize this with the following picture.

![array of addresses to array of strings](/Assets/addresses_array_to_array_names.png)\

If you haven't noticed already, the names in the array are have been sorted alphabetically! This way we could use binary search (which was explained in week 0) to search for a name we are wanting (since binary search requires that we sort the list first).

Now add a `for` loop to move over the addresses in the names array, and access each name.

(edit your code to the following)
```c

```

we used `strcmp` previously, but it turns out it actually looks at each individual character! and compares them

# Structs

# Searching a Phonebook
By default Replit will give you a "hello world" program (remember the famous phrase? -> "Hello World"). 

(default C program)
```c
#include <stdio.h>

int main(void) {
  printf("Hello World\n");
  return 0;
}
```

Delete everything inside of main.

(possible answer)
```c

```

https://www.youtube.com/watch?v=SzJ46YA_RaA&list=PLfQKpWkd0WpDDUDlQ678Q7zgrk6OoSXan

Searching with a limited Turing machine

Linear Search

"mov" assembly instruction

Binary Search