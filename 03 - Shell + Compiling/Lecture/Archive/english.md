Clicking a run button, or using our mouse to "click" on buttons and navigate a computer is what most of us are used to. We call this a "Graphical User Interface", or GUI for short.

But before the time of GUIs we had small black consoles with little white letters that only the beardiest hackers could use. We call these consoles "Command Line Interfaces", or CLI for short.

We are now going to learn to use a CLI! They are actually an extremely common tool that programmers use (and they make you look like a pro).

# Shell
Go to this link https://replit.com/ to open up replit. Now make a new repl. Select the C programming language. Then name the new repl "cli".

You should see the default "Hello world" code in your new repl.

Open the window called Shell.

![replit ide shell](/Assets/replit_ide_shell.png)

The shell window is a Command Line Interface. The console window is also a CLI, but the shell is usually more helpful because it tells us what folder we are currently in. 

You'll notice the word "cli" in the shell.

(shell)
```
~/cli$
```

"cli" is the name of the folder we are in. A shell basivcally lets you do stuff through the files and folders of a computer.

You will also notice the tilde symbol `~`. The tilde symbol `~` represents the "home" folder. Usually a home folder has your documents, downloads, and pictures folders. It is also sometimes called your "user folder".

The most basic command you can run is the list command.

(command)
```
ls
```

Write the `ls` command into the shell. Now run it. To run a command click the enter (or return) key on your keyboard (similar to clicking enter when you send a message to someone). 

Running the `ls` command lists all the files and folders *who are in the same folder as us*.

You should see the following in the shell.

(shell)
```
~/cli$ ls
main.c
~/cli$ 
```

The "main.c" file get will probably get listed. It is the file that is holding the code you see!

You will also notice the dollar sign `$`. We write our commands after the dollar sign... thats... actually the only thing the dollar sign is there for, as a visual indicator for where to write our commands!

Use the shortcut keys `ctrl` + `L` to clear the shell of all yuour old commands. When your shell starts to fill up with all kinds of commands just use `ctrl` + `L` to clear them. Make sure you do this after your done reading the output of a command, otherwise your shell will fill up with all kinds of info and it becomes hard to read.

So how do we move into another folder? We can use the *change directory* command. The "cd" (change directory) command is formatted like this.

(placeholder example command)
```
cd (replace with name of folder to move to)
```

After you type `cd` you can type the name of any neighboring folders... but there are no folders to move into! Lets make one!

Use the make directory "mkdir" command to make a new folder.

(command)
```
mkdir myNewFolder
```

Write the above command into the shell (or just copy paste it). Click the enter (or return) key to run the command. This will make a new folder called "myNewFolder".

Now run the `ls` command to see our new folder get listed!
Your CLI (aka, the Shell) should look like this.

(shell)
```
~/cli$ mkdir myNewFolder
~/cli$ ls
main.c  myNewFolder
~/cli$ 
```

You can see our folder as well as our "main.c" file gets listed.

(Now clear your shell using the `ctrl` + `L` keys)

Now move into your new folder by using the `cd` command.

(command)
```
cd myNewFolder
```

After your run this command you will see that the current folder has changed!

(shell)
```
~/cli$ cd myNewFolder
~/cli/myNewFolder$ 
```

HA! We can also make new files using the touch command.

(command)
```
touch myNewFile
```

Run the above command. Now run the list command. Your Shell should look like this.

(shell)
```
~/cli/myNewFolder$ touch myNewFile
~/cli/myNewFolder$ ls
myNewFile
~/cli/myNewFolder$
```

Now how do we get back to our parent folder (the "cli" folder)? Run the below command. It will move us into our parent folder!

(command)
```
cd ..
```

A double period `..` in computers usually refers to the parent folder (from the current folder). So by running 

(command)
```
cd ..
```

...you move into our parent folder! You should see the follwoing in the shell.

(shell)
```
~/cli/myNewFolder$ cd ..
~/cli$ 
```

Make sure your shell looks like this! And that you are in the "cli" folder before continuing!

Now we can delete files using the remove command.

(command)
```
rm (name of file)
```

But if we want to delete *folders* we also have to remember that folders can contain other folders and files! So we have to tell the remove command to enable a "feature".

(command)
```
rm -r myNewFolder
```

Run the above command. This will delete the "myNewFolder" folder, as well as the "myNewFile" inside of "myNewFolder folder.

(if you run `ls` you will see that "myNewFolder" has been deleted!)

This above command uses the *recursive remove* feature `-r`, which goeas through any sub-folders and files inside of "myNewFolder" and deletes them. 

In the command we typed "myNewFolder". "myNewFolder" is called an argument. 

The `-r` in the remove command is called a feature "flag" (Theres a name for everything!). Although sometimes flags use two minus signs `--` instead of one `-`.

If you run the remove command with the `--help` flag (like this `rm --help`) you will see a list of all the *feature flags* for the remove program!

(example)
```
~/cli$ rm --help
Usage: rm [OPTION]... [FILE]...
Remove (unlink) the FILE(s).

  -f, --force           ignore nonexistent files and arguments, never prompt
  -i                    prompt before every removal
  -I                    prompt once before removing more than three files, or

... I deleted the extra output to make this shorter to read

  -r, -R, --recursive   remove directories and their contents recursively
  -d, --dir             remove empty directories
  -v, --verbose         explain what is being done
      --help     display this help and exit
      --version  output version information and exit

By default, rm does not remove directories.  Use the --recursive (-r or -R)
option to remove each listed directory, too, along with all of its contents.

To remove a file whose name starts with a '-', for example '-foo',
use one of these commands:
  rm -- -foo

  rm ./-foo

... deleted extra output for brevity

~/cli$
```

