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
		// (2) do something with current name
		names[i];
	}
}
```

(1) The variable called `i` will increase every loop until it has looped seven times (remember, we started counting *at zero*, so in total we will count 7 times).

(2) Now we need to compare the current name with the name we want, if they match then we have found what we searched for!

(edit your code to the following)
```c
#include <stdio.h>

// (1)
#include <string.h>

int main(void) {
	char* names[] = {"Bill", "Charlie", "Fred", "George", "Ginny", "Percy", "Ron"};

	for (int i = 0; i < 7; i++)
	{
		// (2) use `strcmp` to compare current name with `Ron`
		if (strcmp(names[i], "Ron") == 0) 
		{
			// (3) found name!
		}
	}
}
```

(1) We have to include "string.h" to get access to `strcmp` for comparing 2 strings (eg names).

(2) We use the `strcmp` function to compare our current name (in the loop) with the desired name.

(3) Now we can print out the current name if we have found it, and "exit" or quit the program by adding `return` (Remember, any code after the `return` keyword, will not get run! Unless `return` is inside of a function, in which case, only the code inside of that function will not get run).

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

If we manage to NOT find the name (and `return` didn't cause us to exit), then after the loop we print out "Name not found!".

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

We `return 1` if we didn't find the name (make sure it is after `printf("Name not found! \n");` or we could "return" before running `printf("Name not found! \n");` to never get run!).

Compile this program in the Shell (or Console) using `make main`, and run it using `./main` (or you can use the run button).

Now searching through a list of names, isn't that cool, or realistic. Instead it would actually be useful if each name also had a phone number grouped with it!

We could just make another list of corresponding phone numbers.

(example)
```c
char* names[] = {"Bill", "Charlie", "Fred"};

char* numbers[] = {"121-121-1212", "123-456-7890", "098-765-4321"};
```

...but we might mix up the order of those 2 lists.

And besides, in C there is a way to "group" 2 types together into 1 type! (Remember a "type" tells a size in memory (which can be found by using `sizeof()`), as well as "how to treat the 0s and 1s").

# Structs
Make a new replit. 

![new repl while in project](/Assets/replit_new_repl_while_in_project.gif)

Select the C language, and name the project "phonebook".

Now C uses what is called a "structure" to combine 2 types together into 1 compound type.

Delete all the code and write the following "structure".

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

The part `struct contact` is the *type*. 

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

(1) We are taking the struct `struct contact` and making a type `contact_t`. We put `_t` (underscore T) at the end, to distinguish it from the struct's name, which is "contact" (`_t` isn't anything special, it's just a custom for some poeple to use `_t` since "t" can mean "type").

Now lets use the new type `contact_t` in our variable.

(edit your code to the following)
```c
struct contact {
	char* name;
	char* phone;
};

typedef struct contact contact_t;

int main(void) {
	// use `contact_t` type
	contact_t myPerson = {"Bob", "545-843-6454"};
}
```

Ahh, much cleaner to read. Although there is a shortcut for using typedef...

(example)
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

(1) Doing `.name` lets us access the `name` variable in the `myPerson` struct variable!

Now run your edited code, to see what it will print!

# Searching a Phonebook
Now lets make an array of "contacts". Delete the code inside of the `main` function.

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

(edit your code to the following)
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

(edit your code to the following)
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

	// (2) search through 5 contacts
	for (int i = 0; i < 5; i++)
	{
		// (3) if name is "Bill"
		if (strcmp(myPeople[i].name, "Bill") == 0)
		{
			// print out phone number
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			// (4) exit the loop without stopping the program
			break;
		}
	}
}
```

(1) We include `string.h` to get access to `strcmp`. 

(2) We create a loop, with an offset number we can use to access each contact, in the contacts array.

(3) We check if `strcmp` returns 0 (meaning the names matched), and then print out Bill's phone number if the names matched.

(4) The `break` keyword is new. The `break` keyword will "break out" of any loops it is in. This way if we find the name we want, we print out its corresponding phone number, and "break out" of the loop (rather than continuing to loop and search, since we've already found the phone number we wanted).

Obviously this algorithm has `O(N)` efficiency, but for such few contacts it would be overkill to do binary search.

In case if you forgot, `O` (the letter O) stands for "in the worst case scenario" and we put the number of steps for that worst case scenario inside of the parenthesis `()`. 

`N` stands for the number of contacts. All put together `O(N)` means "in the worst case scenario it will take 5 (the number of contacts) steps to find Bill".

If we *don't* find the person we were looking for then, we will need to rpint out "not found".

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>

// (1)
#include <stdbool.h>

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

	// (2)
	bool found = false;

	for (int i = 0; i < 5; i++)
	{
		// if name is "Bill"
		if (strcmp(myPeople[i].name, "Bill") == 0)
		{
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			// (3)
			found = true;

			break;
		}
	}

	// (4) never set `found = true`
	if (found != true) {
		printf("not found");
	}
}
```

(1) We include `stdbool.h` to get access to the boolean types `true` and `false`.

(2) We make a variable called `found` and set it to `false`.

(3) If we happen to find the name we were looking for, then `found` is set to `true`...

(4) We check if `found` was never set to `true` (or we could say `if (found == false)`) then that means we didn't find what we were looking for (`found` stayed false) an we print "not found".

This program is kinda lame, we can only ever search for "Bill". Lets get you to type the name of a contact that you want, and then have the program search for it.

We could use `scanf` to get input.

Or we could use the input parameters that "main" gets when we run the program.

We will use the input from "main".

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>

typedef struct {
	char* name;
	char* phone;
} contact;

// (1)
int main(int argc, char* argv[]) {

	// (2)
	if (argc < 2)
	{
		printf("Not enough arguments!");
		return 1;
	}

	contact myPeople[5];

	myPeople[0] = (contact){"Bob", "999-999-9999"};
	myPeople[1] = (contact){"Dylan", "888-888-8888"};
	myPeople[2] = (contact){"Smyth", "777-777-7777"};
	myPeople[3] = (contact){"Bill", "666-666-6666"};
	myPeople[4] = (contact){"Charlie", "555-555-5555"};

	bool found = false;

	for (int i = 0; i < 5; i++)
	{
		// (3)
		if (strcmp(myPeople[i].name, argv[1]) == 0)
		{
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			found = true;

			break;
		}
	}

	if (found != true) {
		printf("not found");
	}
}
```

(1) We change main to take in its parameters, `argc` = argument count, and `argv` = argument array ("v" stands for vector, which can be another name for array).

(2) We make sure that the user (us) has typed a name after running the program, by doing "if argument count is less than 2" (`./main Bobby` is 2 arguments). If we didn't type something after `./main` then we print out a message, and stop any other code from running by `return`ing.

(3) Finally we compare the name supplied in `argv[1]` (we will get "Bobby" from `argv[1]` if we ran "./main Bobby") and if the name we supplied matches any of the names in the phonebook, then we print out the phone number for that person.

Now compile this program using make

(shell command)
```
make main
```

and run the resulting program using

(shell command)
```
./main Bill
```

Run the program using the play button (nothing will get put after `./main`) so we get...

```
Not enough arguments! Exit status 1
```

...in the shell! Its our our error message, and the error code we `return`ed.


```c
if (argc < 2)
{
	printf("Not enough arguments!");
	return 1;
}
```

And thats it for this week!