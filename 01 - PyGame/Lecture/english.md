You just finished learning about the basics of coding. Now you get to actually *do* something with that coding!

We are going to use a "framework" or "library" of code that was made for making games using Python.

"framework" and "library"  are just fancy words for code written by someone else that does the boring code stuff (like getting access to your Operating System's "Windowing" code, or interpreting key presses), so we can focus on making a game.

Make a new Repl and select "PyGame". Name it "Pygame".

We need to get access to the "PyGame" framework in our code. 

(add the following code)
```py
import pygame
```

Now we can use the word "pygame" to access stuff in the PyGame library of code.

PyGame has to set some stuff up for us, so we need to help it out and use their builtin "init" function.

(change your code to the following)
```py
import pygame

pygame.init()
```

First lets tell PyGame how big we want our game's window to be (as well as give the window a title)

(add the following to your code)
```py
# ... not showing irrelevant code

# create the window
pygame.display.set_mode([400, 200])
# set the windows title
pygame.display.set_caption('my overrated jumping game')
```

