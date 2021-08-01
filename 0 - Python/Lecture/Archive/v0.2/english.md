# Data?
The language that computers understand are positive `+` and negative `-` electric charges, because they literally only have electric currents to work with (from a battery or being pluged in to an electric outlet). How does a computer *store* all those electric charges? Millions and millions of switches, containing a positive electric charge, or a negative electric charge. 

Each electric charge is called a "bit". A bit can be either positive, or negative. We use the symbol `1` to represent positive charges and `0` to represent negative charges. This is always the case.

The formal name for the *language* of 0s and 1s is "binary".

In case your wondering how a computers "processor" can take tons of `+` and `-` signals and "process" them, we **won't** be covering that because THAT is not the focus of this course. Instead, we will focus on how we can represent numbers, letters, and everything you see on a computer, using only 0s and 1s (aka electric signals) to be able to code, and understand how that code is able to create images and text files (such as your reading right now; when you click on a letter there is litterally a computer code of 0's and 1's in the background for each letter or symbol).

When we are "coding" it just means we are writing *thousands* of instructions for a computers processor using binary. We put those instructions in a file. Those files of instructions are called a "program" or "app". 

But we don't want to code using 0s and 1s!

Thankfully some smart people made a *program* (using binary!) that took text (aka symbols, letters, numbers...anything) based instructions from a file and turned them into binary instructions for us!

...But, how can you represent text using only binary? Lets answer that question first, then we'll get to coding.


# Lesson 0: BINARY
Lets start by learning how to represent numbers. 

In our standard number system, called the "decimal" system, we have 10 symbols we use to represent numbers. These symbols are `0, 1, 2, 3, 4, 5, 6, 7, 8, 9`.
 
In binary, we only have two symbols, `0` and `1`, to represent every number.

In binary, we have `0` represent the value 0, and `1` represent the value 1.

With one column of binary numbers we can count up to 1.

```
(1s place)
0
1
2 ?
```

But that doesn't get us very far!

The decimal (standard) number system can count up to 9 using only one column.

```
(1s place)
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
```

So how do we count past 9 in decimal?

```
10s | 1s
0     0
0     1
0     2
0     3
0     4
0     5
0     6
0     7
0     8
0     9
1     0 <- represents 10
```

We add another column! THe next column starts at ten since the last one left off at nine.

If we copy the decimal system, we can go beyond the number of symbols we have by moving the `1` over and continuing to count.

```
2s | 1s
0    0
0    1
1    0 <- represents 2
```

We add another column, and that column starts counting at two, because the last column could only count up to one. We call the second column the the "2s place".

```
2s | 1s
0    0
0    1
1    0 <- represents 2
1    1 <- represents 3
```

Here are the "base" (aka places) numbers for binary `1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048...`.

```
8s | 4s | 2s | 1s
0    0    0    0   =  0
0    0    0    1   =  1
0    0    1    0   =  2
0    0    1    1   =  3
0    1    0    0   =  4
```

Here are the base (place) numbers for the tens system `1, 10, 100, 1000`. 

```
1000s | 100s | 10s | 1s
0       0      0     0
0       0      0     1
0       0      0     2
0       0      0     3
0       0      0     4
0       0      0     5
0       0      0     6
0       0      0     7
0       0      0     8
0       0      0     9
0       0      1     0 <- represents 10
```

Note:
- There exist other number systems, and we could actually make our own! A popular one is hexadecimal (it has a base of 16), and octodecimal (it has a base of 8).

# lesson 1: HEXADECIMAL
Lets add another number system to the mix. We need to know this number system since we will probably be using it.

