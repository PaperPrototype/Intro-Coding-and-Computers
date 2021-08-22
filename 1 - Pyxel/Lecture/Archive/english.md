This lecture is not a finished lecture (very unfinished) and is still a work in progress.

Rather than continuing to dredge through the boring stuff we'll let ourselves have some fun with Python and make a game! You can skip this section and keep going if you want to. I've designed the course so that if you skip this section you will be able to understand the rest of the course. 

Originally this was not part of the course as I wanted to make this course as short as possible by only covering the stuff you need to know and not "wasting" time on fun stuff, but hey, thats no fun! :P

Pyxel is a game engine that uses Python for scripting (Unreal Engine and Unity are examples of a game engine). In Pyxel everything is in pixels! The best part is that Pyxel runs inside of Replit!

Here are some useful references:
- pyxel tutorial and documentation (aka, notes / guides on how to use pyxel) https://pypi.org/project/pyxel/
- pyxel game engine code https://github.com/kitao/pyxel
- cool (paid) pixel art editor (accidentally discovered this) https://www.pyxeledit.com/

# Pyxel Game Engine
Now lets learn the basics of making a game with Python!

Here we will teach you the basics of making a game with Pyxel, and then afterwards in the Tutorials there will be tutorials on how to make different types of games using what you learn from this! This way you can have different options depending on the type of game you want to make!

Create a new repl. Select "Pyxel" (a Python "framework" for making games). Name the project "hideous basic game" (you can honestly call it whatever you want).

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

You will also notice the `pass` keyword inside of each function. The `pass` keyword is there (temporarily) for telling Python to ignore the function so we don't get any errors (because we are not allowed to make a function that does nothing!).

In order to tell Pyxel about our 2 new functions we call pyxel's `run` function. The `pyxel.run` function takes 2 arguments (inputs). The first is the name of our "update" function (conveniently called "update"), and the second is the "draw" function (also conveniently named "draw").

Lets add a simple cube using the "rect" function (standing for the word "rectangle").

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

Now click the play button! You should see the following!

![replit pyxel](/Assets/replit_pyxel.png)

We can add some code to "quit" or exit the game. Lets add that code.

```py
import pyxel

pyxel.init(100, 80)

def update():
    # check if replit was paused
    if pyxel.btnp(pyxel.KEY_Q):
        # quit / exit
        pyxel.quit()

def draw():
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

Pyxel gives us code for checking if someone pressed a button. The `btnp` function stands for "button pressed". It gives us back a True or False if the person clicked the key *just now* (AKA, holding down the key won't do anything).

If you run the above code (make sure you click you mouse inside of the game window thingy to "focus" the browser in that area) and click the Q key you should see the game stop running! You can read the code for quitting as this.

```
if pyxel.button pressed(Key Q) then 
    pyxel.quit
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

    # use x and y variables
    pyxel.rect(x, y, 20 + x, 20 + y, 11)

pyxel.run(update, draw)
```

We use the variables instead of putting in the actual positions manually for the rect function.

The positions for the rect are in a grid. X is horizontal (horizontal like the horizon), and Y is vertical (up and down).

Here is a chart visualizing this.

![]

The maximum X and Y positions depend on how big we made the game screen using the `init` function from pyxel. Currently we put 100 width (X height (Y). The size of everyhting is in pixels (which is why Pyxel is called "Pyxel").

If you hover your mouse over the word "rect" in our code you should see a hint telling you what arguments are x and y.

The last number in the "rect" function is a color number, apparently 11 stands for yellow.

TODO
Although technically we aren't supposed to put any...

TODO
- show YouTube tutorials tab in replit

TODO TODO TODO implement this into the lecture,

In order to access variables inside of our update and draw funtion we will have to make an "object".

An "object" in programming is a weird idea that programmers got from biology and how cells work. The father of object "oriented" programming (using objects for everything) is Alan Kay, who was a biologist.

Essentially an object "holds" variables and function *inside of it*. Lets make a simple object in Python for our game.

Delete all your code (or make a new repl if you want), and write the following.

```py
class MyObject():
    # add stuf inside of here
```

For some reason objects are made using the "class" keyword (I honestly have no idea why). We usually uppercase the name of an Object. To "make" the object you simply "call it" like you would a function.

(example, don't write this)
```py
class MyObject():
    # add stuff inside of here

# Made a new object...
MyObject()
```

Lets get our "object" to do something interesting. There is a function that gets called automatically when we "make" a new object. Below we change the `MyObject` object to have the `__init__` function.

Change your code to match this.

```py
class MyObject():
	def __init__(self):
        # print function
		print("Made a new object called:", self)

```

I don't like the fact you have to have the double underscore `__` in the `init` function, but thats just what the creators of Python decided, so we are stuck with it.

You'll also notice that the `__init__` function has a parameter called "self". This is a variable that refers to the object we are curretnly in. Every single function inside of an object will have to have this "self" variable.

I think you can tell what the rest of the code is doing (I'm talking about the `print` function).

Lets now "make" this object, and see code from the `__init__` function print our our message (remember the `init` function runs automatically when we "make" the object).

(answer)
```py
class MyObject():
	def __init__(self):
		print("Made a new object:", self)

MyObject()
```

The above code should print out something like this.

```
Made a new object: <__main__.MyObject object at 0x7f9669431400>
```

The last part `0x7f9669431400>` I think is a memory address telling us where in memory the object is. Its also in hexadecimal (hexadecimal is a number system that uses 16 digits instead of 10). You'll learn hexadecimal in the "Fundamentals" section of this course.

To make a variable in the class you can just... make a new variable called "x" in the class, then print that variable in the `__init__` function.

(answer)
```py
class MyObject():
	x = 0

	def __init__(self):
		print("printing out a variable", self.x)

MyObject()
```

You will notice we have to use the "self" parameter to access the x variable.

TODO make draw and update functions again.

We can also make other funcitons besides the `__init__` function. Make a new function inside of the class (or "object") that prints "hello world".

(answer)
```py
class MyObject():
	x = 0

	def __init__(self):
		print("printing out a variable", self.x)

	def say_hello(self):
		print("hello idiots")

MyObject()
```

Now run the `say_hello` (or whatever you called it) function inside of the `__init__` function.

(answer)
```py
class MyObject():
	x = 0

	def __init__(self):
		print("printing out a variable", self.x)

		# we have to use the "self" parameter to access it
		self.say_hello()

	def say_hello(self):
		print("hello idiots")

MyObject()
```

And thats all there is to know for now! Trust me theres... way more like... objects that inherit from other objects... but thats gonna be too broing and I think we are ready for something more fun like making a game! And that is what the next section will teach you! 

Although... if your just wanting to get things done as fast as possible (like me) you can skip the next section without any problems! We  structured the course (actually currently its just me) so that the next section doesn't cover any crucial concepts and is purely for fun!