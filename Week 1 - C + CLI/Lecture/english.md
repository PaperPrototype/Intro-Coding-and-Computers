Last week we talked about how computers represent data and instructions using only two symbols 0 and 1, representing the *millions and millions of dollars*... I mean switches, in the computers memory. 0 represents off, and 1 represents on.

The programming language we used, called Python, was an interpreted language meaning it is a program file, that reads in our text based "code" (*string* of Unicode characters), and then figures out how to translate that code onto your processor as 0 and 1 instructions.

We are now going to learn a new language called C. This language is a *compiled* language (whereas Python was *interpreted*). 

This just means our code is written as text that gets "compiled" into a program file by a "compiler" program.

Remember how functions work in Python?

```py
def main():
    # put code here
    print("hello world")

main() # run the code
```

Well in C there is a function that gets called automatically. Except here's the catch, it is the only function that gets called! Any code that we want to run, including our own functions, has to go inside of the "main" function. This gives all computers a unifide way to have a "starting point" for where to run your program.

Lets write this "main" function. Go to https://replit.com/ and make a new replit.

(if you don't see the "New replit" button, it is probably hidden. To find it, look in the top left corner of the website, you should see three lines, click those. Then you should see a blue button)

This time select C as the programming language. Name the the project "Hello C", then click "create repl".

There should already be a file called "main.c". In it you should see the following.

```c
#include <stdio.h>

int main(void) {
  printf("Hello World\n");
  return 0;
}
```

Delete everything except for the function called "main" so that the code looks like this. 

```c
int main(void) {
  // code goes here
}
```

Don't run this code yet, as it won't do anything! (if replit did not give you this code automatically then just copy paste the above).

The above code is the "main" function in C, and is the program *starting point* that most computers use.

The word "int" in front of the function, tells C that `main` *returns* (aka "gives back") an *integer*.

(In C we don't use "def" for defining a function)

You will see the word "void" inside of the functions input. In C we have to tell the computer that the function *doesn't* take any input, which is what the `void` keyword is for.

(When using Python, the Python interpreter automatically assumes you don't want input if you don't put anything in the parenthesis "()")

You will notice the code inside of the function goes inside of curly brackets "{}". This is what C uses instead of Python's colon ":".

```c
int main(void) {
  // code goes here
}
```

Now lets make our own function, it will add 2 numbers together. Make a function under `main` so that the code looks like this.

```c
int main(void) {
  
}

int add(int a, int b) {
  return a + b
}
```

We take as input two "integers". In C we have to always know the *type*. A *type* tells C how to treat the 0s and 1s. "Is this a number? Is this a Unicode character?".

We tell the computer this is an integer (aka number) by putting the `int` *type* in front of the function's input variables.

(function variables are called "parameters").

We tell C that the `add` function *returns* (aka gives back) an `int` by putting `int` in front of the functions name.

### Variables
Inside of `main`, make a variable called "result" that holds onto what the `add` function returns ("gives back").

```c
int main(void) {
  int result = add(12, 12)
}

int add(int a, int b) {
  return a + b
}
```

The `result` variable has to have a type of `int`. C doesn't automatically figure out that the `result` variable should be an `int` (it could figure it out since the `add` function returns an `int`, and most programming languages do this).

This code still won't run though!

In C, whenever we type a line of code we have to end it with a semicolon ";". This is how C tells one line of code apart from another.

Change your code to the following.

```c
int main(void) {
  int result = add(12, 12);
}

int add(int a, int b) {
  return a + b;
}
```

You can't just say "get the next line of code". This is because "the next line of code" is stored as a "newline" symbol `\n`. So our code actually looks like this in the file.

`int main(void) {\n  int result = add(12, 12);\n  int result2 = add(12, 12);\n}\n\nint add(int a, int b) {\n  return a + b;\n}`

(Most "text editors" (Microsoft Word) don't show you the newline symbol "\n", they just make a newline)

So yeah, C makes us use a semicolon ";" so it can tell lines of code apart.

Although when making a function we don't have to add a semicolon at the end

```c
int add(int a, int b) {
    return a + b;
}; <- semicolon NOT needed!
```

...since it is easy to tell when the function ends by just using the ending curly bracket "}". You will figure out where to put semicolons and where to not put them given experience.

Sadly, our code (still!) won't work because C reads code from top to bottom. So when C reads the code inside of `main` it doesn't know what the `add` function is because it hasn't seen it yet.

```c
int main(void) {
    int result = add(12, 12); <- where did `add` come from?
}
```

(Again Python took care of this for us, while C won't)

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

Now you can run this code!.. Although it won't print anything...

There is a way to put a function below main. You just have to put a function "hint" above main.

```c
int add(int a, int b); <- function hint

int main(void) {
  int variable = add(12, 12);
}

int add(int a, int b) {
  return a + b;
}
```

"function hints" are called "prototypes". 

We have to put a semicolon ";" at the end of the function *prototype* because there are no curly brackets in a prototype just its name and parameters ("function variables").

# Main returns an int?
Main returns (gives back) a number right?

```c
// function hint
int add(int a, int b);

int main(void) {
  int variable = add(12, 12);

  return 0; <- main returns 0
}

int add(int a, int b) {
  return a + b;
}
```

The number `main` returns is an `int` (obviously). It represents an "error code". returning `0` means success (aka no error). Returning `1` means there was an error! But since we don't *have to* return an number we won't bother returning an "error code" from main.

Nothing gets printed to the console! Lets work on that.

# Printing + including
The `print` function doesn't come builtin in C. So we have to "include" code written by someone else that figures out the specific 0 and 1 instructions.

Change the code to the following.

```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

int main(void) {
  int result = add(12, 12);
}
```

We use a hash symbol "#" followed by "include". "include" is called a "command".

Commands after the hash "#" are things the compiler "pre-processes". Which means
when we *include* this file, the compiler literally replaces `#include <stdio.h>` with the code from the "stdio.h" file.

"including" is part of the "pre-process" stage that the compiler goes through to eventually convert our code into 0s and 1s.

"std" is short for "standard", and "io" is short for "input output". 

Where is the "stdio.h" code? The "stdio.h" code is used so often it comes builtin with the compiler (aka when you download a compiler it also downloads the stdio.h file).

The ".h" means it is a C "header" file. Headers files are normal C code except the code has already been turned into 0s and 1s! (This way the compiler doesn't have to compile all the *headers* we include and can just "link" them all to together in a stage called "linking"). The code in a header file is just a bunch of "function hints" to functions that are in the binary (0s and 1s) code file.

(You can also include `.c` files)

`.h` files after the `include` command get surrounded by triangle brackets `<>`. 

`.c` files after an `include` command get surrounded by double quotes `""`.

Now that we've included the standard input output *header*, we can send output to the console using its `printf` function (`printf` meaning "print formatted").

```c
#include <stdio.h>

int add(int a, int b) {
  return a + b;
}

int main(void) {
  int result = add(12, 12);
  printf("Hello, world");
}
```

Now run this code. You will see "Hello world" get printed.

![replit print hello world](/Assets/Week_1/replit_print_hello_world.png)

But the console didn't make a newline after "Hello world"! So we have to add this manually ourselves. (Again, Python added "\n" for us in its `print` function).

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

Now a newline will be added after the "Hello, world" string (we call words or phrases enclosed with double quotes `""` *strings*).

![replit print hello world with newline](/Assets/Week_1/replit_print_hello_world_2.png)

# Errors? 
If you get a whole bunch of errors when running code... Just scroll up to the first error at the top in the console, since the rest of the errors are the *compiler* (aka program that converts code to binary instructions) getting confused from the first error.

If you encounter any errors and can't figure them out feel free to join our discord to get help https://discord.gg/QhqTE4t2tR <- here is the invite link.

# Printing variables
How can we print a variable?

In C we have to declare the type a variable holds (aka `int result = 12;`). To print variabkes using `printf` we also have to tell it the *type* of the variable.

In `printf` you use the percent symbol `%` followed by a letter. In this case our variable is an `int`, so in `printf` we write `%i` which stands for the `int` type.

Change the code to the following.

```c
#include <stdio.h>

int add(int a, int b) {
	return a + b;
}

int main(void) {
  int result = add(12, 12);

  printf("%i \n", variable);
}
```

The `%i` is a placeholder (with a type), and will get replaced by the `result` variable.

Run this code. You will see that the `%i` in the string gets replaced by 24 (we also make sure to add a newline `\n`).

We refer to the percent sign "%" *placeholders / types* for `printf` as "conversion specifiers". These *conversion specifiers* tell `printf` *how* to treat the 0s and 1s of a variable. 

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

We can use the "%c" conversion specifier to tell `printf` to treat 24 like an ASCII character. Delete the add function and change ht code to this.

```c
#include <stdio.h>

int main(void) {
  int variable = 24;

  printf("Hello %c\n", variable);
}
```

Run this code.

It will print out "Hello " with nothing afterwards. This is because the number 24 maps to a character that is apparently invisible? (Go back to Week 0's notes to see what 24 maps to).

Change `variable` to hold 77. Run the new code and you will see an uppercase "M" get printed like this `Hello M`.

The "f" in `printf` just means print a "formatted" string. standing for the fact we can replace placeholders (aka *converson specifiers*) with a variable.

We can also have multiple *conversion specifiers*. Change the code to this.

```c
#include <stdio.h>

int main(void) {
    int variable = 77;
    
    char character = 'B';

    printf("Hello %c %c\n", variable, character);
}
```

The `character` variable has a type of `char`. We use single quotes `''` around single characters, and double quotes `""` around *strings* of characters (aka words / phrases).

We told `printf` to treat the `character` variable as a character, so we got `B`.

# Comments
In Python we can make programmer comments.

In C you use two slashes "//" for comments.

```c
#include <stdio.h>

int main(void) {
    int variable = 77;
  
    char character = 'B';

    // Treat 77 like ASCII character
    printf("Hello %c %c\n", variable, character);
}
```

notice the `// Treat 77 like ASCII character`, this comment will be ignored by the compiler.

# Command Line Interface
Clicking the run button (at the top center) is a shortcut button that compiles our code (a compiler takes our code and converts it to binary (0s and 1s) instructions). Then Replit runs the "program" file made by the compiler.

Buttons and Menus are called a "Graphical User Interface" (GUI). But before there was GUI's there was a "Command Line Interface", aka CLI.

How can we manually "compile" the code ourselves and run the program file, using a CLI?

We type in text-based "commands" and run them.

You will notice the tab called "shell".

![replit ide shell](/Assets/Week_1/replit_ide_shell.png)

You will notice the word "Hello-C", this means we are in the "Hello-C" folder.

If we want to change the folder we are in we can run a "command".

Type `cd` (a command) into the shell. 

```
~/Hello-C$ cd
            \____this is a command
```

`cd` stands for "Change Directory", or in plain english "change folders".

The `cd` command takes in an *argument* (aka input). Type slash `/` after `cd` like this.

```
~/Hello-C$ cd /
```

Click the return (or enter) key on your keyboard. This runs the command with the slash argument `cd /`.

Running `cd /` moved us into the root folder of the computer! (Actually a server computer that is running our code). slash `/` on its own usually refers to the *root* folder of a computer.

How can we view the files inside of the root folder? Type `ls` into the shell.

```
/$ ls
```

Then click the `enter` (or `return`) key on your keyboard. You will see a LOT of folders and files get listed. Hacking... Hehe. Just kidding...

(Use `ctrl` + `L` to clear the shell).

`ls` stands for "list", and it *lists* all the stuff inside of our current folder (our current folder is currently `/`, the root folder).

How can we get back to our "Hello-C" folder?!

The "Hello-C" folder is inside of a "home" folder. A *home* folder is a folder that has been marked as a default folder for the shell. (usually all the stuff for a specific user is in the users "home" folder (aka pictures, documents, the desktop folder).

To go to your home folder just type `cd` (without any arguments) and click enter.

```
/$ cd  <- ran cd
~$     <- now in the home folder
```

The tilde symbols `~` represents the "home" folder. Whats the name of our home folder? I don't know cause its usually replaced by a tilde symbol `~`, lol.

Now run the `ls` command.

```
~$ ls
Hello-C  _test_runner.py
~$ 
```

You will see our `Hello-C` folder get listed! To move into the Hello-C folder run `cd Hello-C`.

```
~$ cd Hello-C   <- ran a command to change the directory
~/Hello-C$ 
```

And now run `ls` to see our `main.c` file (where we've been writing our code) get listed.

```
~/Hello-C$ ls
main  main.c
```

One important thing to know is that Replit will automatically move you into the "Hello-C" folder after a few minutes of inactivity.

# Command Line Programs (aka Command Line Tools)
So how did this all work? When we type `cd` (and some arguments) and hit enter, the *shell* looks for a program called `cd`.

(there is a file called a "profile" with a list of programs for the shell that the shell uses to find the programs)

Once the shell finds the program called `cd` (using the information a "profile" file), it sends the *arguments* (aka input) we typed and passes them to the `cd` program (that the shell ran for us). `cd` then figures out what to do based on the arguments (sometimes we'll just get an error if `cd` couldn't understand the arguments we typed).

(You could actually make your own "command line" programs! We'll get to this later in the course)

How does the shell, a "command line interface", know what the arguments were?

Well we put a space after the name of the program `cd /` <- notice the space. So, if you didn't put a space you might get an error because the shell looked for a program called `cd/`.

To clear all the *text* and commands in the shell, hold the `ctrl` key and click `L`.

The black "console" tab is a simplified shell. It can do everything that the a shell can do. Although it doesn't tell us the folder we are currently in! So for this course we will be using the shell (not the console). We recommend you use the shell too since it is similar to your computers shell. (You can use the console if you want to, or if the shell stops working).

"Can I go into any folder in the computer by simply typing its name after `cd`?"

No, only the folders that are in the same folder as you (or your parent folder). To find out which folders are available to you run `ls`.

Although, you can type the full "path" to a folder from the root folder `cd /users/bob/Hello-C`. This takes you directly to "Hello-C" regardless of where you were. This is an example and would only work if there was a path of folders `/users/bob/Hello-C` from the root.

How do I get back out of a folder, into my "parent" folder?

Run `cd ..`. 

```
~/Hello-C$ cd ..   <- move into parent folder
~$ 
```

The `..` stands for "go to whoever my *parent* is", so we move into the tilde folder `~` (which conatained our folder).

Data in a computer is just a long line of switches (or electric charges). A *file system* is just a program that lets of think of that data in the form of files and folders.

# Compiling using a CLI 
Now that we know how to use a CLI (Command Line Interface) we can run a compiler (to *compile* our code into binary) using the CLI!

Type in `ls` to see the `main.c` file get listed.

Now type `make`, and the name of our program `make main` (without `.c`), then hit the enter (or return) key to run the command (this may take a second). 

`make` is the name of a compiler, `main` is the name of the file to compile. We can leave out `.c` since `make` automatically figures out that we mean `main.c` (if you type in `make main.c` then `make` will giv eyou an error).

Now type `ls` and click enter to see the file that has been made.

```
~/Hello-C$ ls
main  main.c
```

When we ran `make` it processed our `main.c` file and made a new *program file* called `main`! 

The binary information in the `main` program file (without the ".c") is refered to as "machine code", aka code for the computer to run.

When we clicked the "run" button earlier, replit was first compiling our code into a program file, then running the program file.

To run "main" (our program file) we need to "open" or select the program using commands.

So, to select "main" and run it, type the following `./main` and run this command. You should see "Hello M B" get printed!

A single period `.` refers to the folder we are in right now. To refer to a file (and open it) we type in its *directory* (where it is) using a slash `/myCoolFile`. So to open / run the our `main` program file we typed `./main`.

From now on we will be using the shell to run our programs instead of the button at the top. Please do the same as you will need to know how to use a shell for a coming week when we start using your computers builtin shell.

# List of Common Command Line Tools
There are other *commands line tools* like `cd` and `ls`. Here is a list of some of them that you can use for reference.

`mkdir`
> stands for: Make Directory, aka "make folder"
>
> does: Makes a folder in the current folder
>
> usage: `mkdir myFancyNewFolder`

`touch`
> stands for: touch?
>
> does: Make new empty file, or update an existing files timestamp (eg. last edited date)
>
> usage: `touch myFancyFile` <- makes a file called "myFancyFile" in the current folder

`mv`
> stands for: Move
>
> does: Moves a file (or renames a file)
>
> usage: `mv originalFile.c myFancyFolder` <- moves "originalFile.c" into "myFancyFolder".
> 
> usage: `mv oldFileName newFileName` <- renames the `oldFileName` file to `newFileName`

`rm`
> stands for: Remove
>
> does: Deletes a file
>
> usage: `rm myHorribleFile`

`rmdir`
> stands for: Remove Directory
>
> does: Deletes a folder and any files/folders inside of it
>
> usage: `rmdir myHorribleFolder`

`cd`
> stands for: Change Directory
>
> does: Moves you into a different folder
>
> usage: `cd myRandomFolder`
>
> tips:
>   `cd ..` move up into your "parent folder" (out of the folder you are inside of)

`ls`
> stands for: "list" as in "list everything and show it to me"
>
> does: Lists all the files and folders in yur current Directory (aka current folder)

These commands should work on any Linux or MacOS *command line interface* (aka shell). By default the Mac shell app is called "Terminal", but you can use any shell app. On Linux there are different ones (I think? pull request to correct?). If you are using Linux I assume you already know how to use a shell.

These commands will not work on Windows since Windows has its own set of commands. Window's default command line interface app is called "Command Prompt".

Lets make a folder using `mkdir`. Type in `mkdir NewProject`. This will make a folder called "NewProject", type `ls` (and hit enter) to see a a list of files and folders inside of your current folder. You should see 

```
~/Hello-C$ ls
main  main.c  NewProject
```

Now move into the "NewProject" folder by typing `cd NewProject`. You should now see 

```
~/Hello-C/NewProject$
```

which tells you you are in the "NewProject" folder.

Now lets make a new "main.c" file (Inside of the `NewProject` folder). Type in `touch main.c`. This command makes a file called "main.c". You should see the file in Replits file viewer.

![replit ide touch command](/Assets/Week_1/replit_ide_touch_command.png)

Click the file (using replits "Files" tab). You should be able to open it and edit it.

Run the `ls` command. You should see our new "main.c" file get listed as well.

(We could compile the new "main.c" file by running `make main`, but we haven't added any code to "main.c")

Lets *rename* the new "main.c" file using `mv`. Type `mv main.c deleteMe`.

(The `mv` command can rename files. eg -> `mv oldFileName newFileName`.)

(Replit might break oncew you rename the file)

Once you reload the page you should see the `main.c` file was renamed to `deleteMe`. Open the shell tab again. We have been moved back to the "Hello-C" folder. Run `cd NewProject` to go into the "NewProject" folder in the shell.

Run `ls` to see the `deleteMe` file.

Now run `rm deleteMe`. This runs the "remove" command and will delete the "deleteMe" file.

Run `ls` again, nothing gets listed since we deleted the `deleteMe` file.

How do we get back to our parent folder? 

To refer to a parent folder we use two periods `..`. Run this command `cd ..`.

".." stands for "parent folder". So `cd ..` says "change directory to parent folder".

Run `ls`, you should see "NewProject" get listed.

Now that we are back in the "Hello-C" folder lets delete the "NewProject" directory (aka folder).

Run `rmdir NewProject`. `rmdir` is a command for deleting folders and anything inside of them. `rmdir NewProject` *removes* the "NewProject" *directory*.

Again, replit might break. Just click on the old `main.c` file in the "Files" tab.

Run `ls`. The "NewProject" directory should be gone.

Hold the `ctrl` key and click `L` to clear the commands in the shell.

One last cool feature. You can go through your history of commands by using the up and down arrow keys. This way you don't have to constantly retype every command, you can just use a command you typed earlier.

# Numbers Overflow
Lets make a really big number and print it in C.

Make a new C program called `overflow.c` using `touch overflow.c`.

Go to the shell, run `touch overflow.c`. The `touch` command made a new file called `overflow.c`.

(If you named a file with the wrong name you can delete it using `rm`, then make it again using `touch`)

In the files tab click on the new file called `overflow.c` to open it.

Now write the `main` function and include `stdio.h` since we will be printing stuff to the console.

Your code should look like this.

```c
#include <stdio.h>

int main(void) {
  int a = 4000000000;

  printf("%i", a);
}
```

We set the variable `a` to the number 4 billion.

Run `make overflow` to compile our new program using `make`.
Run `ls` to see our new program called "overflow".
Run our new program using `./overflow`.

You should see the following get printed.

```
~/Hello-C$ ./overflow
-294967296~/Hello-C$ 
```

That number is definitally NOT 4 billion... lets first fix another error, we forgot to include a newline `\n`.

Change the code to add a newline.

```c
#include <stdio.h>

int main(void) {
  int a = 4000000000;

  printf("%i \n", a);
}
```

Compile our change and run the resulting program again.

Now why is the number `-294967296` showing up!?

Lets look at what 4 billion is in binary... Actually lets use a smaller number (lol) so that we don't have to break our mind over such a large number... So the number 47.

To make the number 47 we need 6 bits.

```
places  32th | 16th | 8th | 4th | 2th | 1st
bits    1      0      1     1     1     1 = 32 + 8 + 4 + 2 + 1 = 47
```

But... the type we are using gives us 4 bits for our number, and 1 bit for the *sign*.

```
sign | 8 | 4 | 2 | 1
1      0   0   0   1 = +1
```

If the "sign bit" is `1` the number is positive. If the sign bit is `0` then the number is negative.

```
sign | 8 | 4 | 2 | 1
0      0   0   0   1 = -1
```

What happens when we try to represent a 47 with a type that doesn't have enough bits? Our type can't hold 47, so it ends up cutting off the front of 47 and just putting the bits of 47 into the space it has.

```
PLACES             = 32 | 16  | 8 | 4 | 2 | 1

BITS (OUR NUMBER)  = 1  | 0   | 1 | 1 | 1 | 1  = 101111 = 47

TYPE               =     sign | 8 | 4 | 2 | 1

RESULT             =      0   | 1 | 1 | 1 | 1  =  01111 = -15
                                                  \___we are missing the first bit!
```

By putting 47 into a type that is too small we get negative 15! 

When we tried to put 4 billion into the `int` type our code broke and we got `-294967296`.

The `int` type in C has 32 bits. With 32 bits we could count as high as 4 billion... but the first bit is used for the "sign" of the number. So an `int` we can go almost as high as 2 billion, and as low as -2 billion.

We could switch to using a `long` which gives us 64 bits if we wanted to be able to represent 4 billion.

If we change the code to use the `long` type and try to compile we will get an error.

![replit error](/Assets/Week_1/replit_error.png)

You'll notice the green `%li` in the error. This is a hint saying we need to change the conversion specifier to a `long` conversion specifier which is `%li`.

Fix the code by either changing the conversion specifier in `printf` to `%li` or change the variable to an int and make the number smaller.

Run `make overflow.c`
Run `./overflow`

The `int` type has 32 bits. The first bit is used for the sign. So we have 31 bits for counting. with 31 bits we can hold a number that is 2 to the 31 power, which is 2147483648. We can write this as `2^31`.

# Casting a type
Lets divide two `int`s. Although, the `int` type doesn't let us represent decimal places like `0.5` or `1.34`. So what happens?

Run `touch division.c` to make a new C code file.

Open it by clicking the file.

Copy Paste the following code into the file.

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;
}
```

Now lets divide `a` and `b` and store its result. Now we know that `2 / 3` equals `0.6666` with `6` going on forever.

If we want the result to support decimal places we can't use an `int`. Instead we have to use a `float` which supports decimal places (aka `0.5` and `0.34` are examples of decimal places).

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;

  float result = a / b;
}
```

We name the variable that holds onto `a / b` "result".

Now lets print the result.

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;

  float result = a / b;

  printf("%f \n", result);
}
```

The `%f` is a conversion specifier for a float. We also make sure to add `\n`.

Compile the program using make by running `make division`.
Then run the program `./division`.

We get `0.000000`. We call this "truncation". So what happened?

When we divided `a` and `b` their type is an `int`. And so they gave back an `int` which *cut off* (aka truncated or ignored) the decimal places and we ended up with `0.000000`.

To fix this we have to convert `a` and `b` to a `float`.

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;

  //            "cast" a and b to float
  float result = (float) a / (float) b;

  printf("%f \n", result);
}
```

We use parenthesis `()` around the `float` type in front of `a` and `b`. This converts `a` and `b` to a `float`.

Now with this fix we get a number with decimal places and store it in the `result` variable.

Run `make division`.
Run `./division`.

You should see `0.666667` get printed!

# Conditions
Make a new file using the `touch` command and call it `condition.c`.

Write this code into `condition.c` so that you get used to writing an `if` *statement* (don't copy paste the code).

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;

  if (a < b) {
    printf("%i is less than %i! \n", a, b);
  }
}
```

You'll notice the `if` keyword followed by parenthesis `()`. The *condtion* of true or false is inside of the parenthesis.

If the *condition* is true, **then** we run the code inside of the curly brackets.

```
printf("%i is less than %i! \n", a, b);

prints out:
    2 is less than 3!
```

We call this an "if statement".

We can also do an alternative check using an `else if` statement.

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;


  if (a < b) {
    printf("%i is less than %i! \n", a, b);
  }
  else if (a > b) {
    printf("%i is greater than %i! \n", a, b);
  }
}
```

Now there is one other possibility. If 2 is not less than or greater than 3, then **it could be equal to 3**.

(lets just say you are the type of person who changes the variables all the time and you need to know the answer).

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;


  if (a < b) {
    printf("%i is less than %i! \n", a, b);
  }
  else if (a > b) {
    printf("%i is greater than %i! \n", a, b);
  }
  else if (a == b) {
    printf("%i is equal to %i! \n", a, b);
  }
}
```

Although we don't reallyhave to do that last check. If a number is not greater than or less than another number, the only possibility left is that they are equal. So we cna use a simple `else` block.

```c
#include <stdio.h>

int main(void) {
  int a = 2;
  int b = 3;


  if (a < b) {
    printf("%i is less than %i! \n", a, b);
  }
  else if (a > b) {
    printf("%i is greater than %i! \n", a, b);
  }
  else {
    printf("%i is equal to %i! \n", a, b);
  }
}
```

Run `make condition`.
Run `./condition`.

This code is pretty dumb tho. So we'll use `if` statements again later in the tutorials after the lecture.

# Loops?
Lets work on C *loop*'s.

In C we can loop *while* something is true.

Make a new C program called `loop.c` using the `touch` command.

In the files tab click on the new `loop.c` file to open it.

Now write the `main` function and include `stdio.h` since we will be printing stuff to the console.

Your code should look like this.

```c
#include <stdio.h>

int main(void) {
  
}
```

Now lets use a "while" loop to print "hello world" forever!

```c
#include <stdio.h>

int main(void) {
  while (true) {
    printf("hello world!");
  }
}
```

`while` is like an if statement. Except it runs over and over as long as the *condition* is true.

The `true` and `false` types are lowercase in C, whereas in Python they are uppercase, `True` and `False`.

Also C doesn't come with *booleans* (`true` or `false` types) by default! We have to include them! This is because "false" in C is treated as the (binary) number zero, while true is any number above zero. So the `true` and `false` types in C are actually an "alias" for the number 0 (false), and the number 1 (true).

Include the `stdbool.h` file at the top.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  while (true) {
    printf("hello world!");
  }
}
```

Compile this code and run it using the correct commands.

Hint:
- `make loop`
- `./loop`

To stop the onslaught of "hello world!" click inside of the shell and click `ctrl` + `C`. Ths "cancels" the program.

It may take few seconds for it to stop because of the delay. Now clear the shell using `ctrl` + `L`.

Now lets loop a certain number of times by "counting".

Make a new `int` variable called `counter`, then inside of `while` increase `counter` by 1.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  int counter = 0;

  while (true) {

    // increase counter
    counter = counter + 1;
  }
}
```

`counter = counter + 1`? This sets `counter` to whatever it was *previously* plus 1.

We can use *syntax sugar* (aka a shortcut) to do this.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  int counter = 0;

  while (true) {
    
    // syntax sugar for increasing a number
    counter += 1;
  }
}
```

`counter += 1;` is the same as `counter = counter + 1;`, but its way easier to type.

But... there is an even faster shortcut. It is so common to increase a number by 1 that you can do `counter++;`, this increases a variable by 1.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  int counter = 0;

  while (true) {

    // super sugary syntax
    counter++;
  }
}
```

We want this loop to stop at some point. Every loop we are checking if the condition is true. We can simply change the condition to check if the number has increased to a certain level.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  int counter = 0;

  while (counter < 5) {

    counter++;
  }
}
```

`while (counter < 5)` checks if `counter` is less than 5.

Now add code to print "hello world" (or whatever phrase you want) inside of the while loop.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  int counter = 0;

  while (counter < 5) {
    printf("Hello world \n");

    counter++;
  }
}
```

Compile the code and run it using the shell. You will see "Hello world" get printed 5 times.

# For loops
There even a *super sugary shortcut* for looping! Its all 1 line of code.

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
  
  for (int counter = 0; counter < 5; counter++) 
  {
    printf("Hello world \n");
  }
}
```

This is does exactly the same thing as our while loop! It just does it all in one line! We call this a "for loop".

(very different than Python's for loop).

The last part of a `for` loop, `counter++`, runs at the end of each loop.

`int counter = 0` happens once.

Like I said it is **identical** to our while loop.


# Types
There are a few types in C. Each type takes up a certain number of bits.

### Integers
`int`
- 32 bits
- negative numbers -2^31 (2 to the 31 power)
- positive numbers 2^31 (2 to the 31 power)

`long`
- 64 bits
- negative numbers -2^63 (2 to the 63 power)
- positive numbers 2^63 (2 to the 63 power)

### Unsigned integers
We can use the keyword `unsigned` to not have negative numbers giving us twice as big positive numbers

`unsigned int`
- 32 bits
- positive numbers 2^32
- The exact limit is 2^32 -1

`unsigned long`
- 64 bits
- positive numbers 2^64
- The exact limit is 2^64 -1


### Floats
You cannot have *unsigned* floats.

"There are several ways to represent real numbers on computers." -- Steve Hollasch

Floats are a type that tells us how to represent a number with a decimal point using 0s and 1s.

Floats use scientific notation. The number 123.456 could be represented as `1.23456 × 10^2` (1.23456 times 10 to the 2nd power). This was decided by the IEEE (Institute of Electrical and Electronics Engineers) pronounced "I triple E".

We use 8 bits for the *exponent*. The exponent multiplies the numbers after the decimal point, essentially "floating" (moving) the decimal point over by some desired amount.

23 bits are used for the *fraction*. All fractions are treated as leaving one number in front of the decimal palce and the rest being after the decimal place


`float`
- 32 bits
- 1 bit for the sign
- 8 bits for the expponent
- 23 bits for the fraction (aka number)
- How floats are treated in memory `SEEEEEEE EFFFFFFF FFFFFFFF FFFFFFFF` (S = Sign, E = Exponent , F = Fraction)

`double`
- 1 bit for the sign
- 11 bits for the exponent
- 52 bits for the fraction (aka number)
- How doubles are treated in memory `SEEEEEEE EEEEFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF` (S = Sign, E = Exponent , F = Fraction)

For a deeper explanation of float see http://steve.hollasch.net/cgindex/coding/ieeefloat.html

Floats are endlessly interesting and you can study them forever. But we won't bore you with them. One important thing to note is that floats only have a certain number digits and not a max number. As a result if we have a very big number in front of the decimal point, then the fraction numbers after the decimal point start getting rounded in weird ways.

TODO (FOR TEACHER) printf `%f.2` to print out only 2 decimal places. Then print to 100 decimal places `%f.100` showing how the decial places start to break.

### char
`char`
- A char uses 8 bits (1 byte)
- It is an ASCII type. 
- It can represent 256 different symbols (2^8)

### bool
A boolean uses 8 bits (1 byte). This is because computers store everything in blocks of 8 bits. So the smallest possible type is 8 bits. Although for 8 true an false variabels we could store them all in 1 byte (8 bits).

`true`
- It is an alias for the number 0

`false`
- It is an alias for the number 1

# Operators
We call math symbols like `+`, `-`, `/`, and `*` "operators". 

`+` plus       `4 + 2` = `6`
`-` minus      `4 - 2` = `2`
`/` divide by  `4 / 2` = `2`
`*` multiply   `4 * 2` = `8`

### Remainder Operator
There is one operator that is often not understood well. It is the remainder operator `%`.

It is actually the result of doing a division. `11 / 4`, is how many times does 4 fit into 11?

![operator division](/Assets/operator_division.png)

The remainder gives us back the remainder `11 % 4`.

![remainder remainder](/Assets/operator_remainder.png)

A cool math property of the remainder operator `%` is that we can keep a number inside of the range of 0 to 3 by remainder-ing by 4.

![operator remainder expamples](/Assets/operator_remainder_examples.png)

You can do this with any number and it will hold true. We usually call keepiing a number within a range "wrapping" the number. This will come in very useful later in the course.

And that is week 1! phew. I'm thinking of moving the "Types" section into an optional Tutorial or shortening it, let me know in Discord! Here is a quick invitation link https://discord.gg/QhqTE4t2tR to my Discord server.

The one thing we haven't taught you is how to get input in C, that will be covered next week!

Tutorials
- Mario Pyramid (Text based)