It has sixteen symbols we can use, The symbols are `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. We use the standard symbols for 0 to 9 and then the alphabetical symbols A to F (for 10 to 15).

So we can count up to 15 without needing to add another column.

```
32s | 16s | 1s
0      0     0
0      0     1
0      0     2
0      0     3
0      0     4
0      0     5
0      0     6
0      0     7
0      0     8
0      0     9
0      0     a  <- represents 10
0      0     b  <- 11
0      0     c
0      0     d
0      0     e
0      0     f  <- 15
0      1     0  <- 16
```

Every number system has a 1s place, otherwise we wouldn't be able to represent 1.

Here is a chart showing each number system's values and symbol's side-by-side.

```
     decimal  hexadecimal  binary
     0  =     0   =            0                  (0)
     1  =     1   =            1                  (1)
     2  =     2   =           10              (2 + 0)
     3  =     3   =           11              (2 + 1)
     4  =     4   =          100          (4 + 0 + 0)
     5  =     5   =          101          (4 + 0 + 1)
     6  =     6   =          110          (4 + 2 + 0)
     7  =     7   =         111          (4 + 2 + 1)
     8  =     8   =         1000      (8 + 0 + 0 + 0)
     9  =     9   =         1001      (8 + 0 + 0 + 1)
    10  =     A   =         1010      (8 + 0 + 2 + 0)
    11  =     B   =         1011      (8 + 0 + 2 + 1)
    12  =     C   =         1100      (8 + 4 + 0 + 0)
    13  =     D   =         1101      (8 + 4 + 0 + 1)
    14  =     E   =         1110      (8 + 4 + 2 + 0)
    15  =     F   =         1111      (8 + 4 + 2 + 1)
    16  =    10   =        10000 (16 + 0 + 0 + 0 + 0)
    17  =    11   =        10001 (16 + 0 + 0 + 0 + 1)
```

Techinally you could add empty 0s in front of the numbers, but that would be confusing.

```
     decimal  hexadecimal  binary
    00  =    00   =        00000                  (0)
    01  =    01   =        00001                  (1)
    02  =    02   =        00010              (2 + 0)
    03  =    03   =        00011              (2 + 1)
    04  =    04   =        00100          (4 + 0 + 0)
    05  =    05   =        00101          (4 + 0 + 1)
    06  =    06   =        00110          (4 + 2 + 0)
    07  =    07   =        00111          (4 + 2 + 1)
    08  =    08   =        01000      (8 + 0 + 0 + 0)
    09  =    09   =        01001      (8 + 0 + 0 + 1)
    10  =    0A   =        01010      (8 + 0 + 2 + 0)
    11  =    0B   =        01011      (8 + 0 + 2 + 1)
    12  =    0C   =        01100      (8 + 4 + 0 + 0)
    13  =    0D   =        01101      (8 + 4 + 0 + 1)
    14  =    0E   =        01110      (8 + 4 + 2 + 0)
    15  =    0F   =        01111      (8 + 4 + 2 + 1)
    16  =    10   =        10000 (16 + 0 + 0 + 0 + 0)
    17  =    11   =        10001 (16 + 0 + 0 + 0 + 1)
