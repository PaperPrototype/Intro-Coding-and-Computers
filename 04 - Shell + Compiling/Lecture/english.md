We are going to learn to use a "Command Line Interface" to *do* stuff on our computer (rather than using buttons and clicking with your mouse). A CLI (Command Line Interface) are an extremely common tool that programmers use (and they make you look like a pro). Whats a CLI? Its the little black console that we have been printing words into!

# Shell
Go to this link https://replit.com/ to open up replit. Now make a new repl. Select the C programming language, and name the new repl "cli".

You should see the default "Hello world" code in your new repl.

(default C code)
```c
#include <stdio.h>

int main(void) {
	printf("Hello world");
}
```

Open the window called Shell. The "Shell" window does essentially the same thing as the console window.

![replit ide shell](/Assets/replit_ide_shell.png)

The difference between the console and the shell is that the console is essentially a simplified CLI (Command Line Interface).

You'll notice the word "cli" in the shell window.

(shell)
```
~/cli$
```

"cli" is the name of the folder we are inside of. In a CLI we *do* stuff by editing the files and folders of your computer, and we have to "go inside of a folder" to access its files and folders.

To *do* something in a CLI we have to run a program! Except rather than double clicking an "app", we have to write its name.

The most basic "command" you can run is the "list" command.

(command)
```
ls
```

Whenever we say "command" we are refering to stuff we wrote into the CLI.

Write `ls` into the shell ("LS" not "1s"). To run the `ls` program click the enter (or return) key on your keyboard (similar to clicking enter when you send a message to someone).

You should see something like the following!

![replit ls command output](/Assets/replit_ls_command_output.png)

The `ls` command "lists" all the files and folders *who are in the same folder as you* (and currently we are in the "cli" folder!).

The "main.c" file will probably get listed. It is the file that is holding the code you see!

On the left in the files window you can see that indeed there is a file called "main.c".

You might notice the dollar sign `$`. We write our commands after the dollar sign and... thats... actually the only thing the dollar sign is there for, as a visual indicator for where to write our commands!

Click the `ctrl` + `L` keys to clear the shell (if your on mac it will be the `control` + `L` keys) <- go ahead and click those keys to clear the shell!

When your shell starts to fill up with all kinds of commands you can use `ctrl` + `L` to clear them. Make sure you do this after your done reading the output of a command, otherwise your shell will fill up with all kinds of info and it becomes hard to read.

So how do we "move into" another folder? We can use the "change directory" command (which runs a program that moves us into a folder, much like when you double click a folder in your computer). The `cd` (change directory) command is formatted like this.

(example command)
```
cd myExampleFolder
```  

After you type `cd` you can type the name of any folders that are in the same folder as you.... but currently, there are no folders to move into! Lets make one!

Use the make directory `mkdir` command to make a new folder.

(command)
```
mkdir myNewFolder
```

Write the above command into the shell (or just copy paste it). Click the enter (or return) key to run the command. This will make a new folder called "myNewFolder".

Now run `ls` to see our new folder get listed.

(list command)
```
ls
```

![replit ls command folder listed](/Assets/replit_ls_command_folder_listed.png)

You can see our folder as well as our "main.c" file gets listed!

(Clear the shell window using `ctrl` + `L` keys)

Now move into your new folder by using the `cd` command.

(change directory command)
```
cd myNewFolder
```

After your run this command you will see that the current folder the shell is "inside of" has changed!

![replit shell dir changed](/Assets/replit_shell_dir_changed.png)

TADA! 

We can also make new file (inside of "myNewFolder") using the `touch` command.

(command)
```
touch myNewFile
```

Writing "touch" runs a program that makes a new file.

Run the above command.

Now use the list command `ls` to see the newly made file! 

![replit shell touch command](/Assets/replit_shell_touch_command.png)

We just made a new file called "myNewFile", pretty cool! 

(Clear the shell using the `ctrl` + `L` keys)

Now how do we get back to our parent folder (the folder called "cli" is currently the "parent" folder of "myNewFolder").

Run the below command.

(command)
```
cd ..
```

A `..` in computers usually refers to the "parent" folder (the folder above us).

![replit shell move to parent folder](/Assets/replit_shell_moveto_parent_folder.png)

So by running `cd ..` you move into the parent folder.

Make sure your shell looks like this! Also make sure you are are in the "cli" folder before continuing!

We can delete files using the remove command.

(command example)
```
rm (name of file)
```

But if we want to delete *folders* we also have to remember that folders can contain other folders and files, and those folders can contain other folder and files... So we have to tell the remove command to enable a "feature".

(command example)
```
rm -r (name of folder)
```

This above command uses the *recursive* feature `-r`, which goes through any sub-folders/files and deletes them. 

Lets delete our useless "myNewFolder" folder (which has the "myNewFile" file in it).

(command)
```
rm -r myNewFolder
```

Run the above command.

Now run `ls` to see the changes.

(command)
```
ls
```

When we ran `rm -r myNewFolder` the word "myNewFolder" is called an "argument" for the `rm` *program*. 

`rm` is actually the name of a program, that we run, so is `touch` and `mkdir` and `ls` <- they are all "Command Line Programs" or "CLI Programs".

The `-r` in the remove command is called a feature "flag" (Theres a name for everything!). Although sometimes flags use two minus signs `--feature` instead of one `-feature`.

If you run the remove command with the `--help` flag, like this `rm --help`, you will see a "guide" get print out on feature flags or options available for the `rm` program.

