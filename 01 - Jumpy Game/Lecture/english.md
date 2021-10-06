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

When we make a new window using `pygame.display.set_mode([400, 200])` it gives us back something that we can store in a variable.

(change your code to the following)

```py
# ... irrelevant code

# save into "window" variable
window = pygame.display.set_mode([400, 200])

pygame.display.set_caption("Jumpy Game")
```

Now we can "fill" the entire window with the color black!

(add the following to your code)
```py
# ... irrelevant code

black = [20, 20, 40]
window.fill(black)
```

We make a new variale called "black". It is a list of 3 numbers. Each number corresponds with the colors Red Green and Blue, AKA "RGB". 

Mixing different amounts of Red Green and Blue light you can get any color of the rainbow (but you probably already know that).

If you click play now, the game will start and then stop, after only a second. We need some code that will run over and over, an endless loop!

(add the following to your code)
```py
# ... irrelevant code

# Endless loop
Stop = False
while Stop == False:

	# Go through each mouse press and key press
	for myEvent in pygame.event.get():
		if myEvent.type == pygame.QUIT:
			Stop = True
```

We make an endless loop, that loops "while Stop is equal to False". We set the `Stop` varialbe to False, so the loop will run over and over.

We go through each "event" that has happened, and "get" it (store it) in the "myEvent" variable. Each loop we check if the event type (in the "myEvent" variable) is `QUIT`. If the quit button gets pressed then this will be true, causing us to set `Stop` to True, which makes the next `while` loop not run (and our game exits).

Run this code and you should see the following!

![replit jumpy game plain](/Assets/replit_jumpy_game_plain.png)

There is one noticable problem. The window area is white! (not black how it should be!).

At the end of each loop we need to "update" the picture on the canvas.

(add the following to your code)
```py
# ... irrelevant code
while Stop == False:

	# ... irrelevant code

	# Update picture in the window
	pygame.display.update()
```

You can see we did not show any old code (except for `while Stop == False:` so that you can figure out where to put the new code). We also put a comment `# Update picture in the window` above the new code.

Now run the code and the window should be colored black! Yay!

![replit jumpy game lack window](/Assets/replit_jumpy_game_black_window.png)

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
