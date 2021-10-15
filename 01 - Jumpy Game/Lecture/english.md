TODO:
- explain velocity as length, and moving y pos by every increasing y_vel length (use downwards moving chart with arrow lines with length, and adding y_vel to y pos)

You just finished learning about the basics of coding. Now you get to actually *do* something with that coding!

We are going to use a "framework" or "library" of code that was made for making games using Python.

"framework" and "library"  are just fancy words for code written by someone else that does the boring code stuff (like getting access to a Windows "Window", or interpreting key presses from files) so we can focus on making our game.

Make a new Repl and select "PyGame". Name it "Pygame".

Now we recommend you change your codes layout to be "stacked", so that it looks like the following.



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

We make a new variale called "black". It is a list of 3 numbers. Each number corresponds with the colors Red Green and Blue (AKA "RGB"). By mixing different amounts of Red Green and Blue light you can get any color of the rainbow (but you probably already know that).

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
		y += 1

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	pygame.display.update()
```

(1) if `y` position is less than the height of the window, then move the `y` position downwards (increasing `y` moves us downwards).

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

If you make a mistake when editing your code, you can always "undo" the last thingyou did by clicking the `ctrl` + `Z` keys (if your on a Mac computer, the its `command` + `Z`). Go ahead and click `ctrl` + `Z`. Then to "redo" click the `ctrl` + `shift` + `Z` keys.

![todo] gif of someone clicking ctrl + Z on keyboard

STILL WRITING THIS LECTURE...

Here is the final code for the game.
```py
import pygame

pygame.init()
window = pygame.display.set_mode([400, 200])
pygame.display.set_caption('First game')

white = [255, 255, 255]
black = [20, 20, 40]
window.fill(black)

x = 100
y = 100

y_velocity = 0

# Endless loop
Stop = False
while Stop == False:
	# Delay
	pygame.time.delay(100)

	# Clear the screen to black
	window.fill(black)

	# Draw rectangle
	pygame.draw.rect(window, white, [x, y, 20, 20])

	# Get "mapping" of the keys
	keys = pygame.key.get_pressed()

	# if right arrow
	if keys[pygame.K_RIGHT]:
		x += 10

	if keys[pygame.K_LEFT]:
		x -= 10

	if keys[pygame.K_SPACE]:
		# Set y velocity to -5 (makes us jump)
		y_velocity = -5
	elif y + 20 > 200:
		y_velocity = 0
		y = 200 - 20
	else:	
		# Increase y velocity (falling)
		y_velocity += 1

	# Move y according to y_velocity
	y += y_velocity

	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True

	# Update the display
	pygame.display.update()
```