```

People find hexadecimal more easy than binary because it can represent larger numbers with less digit (don't have to carry the 1 over so many times resulting in less digits).

Often you will see hexadecimal in place of binary. Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (which is binary's "base" number).

If you are really geeking out right now try to make a number system with a base of 8, or 5, or 3!

There is a number system called trinary that has a base of 3. Quantum computers use it because the switches in a quantum computer can be on, off, or half way, giving 3 possible symbols.

# lesson 2: Numbers can represent letters
Now that we can use binary (`0`'s and `1`'s) to represent numbers, we can use those numbers to stand for letters! 

For example the symbol "H" could be represented by the number "15" (or in binary "1111", or in hexadecimal "F").

If we want to tell the computer to say "Hello!", or actually just the letter "H", all we have to do is tell the computer ***when*** the number 15 should represent the symbol "H".

All thats left is to make a long list of what numbers map to what symbols. As you might have guessed there is already a "standard" that exists that every computer uses. Its called ASCII which stands for American Standard Code for Information Interchange. Below is the ASCII "encoding" of latin based characters letters and symbols.

**Don't** read this whole list! It is just for reference purposes. Most programmers have so much information they have to remember they just look it up. That is what this list is for, looking up what number, represents what symbol / letter.

(To see the whole list see the notes of this lecture)

```
ASCII ENCODING
	...
	32	 	(space)			
	33	!	(exclamation mark)			
	34	"	(Quotation mark)			
	35	#	(Number sign)			
	36	$	(Dollar sign)			
	37	%	(Percent sign)			
	38	&	(Ampersand)			
	39	'	(Apostrophe)			
	40	(	(round brackets or parentheses)			
	41	)	(round brackets or parentheses)			
	42	*	(Asterisk)			
	43	+	(Plus sign)			
	44	,	(Comma)			
	45	-	(Hyphen)			
	46	.	(Full stop , dot)			
	47	/	(Slash)			
	48	0	(number zero)			
	49	1	(number one)			
	50	2	(number two)			
	51	3	(number three)			
	52	4	(number four)			
	53	5	(number five)			
	54	6	(number six)			
	55	7	(number seven)			
	56	8	(number eight)			
	57	9	(number nine)			
	58	:	(Colon)			
	59	;	(Semicolon)			
	60	<	(Less-than sign )			
	61	=	(Equals sign)			
	62	>	(Greater-than sign ; Inequality) 			
	63	?	(Question mark)			
	64	@	(At sign)			
	65	A	(Capital A )			
	66	B	(Capital B )			
	67	C	(Capital C )			
	68	D	(Capital D )			
	69	E	(Capital E )			
	70	F	(Capital F )			
	71	G	(Capital G )			
	72	H	(Capital H )			
	73	I	(Capital I )			
	74	J	(Capital J )			
	75	K	(Capital K )			
	76	L	(Capital L )			
	77	M	(Capital M )			
	78	N	(Capital N )			
	79	O	(Capital O )			
	80	P	(Capital P )			
	81	Q	(Capital Q )			
	82	R	(Capital R )			
	83	S	(Capital S )			
	84	T	(Capital T )			
	85	U	(Capital U )			
	86	V	(Capital V )			
	87	W	(Capital W )			
	88	X	(Capital X )			
	89	Y	(Capital Y )			
	90	Z	(Capital Z )			
	91	[	(square brackets or box brackets)			
	92	\	(Backslash)			
	93	]	(square brackets or box brackets)			
	94	^	(Caret or circumflex accent)			
	95	_	(underscore , understrike , underbar or low line)			
	96	`	(Grave accent)			
	97	a	(Lowercase  a )			
	98	b	(Lowercase  b )			
	99	c	(Lowercase  c )			
	100	d	(Lowercase  d )			
	101	e	(Lowercase  e )			
	102	f	(Lowercase  f )			
	103	g	(Lowercase  g )			
	104	h	(Lowercase  h )			
	105	i	(Lowercase  i )			
	106	j	(Lowercase  j )			
	107	k	(Lowercase  k )			
	108	l	(Lowercase  l )			
	109	m	(Lowercase  m )			
	110	n	(Lowercase  n )			
	111	o	(Lowercase  o )			
	112	p	(Lowercase  p )			
	113	q	(Lowercase  q )			
	114	r	(Lowercase  r )			
	115	s	(Lowercase  s )			
	116	t	(Lowercase  t )			
	117	u	(Lowercase  u )			
	118	v	(Lowercase  v )			
	119	w	(Lowercase  w )			
	120	x	(Lowercase  x )			
	121	y	(Lowercase  y )			
	122	z	(Lowercase  z )			
	123	{	(curly brackets or braces)			
	124	|	(vertical-bar, vbar, vertical line or vertical slash)			
	125	}	(curly brackets or braces)			
	126	~	(Tilde ; swung dash)			
	127	DEL	(Delete)			
	...
```
(taken from https://theasciicode.com.ar/ascii-codes.txt.  See notes for full table)

The ASCII table is pretty long. But even still it doesn't cover all the possibility's! This is because we only use 8 bits (eight columns of 0's and 1's). 

Using only 8 columns of bits for a binary number only lets us count from 0 to 255, giving us 256 possible symbols! 

Why 8 bits? and not 7 or 3 bits? Modern computers store everything in sets of 8 bits.

This helps speed up your computer as it only has to remember the location of something every 8 bits rather than every bit (literally giving you an 8x speedup).

There is a short name for the size "8 bits" called a "byte". Whenever someone says "byte" they are just refering to a block of memory that is 8 bits long. THe word *byte* is very common as literally every computer these days stores memory in bytes (a set of 8 bits).

What about emoji's? The ASCII encoding doesn't include emoji's (I don't think)! This is probably because (according to Wikipedia) the ASCII encoding was invented in 1963!

A new modern mapping system called Unicode is based off of ASCII. The mapping of 0 to 255 is the same as ASCII's.

Unicode offers several formats each one storing twice as many symbols and letters as the previous one. Each Unicode variant is called a Unicode Transform Format, or more commonly UTF. 

The first format is called UTF-8. The "8" stands for the number of bits it uses. UTF-8 stores the same things as ASCII and takes up 1 byte of space for each symbol (remember 1 byte is 8 bits).

How is Unicode different from ASCII? Well, with Unicode, if you add another byte you get UTF-16 which adds support for many more letters and symbols. And then UTF-32 adds even more support for symbols.

The original goal of Unicode was to cover every possible letter and symbol, this includes emoji's. UTF-8 lets us use a small amount of space if we only need the most common (latin / english) letters and symbols. And then for the less common symbols UTF-16. Then UTF-32 for even rarer symbols. There is even a UTF-64, but nobody uses it since we haven't even finished mapping UTF-32.

