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
#include <string.h> // (1)

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

We `return 1` if we didn't find the name (make sure it is after `printf("Name not found! \n");` or we could "return" before doing `printf("Name not found! \n");`).

Compile this program in the Shell (or Console) using `make main`, and run it using `./main` (or you can use the run button).

Now searching through a list of names, isn't that cool, or realistic. Instead it would actually be useful if each name also had a phone number grouped with it!

We could just make another list of corresponding phone numbers.

(example)
```c
char* names[] = {"Bill", "Charlie", "Fred"};

char* numbers[] = {"121-121-1212", "123-456-7890", "098-765-4321"};
```

...but, as programmer we might mix up the order of those 2 lists, and end up calling Charlie instead of Bill.

And besides, in C there is a way to "group" 2 types together into 1 type! Which would let us group a name with a phone number! 

Remember a "type" tells a size in memory (which can be found by using `sizeof()`), as well as "how to treat the 0s and 1s" and which 0s and 1s represent specific things. Like the first bit (0 or 1) in an `int` type stands for negative (if its 0) or positive (if its 1).

# Structs
Make a new replit. 

![new repl while in project](/Assets/replit_new_repl_while_in_project.gif)

Select the C language, and name the project "phonebook".

Now C uses what is called a "structure" to combine 2 types together into 1 compound type.

Delete all the code that is there, and write the following "structure".

```c
struct contact {
	char* name;
	char* phone;
};
```

This "struct" type is grouping 2 `char` arrays (we make them pointers rather than using `char name[]`, since we don't know how many `char`s there will be in the arrays). 

Most C programmars use `char*` pointers for a `string` type. Although if you include "string.h" then you could get access to a type called (literally) `string`! Although if you look inside of `string.h` you will see that "string" is an alias for `char*`...

(example, string.h code)
```c
#define string char*
```

Ok, lets get back to what we were doing.

Add the "main" function and lets make a "contact" variable.

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

The part `struct contact` is the "*type*". 

The word `contact` doesn't count as a type by default (at least in C) so we have to put `struct contact` rather than just `contact` in front of the variable `myPerson`.

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

(1) We are taking the struct `struct contact` and making a type `contact_t`. We put `_t` (underscore T) at the end, to distinguish it from the struct's name (`_t` isn't anything special, it's just a Unix tradition for some poeple to use `_t`, since "t" can mean "type").

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

Ahh, much cleaner to read. Although it its pretty anoying to have to do the whole darn `typedef struct contact contact_t;`, instead we can just do this.

(example)
```c
typedef struct contact {
	char* name;
	char* phone;
} contact_t;
```

...and we can even remove the `contact` word at the top...

(example)
```c
typedef struct { 
	char* name; 
	char* phone; 
} contact_t;
```

...which would mean we also don't need to put `_t` at the end to tell the "type" name apart form the struct name...

(example)
```c
typedef struct { 
	char* name; 
	char* phone; 
} contact;
```

Tada! Even better! Now the word `contact` counts as a "type".

(edit your code to the following)
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

Where were we? Ah right, setting upi the stuff inside of the variable...

(2) The ` = {"Bob", "545-843-6454"};` is just setting the 2 strings in our variable `myPerson` (since `contact` groups 2 strings).

We can now access the name and phone number in a single variable!

(edit your code to print out the name and phone number in `myPerson`)
```c
#include <stdio.h> 
// make sure to include stdio.h (standard input output)

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

(1) Doing `.name` lets us access the `name` part of `contact`. The same is true for `.phone`.

Now run your edited code, to see what it will print!

# Searching a Phonebook
Now lets make an array of "contacts". Delete the code inside of the `main` function and change it to the following.

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

(2) We set the first person by "going to" the first address with an offset of 0. Although C is so clueless it won't realize that `{"Bob", "999-999-9999"}` is in the format of the `contact` type!

So we have to "cast" (AKA hint) and tell C "hey, idiot this is a `(contact)` type".

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

	// (1)
	myPeople[0] = (contact){"Bob", "999-999-9999"};
	myPeople[1] = (contact){"Dylan", "888-888-8888"};
	myPeople[2] = (contact){"Smyth", "777-777-7777"};
	myPeople[3] = (contact){"Bill", "666-666-6666"};
	myPeople[4] = (contact){"Charlie", "555-555-5555"};
}
```

(1) Make sure to increase the offset in the square brackets `[]` for each person in the `myPeople` array.

Now, we can search through the contacts!

(edit your code to the following)
```c
#include <stdio.h>
#include <string.h>
// (1) include string.h to get access to `strcmp`

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
		// (3) if current name at `i` is "Bill"
		if (strcmp(myPeople[i].name, "Bill") == 0)
		{
			// print out phone number
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			// (4) exit the loop and do any code afterwards
			break;
		}
	}

	printf("This code will run!");
}
```

(1) We include `string.h` to get access to `strcmp`. 

(2) We create a loop, with an offset number we can use to access each contact, in the contacts array. `i` is the name of our offset number variable that will get increased each loop.

(3) We check if `strcmp` returns 0 (meaning the current `.name` in `myPeople` array matched), and then print out Bill's phone number (if Bill is in the contacts of course).

(4) The `break` keyword is new. The `break` keyword will "break out" of any loops it is in. This way if we find the name we want, we print out its corresponding phone number, and "break out" of the loop (rather than continuing to search since we've already found the phone number we wanted).

Obviously this algorithm has `O(N)` efficiency, but for such few contacts it would be overkill to do binary search.

In case if you forgot, `O` (the letter O) stands for "in the worst case scenario" and we put the number of steps for that worst case scenario inside of the parenthesis `()`. In this case we have 5 contacts so its `O(5)` efficiency.

Rather than putting 5 inside of the parenthesis `N` stands for the number of contacts. That way if we change the number of contacts we can still just say `O(N)`.

What If we *don't* find the person we were looking for? In that case we will need to print out "not found".

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
		// if current name is "Bill"
		if (strcmp(myPeople[i].name, "Bill") == 0)
		{
			printf("Found Bill, his number is: %s \n", myPeople[i].phone);

			// (3)
			found = true;

			break;
		}
	}

	// (4) never set `found = true`
	if (found == false) {
		printf("not found");
	}
}
```

(1) We include `stdbool.h` to get access to the boolean types `true` and `false`.

(2) We make a variable called `found` and set it to `false` (initially).

(3) If we happen to find the name we were looking for, then `found` is gets set to `true`...

(4) After the loop, we check if `found` is still `false` If it is then that means we didn't find what we were looking for (`found` stayed false) an we print "not found".

# Dynamic Search
This program is pretty stupid, we can only ever search for "Bill".

Lets make it so that you can type the name of a contact you want, and then have the program search for their phone number.

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

(1) We change `main` to take in its special parameters (variables), `argc` = argument count, and `argv` = argument vector (vector is another old word for array).

(2) We make sure that the user (us) has typed a name after running the program, by doing "if argument count is less than 2" (`./main Bobby` is 2 arguments). If we didn't type something after `./main` then we print out a message, and stop any other code from running by `return`ing.

(3) Finally we compare the name supplied in `argv[1]` (we will get "Bobby" from `argv[1]` if we ran "./main Bobby") and if the name we supplied matches any of the names in the phonebook, then we print out the phone number for that person.

Now compile this program using make

(command)
```
make main
```

and run the resulting program to search for "Bill".

(command)
```
./main Bill
```

Now try searching for "Smyth".


(ommand)
```
./main Smyth
```

Tada!

If we try running the program without any arguments...

(command)
```
./main
```

We get an error!

```
Not enough arguments! Exit status 1
```

Its our our error message, and the error code we `return`ed!

(error message code we made)
```c
if (argc < 2)
{
	printf("Not enough arguments!");
	return 1;
}
```

Pretty cool!

One other problem we could face is if we forgot to Uppercase the first letter in "Bill", like this "bill". That would result in use not finding "Bill"!

This is because UPPERCASE and lowercase letters have different mappings in the ASCII encodings!

(example ASCII encodings)
```
...
	65	A	(Capital A )			
	66	B	(Capital B )			
	67	C	(Capital C )			
	68	D	(Capital D )			
	69	E	(Capital E )			
	70	F	(Capital F )			
	71	G	(Capital G )			
	72	H	(Capital H )			
	73	I	(Capital I )			
	74	J	(Capital J )			
	75	K	(Capital K )			
	76	L	(Capital L )			
	77	M	(Capital M )			
	78	N	(Capital N )			
	79	O	(Capital O )			
	80	P	(Capital P )			
	81	Q	(Capital Q )			
	82	R	(Capital R )			
	83	S	(Capital S )			
	84	T	(Capital T )			
	85	U	(Capital U )			
	86	V	(Capital V )			
	87	W	(Capital W )			
	88	X	(Capital X )			
	89	Y	(Capital Y )			
	90	Z	(Capital Z )			
