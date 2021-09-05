This lecture is not a finished lecture (very unfinished) and is still a work in progress.

Rather than continuing to dredge through the boring stuff we'll let ourselves have some fun with Python and make a game!

Originally this was not part of the course as I wanted to make this course as short as possible by only covering the stuff you need to know and not "wasting" time on fun stuff, but hey, thats no fun! :P

Pyxel is a game engine that uses Python for scripting (Unreal Engine and Unity are examples of a game engine). In Pyxel everything is in pixels! The best part is that Pyxel runs inside of Replit!

Here are some useful references:
- pyxel tutorial and documentation (aka, notes / guides on how to use pyxel) https://pypi.org/project/pyxel/
- pyxel game engine code https://github.com/kitao/pyxel


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

Now click the play button! You should see a yellow cube!

![replit pyxel](/Assets/replit_pyxel.png)

We can add some code to "quit" or exit the game. Edit your code to look like the following.

```py
import pyxel

pyxel.init(100, 80)

def update():
    # check if Q was clicked
    if pyxel.btnp(pyxel.KEY_Q):
        # quit / exit
        pyxel.quit()

def draw():
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

Pyxel gives us code for checking if someone pressed a button. The `btnp` function stands for "button pressed". It gives us back a True or False if the person clicked the key *just now* (AKA, holding down the key will only count as a single click).

If you run the above code (make sure you click the mouse inside of the "game window thingy" to "focus" the browser in that area) and click the Q key you should see the game stop running! You can read the code for quitting as this.

```
if pyxel.button pressed(Key Q) then 
    pyxel.quit
```

Now lets make our cube fall as if it had gravity! We'll make two variables called `x` and `y`, to control the position of the cube.

(not working code)
```py
import pyxel

pyxel.init(100, 80)

x = 10
y = 10

def update():
    # check if replit was paused
    if pyxel.btnp(pyxel.KEY_Q):
        # quit / exit
        pyxel.quit()

def draw():
    pyxel.rect(x, y, x + 10, y + 10, 11)

pyxel.run(update, draw)
```

We use the variables instead of putting in the actual positions manually for the rect function.

The positions for the rect are in a grid. X is horizontal (horizontal like the horizon), and Y is vertical (up and down).

Here is a chart visualizing this.

![pyxel coordinates](/Assets/pyxel_coordinates.png)

We want to simulate physics so that the cube falls. We can do this by changing the y variable every "update".

But... currently there's a problem. We can't access the x and y variables inside of the `draw` function (or the `update` function) since x and y are outside of the functions!

We could pass x and y as arguments (inputs) to the `update` function, but the problem is that function arguments in most language are a **copy of the value** (copy of whatever was *inside of* the variable), so modifying x and y inside of update or draw, won't affect the x and y variables we originally made. 

To overcome this problem we will have to use a concept in programming where we wrap everything in an "object" (including the variables). 

An "object" in programming is a weird idea that programmers got from biology and how cells work. Essentially an object "holds" variables and function *inside of it*.

By using an "object" we will be able to modify the values of x and y in `update`, and then "use" the changed x and y values in `draw`.

Change your code to look like the following.

```py
import pyxel

pyxel.init(100, 80)

class Game():
    x = 10
    y = 10

    def update():
        # check if replit was paused
        if pyxel.btnp(pyxel.KEY_Q):
            # quit / exit
            pyxel.quit()

    def draw():
        pyxel.rect(x, y, x + 10, y + 10, 11)
```

(If you run this nothing will happen, don't worry we'll get to that in a second)

We create a new object using the "`class`" keyword. Making an object is much like making a function (at least in Python). Highlight all the code that is supposed to be inside of the class (aka "object") and click `ctrl` + `tab`. Just like in functions we have to let Python know what code is inside of the object and what is outside of the object.

We also deleted the `pyxel.run(update, draw)` function call.

Now to be able to access x and y in the `update` and `draw` functions we have to add a special parameter (function variable) to `update` and `draw` called "self".

Change your code to the following.

```py
import pyxel

pyxel.init(100, 80)

