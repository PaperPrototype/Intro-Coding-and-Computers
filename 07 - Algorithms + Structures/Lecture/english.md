Searching is a difficult problem for computers. They can't just take a glance at everything and find what they are looking for. Nope.

This is partly due to that fact a computer is just a glorified Turing Machine.

# The Turing Machine
The idea behind a Turing Machine is first imagine an infinitely long tape, split into cells of symbols (For a computer it is 0s and 1s, AKA the many switches in our computers memory).

![tape of memory](/Assets/tape_of_memory.png)

Then imagine a "head" that move along the tape, and can read and write symbols (0s and 1s) to the tape.

![head reading memory tape](/Assets/head_reading_memory_tape.png)

Then there is a "state register" which you can think of as a number telling us "where" we are at in our code (what line of code we are at). Then there the code (some instructions) for this "head" that specify "what instruction to move to next, based on current symbol the head is currently looking at."

![head state register](/Assets/head_state_register.png)

Without realizing it our C code is getting converted to Assembly Instructions, and then into Machine Code for this glorified dumb Turing Machine!

When we load a program file to run it, we are loading it into the "RAM" (Random Access Memory, which is a faster piece of memory than our hard drive (the hard drive is where our files are stored)) and our processor loads the machine code instructions from this RAM and "does" them.

When we "search" something in a computers memory, we have to remember that this Turing Machine of ours has to send its "head" to some position in memory and look at each item individually.

# Linear Search
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

The "names" variable is an array of addresses, each to a name (a `char` array or "string").

You can visualize this with the following picture ("pointer" means address in C).

![array of addresses to array of strings](/Assets/addresses_array_to_array_names.png)

If you haven't noticed already, the names in the array are have been sorted alphabetically! This way we could use binary search (which was explained in week 0) to search for a name we are wanting (since binary search requires that we sort the list first).

Now add a `for` loop to go over the addresses in the names array, and access each name.

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void) {
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

	// (1) create offsetting variable
	for (int i = 0; i < 7; i++)
	{
		// do something with current name
		names[i];
	}
}
```

(1) The variable called `i` will increase every loop until it has looped seven times (remember, we started counting *at zero*, so in total we will count 7 times).

Now we need to compare the current name with the name we want, if they match then we have found the name we want!

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void) {
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

	for (int i = 0; i < 7; i++)
	{
		// use `strcmp` to compare curretn name with `Ron`
		if (strcmp(names[i], "Ron") == 0) 
		{
			// found name!
		}
	}
}
```

We use the `strcmp` function to compare our current name with the desired name, which means we have to include "string.h" to get access to it.

Now we can print out the current name if we have found it, and "exit" or quit the program by adding `return`. Remember, andy code after the `return` keyword, will not get run!

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>

int main(void) {
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

	for (int i = 0; i < 7; i++)
	{
		if (strcmp(names[i], "Ron") == 0) 
		{
			// found name!
			printf("Found name: %s \n", names[i]);
			return 0;
		}
	}
}
```

Now remember, the "main" function gives back an error code. returning 0 means "nothing went wrong".

If our code did not find the desired name, then it will proceed to run any code after the loop (since the `return 0` (which would have caused us to exit) didn't happen).

If we manage to not find the name, then after the loop we will print out "Name not found!".

(print out "Name not found!" after the loop)
```c
#include <stdio.h>
#include <string.h>

int main(void) {
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

	for (int i = 0; i < 7; i++)
	{
		if (strcmp(names[i], "Ron") == 0) 
		{
			// found name!
			printf("Found name: %s \n", names[i]);
			return 0;
		}
	}

	printf("Name not found! \n");
}
```

Compile this program in the Shell (or Console) using `make main`, and run it using `./main` (or you can use the run button).

Now searching through a list of names, isn't that cool, or realistic. Instead it would actually be useful if each name also had a phone number grouped with it! THen if we searched a name, we could also get that persons phone number!

We could just make another list to hold a list of corresponding phone numbers, but in C there is a way to "group" 2 variables together into 1 "type"!

# Structs
Make a new replit. 

![new repl while in project](/Assets/replit_new_repl_while_in_project.gif)

Select the C language, and name the project "phonebook".

Now C uses what is called a "structure" to combine 2 types together into 1 compound type.

Delete all the code and write the following.

```c
struct contact {
	char* name;
	char* phone;
};
```

Now add the "main" function and lets make an "contact" variable.

```c
struct contact {
	char* name;
	char* phone;
};

int main(void) {
	// make a person with a totally real phonenumber
	struct contact myPerson = {"Bob", "999-999-9999"};
}
```

Why did we do "struct contact myPerson"? Well the part "struct contact" is the *type*. A struct doesn't count as a type by default, in C, so we have to put "struct contact" in front as the type. 

We can make our struct become a "type" by using `typedef`.

(edit your code to the following)
```c
struct contact {
	char* name;
	char* phone;
};

// (1)
typedef struct contact contact_t;

int main(void) {
	struct contact person = {"Bob", "999-999-9999"};
}
```

(1) We are taking the struct "struct contact" and making a type "contact_t". We put the underscore t `_t` at the end, to distinguish our new type from the struct name.

Now lets use the new "type" in our variable.

(edit your code to the following)
```c
struct contact {
	char* name;
	char* phone;
};

typedef struct contact contact_t;

int main(void) {
	contact_t myPerson = {"Bob", "545-843-6454"};
}
```

Ahh, much better. Although there is a shortcut, and we can just put the whole darn definition of our struct inside of the `typedef`.

(edit your code to the following)
```c
typedef struct contact {
	char* name;
	char* phone;
} contact_t;

int main(void) {
	contact_t myPerson = {"Bob", "545-843-6454"};
}
```

(New languages just make any `struct` a "type", rather than you havning to go through all this...)

# Searching a Phonebook
Now lets make an array of "contacts".

(edit your code to the following)
```c
struct contact {
	char* name;
	char* phone;
};

typedef struct contact contact_t;

int main(void) {
	// (1) array of 5 contacts
	contact_t myPeople[5];

	// (2) set first person in array
	myPeople[0] = {"Bob", "999-999-9999"};
}
```

(1) We make an array of 5 contacts.

(2) We set the first person (by "going to" the first address with an offset of 0). Although C is so clueless it won't realize that `{"Bob", "999-999-9999"}` is in the format of the `contact_t` type!

So we have to "cast" (AKA "casting is a way of "converting one type to another") and tell C "hey, idiot, this here is a `contact_t` type".

(edit your code to the following)
```c
struct contact {
	char* name;
	char* phone;
};

typedef struct contact contact_t;

int main(void) {
	contact_t myPeople[5];

	//            tell the the "type" by casting
	myPeople[0] = (contact_t){"Bob", "999-999-9999"};
}
```

Now lets go ahead and set the remaining 4 people in the `myPoeple` array.

```c
struct contact {
	char* name;
	char* phone;
};

typedef struct contact contact_t;

int main(void) {
	contact_t myPeople[5];

	myPeople[0] = (contact_t){"Bob", "999-999-9999"};
	myPeople[1] = (contact_t){"Dylan", "888-888-8888"};
	myPeople[2] = (contact_t){"Smyth", "777-777-7777"};
	myPeople[3] = (contact_t){"Bill", "666-666-6666"};
	myPeople[4] = (contact_t){"Charlie", "666-666-6666"};
}
```

You'll notice Bill and Charlie both have the same phone number (its cause they are homeschooled and share the same phone).

Now, we can search through the contacts!