...
	97	a	(Lowercase  a )			
	98	b	(Lowercase  b )			
	99	c	(Lowercase  c )			
	100	d	(Lowercase  d )			
	101	e	(Lowercase  e )			
	102	f	(Lowercase  f )			
	103	g	(Lowercase  g )			
	104	h	(Lowercase  h )			
	105	i	(Lowercase  i )			
	106	j	(Lowercase  j )			
	107	k	(Lowercase  k )			
	108	l	(Lowercase  l )			
	109	m	(Lowercase  m )			
	110	n	(Lowercase  n )			
	111	o	(Lowercase  o )			
	112	p	(Lowercase  p )			
	113	q	(Lowercase  q )			
	114	r	(Lowercase  r )			
	115	s	(Lowercase  s )			
	116	t	(Lowercase  t )			
	117	u	(Lowercase  u )			
	118	v	(Lowercase  v )			
	119	w	(Lowercase  w )			
	120	x	(Lowercase  x )			
	121	y	(Lowercase  y )			
	122	z	(Lowercase  z )			
...
```

So when we do...

(code for comparing names)
```c
if (strcmp(myPeople[i].name, argv[1]) == 0)
```

...the names in `myPeople[i].name` and `argv[1]` will NOT match if even 1 of the letters is not in the correct case (uppercase or lowercase).

We can fix this pretty easily by simply lowercasing both words from `myPeople[i].name` and `argv[1]` and then comparing them.

We won't do that, but if you did want to it would require using the `tolower` (as in "to lowercase") function for each letter/`char`acter in the names (or you could even more manually make your own lowercasing function that deals with the ASCII mappings directly).

And thats it for today!