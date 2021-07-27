![] show picture of mario's pyramid

Goal: Print hashes in the Terminal to make a half pyramid like the one from Mario.

```
~/Hello-C$ ./mario
    #
   ##
  ###
 ####
#####
```

Make a new file called `mario.c` using `touch`. Open it using the "Files" tab.

We could print out hashes out manually. Type in the following code.

```c
#include <stdio.h>

int main(void) {
	printf("   # \n");
	printf("  ## \n");
	printf(" ### \n");
	printf("#### \n");
}
```

Compile this using `make`. Then run it using `./mario`.

This limits us to a certain max pyramid size though!

But if we use a for loop we can make our pyramid be any size we want.

```c
#include <stdio.h>

int main(void) {
	int size = 5;

	for (int hash = 0; hash < size; hash++) {
        printf("#");
    }
}
```

This prints 5 hashes in a row.

```
~/Hello-C$ ./mario
#####~/Hello-C$
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

We also change the placement of the first curly bracket `{`. This is perfeclty correct code, just a different way of writing it. This will make the loop code easier to read.

This prints out 5 hashes with a newline at the end.

```
~/Hello-C$ ./mario
#####
~/Hello-C$ 
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

This will print 5 hashes, stacked on top of eachother 5 times.

```
~/Hello-C$ ./mario
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

Compile this using `make`, then run it using `./mario`.

You will see this.

```
~/Hello-C$ ./mario
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

We recommend you pause and try to figure this out yourself. 

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