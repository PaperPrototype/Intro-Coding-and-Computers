# Terminalogy
Interpreted Language
> A text based programming language that an *interpreter* interprets into binary instructions as it reads them.

Interpreter
> A program that reads Unicode characters (aka text), and figures out the instructions (aka code) we are writing as it reads them.

Compiled Language
> A text based programming language that gets compiled (through a process called "compiling") into the binary instructions as a program or app.

Compiling
> The process of converting text into binary instructions

Clang
> A compiler for the C family of programming languages C, C++, Objective-C, Objective-C++.
> clang explained in detail https://www.joshwieder.net/2014/11/compiling-c-using-clang.html

Syntax
> A specific way of writing code so that the compiler can correctly process convert it to binary instructions (0s and 1s).

Syntax "Sugar"
> Ways of coding something using a shortcut.

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
> Institute of Electrical and Electronics Engineers

Truncation
> Cutting off the decimal places when use an int, or convert a float to an int. It is best to NOT do convert from a float to an int, and round the number. 

# CLI Commands

Compile and run
`make myProgram`
`./myProgram`

Change Directory

Clear shell
`ctrl` + `L`

Cancel (Stop) program
`ctrl` + `C`

# C Keywords

### loops

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

### conditions

`if` checks if the condition is true, if it is then runs the code in the brackets

`else if` must go after an `if` statement. Checks if the condition is true, if it is then runs the code in the brackets

`else` must go after an `if` statement. There is no condition, runs if the previous if statement was false.

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

### Booleans
The stdbool.h file code http://gel.sourceforge.net/examples/stdbool_8h-source.php

`true`
An alias for the number 1

`false`
An alias for the number 0

### syntax sugar

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
float and double
> Numbers that support decimal points
> 
> For a detailed explanation see
> IEEE Standard 754 Floating Point Numbers http://steve.hollasch.net/cgindex/coding/ieeefloat.html