Clicking a run button, or using our mouse to "click" on buttons and navigate a computer is what most of us are used to. We call this a "Graphical User Interface", or GUI for short.

But before the time of GUIs we had small black consoles with little white letters that only the beardiest hackers could use. We call these consoles "Command Line Interfaces", or CLI for short.

We are now going to learn to use a CLI! They are actually an extremely common tool that programmers use (and they make you look like a pro).

# Shell
Go to this link https://replit.com/ to open up replit. Now make a new repl. Select the C programming language. Then name the new repl "cli".

You should see the default "Hello world" code in your new repl.

Open the window called Shell.

![replit ide shell](/Assets/replit_ide_shell.png)

The shell window is a Command Line Interface. The console window is also a CLI (CLI is short for Command Line Interface), but a shell is usually more helpful because it tells us what folder we are currently in.

You'll notice the word "cli" in the shell window.

(shell)
```
~/cli$
```

"cli" is the name of the folder we are in. A "shell" basically lets you do stuff through the files and folders of a computer.

You will also notice the tilde symbol `~`. The tilde symbol `~` represents the "home" folder. Usually a home folder has your documents, downloads, and pictures folders. It is also sometimes called a "user folder".

The most basic command you can run is the list command.

(command)
```
ls
```

Write `ls` into the shell. To run the `ls` command click the enter (or return) key on your keyboard (similar to clicking enter when you send a message to someone).

The `ls` command "lists" all the files and folders *who are in the same folder as you*.

You should see the following in the shell after running the `ls` command

(shell)
```
~/cli$ ls
main.c
~/cli$ 
```

The "main.c" file will probably get listed. It is the file that is holding the code you see!

You will also notice the dollar sign `$`. We write our commands after the dollar sign... thats... actually the only thing the dollar sign is there for, as a visual indicator for where to write our commands!

Click the `ctrl` + `L` keys to clear the shell (if your on mac it will be the `control` + `L` keys) <- go ahead and click those keys to clear the shell.

When your shell starts to fill up with all kinds of commands you can use `ctrl` + `L` to clear them. Make sure you do this after your done reading the output of a command, otherwise your shell will fill up with all kinds of info and it becomes hard to read.

So how do we "move into" another folder? We can use the "change directory" command. The "cd" (change directory) command is formatted like this.

(placeholder example command)
```
cd (replace with name of folder to move into)
```  

After you type `cd` you can type the name of any folder that are in the same folder as you. Currently there are no folders to move into! Lets make one!

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

(command, answer)
```
cd myNewFolder
```

After your run this command you will see that the current folder has changed!

(shell window)
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

We just made a new file called "myNewFile", pretty cool! Now clear the shell using the `ctrl` + `L` keys.

Now how do we get back to our parent folder (the "cli" folder)? Run the below command. It will move us into our parent folder!

(command)
```
cd ..
```

A double period `..` in computers usually refers to the parent folder (from the current folder). So by running `cd ..` you move into the parent folder (which is `cli`). 

The shell window should now look like the following.

(shell)
```
~/cli/myNewFolder$ cd ..
~/cli$ 
```

Make sure your shell looks like this! Also make sure you are are in the "cli" folder before continuing!

Now we can delete files using the remove command.

(command)
```
rm (name of file)
```

But if we want to delete *folders* we also have to remember that folders can contain other folders and files! So we have to tell the remove command to enable a "feature".

(command)
```
rm -r (name of folder)
```

This above command uses the *recursive remove* feature `-r`, which goes through any sub-folders and files inside of a folder and deletes them. 

Lets delete our useless "myNewFolder" folder (which has our "myNewFile" file in it).

(run this command)
```
rm -r myNewFolder
```

Now run `ls` to see that the folder "myNewFolder" has been deleted (and is gone).

(command)
```
ls
```

When we ran this command -> `rm -r myNewFolder` the word "myNewFolder" is called an "argument" for the `rm` *program*. 

`rm` is actually the name of a program, that we run, so is `touch` and `mkdir` and `ls` <- they are all "Command Line Programs" or "CLI Programs".

The `-r` in the remove command is called a feature "flag" (Theres a name for everything!). Although sometimes flags use two minus signs `--feature` instead of one `-feature`.

If you run the remove command with the `--help` flag (like this `rm --help`) you will see some helpful information about the `rm` program.

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

# Compiling
Your computers processor, often called the Central Processing Unit ("CPU" for short), understands sets of binary (0s and 1s) instructions.

"programs" in your computer are a file containing binary instructions (called "Machine Code"), that get loaded into the processor!

