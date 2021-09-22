Rather than continuing to dredge through the boring stuff we'll let ourselves have some fun with Python and make a game!

Pyxel is a game engine that uses Python for scripting (Unreal Engine and Unity are examples of a game engine).

The best part is that Pyxel runs inside of Replit! (So you don't have to download anything!)

# Pyxel Game Engine
Create a new repl. Select "Pyxel" (a Python "framework" for making games). Name the project "hideous basic game" (you can honestly call it whatever you want).

Now add the following code.

```py
import pyxel
```

The "import" keyword gets us access to the code from pyxel.

Now we need to make a "window" for our game. 

(change your code to look like this)
```py
import pyxel

pyxel.init(100, 80)
```

Run this code (it might take a second to load). You will see something flicker for a second then the code gets stopped!

`pyxel.init(100, 80)` gives us a window that is 100 pixels wide by 80 pixels tall (although you barely saw it for a split second).

To prevent the code from finishing so quickly we need some code that will run every single "frame". Have you ever heard of "fps"? Video games are many (MANY) pictures being redrawn onto your screen every few seconds, each picture slightly different, making it look like a video.

(change your code to look like following)
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

In order to tell Pyxel about our 2 new functions (`update` and `draw`) we call pyxel's `run` function  ("call" is a fancy word for "use").

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

The `pyxel.run` will make the `update` function happen again, again, and again, preventing our game from stopping. Without `pyxel.run` you just end up making a window (using the `pyxel.init` function from before) and then immediately quit.

Now run this code. You should see a "window thingy".

Lets clear the background of our screen every time we draw the game.

(change your code to look like this)
```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
	# clear the backgrounds to a nice blue
	pyxel.cls(12)

pyxel.run(update, draw)
```

The `cls` function stands for "clear screen". Run this code to see the background of our "window thingy" be colored blue.

Now lets draw a cube on top of the background using the `rect` function (standing for the word "rectangle").

(change your code to the following)
```py
import pyxel

pyxel.init(100, 80)

def update():
    # code that runs every few milliseconds
    pass

def draw():
	# clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a rectangle
	pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

The format of the `rect` function looks like this

![pyxel rect](/Assets/pyxel_rect.png)

Now click the play button! You should see a yellow cube!

![replit pyxel](/Assets/replit_pyxel.png)

Now we will use the `rect` function to add a sandy beach!

(example code)
```py
import pyxel

pyxel.init(100, 80)

def update():
	# code that runs every few milliseconds
	pass

def draw():
	# clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a rectangle
	pyxel.rect(10, 10, 20, 20, 11)

	# sandy ground
	pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

pyxel.run(update, draw)
```

Using `pyxel.width` gives us the width of the window, and using `pyxel.height` gives us the height of the window.

You can visualize our drawing of the ground as this

![pyxel ground](/Assets/pyxel_ground.png)

Feel free to take your time and make a nice landscape.

Once your done decorating... we will add some code to "quit" or exit the game.

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
    # clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a rectangle
	pyxel.rect(10, 10, 20, 20, 11)
	
	# sandy ground
	pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

pyxel.run(update, draw)
```

Pyxel gives us code for checking if someone pressed a button. The `btnp` function stands for "button pressed". It gives us back a True or False if the person clicked the key *just now* (AKA, holding down the key will only count as a single click the exact moment you clicked it).

Run the above code (make sure you click the "game window" thingy to "focus" the browser in that area) and click the Q key to see the game stop running!

Now lets make our cube fall as if it had gravity! We'll make two variables called `x` and `y`, to control the position of the cube.

(change your code to the following)
```py
import pyxel

pyxel.init(100, 80)

x = 10
y = 10

def update():
	# check if Q was clicked
	if pyxel.btnp(pyxel.KEY_Q):
		# quit / exit
		pyxel.quit()

def draw():
    # clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a cube
	pyxel.rect(x, y, x + 10, y + 10, 11)
	
	# sandy ground
	pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

pyxel.run(update, draw)
```

You'll notice we reaplce the positons of the cube using `x` and `y`. We offset the bottom right corner of the cube using `+ 10` (otherwise the cube would be 0 width by 0 height).

![pyxel positioned rect](/Assets/pyxel_positioned_rect.png)

We want to simulate physics so that the cube falls. We can do this by changing the y variable every "update", causing the cubes position to change making the cube fall.

But... currently there's a problem. We can't access the `x` and `y` inside of `draw` (or `update`) since `x` and `y` are outside of the functions! 

The code may work *for now* but eventually python will not be able to tell if you are making a *new variable* inside of `draw`, or trying to change the old `x` and `y` variables.

(example)
```py
x = 10
y = 10

def draw():
	x = x + 1 # new variable? changing old variable?
	y = 1 # new variable? changing old variable?

    pyxel.rect(x, y, x + 10, y + 10, 11)
```

We call this problem "scope" where a variable has a "scope" of where it can and can't be accessed, and (technically) our `x` and `y` variables are *outside of* the "scope" of `draw` (aka `draw` shouldn't be able to access `x` and `y`).

