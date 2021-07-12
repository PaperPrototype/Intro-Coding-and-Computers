(Oroginally part of the lecture, but moved to the "Archive" folder of old lectures)

In this tutorial we will make a simple game with a jumping cat!

# Scratch, a puzzle piece language
Lets use a program*ing* language (that will be compiled into another programming language that the web browser understands) to get the computer to say the word "Hello!".

We will use a programming language called Scratch, that automatically makes sure we write our programs with correct syntax, because getting used to a programming languages syntax can take a long time (remember syntax makes it so that the compiler or interpreter can figure out how to convert our words into binary (0s and 1s) instructions). 

Scratch runs in your Browser so you don't have to download anything! Just go to (scratch.mit.edu)[https://scratch.mit.edu/] and and click on the "Create" or "Start Creating" button (see picture below).

![create first scratch project](/Assets/create_first_scratch_project.png)

(If you want to save this project you will need to make an account on the scratch website)

You'll notice a tutorial pop up, feel free to follow the tutorial and then keep reading this. Or just close it and keep reading.

![close tutorial popup](/Assets/close_tutorial_popup.png)

Now click on the cat to select it and lets add some code to it (remember "code" is another way of saying "instructions").

![click on cat then add code](/Assets/click_on_cat_add_code.png)

Scratch doesn't make us type words, instead it gives us puzzle pieces with words on them. Because they are puzzle pieces they only fit together if the "syntax" is correct. If we were using another programming language we would have to type those words manually and make sure they are following the rules of syntax. 

So... yeah, scratch makes it much easier to code since you don't have to worry about "syntax". All the possible instructions come as puzzle piece "blocks".

Go to the "looks" tab and drag the code block called "say Hello!" onto the coding area. You can change the word "Hello!" to whatever you want by clicking on it, then typing in the word you want.

![add say code block](/Assets/scratch_add_code.png)

To "run" the code click the green flag. You should see the cat say "hello!"...

Wait why didn't the cat say hello!?... The problem is that we didn't tell the computer "when" run the "say" block. Should it always say hello? Should it say hello when we click the green flag?

We need to tell the computer *when* the cat should say hello. How about *in a robotic voice* "When. green. flag. clicked. say. hello.". 

Sounds good, and scratch gives us a code block called "When green flag clicked" in the "Events" tab. Drag the "When green flag clicked" block into the code area and attatch the "Say Hello!" block under it.

![scratch first working code](/Assets/scratch_first_working_code.png)

Now if we click the green flag the cat will say hello!

# Simulating gravity