(machine code)
```
010001010100010100000001000101011010101000101010000000010001010100010100000001000110000000100010101100001000000010000000100010101100000100010101101000101010001010000000100010101101010100010101000000001000101010001010000000100011000000010001010110000100000001000000010001010110000010001010110100010101000101000000010001010110101010001010100000000100010101000101000000010001100000001000101011000010000000100000001000101011000001000101011
```

So how has our code, that we have been writing in C, gone from written ASCII text to binary instructions in a "program file" for the Processor?

Coding using 0s and 1s would be pretty terrible so humans made a "program" that took word based instructions called "Assembly Instructions" and converted them into binary (0s and 1s) Machine Code instructions for your CPU. 

Assembly processor instructions for a program that prints "Hello world" might look like this.

```x86_64 gcc 11.2
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

"assembly" isn't exactly easy to code with. Also assembly instructions tend to be specific for each type of CPU, so an app written for one processor wouldn't work on another processor.

To solve this problem we made even easier programming languages that look like this.

(the C programming language)
```c
#include <stdio.h>

int main(void) 
{
	printf("Hello world");
}
```

...and those "middle level" programming languages then get converted into assembly (by a compiler), depending on the type of processor!

We then have "higher level" scripting languages like Python, which get interpreted by programs.

The process of converting our C code into Assembly Instruction, and then converting Assembly Instructions into Machine Code is called "compiling". 

Programs called "Compilers" convert these ASCII test instructions into assembly instructions (this process is refered to as "compiling").

Using the shell window we will use a compiler called "clang" to compile our C code inside of the "main.c" file.

(run the following command)
```
clang main.c
```

Now run `ls`.

(command)
```
ls
```

You should see a new file called "a.out" this is an "assembly output" file containing machine code (0s and 1s instructions)! "clang" is a compiler program! and we used it to convert our C code into machine code that the processor can understand.

The name "a.out" is kinda weird. We can tell clang to name the outputted file differently by using a feature flag.

(run this command)
```
clang main.c -o app
```

The `-o` flag stands for "output", and it lets us name the outputted program file to "app".

If you run `ls` you will see a new program file called "app".

(command)
```
ls
```

Using the "clang" compiler is kinda annoying cause it makes us do everything manually. Instead we can just use the "make" program (which runs clang (or a different `cc` compiler) commands for us).

(command)
```
make main
```

Run the above command. We put "main" (without the ".c") because `make` takes the name of the file without the ".c", and then gives us a program file with the name "main". If you run `ls` you will see a new program file called "main" (now we have 3 identical program files "a.out" and "app" and "main").

Run the `ls` command to see all these programs.

(command)
```
ls
```

So how do we run all these program files!?

To run a program using a CLI we have to *refer* to the program directly. The CLI then runs the program for us. 

Run the following command to run the "main" program (or you could change the name to "app" or "a.out")

(command)
```
./main
```

The "." refers to the current folder we are in. The "/main" refers to the "main" program file.

There is something that the `make` program takes care of for us called "linking" where you take two machine code (0s and 1s) files and "link" them together into one program file.

At some point you might "include" some file where the code is not available and all you have access to is a compiled machine code (0s and 1s) version! Then what do you do?

In this case `make` will automatically use the link feature `-l` to "link" that machine code with your program code.

Remember the assembly code we showed?

(assembly)
```x86_64 gcc 11.2
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

You'll notice the assembly code `call printf`, this literally "calls" (AKA "uses") the `printf` function... but where is `printf`?!

`printf` is inside of the `stdio` machine code code! So the "linker" (which is part of the "compiler"), will combine the `stdio` code with our (compiled) `main.c` machine code, and give us a runnable program file.

# CLI explained
So how did this all work? When we type `cd` (and some arguments, like the name of a folder to move into) and hit enter, the *shell* looks for a program called `cd`.

There is a file called the ".profile" that the shell automatically loads and uses to find different programs. You can add your own programs to the profile and then run them using their name, so that you can skip having to type `./app` before the name of "app" and just type its name `app` to run it.

Once the shell finds a program (using the information in the ".profile" file), for example `cd`, it sends the *arguments* (aka input) we typed after the word `cd` and passes them to the `cd` program (that the shell ran for us). `cd` then figures out what to do based on the arguments (aka input) we typed.

How does the shell, the "command line interface", know what the arguments were? Like if we typed `cd /` how does it know that `/` is for `cd` and not part of its name?

The Shell checks for a space after the name of the program `cd /` (<- notice the space). So, if you didn't put a space and just typed `cd/` you might get an error because the shell tried to run a program called "/cd".

And thats pretty much it! See you next section!