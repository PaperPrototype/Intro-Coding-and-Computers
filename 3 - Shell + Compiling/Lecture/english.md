Clicking a run button, or using our mouse to navigate acomputer is what most of us are used to. We call this  Graphical User Interface, or GUI for short.

Now we are going to learn to use an older way of navigating and using computers called a Command Line Interface, or CLI for short.

# Shell
Go to this link https://replit.com/ to open up replit. Now make a new repl. Choose the C programming language. Name the new repl "cli".

You should see the default "Hello world" program made by C.

Now open the window called Shell.

![replit ide shell](/Assets/replit_ide_shell.png)

The shell window is a Command Line Interface. The console window is also a CLI but a shell is usually more helpful because it tells us what folder we are currently in. The word "cli" is the name of the folder we are in.

```
~/cli$
```

the tilde symbol is the "home" folder. Usually a home folder has your documents, downloads, and pictures folders. It is alos sometimes called your "user folder".

The most basic command you can write is the list command

```
ls
```

Write the `ls` command into the shell. Then click the enter (or return) key. Running the `ls` command lists all the files and folders who are in the same folder as us.

You should see the following in the shell.

```
~/cli$ ls
main.c
~/cli$ 
```

We write our commands after the dollar sign. Thats actually the only thing the dollar sign is there for, to indicate where to write our commands.

Use the `ctrl` + `L` keys to clear the shell (actually it just moves all the old commands up and out of view).

So how do we move into another folder? We can use the *change directory* command.

```
cd (insert name)
```

After you type cd you can type the name of any neighboring folders to move into... but if there are none! So lets make one.

Use the make directory command to make a new folder.

```
mkdir myNewFolder
```

Write the above command into the shell (or just copy paste it). Click the enter (or return) key to run the command.

Now run the `ls` command to see your new folder get listed. 
It should look like this.

```
~/cli$ mkdir myNewFolder
~/cli$ ls
main.c  myNewFolder
~/cli$ 
```

You can see the name of your folder as well as our main.c file.

Now move into your new folder by using the `cd` command.

```
cd myNewFolder
```

After your run this command you will see that the current folder has changed.

```
~/cli$ cd myNewFolder
~/cli/myNewFolder$ 
```

We can also make files using the touch command.

```
touch myNewFile
```

Run the above command. Now run the list command. You should see the following in your shell.

```
~/cli/myNewFolder$ touch myNewFile
~/cli/myNewFolder$ ls
myNewFile
~/cli/myNewFolder$
```

Now how do we get back to our cli parent folder? Run the below command.

```
cd ..
```

The `..` in computers usually refers to a parent folder (from the current folder). So by running 

```
cd ..
```

you move into our parent folder! You should see the follwoing in the shell.

```
~/cli/myNewFolder$ cd ..
~/cli$ 
```

We can delete files using the remove command.

```
rm
```

But if we want to delete *folders* we also have to remember that folders can conatain other folders and files. So we have to tell the remove command to enable a "feature".

```
rm -r myNewFolder
```

Run the above command. This will delete the "myNewFolder" folder, as well as the "myNewFile" inside of that folder.

This above command uses the *recursive remove* feature `-r`, which goeas through any sub-folders and files inside of "myNewFolder" and deletes them. 

The word `myNewFolder` is called an argument. The `-r` in the remove command is called a feature "flag" (Theres a name for everything!). Although sometimes flags use two minus signs `--` instead of one `-`.

If you run the remove command with the `--help` flag you will see a list of all the feature flags for the remove program.

```
~/cli$ rm --help
Usage: rm [OPTION]... [FILE]...
Remove (unlink) the FILE(s).

  -f, --force           ignore nonexistent files and arguments, never prompt
  -i                    prompt before every removal
  -I                    prompt once before removing more than three files, or

... deleted extra output for brevity

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

# Compiling
With the C programming language we have to convert our code into series of 0 and 1 instructions for the computer. We store the result of converting our C code into binary instructions (specific to a CPU) in a file, called a program file. In Python we used a program that interpreted our text based code as it read it. With C we create programs from the code.

To convert text based code into a series of 0s and 1s instructions in a program file we use a program called a "compiler". 

In fact whenever your ran your C programs last week you might have seen that Replit did run a compiler command using the console.

```
> clang-7 -pthread -lm -o main main.c
> ./main
Hello World
> 
```

We are now going to use the shell to compile our code. We will be using the clang compiler (the same one replit has been using all along) to compile our code into a program file. 

(Make sure you didn't delete our main.c file because we are about to compile it!)

Run the following command.

```
clang main.c
```

Your shell should look like this 

```
~/cli$ clang main.c
~/cli$
```

Now use the list command to see our new program file we just created! You should see this

```
~/cli$ ls
a.out  main.c
~/cli$ 
```

clang made a new program file called "a.out". The "a" stands for Assembly (we'll get to what assembly is in a second).

You may also see a file called "main" get listed. This is a program file of our "main.c" code that Replit made. We can rename our "a.out" file to be "main" when we compile by using the `-o` flag (which stands for output).

```
clang main.c -o main
```

Now you should see a program file called "main"

Lets now run the resulting "main" program file. To run a program using a CLI we have to *refer* to the program directly. The CLI then runs the program. Type in the following command to run the resulting program.

```
./main
```

The "." refers to our current folder. The "/main" refers to the "main" program file.

# Compilers
Lets now understand how a compiler works.

When we compile our code it goeas through these steps.

```
preprocessing
compiling
assembling
linking
```

First the compiler pre-processes our code. This includes "including" code with the `include` directive. You can view the pre-processed output by running the below command

```
clang -E main.c
```

This prints the preprocessed code into the console! We can make clang put the preprocessed code into a new file by using the below command.

```
clang -E main.c > preprocessed.c
```

This puts the pre-processed output of our main.c code into a new file called a "preprocessed.c".

clang then convert our preprocessed code into assembly instructions, this step is (consfusingly) called "compiling". Assembly code is specific to each CPU (Central Processing Unit). Here is an example of Assembly code from a "Hello world" C program.

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

(I used https://godbolt.org/ to view the resulting assembly in realtime as I edited)

Before we had *compiled programming languages* (like C) everyone had to write code specific to each CPU using Assembly! But now, with C (and others) we can make our code run on any CPU thanks to compilers.

We then go through another step called "assembling". AN assembler program converts our assembly code into a file of 0s and 1s instructions. Assembler programs often come builtin with your computer.

Finally we have "linking". Linking takes files that have already been compiled into binary and "links" them all together into one program file. For example, it is common for the code for the "math.h" code to come already compiled. So rather than the compiler having to compile "math.h" every time, it can just link the binary version at the end. This saves a lot of time in projects with lots of code.

Alright! Now you know how a compiler works!