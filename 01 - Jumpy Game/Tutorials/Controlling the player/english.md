This section not been written yet! Consider contributing to this course to help Paper out! https://github.com/PaperPrototype/Intro-Coding-and-Computers

For now here is the original code...

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

...and here is what it would need to change to...

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

	# Get "mapping" of the keys
	keys = pygame.key.get_pressed()

	# if right arrow
	if keys[pygame.K_RIGHT]:
		x += 10

	if keys[pygame.K_LEFT]:
		x -= 10

	if keys[pygame.K_SPACE]:
		# Set y velocity to -10 (makes us jump)
		y_velocity = -10
	# if y is above bottom of window
	elif y < window.get_height() - 20:
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

Although with that code the game runs at about 20 fps? I think? SO you can change the fps to be faster by changing the delay between loops...


```py
# ... irrelevant code

	# delay
	pygame.time.delay(16)

# .. irrelevant code
```

But that makes everything move to fast, so I changed some of the numbers a bit, which you can see in the following code.

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
	pygame.time.delay(16)

	window.fill(black)

	pygame.draw.rect(window, white, [x, y, 20, 20])

	# Get "mapping" of the keys
	keys = pygame.key.get_pressed()

	# if right arrow
	if keys[pygame.K_RIGHT]:
		x += 4

	if keys[pygame.K_LEFT]:
		x -= 4

	if keys[pygame.K_SPACE]:
		# Set y velocity to -10 (makes us jump)
		y_velocity = -8
	# if y is above bottom of window
	elif y < window.get_height() - 20:
		# increase movement amount 
		y_velocity = y_velocity + 0.5
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