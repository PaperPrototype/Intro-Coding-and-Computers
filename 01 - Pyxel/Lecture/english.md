Rather than continuing to dredge through the boring stuff we'll let ourselves have some fun with Python and make a game!

Pyxel is a game engine that uses Python for scripting (Unreal Engine and Unity are examples of a game engine).

The best part is that Pyxel runs inside of Replit!

# Pyxel Game Engine
Create a new repl. Select "Pyxel" (a Python "framework" for making games). Name the project "hideous basic game" (you can honestly call it whatever you want).

Now add the following code.

```py
import pyxel
```

The "import" keyword gets us access to the code from pyxel.

Now we need to make a "window" for our game. 

(change your code to the following)
```py
import pyxel

pyxel.init(100, 80)
```

Run this code (it might take a second to load). You will see something flicker for a second then the code gets stopped!

`pyxel.init(100, 80)` gives us a window that is 100 pixels wide by 80 pixels tall (although you barely saw it for a split second).

To prevent the code from finishing so quickly we need some code that will run every single "frame". Have you ever heard of "fps"? Video games are many (MANY) pictures being redrawn onto your screen every few seconds, each picture slightly different, making it look like a video.

(change your code to the following)
```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
    # code for drawing / rendering
    pass
```

We make 2 functions. One is for "drawing" shapes and pictures to the screen. The other function called `update` is the one that will have all the code for, say, moving the player around and checking if we clicked a certain key.

You will also notice the `pass` "keyword" inside of each function. `pass` is a special keyword to (temporarily) tell Python to just "pass" the function (because we are not allowed to make a function that does nothing! (`update` and `draw` are a "function")).

In order to tell Pyxel about our 2 new functions (`update` and `draw`) we use (or "call") pyxel's `run` function. 

The `pyxel.run` function takes 2 arguments (inputs). The first is the name of our "update" function (conveniently called "update"), and the second is the "draw" function (also conveniently named "draw").

(change your code to use pyxel's "run" function)
```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
    # code for drawing / rendering
    pass

# pyxel's "run" function
pyxel.run(update, draw)
```

Lets add a simple cube by using pyxel's "rect" function (standing for the word "rectangle").

(change your code to the following)
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

We can add some code to "quit" or exit the game.

(change your code to the following)
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

If you run the above code (make sure you click the mouse inside of the "game window thingy" to "focus" the browser in that area) and click the Q key to see the game stop running!

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

By using an "object" we will be able to modify the values of x and y in `update`, and then "use" the changed x and y values in `draw` to move the cube.

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

We deleted the `pyxel.run(update, draw)` function call for now.

The word "`class`" is keyword for making objects.

Just like in functions we have to let Python know what code is "inside of the object" by putting 2 or 4 spaces in front of them.

Highlight all the code that is supposed to be inside of the class (aka "object") and click `ctrl` + `tab`. This will automatically put the correct amount of spaces in front of the highlighted code.

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

The whole point in the "self" parameter (function variable) is to access variables that are "part of the object", and that is exactly what we do! We use `self` to access x and y through a dot `.` like this `self.x` and `self.y`. Make sure you change your code to use "self" to access the x and y variables.

Now we can finally work on simulating gravity by changing y's position. 

We'll use `update` for the gravity code, since we are supposed to only put "rendering" code inside of `draw`.

Change the code in the `update` function to be the following.

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

We "increase" the y position to move the cube down (since y goes downwards).

Now, if you want this code to actually do something we need to "make" the object. To "make" a new `Game` object we use the following code.

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

"Making" an object looks like running a function. There is a function that gets called automatically when we "make" a new object called `__init__` (I don't know why they have the double underscore in the name, but hey, thats just how it is).

Add the `__init__` function to our object.

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

We made sure to add one extra line of code that clears the screen before drawing the cube `pyxel.cls(0)` <- this clears the screen to red before drawing the cube again.

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

Run this code, by clicking the space key you can make the player fall or "jump" (make sure to click inside of the games window to "focus" on it).

If clicking the space key doesn't do anyhting, make sure to click inside of the game's window, then try clicking the space key (this is because the browser doesn't know you want to send input to the pyxel game, so you have to click on it).

We can prevent the player from falling forever and stop once it hits the bottom of the games window.

(edit your code to look like the following)
```py
# ... snip

    def update(self):
        # ... snip

        # jumping / falling
		if pyxel.btn(pyxel.KEY_SPACE):
			self.y -= 1 # jump
		else:
            # if position + size of cube < height of window...
			if self.y + 10 < pyxel.height:
				self.y += 1 # then fall

# ... snip
```

Now what about making the player (cube) move side to side? Ooooh

(example, optional)
```py
# ... snip

    def update(self):
		# ... snip

		if pyxel.btn(pyxel.KEY_RIGHT):
			self.x += 1
		if pyxel.btn(pyxel.KEY_LEFT):
			self.x -= 1

# ... snip
```

Here are some useful functions for drawing other shapes in Pyxel.

`cls(col)`
- Clear screen with color `col`

`pix(x, y, col)`
- Draw a single pixel of color `col` at (x, y)

`line(x1, y1, x2, y2, col)`
- Draw a line of color `col` from (x1, y1) to (x2, y2)

`rect(x1, y1, x2, y2, col)`
- Draw a rectangle of color `col` from (x1, y1) to (x2, y2)

`rectb(x1, y1, x2, y2, col)`
- Draw the outline of a rectangle of color `col` from (x1, y1) to (x2, y2)

`circ(x, y, r, col)`
- Draw a circle of radius `r` and color `col` at (x, y)

`circb(x, y, r, col)`
- Draw the outline of a circle of radius `r` and color `col` at (x, y)

`text(x, y, s, col)`
- Draw a string (words) `s` of color `col` at (x, y)


(above list taken from https://pythonawesome.com/a-retro-game-development-environment-in-python/)