# Instructions
In real life we give people instructions on how to do something. In computers we do the same thing using "code".

One of the hardest problems (and often most time consuming problems) is searching.

Lets write a search "algorithm" using instructions, or in programmer lingo *code*. This algorithm can't accidentally miss enything though! So we have to tell it to look at each item one by one.

Code actually looks a lot like english, although a bit more... robotic. Here is some fake code. In it we are searching for a baseball.

```
Look at current item
If current item is baseball
    give baseball
Else if current item not baseball
    go to next item
    start over
```

This code assumes we have every item in one long line. It goes through each item until it finds a baseball.

But what if the item we are looking for isn't in our "one long line" of items! If this was real computer code, then the computer would probably crash! Or the computer would endlessly keep searching. I'm not entirely sure.

We call this a "bug". "Bugs" in computer programming are surprisingly common.

To fix this "bug" we have to change the code to expect the possibility of the item not being there.

```
Look at current item
If all items searched
    stop searching, exit
If current item is baseball
    give baseball
Else if current item not baseball
    go to next item
    start over
```

Now we can expect this possibility and avoid this dumb problem. At this point one thing is obvious, *computers are dumb*. They are not intuitive like humans. They do EXACTLY what we tell them, they'll just keep going until something breaks. This is often what happens when you get an "error" on your computer.

We call a method of solving a problem an "algorithm". This algorithm is pretty inefficient though. Say we had 1000 items to search through. In the worst case scenario it will take us 999 steps before we find what we are looking for!

Its so common to calculate an algorithms "efficiency" that we have a "notation" (way of expressing something) called "Big O Notation". For Big O Notation you write an O rather than say the whole darn sentence "in the worst case scenario". So for our search algorithm we can write "O999". But its kinda hard to tell where the O is so we usually put the number of steps inside of parenthesis, lik this "O(999)". Ahhhh, much better.

This algorithm of ours is actually pretty old. As such it has a name (like most old things) called "linear search". Linear meaning "straight line", cause we lined em up and searched em... one by one. 

It also has to do with math and the fact that for every 1000 items, the code has to "start over" 1000 times (in the worst case scenario), so a "linear" math relationship.

It turns out there's a way to search things WAY faster than using linear search. But first we have to sort each item alphabetically (yes that in itself is slow, so you could argue that it isn't really much faster). Once sorted we can start searching from the center item and move right or left depending on where the item was alphabetically (this is so much faster).

For the sake of simplicity we are now searching through a list of (sorted) contacts for a contact named "Johnny". We start at the center.

```
Open center contact
```

We landed at the center and found Samuels contact.

![binary search 0](/Assets/binary_search_0.png)

Now we know that Johnny is in the upper remaining half between S and A. If we go to the center of the remaining half we land at Dexter.

![binary search 2](/Assets/binary_search_2.png)

Now we know that Johnny is in the lower remaining half (between D and A). We go to the center of the remaining contacts and find Joe (ok, not the *exact* center).

![binary search 3](/Assets/binary_search_3.png)

This algorithm would finds our dearest Johnny really fast compared to the linear search algorithm! The code would look something like this.

```
Open center contact
If no contacts left
    stop searching, exit
If current contact is Johnny
    give back Johnny
Else if current contact after Johnny
    go to center of remaining lower half
    start over
Else if current contact before Johnny
    go to center of remaining upper half
    start over
```

This algorithm is called "binary search", which is honestly just as weird of a name as the last one. It turns out this what your phone uses when searching your contacts! Although there are algorithms that are faster, they require other fancy sorting algorithms.

Phew, that is a lot of code! And... yes, is hard at first, but don't give up! Eventually you'll get used to thinking this way. Later in this course we will make an algorithm that is even faster than binary search.

## Big O Notation
How much more efficient is binary search than linear search? For 1000 contacts it is O(log 1000). "log" stands for the fact that every time we "start over" we've removed half of the contacts. If we chart each algorithm at different numbers of contacts you would see this.

![graph both search algorithms](/Assets/graph_both_search_algorithms.png)

The more work binary search has the more efficient it is!

It gets annoying to say "for 1000 contacts `O(log 1000)`" so we often replace the exact number with the letter `N` giving us `O(log N)`. This way we don't have to say the exact number of contacts every time and we just use the letter `N`.

