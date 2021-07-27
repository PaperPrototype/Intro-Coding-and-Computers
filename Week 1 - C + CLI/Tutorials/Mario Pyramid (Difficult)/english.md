![] show picture of mario's pyramid

Goal: Print hashes in the Terminal to make a full pyramid like the one from Mario.

```
~/Hello-C$ ./mario
    # #
   ## ##
  ### ###
 #### ####
##### #####
```

Make a new file called `mario2.c` using `touch`. Open it using the "Files" tab.

We could print out hashes out manually. Type in the following code.

```c
#include <stdio.h>

int main(void) {
	printf("   # #   \n");
	printf("  ## ##  \n");
	printf(" ### ### \n");
	printf("#### ####\n");
}
```

Compile this using `make`. Then run it using `./mario2`.

This limits us to a certain max pyramid size though!

We can use 2 loops to make two rows of hashes.

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
}
```

We put a space between both rows of hashes using a `printf`.

This prints 10 hashes in a row with a space between.

```
~/Hello-C$ ./mario
##### #####~/Hello-C$
```

Now we also need to add a newline at the end.

```c
#include <stdio.h>

int main(void)
{
	int size = 5;

	for (int hash = 0; hash < size; hash++)
    {
        printf("#");
    }

	printf(" ");

	for (int hash2 = 0; hash2 < size; hash2++)
    {
        printf("#");
    }

	printf("\n");
}
```

We also change the placement of the first curly brackets `{` in the code. This is perfeclty correct code, just a different way of writing it. This will make the loop code easier to read.

This prints out 10 hashes with a space in the middle, and a newline at the end.

```
~/Hello-C$ ./mario
##### #####
~/Hello-C$ 
```

Now we can stack both loops of hashes by putting them in a loop.

```c
#include <stdio.h>

int main(void)
{
	int size = 5;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = 0; hash < size; hash++)
		{
			printf("#");
		}

		printf(" ");

		for (int hash2 = 0; hash2 < size; hash2++)
		{
			printf("#");
		}

		printf("\n");
	}
}
```

This prints out the following.

```c
##### #####
##### #####
##### #####
##### #####
##### #####
```

Now we need an offset number that we decrease and increase. We can use if statements to check if the current hash is greater or less than the offset. 

You will likely need 2 separate offsets for each half of the pyramid. If this is too hard go to the easy mario pyrmaid tutorial to see how you achive this using one offset, then come back and attempt this challenge again.

The rest of the algorithm you will have to figure out but in the end you should see the following (if your using a size of 5 for the pyramid).

```c
    # #    
   ## ##
  ### ###
 #### ####
##### #####
```