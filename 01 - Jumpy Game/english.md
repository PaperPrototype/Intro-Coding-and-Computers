TODO:
- explain velocity as length, and moving y pos by every increasing y_vel length (use downwards moving chart with arrow lines with length, and adding y_vel to y pos)

You just finished learning about the basics of coding. Now you get to actually *do* something with that coding!

We are going to use a "framework" or "library" of code that was made for making games using Python.

"framework" and "library"  are just fancy words for code written by someone else that does the boring code stuff (like getting access to a Windows "Window", or interpreting key presses from files) so we can focus on making our game.

Make a new Repl and select "PyGame". Name it "Pygame".

We need to get access to the "PyGame" framework in our code. 

(add the following code)
```py
import pygame
```

Now we can use the word "pygame" to access stuff in the PyGame library of code.

PyGame has to set some stuff up for us, so we need to help it out and use its builtin "init" function.

(change your code to the following)
```py
import pygame

pygame.init()
```

The `init()` function sets some stuff up for us (I honestly don't know what it does).

Now lets tell PyGame how big we want our game's window to be (as well as give the window a title)

(add the following code below your current code)
```py
# ... irrelevant code

# creates a window of 400 width, 200 height
pygame.display.set_mode([400, 200])
# set the title
pygame.display.set_caption("Jumpy Game")
```

(Make you don't delete your existing code! Simply add the code we showed you *below* your current code! We put a comment that says `# ... irrelevant code` <- this just means we are only showing you new code that needs added, rather than showing you code you've already seen!)

Inside of the `pygame.display.set_mode` function we give it a list of two numbers `[400, 200]` which represent a width and height.

Inside of the `pygame.display.set_caption` function we put the string `"Jumpy Game"`(remember "string" means words or phrases enclosed in double quotes).

The `pygame.display.set_mode([400, 200])` will give us back a "display" (AKA access to the window). We will store that in a variable called "window".

(change your code to have a window variable)
```py
window = pygame.display.set_mode([400, 200])

pygame.display.set_caption("Jumpy Game")
```

Now we can "fill" the entire window with the color black!

(add the following to your code, below the previous code)
```py
# ... irrelevant code

black = [20, 20, 40]
window.fill(black)
```

We make a new variable called "black". It is a list of 3 numbers. Each number corresponds with the colors Red Green and Blue (AKA "RGB"). By mixing different amounts of Red Green and Blue light you can get any color of the rainbow (but you probably already know that).

If you click play now, the game will start and then stop, after only a second. We need some code that will run over and over, an endless loop!

(add the following to your code)
```py
# ... irrelevant code

# (1) Endless loop
Stop = False
while Stop == False:

	# (2) Go through each mouse press and key press
	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True
```

(1) We make an endless loop, that loops "while Stop is equal to False". We set the `Stop` variable to False, so the loop will run over and over (until the `Stop` variable becomes True).

(2) We then go through each "event" that has happened, and "get" it (store it) in the "myEvent" variable. Each loop we check if the event type (in the "myEvent" variable) is `QUIT`. If the quit button gets pressed then this will be true, causing us to set `Stop` to True, which makes the next `while` loop not run (and our game exits).

Run this code and you should see the following!

![replit jumpy game plain](/Assets/replit_jumpy_game_plain.png)

There is one noticable problem. The window area is white! Not black how it should be!.

At the end of each loop we need to "update" the picture on the canvas.

(add the following to your code)
```py
# ... irrelevant code
while Stop == False:

	# ... irrelevant code

	# (1) Update the display
	pygame.display.update()
```

You will notice we did not show any old code (except for "`while Stop == False:`" so that you can figure out where to put the new code).

Make sure the `pygame.display.update()` code is "indented" using the "tab" key (so that it is inside of the "while" loop). Make sure you only "indent" 1 time for this code, or you will put it inside of the wrong loop! (The `for myEvent in pygame.event.get():` loop would be the wrong loop).

(1) The `pygame.display.update()` will update our display (AKA the window). Now run the code and the window should be colored black! Yay!

![replit jumpy game black window](/Assets/replit_jumpy_game_black_window.png)

Lets draw a cube.

```py
# ... irrelevant code

# (1) white color
white = [255, 255, 255]
black = [20, 20, 40]
window.fill(black)

# Endless loop
Stop = False
while Stop == False:

	# (2) draw a rectangle
	pygame.draw.rect(window, white, [10, 10, 20, 20])

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	pygame.display.update()
```

(1) We add a white color.

(2) We draw a rectangle. We tell it what window to draw to, as well as give it a color. We give it a list of numbers. The first two numbers are an `x` and `y` position.

Run this code, you should see the following.

![replit pygame cube](/Assets/pygame_cube.png)

The position `10, 10` and size `20, 20` of our rect works like this.

![replit pyagem rect](/Assets/pygame_rect.png)

Now to control our cube, we will use `x` and `y` variables for the cubes position.

(edit your code to the following)
```py
# ... irrelevant code

# (1)
x = 10
y = 10

Stop = False
while Stop == False:

	# (2) use x and y variables
	pygame.draw.rect(window, white, [x, y, 20, 20])

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	pygame.display.update()
```

(1) We make 2 variables `x` and `y`.

(2) We use the variables in the `rect` function.

Now lets make our cube fall by changing the `y` position to move it down, as long as the `y` position is inside of the window!

```py
# ... irrelevant code

Stop = False
while Stop == False:

	pygame.draw.rect(window, white, [x, y, 20, 20])

	# (1) if inside of window
	if y < window.get_height():
		# move downwards
		y = y + 1

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	pygame.display.update()
```

(1) if `y` is less than the height of the window, then move the `y` position downwards (increasing `y` moves us downwards).

Although really we are just comparing 2 numbers to see if one is bigger than the other.

Run this code. Woh! That cube *smeeeears* down the window. To prevent "smearing" we have to re-color the entire window black again before drawing another cube (when you draw a cube it just "paints" it on top of everything else).

(re-color by using `fill` at the beginning)
```py
# ... irrelevant code

Stop = False
while Stop == False:

	# (1)
	window.fill(black)

	pygame.draw.rect(window, white, [x, y, 20, 20])

	# ... irrelevant code
```

(1) Before painting another cube onto the window, we first clear/fill the entire window with `black` (`black` is a variable we made earlier).

Remember, you can always "undo" the last edit you did by clicking the `ctrl` + `Z` keys.

![windows undo](/Assets/win_undo.png)

If your on a Mac/Apple computer its `command` + `Z`.

![macos undo](/Assets/mac_undo.png)

Now, the cube fell really fast! This is because our "loop" was running at like 1000 frames per second! ("frames" is the number of times we "update" the window with `pygame.display.update()`). Basically running the code inside of the `while Stop == false:` loop 1000 times per second, which is moving our cube by 1 pixel down 1000 times per second.

Rather than looping 1000 times per second, we will tell pygame to "delay" and make sure we wait at least 100 milliseconds (which is 0.1 seconds).

(add delay)
```py
# irrelevant code

# Endless loop
Stop = False
while Stop == False:

	# delay
	pygame.time.delay(100)

	# ... irrelevant code
```

Now click play and the cube falls at more.. predicable (yet slow) speed. "Predictable" because the amount of time between each loop will be the same, which will help us when doing some physics (if you speed up (or slow down) "time" then the physcis will move faster (or slower), and we want the physics to move at a certian "rate" (AKA speed)).

Lets add some realistic physics for gravity (AKA falling) and jumping by using some math and a few basic laws of physics such as acceleration and velocity.

Every second we are moving 10 pixels down (at least we should be).

Here's why:

We have 0.1 seconds each loop, and move 1 pixel per loop... So `0.1 seconds = 1 pixel (of movement)`. If we multiply both sides of the equal sign `=` then nothing will break (mathematically). So multiply both sides by 10, and you get `1 second = 10 pixels`.

Now, every second we want to *increase* the number of pixel's we move by to fall faster as time passes (AKA "accelerate" from the force of gravity pulling us down).

![pygame gravity velocity](/Assets/pygame_gravity_velocity.png)

Basically every loop we will fall faster.

Make a variable called `y_velocity` and we will use it as the number to increase each loop (then we will move our cubes position based on this ever increasing "velocity" number).

(edit the code to the following)
```py
# ... irrelevant code

# (1)
y_velocity = 0

Stop = False
while Stop == False:

	pygame.time.delay(100)

	window.fill(black)

	pygame.draw.rect(window, white, [x, y, 20, 20])

	# (2) if inside of window
	if y < window.get_height():
		# increase movement amount 
		y_velocity = y_velocity + 2

	
	# (3) move y based on y_velocity every loop
	y = y + y_velocity

	# ... irrelevant code

```

(1) We make a `y_velocity` variable.

(2) If the `y` position is inside of the window, then "increase" the falling velocity.

(3) Increase the `y` *position* based on the `y_velocity` number.

Now you should have simple gravity working! And the cube should speed up as it falls, giving the illusion of gravity physics!!

![pygame falling gravity](/Assets/pygame_falling_gravity.gif)

You can make this more obvious by increasing the `y_velocity` at a faster rate.

(example)
```py
# ... irrelevant code

	# if inside of window
	if y < window.get_height():
		y_velocity = y_velocity + 10 # increasing by 10 (rather then 2) each loop

# ... irrelevant code
```

... which would look like this.

![pygame falling gravity faster](/Assets/pygame_falling_gravity_faster.gif)

# Accuracy and Offsetting
Offset `if y < window.get_height():` by cube height (20) since y position is at top left.

# Collision
The player will keep falling past the bottom of the window, because even though we stop growing the "y_velocity" number, we are still *moving* our position based on whatver `y_velocity` was left at...

```py
	y = y + y_velocity
```

...and we never reset `y_velocity` when we touch the bottom of the window!

```py
	if y < window.get_height() - 20:
		y_velocity = y_velocity + 10
```


So we need to add an `else y_velocity = 0` if we have hit the bottom of the window!...

(edit the code to the following)
```py
# ... irrelevant code

	# if above bottom of window
	if y < window.get_height() - 20:
		# increase movement amount 
		y_velocity = y_velocity + 2
	else:
		# (1) reset the y_velocity
		y_velocity = 0
	
	# (2) move y based on y_velocity every loop
	y = y + y_velocity
# ... irrelevant code
```

(1) If we ARE outside of the window, then we reset the y_velocity.

(2) (This code stays the same) Since the `y_velocity` has been reset to `0`, when we apply the `y_velocity` to the `y` position it won't keep moving the cube when we hit th ebottom of the window!

Now run this code using the play button!

# Physics Limitations and Accuracy
You might notice that the player gets stuck halfway at the bottom of the window.

![](/Assets/pygame_rect_stuck_bottom.png)

This is because when we do the check...

```py
	# if above bottom of window
	if y < window.get_height() - 20:
		# increase movement amount 
		y_velocity = y_velocity + 2
	else:
		# (1) reset the y_velocity
		y_velocity = 0
	
```

The players `y` position might just barely be above the bottom of the window. So we don't reset `y_velocity`, causing the next piece of code...

```py
	# (2) move y based on y_velocity every loop
	y = y + y_velocity
```

To still move the `y` positon! And so we are halfway under the window!

We can fix this player by just reseting the `y` position to `window.height` but since the position is based on the top left of the cube we have to offset upwards a little by the rectangles/cubes height, so `y = window.height - 20` (since the rect height is 20).

(change your code to the following)
```py
# ... irrelevant code

	# if y is above bottom of window
	if y < window.get_height() - 20:
		# increase movement amount 
		y_velocity = y_velocity + 2
	else:
		# reset the y_velocity
		y_velocity = 0

		# (1) reset y position
		y = window.get_height() - 20

# ... irrelevant code
```

(1) We reset the y position if we are at the bottom of the window.


# Bounce
This is super easy, we can just change one line of code!

Rather than reseting the `y_velocity` to `0` when we hit the bottom of the screen...

(code for resetting `y_velocity`)
```py
	else:
		# reset the y_velocity
		y_velocity = 0
		 
		# ... irrelelvant code
```

...we can reverse the `y_velocity`...

(change the code to the following)
```py
	else:
		# invert y_velocity
		y_velocity = -y_velocity
		 
		# ... irrelelvant code
```

...and set it to its itself but negative! 

If you hit play you will see a "perfect" bounce!

![pygame perfect bounce](/Assets/pygame_perfect_bounce.gif)

Although rather than prefeclty inverting the `y_velocity` we will only invert by 40%.

(change the code to the following)
```py
	else:
		# invert by 40%
		y_velocity = -(y_velocity * 0.4)
		 
		# ... irrelelvant code
```

If you have ever done any math with precentages before you'll know that multiplying by `0.4` gives us 40% of the number we multiplied.

If you run this code, we get a more realistic bounce, that gradually stops.

![pygame realistic bounce](/Assets/pygame_realistic_bounce.gif)

Here is the final code!

(final code)
```py
import pygame

pygame.init()
window = pygame.display.set_mode([400, 200])
pygame.display.set_caption('First game')

white = [255, 255, 255]
black = [20, 20, 40]
window.fill(black)

x = 10
y = 10
y_velocity = 0

# Endless loop
Stop = False
while Stop == False:

	# delay
	pygame.time.delay(100)

	window.fill(black)

	pygame.draw.rect(window, white, [x, y, 20, 20])

	# if y is above bottom of window
	if y < window.get_height() - 20:
		# increase movement amount 
		y_velocity = y_velocity + 2
	else:
		# reset the y_velocity
		y_velocity = - (y_velocity *0.4)
		# reset y position
		y = window.get_height() - 20
	
	# move y based on y_velocity every loop
	y = y + y_velocity

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	pygame.display.update()
```

And that is all for this lecture!... but if you want to add more features to the game (like clicking the arrow keys to move the player, or colliding with the side walls) then check out the tutorials of this section!