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
`while`

`if`

Less than
`<`

Greater than
`>`

> You (usually) use your right hand to write so it is "greater" than your left hand.
> 
> use this pun "your right hand opens towards the left hand and eats it! because it is greater than your left hand".
> 
> If you open your right hand towards your left you make a *greater than* symbol `>`.
> 
> Now its easy to remember to less than symbol `<` because it gets eaten by the greater right hand.

# Types
float and double
> Numbers that support decimal points
> 
> For a detailed explanation see
> IEEE Standard 754 Floating Point Numbers http://steve.hollasch.net/cgindex/coding/ieeefloat.html