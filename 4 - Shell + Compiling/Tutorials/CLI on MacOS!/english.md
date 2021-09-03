Lets play around with your Macs CLI.

Open launch pad. Then click on the grouped apps called "Other". This contains utility apps builtin on your Mac. You should see an app called Terminal. Click the "Terminal" app to open it.

If your Mac computer is running the newest version of MacOS then you can use the shortcut `cmd` + space bar, to open a search menu, then you can search "Terminal" and click enter.

Now we can type all the same commands from the lectures!

Lets start with a simple command.

(simple command)
```
ls
```

Running this will list all folders and files in your current user folder!

There is also another fun command

(fun command)
```
tree
```

This command will list all your files and folders like a "tree".

(short snippet of tree)
```
.
├── Applications
│   ├── Brave\ Browser\ Apps.localized
│   │   ├── Google\ Chat.app
│   │   │   └── Contents
│   │   │       ├── Info.plist
│   │   │       ├── MacOS
│   │   │       │   └── app_mode_loader
│   │   │       ├── PkgInfo
│   │   │       └── Resources
│   │   │           ├── app.icns
│   │   │           └── en-US.lproj
│   │   │               └── InfoPlist.strings
│   │   └── Icon\r
│   ├── Cloud\ Gardens.app
│   │   └── Contents
│   │       ├── Info.plist
│   │       ├── MacOS
│   │       │   └── run.sh
│   │       └── Resources
│   │           └── shortcut.icns
│   ├── Edge\ Apps.localized
│   │   ├── Flashcards\ Mobile.app
│   │   │   └── Contents
│   │   │       ├── Info.plist
│   │   │       ├── MacOS
│   │   │       │   └── app_mode_loader
│   │   │       ├── PkgInfo
│   │   │       ├── Resources
│   │   │       │   ├── app.icns
│   │   │       │   └── en-US.lproj
│   │   │       │       └── InfoPlist.strings
│   │   │       └── libc++.dylib
│   │   └── Icon\r
│   ├── King\ Arthur's\ Gold.app
│   │   └── Contents
│   │       ├── Info.plist
│   │       ├── MacOS
│   │       │   └── run.sh
│   │       └── Resources
│   │           └── shortcut.icns
│   ├── MagicaVoxel-0.99.6.2-macos-10.7
```

Although this command lists ALL the files and folders inside of your current folder!

To stop the `tree` program from crashing your computer use the keyboard keys `ctrl` + `C`.

And the rest is mostly the same as Replits shell!

If you want to get a "manual" of MacOS commands you can use the `man` command

(man command)
```
man
```

Although you need to tell `man` what page you want. 

(command)
```
man ls
```

This gives us a "manual" of the `ls` command! Once your done reading the "manual" for `ls` type the letter "Q" to exit the manual.

You can also display the current director you are in by running `pwd`

(command)
```
pwd
```

Here is a list of Unix (Mac or Linux) commands and their corresponding Windows commands

http://www.kevinbrotcke.com/windows/windows-vs-linux-command-line.html