# Python
Lets learn a real coding language now and put aside this (insert funny word) of fake code. 

Click this link to go to the greatest coolest code editing tool https://replit.com/

We recommend you put this website in another tab, and split your screen so that you can read along while coding.

![course workflow window layout](/Assets/course_workflow_window_layout.gif)

Click the big blue button that says "Start coding". Now you will be asked to make an account (if you don't already have one).

Once you've finished with that you will be presented with a screen like this.

![replit landing page](/Assets/replit_landing_page.png)

Click the three lines to open a sidebar. In the sidebar there is a blue button that says "`+ New repl`", click it and you will see a popup like this.

![replit new repl](/Assets/replit_new_repl.png)

Select the Python programming language and click create repl. You will be welcomed by Replit's in browser code editor.

![replit ide](/Assets/replit_ide.png)

This is called an IDE. IDE stands for Integrated Developer Environment. We have highlited the different windows of the IDE. You can go ahead and close the files window.

![replit close files window](/Assets/replit_close_files_window.gif)

This should give you some extra coding room. You can always resize windows if you need to. 

You can also turn on dark mode.

![replit dark mode](/Assets/replit_dark_mode.gif)

You can also resize everything in your browser by using the `ctrl` and `+` keys to zoom in (use the `ctrl` and `-` keys to zoom out).

![replit resize](/Assets/replit_resize.gif)

Now lets print a *famous* sentence using Python. Paste the following code into the code window.

```py
print("Hello world! I am an idiot!")
```

Now click the play button at the top. You will see the words "Hello world! I am an idiot!" get printed to the console window (The last part "I am an Idiot" is not part of the famous phrase).

We wrote "print" and then parenthesis? The `print` word is a special *function* in Python (I know, another weird name). The parenthesis, like Big O Notation, are there to make reading the code easier. Then inside of the parenthesis we put the words we want to print.

Why the quotation `""` marks? We add those so that we can tell code apart from words. We can put ANYTHING between those quotation marks (except for another quotation mark) and it won't get treated as code!

Now print the most random thing you can think of inside of the quotation marks!

```py
print("I am an IDIOT!!!! 13413 bla, bla, print('Hello world') this is words not code!!!")
```

And click the run button. You'll notice I put a single quotation marks `'` inside of double quotation marks `"` and Python (the coding language) didn't get confused. 

Obviously if you don't use quoation marks you will get an error because Python can't figure out what is words and what is code.

We call words inside of quotation marks *strings* (don't ask me why).

# Variables
In coding you can use code-words to "hold onto" information. Delete all your code then write the following code.

```py
number = 12

print(number)
print(number + 5)
print(number * 12)
```

We make a code-word that holds onto the number 12. We can then use that code word in place of just writing 12 every time. Use the play button to run this code.

We call "code-words" that hold onto information *variables* (yes, there's a name for literally ***everything***).

We can also change the number variable by re-setting it.

```py
number = 12

print(number)

number = 14

print(number)
```

Run this code. It prints 12 then 14.

How can we increase the number without resetting it? 

```py
number = 12

print(number)

# set number to number plus 1
number = number + 4

print(number)
```

We set number to what is was *previously* plus 4. This will increaser the `number` variable by 4. Run this code. You will see 12 then 14 get printed.

# Input
How can we "give" something to our code? There is a function called `input`. Delete all your old code then write the following code.

```py
result = input("Type something:")
print(result)
```

The `input` function prints "Type something:" then waits for you to type something. 

Once you type something (and click enter), the words you typed get stored in the variable called `result`.

![replit console input](/Assets/replit_console_input.gif)

The `result` variable holds onto the *string* you typed, so when we print `result` we get the words you typed again.

Now we can combine the `result` variable with another string "Hello".

```py
# get input
result = input("Type something:")

# print input
print("Hello", result)
```

If you typed in "Bob", then "Hello Bob" will get printed. We give the `print` function 2 inputs and separate them using a comma `,`.

# Comments
You saw that we put a hash `#` in front of a comment. 

```py
# this is a comment
```

Our comment gets ignored by the code. It is a good idea to use comments to tell other programmers what our code is doing.

# Lists
We can make a variable that holds onto a list of information. Delete your old code. You can hold `ctrl` and click `delete` (or `backspace`) to delete entire lines of code at once. Now write the following code.

```py
contacts = ["Mary", "John", "Jackson", "David"]

print(contacts)
```

This will print out `['Mary', 'John', 'Jackson', 'David']`. We could also hold onto a list of numbers.

(example)
```py
numbers = [12, 2312, 123, 124, 21]
```

# Loops
We can go through each item in a list and print it out. Delete your code again and write the following code.

```py
for name in ["Mary", "John", "Jackson", "David"]:
	print(name)
```

Make sure to add the colon `:` at the end of `for name in list`. You can read this code as.

```
for every name variable in ["Mary", "John", "Jackson", "David"]:
    print(current name variable)
```

The code goes through each item in the list and stores it in the `name` variable. Every time we go through one of the names in the list the code after the colon `:` gets run. In this case we print the `name` variable every "loop".

You should notice the 2 or 4 spaces in front of the code `print(name)`. This lets Python know what code is inside of the loop, and what code is outside of the loop.

We could also reference (aka "hold onto") the list using a variable and then "loop over" the variable.

```py
names = ["Mary", "John", "Jackson", "David"]

for name in names:
	print(name)
```

We call this a "for loop" because of the `for` keyword.

If we just want to loop a certain number of times without having to use a list we can use the special `range` function in the loop. Delete your old code and write the following.

```py
for number in range(12):
    print(number)
```

This prints the numbers from 0 to 11 (in total you loop 12 times). For reasons we'll see later computers start counting at 0.

## While
Python also has a while loop. Delete all the code and write this.

```py
counter = 0

while True:
    counter = counter + 1
    print(counter)
```

Woh! 

`while` is a loop that runs *while* something is true. In this case its always true so it infinitely runs the code inside of it forever! `True` and `False` have to be uppercase in Python (again, I don't know why).

We have a variable called a counter that we increase every loop and then print its *value* (the number it holds). Play this code and see how fast your computer can count!!

# Conditions
Lets write one of those progrsams that asks you to agree some to "terms and conditions".

```py
answer = input("Do you agree to the terms and conditions:")

if answer == "yes":
	print("Ha! You agreed to eating a booger!")

elif answer == "no":
	print("Welp, no boogers for you. *wispers* that was a bad idea...")

else:
    print("error.")
```

Run this the code. It will ask you if you agree to the "terms and conditions". Your answer gets stored in the `answer` variable.

If your answer was `yes` then you (apparently) have agreed to eating boogers! Ew! You use a double equal sign `==` to check if two things are equal to eachother. We use a double equal sign `==` because the single equals sign `=` has already been used for setting a variables value (what the variable "holds onto").

Then we say "elif" (meaning "otherwise if") you typed `no` then you've just saved yourself.

Finally we say "else" (menaing "otherwise") print a *helpful* error message.

But what if you typed an uppercase Y? We could change the code to account for this.

```py
word = input("Do you agree to the terms and conditions:")

if word == "yes" or word == "Yes":
	print("Ha! You agreed to eating a booger!")

elif word == "no" or word == "No":
	print("Welp, no boogers for you. *wispers* that was a bad idea...")

else:
    print("error.")
```

Obviously we could also provide a million different possible answers. 

# Functions
Lets make our own function. Delete the code and type in the following code.

```py
# defining a function that we can use later
def print_hello_3_times():
    print("Hello")
    print("Hello")
    print("Hello")
```

We made a function (called `print_hello_3_times`) that just groups some code. Now we can print "Hello" 3 times by just using the function. Change the code to use the function.

```py
def print_hello_3_times():
    print("Hello")
    print("Hello")
    print("Hello")

# using the function
print_hello_3_times()
```

Click the play button to run this code. You will see "Hello" get printed 3 times. When writing code you don't want to write the same thing over and over, so we reuse code by making functions.

## Function inputs
Although this function is pretty dumb. So lets make one that is slightly more useful.

```py
# defining a function
def say_hello(number):
    for i in range(number):
        print("Hello")
```

The loop uses the `range` function which is a shortcut for looping a certain number of times. We make a "variable function" called `number` that determines how many times to loop.

We can now use this function very usefully.

```py
def say_hello(number):
    for i in range(number):
        print("Hello")

# using the function to print hello 3 times
say_hello(3)
```

This prints hello 3 times! Pretty cool right? We can just calle the function and tell it how many times to say that thing.

We also have a name for these "function variables". The variable called `number` is called a *parameter* (I honestly don't know who came up with that name).

When we used the function and put in "3" the 3 is called an *argument* (I'll put this stuff in the notes so you don't have to remember it all).

If we add another *parameter* to the function we can make the function print whatever we want, any number of times we want.

```py
def say(phrase, number):
    for i in range(number):
        print(phrase)

# using the function
say("Hello everyone!", 3)
```

This function will print "Hello everyone!" 3 times.

# Return
The `input` function gave us back a string that could hold onto using a variable. We say that the `input` function "returned" something (aka "gave us back" something). Function can give us back something using the `return` keyword.

Delete all the code and write in the following.

```py
def add(a, b):
    return a + b
```

This function adds 2 numbers (Lol, that is so lame XD).

We can use this function with a variable.

```py
def add(a, b):
    return a + b

result = add(2, 2)
```

The `result` variable now has the number 4. One VERY important thing to know about `return` is that any code after it won't get run!

(example)
```py
def divide(a, b):
    return a / b

    # this code inside the function will never get run!
    if a == 0 or b == 0:
        print("Can't divide by zero!!!")

result = divide(2, 0)
```

The `if` *statement* at the end of the function will never get run. TO fix this we have to put it before the `return` keyword.

(example)
```py
def divide(a, b):
    if a == 0 or b == 0:
        print("Can't diivide by zero!!!")

    return a / b

result = divide(2, 0)
```

Now this code will work! Now you know the basics of coding!



TODO save for later? too advanced?

# PyGame
Now lets learn the basics of making a game with Python! 

Afterwards in the Tutorials there will be tutorials on how to make different types of games using what you've learned.

Create a new repl. Select Pyxel (a Python framework for making games). Name the project "bounce".

Now we need to get access to the Pyxel code. Write this into your code.

```py
import Pyxel
```

This "imports" the code for making Pyxel games.

Now we need to make a window for our game. Make your code look like the following.

```py
import pyxel

pyxel.init(100, 80)
```

This gives us a window that is 100 pixels wide by 80 pixels tall. Now we need some code that will run every single frame (every few milliseconds) that we can put the code for moving our cube that we will make. We will make a function that we put all the code that will happen every frame.

We will also make a separate function for the rendering / drawing code. Change your code so that it looks like the following.

```py
import pyxel

pyxel.init(100, 80)

def update():
    # code to run every frame
    # the movement code
    pass

def draw():
    # code for drawing / rendering
    pass

pyxel.run(update, draw)
```

We are not allowed to make a function that does nothing! So we have to put the "pass" function temporarily.

Now lets draw a simple cube. Although its called a "rect", standing for the word "rectangle".

```py
import pyxel

pyxel.init(100, 80)

def update():
	pass

def draw():
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

Click the play button to see the following!

![replit pyxel](/Assets/replit_pyxel.png)

Techincally when we stop the game using Replits pause button our code is supposed to "quit" or exit the game so lets add that code.

```py
import pyxel

pyxel.init(100, 80)

def update():
	if pyxel.btnp(pyxel.KEY_Q):
		pyxel.quit()

def draw():
    pyxel.rect(10, 10, 20, 20, 11)

pyxel.run(update, draw)
```

The extra code we added can be turned into this 

```
if pyxel.button pressed(pyxel Key "Q") then 
    quit
```

Now lets make our cube fall as if it had gravity.

Now lets make the rect fall with gravity. We will make two variables called `x` and `y`, and then set the rects position using the variables.


NOT WORKING CODE
```py
import pyxel

pyxel.init(100, 80)

# x and y variables
x = 10
y = 10

def update():
	if pyxel.btnp(pyxel.KEY_Q):
		pyxel.quit()

def draw():
    pyxel.rect(x, y, 20, 20, 11) # use x and y variables

pyxel.run(update, draw)
```

Now lets move the y position down every "update".