# CLI explained
So how did this all work? When we type `cd` (and some arguments) and hit enter, the *shell* looks for a program called `cd`.

There is a file called a "profile" that the shell uses to find the different programs. You can add your own programs to the profile *file*!

You could actually make your own "command line" programs (like cd and rm) by simply adding them to the *profile* file, which would make it so that you can skip having to type `./cd` before the name of make and just type its name `cd`.

Once the shell finds a program, for example `cd`, it sends the *arguments* (aka input) we typed after the word `cd` and passes them to the `cd` program (that the shell ran for us). `cd` then figures out what to do based on the arguments (aka input) we typed.

How does the shell, a "command line interface", know what the arguments were? Liek fi we typed `cd /` how does it know that `/` is for `cd` and not part of its name?

The Shell checks for a space after the name of the program `cd /` (<- notice the space). So, if you didn't put a space and just typed `cd/` you might get an error because the Shell uses a space to find the program name and then search the "profile" file for any programs with that name and runs them.

# Compiling
With the C programming language we have to convert our code into series of 0 and 1 instructions for the computer. We store the result of converting our C code into binary instructions (specific to a CPU) in a file, called a program file. In Python we used a program that interpreted our text based code as it read it. With C we create programs from the code.

To convert text based code into a series of 0s and 1s instructions in a program file we use a program called a "compiler". 

In fact whenever you clicked the "run" button in Replit you might have seen that Replit compiled your code then ran it for you!

(Replits console when you click the play button)
```
> clang-7 -pthread -lm -o main main.c
> ./main
Hello World
> 
```

We are now going to use the shell to compile our code. We will be using the clang compiler (the same one replit has been using all along) to compile our code into a program file. 

(Make sure you didn't delete your main.c file because we are about to compile it!)

Run the following command.

(command)
```
clang main.c
```

Your shell should look like this 

(shell)
```
~/cli$ clang main.c
~/cli$
```

Now use the list command to see our new program file we just created! You should see this

(shell)
```
~/cli$ ls
a.out  main.c
~/cli$ 
```

clang made a new program file called "a.out". The "a" stands for Assembly (we'll get to what assembly is in a second), and the "out" stands for "output".

You may also see a file called "main" get listed if you ran the code using the play button. This is a program file of our "main.c" code that Replit made. We can rename our "a.out" file to be "main" when we compile by using the `-o` flag (which stands for output).

(command)
```
clang main.c -o main
```

Now you should see a program file called "main".

Lets now run the resulting "main" program file. To run a program using a CLI we have to *refer* to the program directly. The CLI then runs the program. Type in the following command to run the resulting program.

(command)
```
./main
```

The "." refers to our current folder. The "/main" refers to the "main" program file.

Run the above command to "run" the main program.

# Make
It will get annoying to have to write a clang command with the `-o` feature to rename the output program file to be named "main". So instead we can use the make program.

(command)
```
make main
```

Run the above command. This will compile our "main.c" code into a program file called "main". The `make` program doesn't make us type the ".c" in `make main.c`, instead we can just say `make main` and the `make` program figures out that our code is in a file called "main.c".

The make program also outputs a program file called "main" and not "a.out".

Now run the resulting "main" program using 

```
./main
```

# Compilers
Lets now understand how a compiler works.

When we compile our code it goeas through these steps.

```
preprocessing
compiling
assembling
linking
```

First the compiler pre-processes our code. This includes "including" code into our "main.c" file from the header files. You can view the pre-processed code by running the below command

(command)
```
clang -E main.c
```

This prints the preprocessed code into the console! We can make clang put the preprocessed code into a new file by using the below command.

(command)
```
clang -E main.c > preprocessed.c
```

This puts the pre-processed code (with the included headers) from our main.c code into a new file called a "preprocessed.c". Use Replits files tab to view the output.

Clang then convert our preprocessed code (with all the header code) into assembly instructions, this step is (consfusingly) called "compiling". Assembly code is specific to each CPU ("Central Processing Unit:, or just processor). Here is an example of Assembly code from a "Hello world" C program.

(assembly instructions for a CPU)
```x86_64
.LC0:
        .string "Hello world"
main:
        push    rbp
        mov     rbp, rsp
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        mov     eax, 0
        pop     rbp
        ret
```

(I used https://godbolt.org/ to view the resulting assembly in realtime)

Before we had *compiled programming languages* (like C) everyone had to write code specific to each CPU using Assembly! But now, with C (and others) we can make our code run on any CPU thanks to modern compilers that convert our code into Assembly.

```
preprocessing
compiling <- converting code into assembly instructions
assembling
linking
```

We then go through another step called "assembling". An assembler program converts our assembly code into a file of 0s and 1s instructions. Assembler programs often come builtin with your computer.

```
preprocessing
compiling
assembling <- convert to 0s and 1s
linking
```

Finally we have "linking". Linking takes files that have already been compiled into binary and "links" them all together into one program file. 

Sometimes code comes already compiled into 0s and 1s, and all we are given is a header with functions hints. This helps save time because rather than the compiler having to compile some code every time, it can just "link" the binary version at the end. This is also common when it comes to proprietary (patented) code. Often you are not allowed to see the actual code, so all you get is a binary version, that you have to "link" with your code.

Now you know how a compiler works!

Sometimes a program will stop working (or you find experimenting with an inifite for loop that prints "Hello world" forever) you can stop the program by first clicking inside of the shell (so that replit knows you are "focused on" the shell window) then click the `ctrl` + `C` keys. This "cancels" the program.