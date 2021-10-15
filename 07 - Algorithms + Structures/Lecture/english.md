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

`names[]` is an array of `char*` addresses. Each address, leads to a name.

You can visualize this with the following diagram.

![array of addresses to array of strings](/Assets/addresses_array_to_array_names.png)

If you haven't noticed already, the names in the array have been sorted alphabetically! 

Although, it is really "ASCII-betically", because we use the ASCII number for that letter to decide the order (smaller number = first, larger number = last).

This way we could use binary search (which was explained in week 0) to compare a name's letters (as if they were numbers) to search for a name in the list (since binary search requires that we sort first).

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

If we manage to NOT find the name, then after the loop we will print out "Name not found!".

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
	return 1;
}
```

We `return 1` if we didn't find the name (make sure it is after `printf("Name not found! \n");`, or we could cause `printf("Name not found! \n");` to never get run!).

Compile this program in the Shell (or Console) using `make main`, and run it using `./main` (or you can use the run button).

Now searching through a list of names, isn't that cool, or realistic. Instead it would actually be useful if each name also had a phone number grouped with it! THen if we searched a name, we could also get that persons phone number!

We could just make another list to hold a list of corresponding phone numbers, but in C there is a way to "group" 2 variables together into 1 "type"!

# Structs
Make a new replit. 

![new repl while in project](/Assets/replit_new_repl_while_in_project.gif)

Select the C language, and name the project "phonebook".

Now C uses what is called a "structure" to combine 2 types together into 1 compound type.

Delete all the code and write the following code.

```c
struct contact {
	char* name;
	char* phone;
};
```

Now add the "main" function and lets make a "contact" variable.

```c
struct contact {
	char* name;
	char* phone;
};

int main(void) {
	// make a person with a totally real phone number
	struct contact myPerson = {"Bob", "999-999-9999"};
}
```

Why did we do `struct contact myPerson`? Well the part `struct contact` is the *type*. 

A `struct` doesn't count as a type by default (at least in C) so we have to put `struct contact` rather than just `contact` in front of the variable `myPerson`.

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

(1) We are taking the struct `struct contact` and making a type `contact_t`. We put `_t` (underscore T) at the end, to distinguish it from the struct's name (`_t` isn't anything special, it's just a custom for some pople to use `_t` since "t" can mean "type").

Now lets use the new type `contact_t` in our variable.

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

Ahh, much cleaner to read. Although there is a shortcut for using typedef...
```c
typedef struct contact contact_t;
```
...where we can just put the curly brackets (for the struct)...

```c
{
	char* name;
	char* phone;
}
```

...in the `typedef`...

```c
typedef struct contact { char* name; char* phone; } contact_t;
```

...which looks like this if we move the curly brackets around...

```c
typedef struct contact { 
	char* name; 
	char* phone; 
} contact_t;
```
...and we can even remove the the `contact` word at the top...

```c
typedef struct { 
	char* name; 
	char* phone; 
} contact_t;
```
...which would mean we also don't need to put `_t` at the end to tell the "type" name apart form the struct name...

```c
typedef struct { 
	char* name; 
	char* phone; 
} contact;
```

Tada! Even better! This is how I recommend you make a `struct` in C.

(edit your struct to the following)
```c
// (1)
typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	// (2)
	contact myPerson = {"Bob", "545-843-6454"};
}
```

(1) Modern languages treat all `struct`'s as a type, rather than you having to go through all this nonsense.

(2) The ` = {"Bob", "545-843-6454"};` is just setting the 2 strings in our variable `myPerson` (since the `contact` struct groups 2 strings ("string" = `char` array)).

We can now access the name and phone number in the contact struct!

(edit your code to print out the name and phone number)
```c
// include stdio.h (standard input output)
#include <stdio.h>

typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	contact myPerson = {"Bob", "545-843-6454"};

	// (1)
	printf("name %s, phone number %s \n", myPerson.name, myPerson.phone);
}
```

(1) Doing `myPerson.name` lets us access the `name` variable in the `contact` struct!

Now run your code, to see what it will print!

# Searching a Phonebook
Now lets make an array of "contacts".

(edit your code to the following)
```c
typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	// (1) array of 5 contacts
	contact myPeople[5];

	// (2) set first person in array
	myPeople[0] = {"Bob", "999-999-9999"};
}
```

(1) We make an array of 5 contacts.

(2) We set the first person (by "going to" the first address with an offset of 0). Although C is so clueless it won't realize that `{"Bob", "999-999-9999"}` is in the format of the `contact` struct type!

So we have to "cast" (hint) and tell C "hey, idiot, this is a `contact` struct type".

(edit your code to help C understand)
```c
typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	contact myPeople[5];

	//            tell C the the type by casting
	myPeople[0] = (contact){"Bob", "999-999-9999"};
}
```

Now lets go ahead and set the remaining 4 people in the `myPoeple` array.

```c
typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	contact myPeople[5];

	myPeople[0] = (contact){"Bob", "999-999-9999"};
	myPeople[1] = (contact){"Dylan", "888-888-8888"};
	myPeople[2] = (contact){"Smyth", "777-777-7777"};
	myPeople[3] = (contact){"Bill", "666-666-6666"};
	myPeople[4] = (contact){"Charlie", "555-555-5555"};
}
```

Make sure to increase the offset in the square brackets `[]` for each person!

Now, we can search through the contacts!

```c
#include <stdio.h>

// (1) include string.h to get access to `strcmp`
#include <string.h>

typedef struct {
	char* name;
	char* phone;
} contact;

int main(void) {
	contact myPeople[5];

	myPeople[0] = (contact){"Bob", "999-999-9999"};
	myPeople[1] = (contact){"Dylan", "888-888-8888"};
	myPeople[2] = (contact){"Smyth", "777-777-7777"};
	myPeople[3] = (contact){"Bill", "666-666-6666"};
	myPeople[4] = (contact){"Charlie", "555-555-5555"};

	// (2) search through contacts
	for (int i = 0; i < 5; i++)
	{
		// if name is "Bill"
		if (strcmp(myPeople[i].name, "Bill") == 0)
		{
			// print out phone number
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			// (3) exit the loop without stopping the program
			break;
		}
	}
}
```

(1) We include `string.h` to get access to `strcmp`. 

(2) We check if `strcmp` returns 0 (meaning the names matched), and then print out Bob's phone number if the name did match.

(3) The `break` keyword is new. The `break` keyword will "break out" of any loops it is in. This way if we find the name we want, we stop looping and any code after the loops gets to run!

Obviously this algorithm has `O(N)` efficiency, but for such few contacts it would be overkill to do binary search.

In case if you forgot, `O` (the letter O) stands for "in the worst case scenario" and we put the number of steps for thqat worst case scenario inside of the parenthesis `()`. 

`N` stands for the number of contacts. All put together it means "in the worst case scenario it will take 5 (the number of contacts) steps to find Bill".

And that's it for this week!