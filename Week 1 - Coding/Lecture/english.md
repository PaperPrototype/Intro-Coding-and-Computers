Last week we talked about how computers represent data and instructions using only two symbols 0 and 1, representing the *millions and millions* of dollars... I mean switches, in the computers memory. 0 represents off, and 1 represents on.

The programming language we used, called Python, was an interpreted language. Python is a program file (of 0 and 1 instructions), that reads in our "code" in the form of english words (aka *string* of Unicode characters), and then figures out how to run that code on your processor as 0 and 1 instructions.

We are now going to learn a new language called C. This language is a *compiled* language. It is written as text that gets converted to binary instructions by a programm called a *compiler*.

Remember how functions work in Python?

```py
def main():
    # put code here
    print("hello world")

main() # run the code
```

Well in C there is a function that gets called automatically. Except here's the catch, it is the only function that gets called! Any code that we want to run, including our own functions, has to go inside of the "main" function (which is the only function that gets called by default in C, otherwise your computer wouldn't know where to start).

Lets write this function. Go to https://replit.com/ and make a new replit.

(if you don't see the "New replit" button, it is probably hidden. To find it, look in the top left corner of the website, you should see three lines, click those. Then you should see a blue button)

This time select C as the programming language. Name it "Hello C". Now click "create repl".

Now there should already be a file called "main.c". In it you should see the following.

```c
#include <stdio.h>

int main(void) {
  printf("Hello World\n");
  return 0;
}
```

Delete everything except for the function called "main" so that the code looks like this. Don't run this code yet, as it will not work.

```c
int main(void) {
  // code goes here
}
```

This is the "main" function in C.

The word "int" in front of the function, tells C that `main` *returns* an integer.

(In C we don't use "def" for defining a function. Other languages often use "fn" or "func" for functions)

You will also see the word "void" inside of the functions input. In C we have to tell the computer that the function *doesn't* take any input, so we type the `void` keyword.

(When using Python, the Python interpreter automatically assumes you don't want input if you don't put anything in the parenthesis "()")

You will notice the code inside of the function goes inside of curly brackets "{}". This is what C uses instead of the colon ":".

```c
int main(void) {
  // code goes here
}
```

Now lets make our own function, it will add 2 numbers together. Make another function under `main` so that the code looks like this.

```c
int main(void) {
  
}

int add(int a, int b) {
  return a + b
}
```

We take as input two "integers". In C we have to always know the *type* "is this a number, or is it some letters?".

We tell the computer this is an integer (aka number) by putting a "type" in front of the functions variables. In this case the *type* is an `int` (aka integer, a number with no decimal places).

The `int a, int b` are two integer parameters for the `add` function.

(remember, function inputs are called "parameters" meaning "function variable").

We tell C that the `add` function *returns* (aka gives back) an `int` by putting "int" in front of the function.

Inside of `main`, make a variable called "result" that holds what the `add` function gives us (aka "returns").

```c
int main(void) {
  int result = add(12, 12)
}

int add(int a, int b) {
  return a + b
}
```

The `result` variable also has a type, its type is `int`.

This code still won't run though!

In C, whenever we type a line of code we have to end it with a semicolon ";". This is how C tells one line of code apart from another.

```c
int main(void) {
  int result = add(12, 12);
  int result2 = add(12, 12);
}

int add(int a, int b) {
  return a + b;
}
```

You can't just say "get the next line of code". This is because "the next line of code" is stored using a "newline" symbol `\n`. So our code actually looks like this in the file.

`int main(void) {\n  int result = add(12, 12);\n  int result2 = add(12, 12);\n}\n\nint add(int a, int b) {\n  return a + b;\n}`

(Except most "text editors" (like the one we are using) don't show you the newline symbol "\n", they just make a newline)

So yeah, we use a semicolon ";" to make it easier for C. Although when we made the `add` function we don't have to add a semicolon since it is easy to tell when the function ends. Eventually you will figure out where to put semicolons and where to not put them.

Sadly, this code (still!) won't work because C reads code from top to bottom. So when C reads the first function (aka `main`) it doesn't know what the `add` function is because it hasn't seen it yet.

(Again Python took care of this for us, while C won't)

```c
int main(void) {
    int result = add(12, 12); <- where did `add` come from?
    int result2 = add(12, 12);
}
```

and honestly we wouldn't know where `add` was unless we kept scrolling down to find it.

So we just have to put the `add` function above `main`. Change the code so that `add` is above `main`.

```c
int add(int a, int b) {
  return a + b;
}

int main(void) {
  int variable = add(12, 12);
}
```

Now you can run this code!

There is a shortcut for being able to put a function below main.

```c
// function hint
int add(int a, int b);

int main(void) {
  int variable = add(12, 12);
}

int add(int a, int b) {
  return a + b;
}
```

So above main we put a function "hint". Interestingly we have to put a semicolon ";" at the end of the hint. This is because C automatically figures out when you finish a function by looking for the curly brackets "{}" that contain the code for the function.

If we take the curly brackets away then C doesn;t know when the function ends. So we have to put a semicolon ";". 

(Why a semicolon? I honestly don't know and haven't taken the time to look it up)

# Errors? 
If you get a whole bunch of errors... Just scroll up to the first error at the top, since the rest of the errors are the *compiler* (aka program that converts code to binary instructions) getting confused from the first error.

If you encounter any errors and can't figure them out feel free to join our discord to get help https://discord.gg/QhqTE4t2tR <- here is the invite link.

Nothing gets printed to the console! Lets work on that.

# Printing
The `print` function in C doesn't come builtin, we have to "include" code written by someone else (that figures out the specific binary (0 and 1) instructions). We use a hash symbol "#" followed "include". "include" is called a "command".

Commands after the hash "#" are things the the compiler should "pre-process". In this case we want to *include* all the code from the "stdio.h" file into our main.c file.

Change the code to the following.

```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

int main(void) {
  int variable = add(12, 12);
}
```

(The name of the file we want to include is surreounded by "<>")

"std" is short for "standard", and "io" is short for "input output". 

When we *include* this file, the compiler literally replaces `#include <stdio.h>` with the code from the "stdio.h" file.

(stdio.h is used so often it (usaually) automatically gets downloaded along with a compiler)

The ".h" means it is a C "header" file. Headers files are code that is for "program code" to use. "main.c" will get compiled into a program.

Now that we've included the standard input output header, we can send output to the console using its `printf` function (`printf` meaning "print formatted").

```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

int main(void) {
  int variable = add(12, 12);
  printf("Hello, world");
}
```

Now run this code. You will see "Hello world" get printed.

![replit print hello world](/Assets/Week_0/replit_print_hello_world.png)

But the console didn't make a newline after printing! So we have to add this manually ourselves. (Again, Python added "\n" for us).

```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

int main(void) {
  int variable = add(12, 12);
  printf("Hello, world\n");
}
```

And now a newline will be added.

# Print formatted
How can we print a variable?

In C we have to declare the type a variable holds. `printf` also makes us put *types*.

In `printf` you use the percent symbol `%` followed by a letter to represent a *type*. In this case `variable` has a type of `int`. So in `printf` we have to write `%i` which stands for the `int` type.

Change the code to the following.

```c
#include <stdio.h>

int main(void) {
  int variable = add(12, 12);

  printf("%i \n", variable);
}
```

Run this code. You will see that the "%i" in the string gets replaced by an 24 (we also added a newline "\n").

We refer to the percent sign "%" *types* for `printf` as "conversion specifiers". These *conversion specifiers* tell `printf` *how* to treat the 0s and 1s of a variable. 

Here is a list of *conversion specifiers*.

```
commonly used conversion specifiers
  %d    int (signed decimal integer) 
  %u    unsigned decimal integer 
  %f    floating point values (fixed notation) - float, double 
  %e    floating point values ("exponential notation" (aka 11.4e+10)) 
  %s    string 
  %c    character  
```

We can use the "%c" conversion specifier to tell `printf` to treat 24 like an ASCII character.

```c
#include <stdio.h>

int main(void) {
  int variable = 24;

  printf("Hello %c\n", variable);
}
```

Run this code.

It will print out "Hello " with nothing afterwards. This is because the number 24 maps to a character that the web browser doesn't support (I think?). Change the number to 77, and you will see an uppercase "M" get printed, "Hello M".

The "f" in `printf` just means print a "formatted" *string* standing for the fact we can replace the *converson specifiers* with a variable.

(Why all the techinical words? When talking to another programmer it's nice when you can figure out what the heck he is talking about)

# Comments
In python we could make programmer comments. In C we can do the same thing, with different syntax.

We use two slashes "//".

```c
#include <stdio.h>

int main(void) {
    int variable = 77;

    // Convert int to char
    printf("Hello %c\n", variable);
}
```

notice the `// Convert int to char`, this will be ignored by `make`. ("make" is one of many compilers for C).

# Command Line Interface
Clicking the run button (at the top center) is a shortcut button made by Replit that runs a program called a compiler. The compiler takes our text code and converts it to binary (0s and 1s). Then Replit runs the "program" file.

But how can we compile the code ourselves? And then run the resulting (binary) program file?

You are used to using all sorts of buttons, and menus for *doing* stuff in your computer, but before there was graphical buttons and menus, there was text-based commands.

You will notice the tab called "shell".

![replit ide shell](/Assets/Week_1/replit_ide_shell.png)

You will notice the word "Hello-C", this means we are in the "Hello-C" folder (at least in the picture above. Yours may be different).

If we want to change the folder we are in we can run a command. 

Type "cd" (a command) into the shell. "cd" stands for "Change Directory", or in plain english "change folders".

The "cd" command takes in an *argument*. Type "/" after "cd" like this `cd /`. Then click the return (or enter) key on your keyboard. This runs the command.

Now we are in the root folder of the computer! (Actually a server computer that is running our code). "/" stands for the root folder of a computer.

Now lets "list" all the files and folders in the root folder! Type `ls` and hit enter.

Ooooh. Thats quite a lot of files and folders! How can we get back to our "Hello-C" folder?

The "Hello-C" folder is our "home" folder, so if we type `cd` and hit enter (without any arguments), the `cd` command will take back "home", which is conviently the "Hello-C" folder!

So how did this all work? When we type `cd` (and some arguments) and hit enter, the *shell* looks for a program called `cd`. Once it finds the program called `cd` it sends the arguments we typed and passes them to the `cd` program. `cd` then figures out what to do with the arguments.

(You could actually make your own "command line" programs!)

How does the shell, or "command line interface" know the difference between `cd` and the arguments we gave it? (aka `cd /`).

Well we typed in a spce between them! That is how it can tell. So, if you didn't put a space you might get an error. Also if you type in the name of a "command line" tool (like `cd`) that doesn't exist, you will also get an error.

To clear all the text in shell, hold the `ctrl` key and click `L`.

(The black "console" tab can run the same commands, but it is a simplified shell, and it doesn't tell us what folder we are currently in. So for this course we will be using the shell, and we recommend you do too as we will switch to using your computers shell, so it will help to be familiar with shell layouts).

# Compiling
Now that we know how to use a CLI (Command Line Interface) we can run a compiler.

Type in `cd` and hit enter to make sure you are in your "home" directory (aka folder).
Type in `ls` to see that "main.c" file is in that same folder as you.

Now type `make`, and the name of our program (aka "main.c") except leave out ".c", like this `make main`, click the `enter` (or `return`) key to run the command (this may take a second). 

`make` is the name of a compiler, `main` is the name of the file to compile. `make` automatically figures out that "main" is the name of a file called `main.c`.

Now type `ls` and click enter to see the (binary instruction) program files that the compiler made. You should see this

```
~/Hello-C$ ls
main  main.c
```

Ha! The file called "main" (without the ".c") is our program! The binary information in it is referd to as "machine code", aka code for the computer to run.

To run "main" (our program) we need to "open" or select the program file called `main`.

Typing a single period "." (in the shell) refers to the folder we are in right now (aka "Hello-C"). To refer to the "main" file we do "/main". 

So, to select "main" and run it, type the following `./main`. THen clicking enter will run the program! You should see "Hello M" get printed (from our main.c code).

From now on we will be using the shell to run our programs instead of the button at the top. Please do the same as you will need to know how to use a shell for a coming week when you start using your computers builtin shell.

# Commands
There are other *commands line tools* like `cd` and `ls`. Here is a list of some of them.

`mkdir`
> stands for: Make Directory, aka "make folder"
> does: Makes a folder in the current folder
> usage: `mkdir myFancyNewFolder`

`touch`
> stands for: touch?
> does: Make new empty file, or update existing an files timestamp (eg. last edited date)
> usage: `touch myFancyFile` <- makes a file called "myFancyFile" in the current folder

`mv`
> stands for: Move
> does: Moves a file (or renames a file)
> usage: `mv originalFile.c myFancyFolder` <- moves "originalFile.c" into "myFancyFolder".

`rm`
> stands for: Remove
> does: Deletes a file
> usage: `rm myHorribleFileThatIWantToDelete`

`rmdir`
> stands for: Remove Directory,
> does: Deletes a folder and any files/folders inside of it
> usage: `rmdir myHorribleFolder`

`cd`
> stands for: Change Directory
> does: Moves you into a different folder
> usage: `cd myRandomFolder`
> tips:
>   `cd ..` to go into your "parent folder".

`ls`
> stands for: "list" as in "list everything and show me"
> does: Lists all the files and folders in yur current Directory (aka current folder)

These commands should work on any Linux or MacOS *command line interface* (aka shell). By default the Mac shell app is called "Terminal", but you can use an alternative terminal app. On Linux there are different ones (I think? pull request to correct?). 

(Although, these commands will not work on Windows since Windows has its own set of commands. Window's default \ command line interface app is called "Command Prompt").

Lets make a folder. Type in `mkdir NewProject`. This will make a folder called "NewProject", type `ls` (and hit enter) to see a a list of files and folders inside of your current folder. You should see 

```
~/Hello-C$ ls
main  main.c  NewProject
```

Now move into the "NewProject" folder by typing `cd NewProject`. You should now see `~/Hello-C/NewProject$ ` which tells you you are in the "NewProject" folder.

Now lets make a new "main.c" file. Type in `touch main.c`. This command makes a file called "main.c". You should see the file in Replits file viewer.

![replit ide touch command](./Assets/Week_O/replit_ide_touch_command.png)

Click the file, you should be able to open it and edit it.

Type run the `ls` command. You should see "main.c" get listed.

(From the folder we are in we could compile the new "main.c" file by running `make main`)

Lets *rename* the new "main.c" file. Type `mv main.c deleteMe`. 

(The `mv` command can also rename files. eg -> `mv oldFileName newFileName`.)

Replit will break since you renamed the file it was trying to show you!

Once you reload the page you should see the `main.c` file was renamed to `deleteMe`. Open the shell tab again. We have been moved back to the "Hello-C" folder. Run `cd NewProject` to go into the "NewProject" folder in the shell.

Run `ls` to see the `deleteMe` file.

Now run `rm deleteMe`. This runs the "remove" command and will delete the "deleteMe" file.

Run `ls` again, nothing gets listed!

How do we get back to our parent folder? Since "Hello-C" (our parent folder) is the home folder we could just type `cd` and click enter, since that takes us back to the home directory... But don't do that! What if the parent folder was not the *home directory*?

To refer to a parent folder we use two periods `..`. Run this command `cd ..`.

".." stands for "parent folder". So `cd ..` says "change directory to parent folder".

Run `ls`, you should see "NewProject" get listed.

Now that we are back in the "Hello-C" folder lets delete the "NewProject" directory (aka folder).

Run `rmdir NewProject`. `rmdir` stands for Remove Directory. The command *removes* the "NewProject" *directory*.

Again, replit will break. Just click on the old `main.c` file.

Run `ls`. The "NewProject" directory should be gone.

Hold `ctrl` key and click `L` to clear the commands in the shell.

# Loops?

# Getting input - Strings, memory addresses (pointers), and arrays and iterators
TODO place above CLI? Or is it good to take a break from coding?
- Yes. Now while coding they can use the shell instead of the button

# Linear search

TOSAY:
If you didn't take the "Searching Algorithms" tutorial for week 0 then we highly recommend you do.

- Don't expect they have done the "searching algorithms" tutorial.

AFTER "linear search" finish the lecture

To cover? (don't do in same order)
- addition `int` max number size
    - first bit used for negative or positive sign

- int overflow
- float overflow

- int division equals no decimal places! (aka truncation)
    - cast to float which is a number with decimal places

- increase a number
    - equal sign means "gets" not "equal to"
    - syntax sugar for increasing a number

- loops
    - while true
    - count up to 50
    - syntax sugar
    - all in one line with `for`

- if statements (conditions)
    - agree

- strings (aka arrays + pointers)

- `cd ..` go to parent folder?

- linear search in C
- binary search in C

TODO talk about
- IDE (Integrated developer environment)
- the C language

Coding in C

Coding with compilers
 - hello world
 - 

functions
variables