(example, don't worry about reading all this)
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

Most *Command Line Programs* (like `rm` and `touch`) come with a `--help` flag you can use to find out more about how to use the program.

# Compiling
Your computers processor, often called the Central Processing Unit ("CPU" for short), understands sets of binary (0s and 1s) instructions.

A "program" or "app" in your computer is a file containing binary (0 and 1) instructions called "Machine Code".

(machine code)
```
010001010100010100000001000101011010101000101010000000010001010100010100000001000110000000100010101100001000000010000000100010101100000100010101101000101010001010000000100010101101010100010101000000001000101010001010000000100011000000010001010110000100000001000000010001010110000010001010110100010101000101000000010001010110101010001010100000000100010101000101000000010001100000001000101011000010000000100000001000101011000001000101011
```

This "Machine Code" is what processors understand. Each type of processor has its own "format" of 0s and 1s commands they understand called an "instruction set".

So how has our code, that we have been writing in C, gone from written ASCII text to binary instructions in a "program file" for the Processor?

First our C code gets converted to "Assembly instructions" which are basically the text version of Machine Code.

Assembly instructions for a program that prints "Hello world" might look like this.

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

"assembly" isn't exactly easy to code with and very few people write assembly code. 

The biggest problem with Assembly instructions (which really just convert to Machine Code) is that each type of assembly is for a specific *instruction set*, and assembly written for a processor that uses the x86_64 instruction set (Intel and AMD processors) wouldn't work for a processor that uses ARM instructions set! (iPhone processors use an ARM/Darwin instruction set).

To solve this problem we made even easier programming languages that look like this.

(the C programming language)
```c
#include <stdio.h>

int main(void) 
{
	printf("Hello world");
}
```

...and those "middle level" (C or C++) programming languages then get converted into assembly (by a "compiler" program) depending on the type of processor you are targeting/wanting to run the code on.

(We then also end up with "high level" scripting languages like Python, which get interpreted by interpreter programs written in C)

The process of converting our C code into Assembly Instruction, and then converting Assembly Instructions into Machine Code is called "compiling". 

Programs called "Compilers" convert C (ASCII or UTF-8 based text) code into assembly instructions. 

"Assembler" programs then take the assembly instructions, and convert them into machine code (0s and 1s). 

There is also something called a "linker" program that "links 2 machine code files and puts them together into 1 single program file".

If your interested in "linking" and compiling then we recommend you watch this video!

https://www.youtube.com/watch?v=tlYn2kN0g8c

Casey (the author of the video) will be talking about C++, a slightly more complex language than C, but don't you don't need to know C++ to watch the video since he will only be talking about compiling and linking 

(also, any code written in C, is valid C++ code (C++ just adds more features to C) so really if you are familiar with C then you will do fine).

Using the shell window we will use a compiler to convert our C code into machine code that we can run as an app!

The compiler we will use is called "clang". Run the following command.

(command)
```
clang main.c
```

Now run `ls`.

(command)
```
ls
```

You should see a new file called "a.out" this is an "assembly output" file containing machine code (0s and 1s instructions)! "clang" is a compiler program! and we used it to convert our C code into machine code that the processor can understand!

To run our newly made program in the file "a.out" using the CLI we have to *refer* to the file of machine directly. The CLI then runs takes care of loading the file into the processor for us.

Run the following command to run "a.out".

(command)
```
./a.out
```

The "." refers to the current folder we are in (which is currently called "cli"). The "/a.out" refers to the "a.out" program file.

The name "a.out" is kinda weird though, so we can tell clang to name the outputted file differently by using a feature flag.

(run this command)
```
clang main.c -o app
```

The `-o` flag stands for "output", and it lets us set the name of the outputted program file to (in this case) `app`.

If you run `ls` you will see a new program file called "app"!

(command)
```
ls
```

Now run our program file called app!

(command)
```
./app
```

Using the "clang" compiler is kinda annoying though cause it makes us do everything manually. Instead we can just use the "make" program, which runs clang with all the correct feature flags for us.

(command)
```
make main
```

Run the above command. 

We put "main" (without the ".c") because `make` takes the name of the file (without the `.c`).

If you run `ls` you will see a new program file called "main" (now we have 3 identical program files "a.out" and "app" and "main").

Run the `ls` command to see all these programs.

(command)
```
ls
```

The most important thing that `make` will take care of for us is  "linking".

In linking you take two machine code (0s and 1s) files and "link" them together into one program file. Why? At some point you might "include" a header file (which contains a bunch of fuction hints) and you will use one of the functions in it (like printf comes from `stio.h`). But say the code from `stdio.c` is patented! Well then you will only get access to a machine code file of the compiled C code! Then what do you do?

Well, we just use the function hints inside of the header (the `.h` file) and when compiling, you can just link the machine code from `stdio` with your codes machine code into a single program file of machine code. Pretty simple, and it works!

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

You'll notice the assembly code `call printf`, this literally calls (AKA "uses") the `printf` function... but where is `printf`?!

`printf` is inside of the `stdio` machine code file! So the "linker" (which usually comes with the compiler program), will combine the `stdio` code with our (compiled) `main.c` machine code, and give us a run-able program file, that has access to the code from `stdio`.

`make` will automatically run clang with the link feature `-l` when needed.

# CLI explained
You might have noticed we didn;t have to type `./cd` when running the change directory program `cd`.

There is a file called the ".profile" that the shell automatically loads and uses to find different programs. 

You can add your own programs to the "profile" and then run them using their name (so that you can skip having to type `./` before the name of "app" and just type its name `app` to run it).

And thats pretty much it! See you next section!