The crying face emoji is represented by the number 128,512, which is technically a pattern of bits 00000001 11110110 00000010 <- this may not be the correct sequence.

# Color
Emoji's are represresented by a number, but we render them as colored pictures. That may make you wonder, how are colors represented in a computer? Well we just have to find a way to map 0's and 1's to colors, or actually we can use numbers and map them to colors.

RGB is the most popular format, standing for Red Green Blue. The reason for this is that by only using Red Green and Blue lights we can make every color of the rainbow! This is what the pixels on *your* screen are doing right now. They are mixing different amounts of Red Green and Blue light to make colors!

We can use 1 byte for each color giving us numbers ranging from 0 to 255. As with Unicode, RGB also has RGB-16 and RGB-32.

By mixing the right amount of Red Green and Blue we can represent the color yellow with 249, 255, and 0.

![yellow color](/Assets/yellow_color.png)

Pictures are typically made up of thousands of pixels, this results in a lot of memory being used. For a picture of 512 x 512 pixels we end up with 512 x 512 x 3 bytes. For such large memory sizes we have other names such as kilobyte, megabyte, and gigabyte. 

A kilobyte is 1024 bytes, a megabyte is 1024 kilobytes, and a gigabyte is 1024 megabytes. A typical computer usally has a couple hundred gigabytes aroung 128 to 512 gigabytes. Some computers even have 1024 gigabytes, which is 1 terrabyte.

# Audio?
For audio... Well we also use numbers. We can have a number representing the frequency (aka deep rumble vs squeaky squeak), and then another number representing the loudness, and then another representing bass. Then we can just store a bunch of sets of these numbers one after the other in memory to make a sound or store music. You get the idea.


# Algorithms
Now lets start getting ourselves familiar with the idea of "coding", or really, writing instructions for the computer in what we call "algorithms".

Lets take an example using example code. In your phone you probably have a bunch of contacts of people you call or text. How does your phone find that contact using only instructions?

Say we have 1000 contacts and we want to find someone with the name of Johnny. How can we make some instructions about how to find the contact "Johnny"? We'll make some "code" (not real code). We call the idea of fake code "pseudo-code" (You will hear the term a lot).

```
1|  open first contact
2|  if johnny is on contact
3|    return (give back) johnny's info
4|    exit finished
5|  else if johnny not on contact
6|    move to next contact
7|    go back to line 2
```

If the above is resembling instructions for a computer, what (theoretically), is the computer doing when it follows the instructions?

Well, first we tell the computer to "open the first contact", then "if johnny is on contact" we should "return (give back) johnny's info".

But, most likely that won't happen. So, then we say "else if johnny not on contact" the computer should "move to next contact" and "go back to line 2" of the code.

Returning to line 2, makes us ask again "if johnny is on contact", but now we are on the second contact (thanks to the previous code). If Johnny is on the contact "return (give back) johnny's info". 

This code will jsut keep running in circles "looping" as we call it, until it finds Johnny. 

This "algorithm" (a way of solving something through a specific set of steps) is what we call a "linear" search algorithm because we go over every single contact "linearly" one by one.

There is one a problem though, what if we don't find Johnny? Well, the code would try to just keep searching! Because we never told it to stop! (Or it will crash your computer, or you will get an endless loading screen...) We call these coding mistakes a "bug". You'll hear the word "bug" used to refer to these kinds of coding errors (Check the notes of this Week to learn about the origins of the term "bug", its actually pretty interesting).

So, we need a way for the computer to know when it should stop searching. To do this, we can add 2 more lines of code at the bottom.

```
1|  open first page
2|  if johnny is on page
3|    return (give back) johnny's info
4|    exit finished
5|  else if johnny not on page
6|    move to next page
7|    go back to line 2
8|  else if Johnny not in contacts
9|    exit
```

This last piece of code, although it may be small, is very important because without it, we would probabaly get an endless loading bar as the computer kept "searching" for Johnny, even if it didn't find him! Because we never told it to stop after it went through all the contacts!

This "algorithm" for searching seems pretty dumb though. If we had say 1000 contacts, in a worst case scenario, it would take 1000 page turns, or "loops", to find johnny. What if there was a shortcut to make the code run faster? Rather than taking 1000 loops for every 1000 contacts? What if, in a worst case scenario, we could take only 10 loops for 1000 contacts, to find Johnny?

