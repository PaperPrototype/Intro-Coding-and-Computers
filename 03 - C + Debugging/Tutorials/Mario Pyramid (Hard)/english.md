This tutorial assumes you have finished the "Mario (Medium)" tutorial.

THe challenge is to use two loops to print out two pyramids with a space between them like this.

```
    # #
   ## ##
  ### ###
 #### ####
##### #####
```

Make a new repl and call it "mario3". Select the C programming language.

As a tip here is code that prints out two rows of hashes.

```c
#include <stdio.h>

int main(void)
{
	int size = 5;

	for (int hash = 0; hash < size; hash++) {
		printf("#");
	}

	printf(" ");

	for (int hash2 = 0; hash2 < size; hash2++) {
		printf("#");
	}

	printf("\n");
}
```

We put a space between both rows of hashes using a `printf(" ")`.

This prints 10 hashes in a row with a space between.

```
##### #####
```

Then you can stack each of these rows, then have an offset number for half-pyramid. The end result should look like this.

```
    # #
   ## ##
  ### ###
 #### ####
##### #####
```