We could try to pass x and y as arguments (inputs) to the `draw` function...

(example)
```py

x = 10
y = 10

def draw(x, y):
    pyxel.rect(x, y, x + 10, y + 10, 11)
```

...but that actually just makes separate variables for `draw` that happen to be called `x` and `y`.

To overcome this terrible problem we will have to use a concept in programming where we wrap everything in an "object" (including the variables).

An "object" in programming is a weird idea that programmers got from biology and how cells work. Essentially an object can "holds" variables and functions ***inside of it*** (Whaaaaaaaaaaaaaaaaaaaaaaaaat? Huh?).

We could make a person "object" that has a `health` or `speed` variable, and a `moveForwards` function inside of it.

By using an "object" we will be able to access `y` in `update` or `draw` *and change y* (*changing* `y` is where it would get tricky as you saw in the example)

To put all our code in an object first delete the `pyxel.run()` and the `pyxel.init()` functions (this is temporary).

(change your code to look like this)
```py
import pyxel

x = 10
y = 10

def update():
  # check if Q was clicked
  if pyxel.btnp(pyxel.KEY_Q):
    # quit / exit
    pyxel.quit()

def draw():
  # clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a cube
	pyxel.rect(x, y, x + 10, y + 10, 11)
	
	# sandy ground
	pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)=
```

Now add `class Game():` right below `pyxel.import`. "class" is a fancy word for object.

(change your code to look like this)
```py
import pyxel

class Game():

x = 10
y = 10

def update():
  # check if Q was clicked
  if pyxel.btnp(pyxel.KEY_Q):
    # quit / exit
    pyxel.quit()

def draw():
  # clear the backgrounds to a nice blue
	pyxel.cls(12)

	# draw a cube
	pyxel.rect(x, y, x + 10, y + 10, 11)
	
	# sandy ground
	pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)
```

Just like with functions we have to tell Python what code is "inside of the object" by putting a tab (2 or 4 spaces) in front of the code that is supposed to be inside of it.

To "indent" the code to be *inside of* the `Game` class/object, highlight/select all the code below `class Game():` (using the mouse) and click `tab`. This will indent all of the highlighted code.

```py
import pyxel

class Game():

	x = 10
	y = 10

	def update():
		# check if Q was clicked
		if pyxel.btnp(pyxel.KEY_Q):
			# quit / exit
			pyxel.quit()

	def draw():
		# clear the backgrounds to a nice blue
		pyxel.cls(12)

		# draw a cube
		pyxel.rect(x, y, x + 10, y + 10, 11)

		# sandy ground
		pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

```

Now to be able to access `x` and `y` in the `update` or `draw` functions we have to add a special parameter (function variable) to `update` and `draw` called "self".

(change your code to the following)
```py
import pyxel

class Game():

	x = 10
	y = 10

	def update(self):
		# check if Q was clicked
		if pyxel.btnp(pyxel.KEY_Q):
			# quit / exit
			pyxel.quit()

	def draw(self):
		# clear the backgrounds to a nice blue
		pyxel.cls(12)

		# draw a cube
		pyxel.rect(self.x, self.y, self.x + 10, self.y + 10, 11)

		# sandy ground
		pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

```

The "self" parameter (function variable) gives us access to the stuff inside the object, and that is exactly what we do! We use `self` to access `x` and `y` through a dot `.` like this `self.x` and `self.y` (make sure you change your code to use `self` to access the `x` and `y` variables)

Now we can finally work on simulating gravity by changing y's position!

We'll use `update` for the gravity code, since we are supposed to only put "rendering" code inside of `draw`.

(If you see `# ...` that means there is some code we are (temporarily) ignoring)

(change your code to the following)
```py
# ...
    def update(self):
        # ...
        self.y = self.y + 0.5

# ...
```

Our gravity code is litterally one line `self.y = self.y + 0.5` although we can use the shortcut for decreasing a number.

