![marios pyramid](/Assets/marios_pyramid.png)

This tutorial assumes you've finished the previous "Mario (Easy)" tutorial.

The end goal for this tutorial is to print hashes to make a half pyramid like the one in mario. Except in this case in needs to be slanted to the right.

(end goal)
```
    #
   ##
  ###
 ####
#####
```

Lets do it! Make a new replit called "mario2". Select the C programming language.

Now we'll put in the code from last time.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = size; hash > 0; hash--) 
		{
			if (hash <= offset + 1)
			{
				printf("#");
			}
		}

		offset++;

		printf("\n");
	}
}
```

The output into the console is

```
#
##
###
####
#####
```

Hmm, if invert the above `if` statement print hashes instead of spaces and then do an `else` statement that prints the hashes, we can flip the pyramid!

```c
			if (hash > offset + 1)
			{
				printf(" ");
			}
			else
			{
				printf("#");
			}
```

Now run the code with the new if statement so that it looks like this.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = size; hash > 0; hash--) 
		{
			if (hash > offset + 1)
			{
				printf(" ");
			}
			else
			{
				printf("#");
			}
		}

		offset++;

		printf("\n");
	}
}
```

If you run this code it will flip the pyramid!

```
    #
   ##
  ###
 ####
#####
```