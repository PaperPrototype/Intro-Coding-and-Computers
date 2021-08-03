![] show picture of mario's pyramid

The end goal for the tutorial is to print hashes to make a pyrmaid liek the one in mario. Below is an example.

(example)
```
~/Hello-C$ ./mario
    #
   ##
  ###
 ####
#####
```

Lets do it! Make a new replit called "mario".

Now we could print out hashes out manually. Type in the following code.

```c
#include <stdio.h>

int main(void) {
	printf("   # \n");
	printf("  ## \n");
	printf(" ### \n");
	printf("#### \n");
}
```

Run this code.

The problem is it limits us to a certain pyramid size!

But... if we use a for loop we can make our pyramid be any size we want.

```c
#include <stdio.h>

int main(void) 
{
	int size = 5;

	for (int hash = 0; hash < size; hash++) 
	{
        printf("#");
	}
}
```

Run this code. It prints 5 hashes in a row.

```
#####
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

    printf("\n");
}
```

This prints out 5 hashes with a newline at the end.

```
#####
```

Now lets put each row of hashes in another loop so that we "stack" the rows.

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

Now we need an offset that we increase every stack. This will give us a bigger offset each stack. 

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

			printf("#");
		}

		offset++;

		printf("\n");
	}
}
```

We can use that offset and check if the current hash is less than the offset giving us a slowly increasing stack!

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

			if (hash <= offset) {
				printf("#");
			}
		}

		offset++;

		printf("\n");
	}
}
```

Run this code. You will see this.

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
