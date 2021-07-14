(Originally part of the lecture, but moved to the "Archive" folder of old lectures)

In this tutorial we will make a simple game with a jumping cat! In the end the game will be like this.

![scratch final game](./Assets/scratch_final_game.gif)

# Scratch, a puzzle piece language
Lets use a programing language called Scratch, that automatically makes sure we write our programs with correct syntax, because getting used to a programming languages syntax can be... interesting. 

(remember we need syntax so that a *compiler* (or interpreter) can figure out how to convert our words into instructions for the computer).

Scratch runs in your Browser so you don't have to download anything! Just go to [scratch.mit.edu](https://scratch.mit.edu/) and and click on the "Create" or "Start Creating" button.

(see picture below)

![create first scratch project](./Assets/create_first_scratch_project.png)

You'll notice a tutorial pop up, feel free to follow the tutorial and then keep reading this. Or just close it and keep reading.

![close tutorial popup](./Assets/close_tutorial_popup.png)

Now click on the cat to select it and lets add some code to the cat. 

(remember "code" is another way of saying "instructions")

![click on cat then add code](./Assets/click_on_cat_add_code.png)

Scratch doesn't make us type words, instead it gives us puzzle pieces with words on them. Because they are puzzle pieces they only fit together if the "syntax" or code is correct.

All the instructions come as puzzle piece "blocks". You can also make your own.

Go to the "looks" tab and drag the code block called "say Hello!" onto the coding area. You can change the word "Hello!" to whatever you want by clicking on it, then typing in the word you want.

![add say code block](./Assets/scratch_add_code.png)

To "run" the code click the green flag. You should see the cat say "hello!"...

Wait why didn't the cat say hello!?... The problem is that we didn't tell the computer *when* the `say` block should run. 

Should it always say hello? Should it say hello when we click the green flag?

The last question sounds logical, and, it turns out, scratch gives us a code block called "When green flag clicked"!

Go to the "Events" tab. Drag the "When green flag clicked" block into the code area and attatch the "Say Hello!" block under it.

![scratch first working code](./Assets/scratch_first_working_code.png)

You'll notice that the code blocks "fit" together. Now if we click the green flag the cat will say "Hello!"!

# Follow the mouse-pointer
We can make the cat follow the mouse. 

Go to the "Motion" tab and simply add the `go to` code block under the `say` block. Then change the `go to` block to go to the "mouse-pointer"... 

![scratch follow mouse](./Assets/scratch_follow_mouse.png)

If you try this it will work, but not quite how we want it to.

Since the code under the "When green flag clicked" only runs one time (when the green flag is clicked) the cat goes to the mouse the moment you clicked the green flag, but it doesn't continue moving the cat to *follow* the mouse pointer.

To fix this we need our code to "forever" run some code that says `go to (mouse-pointer)`, over and over again, making the cat follow the mouse pointer.

If you go to the "Control" tab you will find a code block that does just that, its called the `forever` block.

![scratch forever block](./Assets/scratch_forever_block.png)

To delete a code block, drag it onto the tab area, this will delete it.

![scratch delete code block](./Assets/scratch_delete_code_block.png)

Now add the `forever` block under the `say` block, then inside of the `forever` block put a `go to (mouse-pointer)` block.

![scratch final follow code](./Assets/scratch_final_follow_code.png)

# Gravity
If we want to simulate gravity we have to do more than follow the mouse pointer, we need to move the cat so that it looks like it is falling.

For this we will create a variable (a code-word that references a value (in this case the *value* is a number)). 

That variable will reference a number representing a y-velocity. We will then use that y-velocity number to move the player down. Every `forever` loop, we decrease the y-velocity.

Go to the "Variables" tab. and click "Make a Variable"

![scratch make variable](./Assets/scratch_make_variable.png)

name it "y-velocity". 

Now in the forever loop we can decrease the y-velocity number every `forever` loop.

![scratch decrease y velocity](./Assets/scratch_decrease_y_velocity.png)

Then go to the "Motion" tab and use the `change y by` block to change the y position of the cat by some number

![scratch change y by 10](./Assets/scratch_change_y_by_10.png)

