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


TODO remove
In the Tutorials folder you will find tutorials on how to implement the search algorithms we talked about earlier. Here is a quick link [(click this)](https://github.com/PaperPrototype/Intro-to-Coding/blob/main/Week%200%20-%20Fundamentals/Tutorials/Searching%20Algorithms/english.md)

If you need any help you can join our Discord chat to ask questions and get help from me https://discord.gg/QhqTE4t2tR

The tutorials folder also has a tutorial on making a simple game with gravity! Be sure to check it out!

And that is it for week 0! Have fun! Remember, the more tutorials you do after each lecture the better you will get at coding!