(example)
```py
# ...
    def update(self):
        # ...
        self.y += 0.5

# ...
```

We increase the y position to move the cube down (since y goes downwards).

So far we have only defined an object. To "make" a new `Game` object we use the following code.

```py
import pyxel

pyxel.init(100, 80)

class Game():
	# ...

	def update(self):
		# ...

	def draw(self):
		# ...

# "Make" a Game object.
Game()
```

"Making" an object looks like running a function. We could hold onto the object we made using a variable...

(change your code to the following)
```py
mygame = Game()

# run the update function inside of Game
mygame.update()

# access the x variable inside of Game
mygame.x
```

... but we don't need to do that.

When we "make" the new object there is a function will get run automatically called `__init__` (Don't ask me why they have a double underscore in the name...).

Add the `__init__` function somewhere in our object.

(change your code to the following)
```py
import pyxel

class Game():
	# ...

	# the `__init__` function
	def __init__(self):
		pyxel.init(100, 80)
		pyxel.run(self.update, self.draw)

    def update():
        # ...

    def draw():
        # ...

# "Make" a Game object.
Game()
```

Inside of `__init__` we make our games window with `pyxel.init` and then tell pyxel about our `update` and `draw` functions with `pyxel.run`. 

All of the code inside of an `__init__` funciton (in an object) will get called/run automatically when you "make" the object.

In the end your code should look like this

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

		self.y += 0.5

	def draw(self):
		# clear the backgrounds to a nice blue
		pyxel.cls(12)

		# draw a cube
		pyxel.rect(self.x, self.y, self.x + 10, self.y + 10, 11)

		# sandy ground
		pyxel.rect(0, pyxel.height - 10, pyxel.width, pyxel.height, 40)

# "Make" a Game object
Game()
```

We made sure to add one extra line of code that clears the screen before drawing the cube `pyxel.cls(0)` <- this clears the screen to red before drawing the cube again.

If you run this code you should see a yellow cube falling! Without the `cls` (clear screen) function, we would draw a cube every few milliseconds without clearing the old ones (making a "smear" of green cubes).

Now we can simulate jumping / falling with a simple if statement.

(pseudo code <- fake example code)
```
if space_key pressed then
    move up
else
    fall down
```

Change the code inside of the `update` function have "jumping"

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

Run this code, by clicking the space key you can make the player fall or "jump" (make sure to click inside of the games window to "focus" the browser on it).

If clicking the space key doesn't do anything, make sure to click inside of the game's window, then try clicking the space key (this is because the browser doesn't know you want to send input to the pyxel game, so you have to click on it).

We can prevent the player from falling forever and stop once it hits the bottom of the games window.

(change your code to the following)
```py
# ...

    def update(self):
		# ...

		# jumping / falling
		if pyxel.btn(pyxel.KEY_SPACE):
			self.y -= 1 # jump
		# else if below window
		elif self.y < pyxel.height:
			self.y += 1 # fall

# ...
```

Although we should probably offset this `elif self.y < pyxel.height` because the `self.y` variable is the top left corner of the cube.

![pyxel self rect](/Assets/pyxel_self_rect.png)

And it would be nice to accound for the height of the ground, so probably an offset around 20.

(change your code to add an offset)
```py
	# ...

		# offset of 20
		elif self.y + 20 < pyxel.height:
			# ...
	# ...
```

Now what about making the player (cube) move side to side? Ooooh!

(change your code to the following)
```py
# ...

    def update(self):
		# ...

		# move side to side
		if pyxel.btn(pyxel.KEY_RIGHT):
			self.x += 1
		if pyxel.btn(pyxel.KEY_LEFT):
			self.x -= 1

# ...
```

Now go ahead and try this code out and have fun with it!

Here are some useful functions for drawing other shapes in Pyxel.

`pix(x, y, col)`
- Draw a single pixel of color `col` at (x, y)

`line(x1, y1, x2, y2, col)`
- Draw a line of color `col` from (x1, y1) to (x2, y2)

`rectb(x1, y1, x2, y2, col)`
- Draw the outline of a rectangle of color `col` from (x1, y1) to (x2, y2)

`circ(x, y, r, col)`
- Draw a circle of radius `r` and color `col` at (x, y)

`circb(x, y, r, col)`
- Draw the outline of a circle of radius `r` and color `col` at (x, y)

`text(x, y, s, col)`
- Draw a string (words) `s` of color `col` at (x, y)

(above list taken from https://pythonawesome.com/a-retro-game-development-environment-in-python/)