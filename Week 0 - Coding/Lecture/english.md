# Intro
Computers have a language that they understand, positive `+` and negative `-` electric signals. We usually use the symbol `1` to represent positive and `0` to represent negative. Computer nerds like to say that these two symbols are enough to make a language. That language is called "binary". How does this language live in the computer? Millions and millions of switches, representing on, a positive electric charge, or off, a negative electric charge.

When we are "coding" it just means we are writing instructions for a computers processor. In coding we put a bunch of instructions into a file in the form of 0's and 1's or "binary". We call these files a "program". A simple program could tell the computer to display the word "hello" on the screen.

If we wanted to write a program we could use binary, the 0's and 1's language... That would be really hard. Thankfully though some smart people made a program (origianlly written using binary!) that took *word* based instructions from a file and turned them into binary based instructions for us!

The programs that turn our word based instructions into binary instructions are called "Compilers" because they "compile" our word based instructions into binary that the computer can understand.

These compilers could only understand instructions if they were written in a specific way. We call this "specific way" of writing instructions "syntax". The english language has syntax as well, if I just said "wnfkwebf enfwwen234ef +Bbqew *wqefb11" you wouldn't be able to understand it. So we have rules about how to layout words.

When computers are made they come with only a few builtin instructions that they understand. In english we have thousands of instructions, but computers have only a few to work with. Those instructions are written in binary, and the compiler has to figure out how to convert our words to those few binary instructions. Compilers can more easily compile a programming language (turn the words into functioning binary instructions) if the programming language has strict rules.

You can think of these "word" based programming languages as if you were looking from a very high mountain at a pasture of rocks. From your perspective those rocks are in the shape of some words! But if you looked at them up close you would see that they are rocks. Because of this word based programming languages are often called "high level" languages because they don't make us look really closely at the 0's and 1's, while the 0's and 1's are called a "low level" programming language.

