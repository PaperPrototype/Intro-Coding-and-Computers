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

So how do we move into another folder? We can use the change directory command.

```
cd (insert name of folder)
```

After you type cd you can type the name of any neighboring folders to move into... but there are none so lets make one.

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

Now how do we get back to our cli parent folder? RUn the below command.

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

Now we can delete files using the remove command.

```
rm
```

But if we want to delete *folders* we also have to rememer that folders can conatain other folders and files. So we have to tell the remove command to enable a "feature".

```
rm -r myNewFolder
```

Run the above command. This above command uses the *recursive remove* feature. We call the text we put after the command are called arguments.  The `myNewFolder` in the remove command is an argument.

The `-r` in the remove command is called  a "flag" (Theres a name for everything). Although sometimes flags use two minus signs `--` instead of one `-`.

If you run the remove command with the `--help` flag you will see a list of all the commands for the remove program.

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
It truns out we can use a Command Line Program to compile our code.