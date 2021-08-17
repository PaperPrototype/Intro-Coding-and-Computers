![] TODO show picture of mario's pyramid

The end goal for the tutorial is to print hashes to make a half pyrmaid like the one in mario. Below is an example.

(example)
```
#
##
###
####
```

First watch this walkthrough (click on the picture, it is a link to the youtube video).

![![](https://i.ytimg.com/vi/zm3D1CHDt0s/hqdefault.jpg?sqp=-oaymwEcCNACELwBSFXyq4qpAw4IARUAAIhCGAFwAcABBg==&rs=AOn4CLA7EJlXDh12QBbJ1nQ1fX-lgUwoww)](https://www.youtube.com/watch?v=zm3D1CHDt0s)

Lets do it! Make a new replit called "mario". Select the C programming language.

Now we could can print out the hashes manually using the below code. (write the below code).

```c
#include <stdio.h>

int main(void) 
{
	printf("#    \n");
	printf("##   \n");
	printf("###  \n");
	printf("#### \n");
}
```

We manually make the pyramid using 4 printf's.

Run this code. The problem with this code is that the pyrmaid will never change! If we use a for loop we can dynamically change the pyramid based on a size. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int size = 4;

	for (int hash = 0; hash < size; hash++)
    {
        printf("#");
    }

    printf("\n");
}
```

The above for loop starts the `hash` variable at `0`. It increases the hash number until it reaches `3`, then the loop stops. In total the loop will have run 4 times (0, 1, 2, 3 <- 4 times).

Run this code. It will print 4 hashes in a row.

```
####
```

This code loops, and every time it loops it increases the `hash` variable and prints a hash. Once the hash variable is greater than the `size` variable (which is set at 4) then the loop stops.

We can put our loop (that prints hashes) inside of another loop to "stack" the hashes. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int size = 4;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = 0; hash < size; hash++)
		{
            printf("#");
		}

		printf("\n");
	}
}
```

We make sure to add a newline after every row of hashes. Run this. It will print 4 rows of hashes, stacked on top of eachother 4 times.

```
####
####
####
####
```

To slowly make hashes increase as we move down we need an offset number. We will increase this offset number every "stack".

```c
#include <stdio.h>

int main(void) 
{
	iint size = 4;
	int offset = 0;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = 0; hash < size; hash++)
		{
			if (hash <= offset)
			{
				printf("#");
			}
		}

		printf("\n");
		offset++;
	}
}
```

Every time we print a hash we increase the hash variable, but, we increase the offset every "stack" loop, so for every row the offset number gets bigger.

The `<=` stands for "less than or equal to", so you can read this as.

```
if hash number is less than or equal to offset
{
	print "#"
}
```

Running this code will yield the following.

```
#
##
###
####
```

And we made a half pyramid! Yay! If your still unsure of how the code worked at each step of the program you can use Replits debugger! Just add breakspoints (by clicking next to the line of code number), and then open Replits debug tab and click play (make sure you click the play button in the debugger, and not the main play button at the top center).