# Scratch, your first language
Lets use a program*ing* language (that will be compiled into 0's and 1's by a compiler) to get the computer to say the word "Hello!" (Well ok, *this* programming language doens't get converted to 0's and 1's because it is running in the browser).

We will use a programming language called scratch, that automatically makes sure we write our programs with correct syntax, because getting used to a programming languages syntax can take a long time (remember syntax makes it so that the compiler can fiqure out how to convert our instructions into 0's and 1's). Scratch runs in your Browser so you don't have to download anything! Just go to (scratch.mit.edu)[https://scratch.mit.edu/] and and click on the "Create" or "Start Creating" button highlighted in the picture.

!(create first scratch project)[/Assets/create_first_scratch_project.png]

(You will need to make an account on the scratch website if you want to save this project we will make)

A tutorial should pop up, feel free to follow the tutorial and then keep reading this. Or just close it and keep reading.

!(close tutorial popup)[/Assets/close_tutorial_popup.png]

Now click on the cat to select it and lets add some code to it (remember "code" is another way of saying "instructions").

!(click on cat then add code)[/Assets/click_on_cat_add_code.png]

Scratch doesn't make us type words, instead it gives us puzzle pieces with words on them. Because they are puzzle pieces they only fit together if the syntax is correct. If we were using another programming language we would have to type those words manually and make sure they are following the rules of syntax. So yeah, scrath makes it much easier so you don't have to worry about "syntax". But scrathc still lets us see how syntax would work if we were typing it manually.

Go to the "looks" tab and drag the code block that says "say Hello!" onto the code area. You can change the word "Hello!" to whatever you want.

!(add say code block)[/Assets/scratch_add_code.png]

Now click the green flag to see the cat say "hello!"! Wait why didn't the cat say hello!?... The problem is that we didn't tell the computer "when" to say hello. Yes, computers only do EXACTLY what we tell them.

So we need to tell the computer when the cat should say hello? How about *in a robotic voice* "When. green. flag. clicked. say. hello.". Sounds good, and scratch gives us a code block called "When green flag clicked" in the "Events" tab. Drag the "When green flag clicked" block into the code area and attatch the "Say Hello!" block under it.

!(scratch first working code)[/Assets/scratch_first_working_code.png]

Now if we click the green flag the cat will say hello!

# Conclusion
What have we learned. Computers understand everything in binary (0's and 1's) but writing instructions for a computer in binary is hard. So some people made Compilers that take word based instructions and turn them into binary. We often call our word based instructions (that the compiler turns into binary) a programming language. Programming languages have to follow strict syntax rules so that the compiler can turn the words into the few binary instructions that our computer processors understand.

# Binary
So how can we make instructions out of just 0's and 1's in this arcane (meaning mysterious or secret) language? Lets start by understanding how we can count using only 0 and 1.

In the "decimal" or normal number system we have ten symbols to work with `0, 1, 2, 3, 4, 5, 6, 7, 8, 9`. This is why people will say the decimal number system has a "base" of ten.

In binary we only have two symbols `0, 1` and that is why it is called a base of 2. We can make 0 represent 0 and 1 represent 1.

Now why count from 0? If we don't include zero we will never be able to use 0 since there is no way to represent it. So we have to include 0 in the representation of numbers. Also its really easy to represent zero.

Lets count to 4 from 0 using decimal numbers.

0
1
2
3
4

Ok now lets try with binary.

0
1
... uh

Now we've run out of symbols! But what do we do when we run out of symbols in the decimal number system?

```
0
1
2
3
4
5
6
7
8
9
10 <- we move 1 over and put a zero!
```

Ok, so if we want to go beyond the number of symbols we have, we have to move the 1 over.

```
(binary) 0, 1, 10 and...
(normal) 0, 1, 2...
```

Interesting we carry the 1 over once the number system reaches its "base" number, so once we try to reach the number two in binary we have to move the 1 over.

In the decimal number system we only have to move the 1 over and put a zero if we reach ten!

So

```
(binary)            |  (normal)
                    |   
    0               |    0
    1               |    1
    10              |    2
    (3)  (2) + (1)  |   (3)
    11 = 10  +  1   |    3
    ...             |    ...
```

Now how about counting past three? How do we carry that over? Well we need another digit. Just like if we maxed out the tens system `99 + 1 = 100` we have to grow and add another digit.

```
binary  11 + 1  = 100
decimal 3  + 1  = 4
```

In the decimal system, every time we carry a 1 over we increase the number by a multiple of ten (10, 100, 1000, 10000). But in binary, we increase the number by a multiple of two, every time we move 1 over.

```
binary  (16) + (8) + (4) + (2) + (1)
         0      1     0     0     0    = 01000 = 8 (eight)

decimal (10000) + (1000) + (100) + (10) +(1)
         0         1        0       0     0    = 1000 (one thousand)
```

# hexadecimal
Lets add another number system to the mix. It has a base of sixteen.

the symbols it uses are `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`.

So we can count up to sixteen without needing to add another digit.

```
(read) tens    hexadecimal  binary
--->   0   =   0    =        0    
       1   =   1    =        1    
       2   =   2    =        10    (2)
       3   =   3    =        11    (2 + 1)
       4   =   4    =        100   (4)
       5   =   5    =        101   (4 + 1)
       6   =   6    =        110   (4 + 2)
       7   =   7    =        111   (4 + 2 + 1)
--->   8   =   8    =        1000  (8)
--->   9   =   9    =        1001  (8 + 1)
       10  =   A    =        1010  (8 + 2)
       11  =   B    =        1011  (8 + 2 + 1)
       12  =   C    =        1100  (8 + 4)
       13  =   D    =        1101  (8 + 4 + 1)
       14  =   E    =        1110  (8 + 4 + 2)
       15  =   F    =        1111  (8 + 4 + 2 + 1)
--->   16  =   G    =        10000 (16)
       17  =   10   =        10001 (16 + 1)
```

People like hexadecimal more than binary because it is easier to read. For exampole it took me 30 miutes to figure out the binary equivalents to every number.

Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (binary has a base of 2).

# Numbers represent letters
Now that we can use binary (0's and 1's) to represent numbers we can use those numbers to represent letters. For example the letter "H" could be represented by "16", or in hexadecimal "F". 

If we want to tell the computer to say "Hello!", or actually just the letter "H", we have to tell the computer *when* the number 16 should represent "H".

We won't get into that just yet, but in code it is just "H = (char)16".