To change the cats position using our `y-velocity` variable, go to the "Variables" tab and drag the `y-velocity` variable onto the `change y by` code block where the number is (`change y by` should adjust to fit the `y-velocity` variable in it).

![scratch change y](./Assets/scratch_change_y.png)

Now tha cat falls! Although it stays stuck at the bottom of the canvas!

We can manually go to its position and change it back to `x(0) y(0)`.

![scratch gif manaully set position](./Assets/scratch_manually_set_pos.gif)

Or we could just click and drag the cat "sprite" to the center of the cavnas. ("sprite" is just another name for a 2D picture)

![scratch gif drag sprite](./Assets/scratch_gif_drag_sprite.gif)

An even easier way is to reset the cats position when the green flag is clicked through a `set x to (0)` and `set y to (0)` block. These blocks set the cats position to whatever you want.

![scratch reset pos](./Assets/scratch_reset_pos.png)

In this case we reset the cats position to the center whenever we click the green flag.

# Collision
It would be cool if the cat stopped falling when it touched the edge. To do this we can use an `if` statement.

Go to the "Control" tab and get the `if < > then else` block and put it inside of the `forever` block.

![scratch if touching else](./Assets/scratch_if_touching_else.png)

Then from the "Sensing" tab we put the `is touching ()` *conditional* code block. 

(Make sure to change the drop down from `mouse-pointer` to `edge`!)

Now when the cat touches the edge, the code does nothing, but if the cat is NOT touching the edge the cat falls!

You might notice that the y-velocity variable is very big! And as a result we fall VERY fast, and it only gets worse because we never reset `y-velocity`!

![scratch y velocity](./Assets/scratch_y_velocity.png)

To fix this, whenever the cat touches the edge, we reset the `y-velocity` variable, *if*, the cat touches the edge.

![scratch reset y velocity](./Assets/scratch_reset_y_velocity.png)

Now we can drag the cat up, and it will slowly fall every time! Yay!

![scratch drag fall](./Assets/scratch_drag_fall.gif)

# Jumping
The code for jumping is shown below.

![scratch jumping code](./Assets/scratch_jumping_code.png)

We add another if statement, and in it we put a "Sensing" block called `key (space) pressed?`.

If the spcae key is pressed we set the `y-velocity` variable to 10 (upwards), and then change the cats y position using the newly changed `y-velocity`.

At first the cat goes up, but then it transitions to going down, this is because the `forever` loop decreases the `y-velocity` constantly. Pretty cool eh?

See if you can figure out how to get this code working! It shouldn't be hard!

# Moving side to side?... Functions
We just need an `x-velocity`. But this code is starting to get a little messy.

Lets put the jumping code, and the gravity code into their own custom blocks!

Go to the "My Blocks" tab (at the bottom) and click "Make a Block". Name it "simulate gravity" and put the code that simulates gravity under it.

![scratch simulate gravity](./Assets/scratch_simulate_gravity.png)

Now we can just put the `simulate gravity` block in place of it! 

("Custom Blocks" in Scratch are the same as functions in Python)

![scratch use gravity block](./Assets/scratch_use_gravity_block.png)

Ah much better!

Now do the same for the jumping code.

![scratch use jump block](./Assets/scratch_use_jump_block.png)

Hmm... lets edit the jump function (aka custom block) so that it takes in a number for how high we want the player to jump.

Left click the jump block in "My Blocks" and select edit.

![scratch edit custom block](./Assets/scratch_edit_custom_block.png)

Then add an input to the block. Call the input "height".

![scratch add block input](./Assets/scratch_add_block_input.gif)

Now in the blocks "define", drag the input into the `set [y velocity] to (10)` block.

![scratch set block input](./Assets/scratch_set_block_input.gif)

Now we can set the jump height to whatever we want!

# Finally... Moving side to side
Make a new custom block called "movement".

Then add the following code.

![scratch movement code](./Assets/scratch_movement_code.png)

Also make sure to *call upon* the movement block in the `forever` loop.

![scratch update movement](./Assets/scratch_update_movement.png)

In video games, we usually refer to the `forever` loop as an "Update loop".

Now, show me your skills and make something epic. Good luck soldier.



