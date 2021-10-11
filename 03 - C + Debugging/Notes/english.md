# Terminology

Interpreted Language
> A text based programming language that an *interpreter* interprets into binary instructions as it reads them.

Interpreter
> A program that reads Unicode characters (aka text), and figures out the instructions (aka code) we are writing as it reads them.

Compiled Language
> A text based programming language that gets compiled (through a process called "compiling") into the binary instructions as a program or app.

Syntax
> A specific way of writing code so that the compiler can correctly process convert it to binary instructions (0s and 1s).

Syntax "Sugar"
> A way of coding something using a shortcut.

Functions
> ```c
>   int add(int a, int b) {
>       return a + b;
>   }
> ```
> ```c
>   void print_hello() {
>       printf("Hello");
>   }
> ```

IEEE
> Institute of Electrical and Electronics Engineers. They decided the format for the `float` type in memory

Truncation
> Cutting off the decimal places when use an int, or convert a float to an int. It is best to round the number before converting from a float to an int.

Compiler directives
> Code that tells the compiler to do something in the pre-process stage.

# C Keywords

`return`
give back a number. Any code after a `return` will not get run.

`break`
exits a loop

`include`
- `.h` files after the `include` command get surrounded by triangle brackets `<>`. 

- `.c` files after an `include` command get surrounded by double quotes `""`.

# loops

`while`
while the condition is true it loops the code inside.
example: prints "Hello world" forever
```c
#include <stdio.h>

int main(void) 
{
    while (1) 
    {
        printf("Hello world");
    }
}
```

`for`
Like a while loop that increases a number until a certain point.

for loop example: prints "Hello world" 5 times
```c
#include <stdio.h>

int main(void) 
{
    for (int i = 0; i < 5; i++;) 
    {
        printf("Hello world");
    }
}
```
is the same as
```c
#include <stdio.h>

int main(void) 
{
    int i = 0;
    while (i < 5) 
    {
        printf("Hello world");

        i++;
    }
}
```

# conditions

`if` checks if the condition is true, if it is then runs the code in the curly brackets.

`else if` must go after an `if` statement. Checks if the condition is true, if it is then runs the code in the brackets

`else` must go after an `if` or `else if` statement. There is no condition, runs if the previous if statement was false.

Less than
`<`
- `2 < 3` = `true`
- `3 < 2` = `false`

Greater than
`>`
- `2 > 3` = `false`
- `3 > 2` = `true`

> You (usually) use your right hand to write words so you can remember the greater than symbol using this pun "your right hand opens towards the left hand and eats it! because it is greater than your left hand".
> 
> If you open your right hand towards your left you make a *greater than* symbol `>`.

# syntax sugar

`+=`
- `num += 2`
- same as `num = num + 2`

`-=`
- `num -= 2`
- same as `num = num -2`

`/=`
- `num /= 2` 
- same as `num = num / 2`

`*=`
- `num *= 2` 
- same as `num = num * 2`

`%=`
- `num %= 2`
- same as `num = num % 2`

### super sugary syntax
`++`
- `num++`
- same as `num = num + 1`

`--`
- `num--`
- same as `num = num - 1`

# Types

### floating point numbers
`float` and `double`
- Numbers that support decimal points
- `float` is 32 bits
- `double` is 64 bits

- For a detailed explanation see
- IEEE Standard 754 Floating Point Numbers http://steve.hollasch.net/cgindex/coding/ieeefloat.html

### Integers
`int` and `long`
- Numbers that don't support decimal points
- `int` is 32 bits
- `long` is 64 bits

### Characters
`char`
- ASCII "number" type (under the hood `char`s are is just a number).
- numbers up to 256

### Booleans
The stdbool.h file code http://gel.sourceforge.net/examples/stdbool_8h-source.php

`true`
An alias for the number 1

`false`
An alias for the number 0

# Included headers
"unistd.h"
- `sleep` function
- https://www.poftut.com/what-is-sleep-function-and-how-to-use-it-in-c-program/

"stdio.h"

"stdbool.h"
- booleans use 1 byte = 8 bits
- `true` is an alias for 1
- `false` is an alias for 0