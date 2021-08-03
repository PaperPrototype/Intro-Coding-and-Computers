![] TODO show picture of mario's pyramid

The end goal for the tutorial is to print hashes to make a half pyrmaid like the one in mario. Below is an example.

(example)
```
#
##
###
####
#####
```

Lets do it! Make a new replit called "mario".

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

Run this code. The problem with this code is that the pyrmaid will never change! If we use a for loop we can dynamically change the pyramid based on a size. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	for (int hash = size; hash > 0; hash--) 
	{
        printf("#");
	}

	printf("\n");
}
```

The above for loop starts the `hash` variable at `0`. It decreases the hash number until it reaches `0`.

Run this code. It will print 5 hashes in a row.

```
#####
```

This code loops, and every time it loops it increases the `hash` variable and prints a hash. Once the hash variable is greater than the `size` variable (which is set at 5) then the loop stops.

We can put our loop (that prints hashes) inside of another loop to "stack" the hashes. Change your code ot the following.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	for (int stack = 0; stack < size; stack++)
	{
		for (int hash = size; hash > 0; hash--) 
		{
			printf("#");
		}

		printf("\n");
	}
}
```

We make sure to add a newline after every row of hashes. Run this. It will print 5 hashes, stacked on top of eachother 5 times.

```
#####
#####
#####
#####
#####
```

To slowly make hashes increase as we move down we need an offset number. We will increase this offset number every "stack".

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

Every time we print a hash we increase the hash variable, and check if the hash variable has gotten bigger than the offset (remember we increase the offset every "stack" for loop). 

The `<=` stands for "less than or equal to", so you can read this as.

```
if hash number is less than or equal to offset + 1
{
	print "#"
}
```

When we check if the current hash number is less than the offset we have to add 1 to correct the pyramid slightly. Otherwise you would see this.

```

#
##
###
####
```

Which isn't wrong... but its not what we want. Run the above code to see this.

```
#
##
###
####
#####
```

And we made a half pyramid!