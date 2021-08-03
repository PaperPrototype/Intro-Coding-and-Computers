![] show picture of mario's pyramid

The end goal for the tutorial is to print hashes to make a pyrmaid like the one in mario. Below is an example.

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
	printf("   # \n");
    printf("  ## \n");
    printf(" ### \n");
    printf("#### \n");
}
```

Run this code. The problem with this code is that the pyrmaid will never change! If we use a for loop we can dynamically change the pyramid based on a size. Change your code to the following.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	for (int hash = 0; hash < size; hash++) 
	{
        printf("#");
	}

	printf("n\");
}
```

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
	
	// new loop
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

Run this. It will print 5 hashes, stacked on top of eachother 5 times.

```
#####
#####
#####
#####
#####
```

To slowly make hashes increase as we move down we need an offset number. We will increase this offset number every stack.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

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

		offset++;

		printf("\n");
	}
}
```

Every time we print a hash we increase the hash variable. Run this code. You will see this.

```
#
##
###
####
#####
```

Huh... its stacked the wrong way. We are increasing the offset each stack. If the current hash number is greater than the offset then we print a hash. So we got

```
#
##
###
####
#####
```

We recommend you pause and try to figure this out yourself. There is many ways to solve this.

The answer we found was:

first flip the hashes updside down.

```
#####
#### 
###  
##   
#  
```

You can do this by starting the the hash number at 5, so `int hash = size; hash > 0; hash--)` and decreasing it. Then changing the `if` statement to check if the hash is *bigger* than the offset in the `if` statement.

Then replace printing the hashes using spaces. This results in the following being printed.

```   
    #
   ##
  ###
 ####
```

Which is not entirely correct (yes we are being picky). There is many complex solutions to this. But the easiest mental one is to add an offset to the `if` statement.