class Game():
    x = 10
    y = 10

    def update(self):
        # check if replit was paused
        if pyxel.btnp(pyxel.KEY_Q):
            # quit / exit
            pyxel.quit()

    def draw(self):
        pyxel.rect(self.x, self.y, self.x + 10, self.y + 10, 11)
```

The whole point in the "self" parameter (function variable) is to access variables that are "part of the object", and that is exactly what we do! We use `self` to access x and y through a period `.` like this `self.x` and `self.y`. Make sure you change your code to use "self" to access the x and y variables.

Now we can finally work on simulating gravity by changing y's position. We are supposed to only put "rendering" code inside of `draw`, so we'll use `update` for the gravity code.

Change the code in the update function to be the following.

```py
# ...
    def update(self):
        # ...
        self.y = self.y + 0.5

# ...
```

(We use `# ...` to signify code that is not being shown, in order to focus on code that is important, don't delete code that is not being shown though!)

Our gravity code is litterally one line of code `self.y = self.y + 0.5` although we can use the shortcut for decreasing a number.

(example)
```py
# ...
    def update(self):
        # ...
        self.y += 0.5

# ...
```

We "increase" the y position to go down since y goes downwards (as you saw previously). We also increase y by 0.5 because otherwise it won't fall as fast.

Now, if you want this code to actually do something we need to "make" the object. To make a "new" `Game` object we use the following code.

```py
import pyxel

pyxel.init(100, 80)

class Game():
	# ...

	def update(self):
		# ...

	def draw(self):
		# ...

# "Make" a new Game object.
Game()
```

"Making" an object looks like running a function. There is a funciton that gets called automatically when we "make" a new object. 

Change your cade and add the `__init__` funtion (I don't know why they have the double underscore in the name, but hey, thats just how it is).

```py
import pyxel

class Game():
	x = 10
	y = 10

	def __init__(self):
		pyxel.init(100, 80)
		pyxel.run(self.update, self.draw)

    def update():
        # ... removed for brevity (shortness)

    def draw():
        # ... removed for brevity (shortness)

Game()
```

We "initialize" our games window with `pyxel.init` and then "run" the `update` and `draw` function with `pyxel.run`. All of the code inside of an `__init__` funciton (in an object) will get called once automatically when you "make" a new object.

In the end your code should look like this.

```py
import pyxel

class Game():
	x = 10
	y = 10

	def __init__(self):
		pyxel.init(100, 80)
		pyxel.run(self.update, self.draw)

	def update(self):
		if pyxel.btnp(pyxel.KEY_Q):
			# quit / exit
			pyxel.quit()

		self.y += 1

	def draw(self):
		pyxel.cls(0)
		pyxel.rect(self.x, self.y, self.x + 10, self.y + 10, 11)

# "Make" a new object
Game()
```

We made sure to add one extra line of code that clears the screen before drawing the cube `pyxel.cls(0)` <- this clears the screen to red before drawing a cube again.

If you run this code you should see a yellow cube falling! Without the `cls` (clear screen) function, we would draw cobe after cube, without clearing the old ones (making a "smear" of yellow cubes).

Now we can simulate jumping / falling with a simple if statement.

(pseudo code)
```
if space_key pressed then
    move up
else
    fall down
```

Change the code inside of the `update` function to look like this.

```py
    def update(self):
		if pyxel.btnp(pyxel.KEY_Q):
			# quit / exit
			pyxel.quit()

        # jumping / falling
		if pyxel.btn(pyxel.KEY_SPACE):
            # jumping
			self.y -= 1
		else
            # falling
			self.y += 0.5
```

We make the jumping coe faster than the falling code.

Run thsi code, by clicking the space key you can make the player fall or "jump" (actually just move upwards).

If clicking the space key doesn't do anyhting, make sure to click inside of the game's window, then try clicking the space key (this is because the browser doesn't know you want to send input to the pyxel game, so you have to click on it).

Now what about making the player move side ot side? Ooooh

(pseudo code)
```
if right_arrow pressed then
    self.x += 1
if left_arrow pressed then 
    self.x -= 1
```

I'll let you figure out how to translate this pseudo code (concept code) into real Python code, but this pseudo-code is pretty close to how it would look. (Make sure to put it in the `update` function).

And now go and make a game! Make sure to check out the Tutorials! Or make a tutorial showing other people how to make what you made!