Rather than continuing to dredge through the boring stuff we'll let ourselves have some fun with Python and make a game! You can skip this section and keep going if you want to. I've designed the course so that if you skip this section you will still be able to understand the rest of the course. 

Originally this was not part of the course as I wanted to make this course as short as possible by only covering the stuff you need to know and not "wasting" time on fun stuff, but hey, thats no fun! :P

Pyxel is a game engine that uses Python for scripting (Unreal Engine and Unity are examples of a game engine). The best part is that Pyxel runs inside of Replit!

pyxel tutorial and documentation
https://pypi.org/project/pyxel/

pyxel game engine
https://github.com/kitao/pyxel

cool (paid) pixel art editor
https://www.pyxeledit.com/

# Pyxel Game Engine
Now lets learn the basics of making a game with Python!

Here we will teach you the basics of making a game with Pyxel, and then afterwards in the Tutorials there will be tutorials on how to make different types of games using what you learn from this! This way you can have different options depending on the type of game you want to make!

Create a new repl. Select Pyxel (a Python "framework" for making games). Name the project "hideous basic game" (you can honestly call it whatever you want).

Now add the following code.

```py
import pyxel
```

The "import" keyword gets us access to the code from pyxel.

Now we need to make a "window" for our game. Make your code look like the following.

```py
import pyxel

pyxel.init(100, 80)
```

`pyxel.init(100, 80)` gives us a window that is 100 pixels wide by 80 pixels tall. 

Run this code (it might take a second to load). You will see something flicker for a second then the code gets stopped!

To prevent the code from finishing so quickly we need some code that will run every single "frame". Have you ever heard of "fps"? Video games are many (MANY) pictures being redrawn onto your screen every few seconds, each picture slightly different, making it look like a video.

Change your code so that it looks like the following.

```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
    # code for drawing / rendering
    pass

pyxel.run(update, draw)
```

We make 2 functions. One is for "drawing" shapes and pictures to the screen. The other is the one that will have all the code for, say, moving the player around and checking if we clicked a certain key. 

You will also notice the `pass` keyword inside of each function, we have to add this because we are not allowed to make a function that does nothing! The `pass` keyword is there (temporarily) for telling Python to ignore the function so we don't get any errors.

In order to tell Pyxel about our 2 new functions we call pyxel's `run` function. The `pyxel.run` function takes 2 arguments (inputs). The first is the name of our "update" function (conveniently called "update"), and the second is the "draw" function (also conveniently named "draw").

Now lets draw a simple cube using the "rect" function, standing for the word "rectangle".

```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
    # draw a rectangle
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

Click the play button to see the following!

![replit pyxel](/Assets/replit_pyxel.png)

Techincally when we stop the game using Replits pause button our code is supposed to "quit" or exit so lets add that code.

```py
import pyxel

pyxel.init(100, 80)

def update():
	if pyxel.btnp(pyxel.KEY_Q):
		pyxel.quit()

def draw():
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

`btnp` stands for "button pressed". You can read the coe for quitting as this.

```
if button pressed(Key "Q") then 
    quit
```

Now lets make our cube fall as if it had gravity! We'll make two variables called `x` and `y`, to control the position of the cube.


NOT WORKING CODE
```py
import pyxel

pyxel.init(100, 80)

def update():
	if pyxel.btnp(pyxel.KEY_Q):
		pyxel.quit()

def draw():
	# x and y variables
	x = 10
	y = 10

    pyxel.rect(x, y, 20, 20, 11) # use x and y variables

pyxel.run(update, draw)
```

Now we can change the y's position every draw? TODO: how to decrease y?

TODO
- show YouTube tutorials tab in replit