It turns out we can exploit (take advantage of) the fact that your contacts are sorted alphabetically (most phones also have some code that sorts your contacts). 

Rather than starting at the beginning of the contacts list, we can start right smack in the center. This makes us the closest to every possible contact (literally in the average position of them all).

Lets say the contact we find in the center is Samuel's contact. Well, since all the contacts are in alphabetical order, we know that Johnny will be somewhere before Samuels contact (Since J comes before S in the alphabet).

![binary search 0](/Assets/binary_search_0.png)

But here's the coolest part, now we can literally just ignore all the contacts below Samuel, and eliminate half of the contacts that need searched!

![binary search 1](/Assets/binary_search_1.png)

Remember the linear search code was "looping" once for every contact in the worst case scenario. But now, for every loop we eliminate half of the remaining work!

Lets keep going with this. We start in the center of the remaining contacts. Say we land at Dexter's contact.

![binary search 2](/Assets/binary_search_2.png)

Now we know that the top half of the contacts (that remain) are not going to have Johnny (notice that we also include Dexter's contact in the removal).

![binary search 3](/Assets/binary_search_3.png)

And we've split our work in half again! We could keep doing this until we founnd Johnny. This algorithm is called "binary search" (rather than linear search). The name comes from the fact we always split our work in two (aka half), hence "bi" which stands for two.

There exists a method for graphing the efficiency (aka number of loops, or steps, it would take to solve) of the above algorithms.

The first algorithm, the one we called "linear search", in its worst case scenario, takes 1000 iterations (steps or loops) to find Johhny (If say Johnny was the last contact). 

It takes pretty long to say "for the worst case scenario" so computer scientists (like you) just write a big O. when we write "O" it literally just means "in the worst case scenario". We call this "Big O Notation".

Then after the "O" we put a number representing the number of steps it takes *for the worst case scenario*. In our case its `O(1000)`. Big O notation puts the number of steps *inside of parenthesis*.

If we said `N` stood for the number of contacts we have, then we could change the big O notation to `O(N)`. This way we don't have to write `O(1000)` and then change it to `O(500)` if we changed the number of contacts.

If we have to search 1000 contacts we get 1000 steps of searching. We can graph this.

![graph linear search](/Assets/graph_linear_search.png)

The word "iterations" just means "the number of steps" it takes to find Johnny in the worst case scenario.

What about graphing "binary search"? Binary search in the worst case scenario is written as `O(log N)`. `log` just means we divide the number in half every step.

For an example, if we change the number of contacts to search to 2000, after only one step, we remove half of the contacts (in binary search)! And we end up with 1000 steps. This repeats for every step.

So, even if you double the number of contacts to search (in binary search) we have only to do one extra step!

This makes searching using the Binary Search algorithm VERY fast, even for a lot of work. That is why if you graph Binary Search it looks like this!

![graph binary search](/Assets/graph_binary_search.png)

As you increase the amount of work (or the amount of contacts), you only add 1 more iteration (aka step) of searching.

So how could we turn binary search into pseudo-code? (pseudo-cde just means fake english readable example code, that only illustrates a concept and how the code "might" look). Read through the following code line by line.

```
 1|  go to center
 2|  look at contact
 3|  if person is correct
 4|    return (give back) info
 5|  else if person earlier in contacts
 6|    open to middle of top half
 7|    go back to line 1
 8|  else if person is later in contacts
 9|    open to middle of bottom half
10|    go back to line 1
```

We call these different ways of solving problems "algorithms". An algorithm takes an input, the contacts list and gives us an output, Johhny's contact (or and error message saying the contact was not found).

When we are coing we are making these "aglorithms".

For reference here is the two algorithms and their efficiency" graphed next to each other.

![graph both search](/Assets/graph_both_search.png)

# Your first code
Lets jump into actually learning coding so that we can make these algorithms, and some games (In the tutorials of this week).

We will used a programmig language called Python. Python is a program (a file of instructions written in binary (0s and 1s)). 

It reads text files, and as it reads them it figures out how to translate our text code into binary instructions the computer can understand. 

We call this type of *programming language* an "interpreted" language because it gets "interpreted" by a program, whereas other coding languages actually get converted to binary instructions by a program called a "compiler"! (but that is for next week).

Although we know that text files are also actually just binary *encoded* in the ASII or Unicode format, so really this "interpreter" program, is reading in binary as Unicode, and then figuring out what we mean, and running the instructions as it figures them out.

Lets make some simple interpreted code that prints (aka displays) the phrase "Hello World" on the screen.

We will use an online "code editing" tool. Go to https://replit.com/ <-- click that, and you should see a website like this

![start coding](/Assets/start_coding.png)

Click the "Start Coding" button in the website.

You will need to amke an account (We're sorry about this! If you have any issues contact us in our Discord, or through the repository Issues).

Once you've made an account click the "New repl" button to create a new repl program.

![new repl](/Assets/new_repl.png)

If you don't see the "New Repl" button, click the three lines in top left corner.

Once you click the "New repl" button, you should see this.

![create repl](/Assets/create_repl.png)

Select "Python" as the programming language, and call the project "HelloWorld". 

Then click the "Create repl" button.

We recommend that you "split" your screen in half, having this tutorial on one side, and replits IDE in another.

![course workflow window layout](/Assets/course_workflow_window_layout.gif)

Now we can write some code in replit's IDE!

![replit ide](/Assets/replit_ide.png)

IDE stands for "Integerated Development Environment". It just means we get an editing tool for editing the code, much like Google Docs, or Microsoft Word.

IDE's usually also have a "files" viewer, currently there is only a single file called `hello.py`.

That file is a text file. We end the files name as `.py` so that the computer can know that the file has "code" that is for the Python programming language.

You will see there is some code written in the picture, go ahead an paste this snippet of code, it is the same as the pictures.

```
print("Hello world")
```

This code prints some words onto the screen. In replit's IDE you will see the code gets highlighted and colored. This is not part of the code, but simply a way of making the code easier to read.

From now on we will be highliting the code.

```py
print("Hello world")
```

Click the button at the top (with a green arrow in it) to *run* the code. 

![replit ide run arrow](/Assets/replit_ide_green_arrow.png)

You will see the phrase "Hello world" printed in the "console" (the black box on the right).

The word `print` is the name of a group of code that figures out how to print words onto the screen for us. 

We call these groups of code "functions", because a *function* implements "functionality".

Functions take an input and then do something with it. 

The `print` functions gets input through the parenthesis `()`. In the parenthesis we put two words "Hello world".

Why do we have the quotation marks `"`?

Say we took them away. How is the computer going to know the difference between code we are writing and some words we want to print? 

Remove the old code and type in the following code.

```py
print(Hello, I am 12 + 13)
```

The computer can't figure out how to get this to work! (and yoiu will get an error).

Lets assume you want to litterally print "Hello I am 12 + 13" (without adding the numbers together). For that we can change the code to this.

```py
print("Hello, I am 12 + 13")
```

Now the computer can tell what we mean. We refer to these words as a "string", meaning a *string* of Unicode characters.

In coding, we call this "specific way" of writing or "format"ing how to write words (so that the computer can know when we are trying to write a sentence, vs trying to write some code) "syntax". Syntax is a specific way of coding so that the computer can understand it.

If you ran the `print("Hello, I am 12 + 13")` code (by clicking the green arrow) you will have seen the black "console" (the black box on the right) with the phrase "Hello, I am 12 + 13" somewhere on it.

That console is how the print function is able to display the phrase "Hello world".

# Variables
How can we make code that prints our name?

Well, there is a function that *gets* input from the console.

Delete our old code and type in the following.

```py
input("Type something: ")
```

The `input` function will print the string "Type something: ".

Run the code by clicking the button at the top center of the website (with the green arrow).

You will see "Type something: " get printed. Now type in some words so that the concosle looks like this.


```
Type something: Bob is my name
```

and click enter. 

When you click enter, nothing happens...

We need to be able to get access to the *string* (aka words) you typed! (aka "Bob is my name")

The `input` function has access to the string we typed. We can use a code-word that holds onto the "words" from the `input` function.

```py
myName = input("Type something: ")
```

What is `myName`? It "holds onto" the words that the `input` function got from the console.

We call these holders "variables".

For a clearer example make a *variable* that holds a number. Delete the old code and type this in.

```py
variable = 12
```

And then print the variable below it.

```py
variable = 12

print(variable)
```

If you click play (by clicking the green flag) you will see `12` get printed. Pretty cool right?

We can also add together a variable and some words.

```py
variable = 12

print("Hello, ", variable)
```

and you will get "hello 12".

(Notice that we put a space at the end of "hello ". If we didn't put a space the word *hello* and the number *12* will be mashed together like this "hello12").

Now lets get the code to ask us for our name and print it.

Delete all the other code and type in this.

```py
myName = input("Type something: ")

print(myName)
```

Tada!

We can even get it to greet us! Change the code to this.

```py
myName = input("Type something: ")

print("Hello, ", myName)
```

# Functions
What about functions? How can we make one ourselves? Type in the following.

```py
def say_hello_to_name():
    myName = input("Type something: ")

    print("Hello, ", myName)
```

(When we make a function we use the the special `def` "keyword". This lets Python know that we are about to type in a function)

This make a "definition" of a group of code called a *function*. To *use* the function we have to type in the following underneath it.

```py
say_hello_to_name()
```

This is called "calling" a function.

Now that we have this funciton we can *call* (aka use) it as many times as we want!

```py
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
```

If you run this all the code inside of `say_hello_to_name` will get run 5 times, over and over.

Look at the function definition.

```py
def say_hello_to_name():
    myName = input("Type something: ")

    print("Hello, ", myName)

say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
```

You will notice that the colon symbol `:` comes after the two parenthesis `():`. This tells Python (the coding language we are using) that any code after the colon `:` is *inside* of the function. 

All the code inside of the function also has to have a 2 or 4 spaces in front of it, aside from using the `:` colon symbol. (click the `tab` key to add 2 or 4 spaces automatically).

This is so that Python will be able to tell what code is inside a function, and what code is not. We refer to adding a tab in front of the code as "indenting" the code.

If we go ahead and write our code without adding any *indenting* in front...

```py
def say_hello_to_name():
myName = input("Type in your name: ")

print("Hello, ", myName)

say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
say_hello_to_name()
```

...You can see it is hard to tell what code is *inside* of the function, and what code is *outside* of it. We call this idea of writing our code in a certain way "syntax". We have to have *syntax* so that we type things in a way that Python can understand what we are trying to tell it to do.

Notice when we are *calling* the function we don't indent it because we don't want to call a function inside of a function! That would give us an endless loop of functions running over and over (and might crash the computer, but hey, what's the worst that could happen? Just go ahead and see what happens you curious person).

But wait, the `print` function lets us type in what we wanted to print! It lets us give it some input!

How do we give a function a *parameter* (aka input)? Remember variables? We just make a variable for the function. Delete all the old code and type in the following.

```py
def hello_to(name):
  print("Hello, " + name)
```

And then we can "call" the function and give it an *argument* (aka input).

```py
def hello_to(name):
  print("Hello, " + name)

hello_to("Bob")
```

(An "argument" is the thing we put in when we call a function)

The variable called "name" is a variable for the function.

When we type `hello_to("Bob")` we are passing in "Bob" as an argument to the "name" *parameter* in the function.

Python also lets us give the arguments with an equal sign refering to the parameter (aka variable) for the function.

```py
def hello_to(name):
  print("Hello, " + name)

hello_to(name="Bob")
```

What if we want to make a function that takes many parameters (aka inputs)? To add more parameters we simply separate them using a comma `,`. Delete the old code and type in the this.

```py
def hello_to(name, age):
  print("Hello, " + name + " you are " + age)
```

And to *call* the function (and pass in some *arguments* (aka input)) we do the following.

```py
hello_to("Bob", 12)
```

Or you can do this instead.

```py
hello_to(name="Bob", age=12)
```

# Scope
You can't use functions variables (parameters) outside of their function!

```py
def hello_to(name, age):
  print("Hello, " + name + " you are " + age)

name = "Dan" <- new variable
hello_to("Bob", 12)
```

We try to set the `name` variable to "Dan". But this just makes a new variable. It doesn't change the `name` variable (parameter) in the `hello_to` function.

We call this "scope". Scope means you cannot access variables outside of their functions.

# Lists?
What if we want to make a list of things? In python this is super easy.

Here is a list of numbers

```py
[1, 23, 5]
```

Here is a list of *strings* (aka Unicode symbols).

```py
["A", "Becky", "C", "D"]
```

In python we enclose a list in square brackets `[]` otherwise how would we know when you were trying to make a list?

We can also use a variable to refer to a list.

```py
myList = ["A", "B", "C", "D"]
```

Now we can use the variable "myList" to refer to the list.

Now how do we access each item of the list?

```py
myList[1]
```

By using square brackets `[]` after the variable we can access each item of the variables list.

Now lets print item 1. Type in the following and then run it.

```py
myList = ["A", "B", "C", "D"]
print(myList[1])
```

"It printed B?!"

Yes your right, an interesting thing about computers is that they always start counting from 0. So to access the first item in a list we have to use 0.

```py
myList = ["A", "B", "C", "D"]
print(myList[0])
```

Now you should see A get printed.

Remember when we talked about how computer represent numbers? They use 0s and 1s. So how would we represent zero? We just use the symobl `0`. If we didn't count zero as a number we would end up representing zero as `1` in binary, and that would be confusing!

And honestly, we need the number 0.

# Loops
What if we want to print "hello" 3 times? We can just write `print("hello")` 3 times. Delete our old code and type the following. (I am going to stop saying "delete the old code" as I think you have it figured out)

```py
print("hello")
print("hello")
print("hello")
```

But what if we want it to change the string to "Hello world"? We could just change them all manually.

```py
print("Hello world")
print("Hello world")
print("Hello world")
```

But that is kinda annoying, even with copy paste. Instead we can using a "loop" to run the same code a certain number of times.

```py
for item in [2, 3, 5]:
    print("Hello world")
```

This code prints "Hello world" 3 times.

What is the `for variable in [2, 3, 5]`? It is saying, quite literally, "for every item in the list". 

A "for" loop in Python use lists to know the number of times we want to loop.

Every time we loop, the current item we are at in the list gets stored in the variable "item".

We aren't using the variable called "item", but we could if we changed the code to the following.

```py
for item in [2, 2, 3, 5]:
  print(item)
```

This goes to an item in the list, stores it in the "item" variable, then runs any code inside the loop. In this case we print "item" variable every loop.

When we print a variable we are *accessing* what it represents. We call the thing a variable represents its "value". So really variables just give us "references to values".

You'll notice the `:`, this does the same thing as a function, we have to indent our code after the `:` to show that it is inside of the loop.

# Comments
As a programmer we can leave comments in the code for other programmers to read, this is important to do as it helps others understand what our code is doing. 

In Python you put a hash `#` before human comments. Delete the old code and type in this.

```py
# This is a comment
# Comments don't affect code
print("This a `string`, aka *string* of characters ")
```

By putting a hash "#" in front of a comment the Python programming language can tell comments apart from the code.

# If, then? (Conditions)
What if we want to compare two numbers and see if they are the same?

Most programming languages have a keyword called "if". It works like this.

```py
if 12 == 12:
    print("They are equal")
```

We have to use the the double equal sign "==" so that python doesn't confuse it with the single equal sign "=" since the *single* equal sign is for "assigning" the variables. 

```py
# variable assignment
myVariable = 12
myVariable = myVariable + 12
# vs, checking equality
if 12 == 12:
    print("They are equal")
```

When we say `if 12 == 12` the "==" will give us a True or False variable. This is because if "statements" have to know if something is True or False. We call if statements "conditions" because they make our code only run if their *condition* is True.

We call a True or False variable a "bool" because the guy who made them was named "George Boole".

Also a bool (True or False variable) in Python requires us to uppercase the first letter, so saying `true` will not work, instead you have to use `True`.

```py
if True:
    print("This will get printed")

if False:
    # this code will not ever get run since False is always False
    print("I will never get printed...")
```

# Return types
What if I want to make a function that adds to numbers?

This is easy. Delete your old code and type in the following.

```py
def add(a, b):
    a + b
```

Now lets use the function.

```py
def add(a, b):
    a + b

add(5, 5)
```

5 + 5 = 10. Simple. But... how can we store the resulting number in a variable? Remember the `input` function? 

```py
variable = input("Type in a string:")
```

It "gave us" something to hold onto and store in a variable.

How can we do this with the `add` function!? We use the `return` keyword.

```py
def add(a, b):
    return a + b
```

Then we can do this in our code.

```py
def add(a, b):
    return a + b

result = add(5, 5)
```

The `result` variable "gets" what the `add` function "returns" (aka "gave back").

Now we can print the `result` variable.

```py
def add(a, b):
    return a + b

result = add(5, 5)
print(result)
```

If you run this code you will see 10 get printed!

Yay! Now you know all the basics of coding!

TODO remove
In the Tutorials folder you will find tutorials on how to implement the search algorithms we talked about earlier. Here is a quick link [(click this)](https://github.com/PaperPrototype/Intro-to-Coding/blob/main/Week%200%20-%20Fundamentals/Tutorials/Searching%20Algorithms/english.md)

If you need any help you can join our Discord chat to ask questions and get help from me https://discord.gg/QhqTE4t2tR

The tutorials folder also has a tutorial on making a simple game with gravity! Be sure to check it out!

And that is it for week 0! Have fun! Remember, the more tutorials you do after each lecture the better you will get at coding!