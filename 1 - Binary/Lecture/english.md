Somehow we have been able to write text into a file, call that text code, "run" the code, and somehow our computer understood it.

So how did all that work? You may have hear that computers understand 0s and 1s. Really a 0 or a 1 just represents a switch or electric charge in your computer. 0 representing an off switch or a negative electric charge, and 1 representing an on switch or a positive electric charge. We call this "binary". "bi" meaning 2. Every positive or electriv charge is stored using a switch or electric charge. We call each charge (or switch) a "bit".

So how did our text based code translate to binary? It turns out that your computers processor understands a few instructions. Each instruction is represented by sequences of 0s and 1s. In your computer you have a file, called an app or program, that contains binary instructions. When we "ran" the code, then a program called Python, read through our text file and "interpreted" our text instructions. We call the Python programming language an interpreted programming language because our code gets "interpreted" by the Python program (usually called an "interpreter" program). Don't worry the people who made the Python interpreter didn't have to make the Python interpreter using 0s and 1s! Instead they used a "compiled" programming language, we'll get to this in a second.

You may have noticed if you typed gibberish like "qnerkjq 1924uj1,.3 rj32m,5r)ajebqrkqm }  2}:q2" you would get an error and nothing would happen. Since someone had to write the Python program, they came up with a certain "syntax" (format for writing code) that could be understood by Python (the interpreter program). Without this syntax it would be near to impossible to decipher the code programmers wrote.

This syntax made us put a colon `:` at the end of functions or if statements, as well as "indent" our code using a tab (putting 2 or 4 spaces in front of code). Now you know why.

# Binary
We also store information as 0s and 1s. How does that work? Our number system uses ten symbols, 0 to 9, but it could have used 7 symbols, 0 to 6! 

It turns out you can even count using only two symbols, 0 and 1! Once we can count using two symbols we can then store any symbol as a number in the computer. When I say symbol, I mean anything made of lines and ink that has been written down like "9" or "T" or "$". All that is left is to make a "system" of mapping numbers to specific symbols, in fact these very words are probably encoded using the Unicode standard (we'll get to that in a second.).

Lets learn how to count using only two symbols `0` and `1`.

In the tens system (called "decimal") we can count as high as nine using the symbols we have.

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
```

But then we get stuck at nine. The solution became to add another column, reset the symbols, and say that the second column will multiply all the numbers by ten (since that is where the last column left off).

```
tenth | ones
0       0
0       1
0       2
0       3
0       4
0       5
0       6
0       7
0       8
0       9
1       0 = 1 * ten = ten
```

Then we can count up to nineteen.

```
tenth | ones
1       0 = 1 * ten = ten

1       1 = (1 * ten) + 1 = eleven
```

We will simplify the diagram for your reading, just know that each column is multiplied by its "place" (tenth place, ones place).

```
tenth | ones
1       0   = ten
1       1   = eleven
1       2   = twelve
1       3   = thirteen
1       4   = fourteen
1       5   = fifteen
...
1       8   = eighteen
1       9   = nineteen
```

Now we can keep increasing the columns in sequence to get ever increasing numbers.

```
thousands | hundreds | tens | ones
0           9           9       9 = 999
1           0           0       0 = 1000
```

Lets try this with the twos system (called "binary" or "duodecimal").

```
0
1
```

After only two symbols we have to add another column.

```
twos | ones
0       0 = zero
0       1 = one
1       1 = two
```

See the pattern? And with this system we can count as high as we want, its just going to take a whole lot more columns than decimal does! 

```
fours | twos | ones          decimal (tens system)
0       0       0 =    0  =  0
0       0       1 =    1  =  1
0       1       1 =   11  =  3
1       0       0 =  100  =  4
1       0       1 =  101  =  5
1       1       0 =  110  =  6
1       1       1 =  111  =  7
```

Although since technically all these bits (a `0` or `1`) are just switches or electric charges all in a row, so the emtpy `0`s in front of our numbers are still present.

```
fours | twos | ones          decimal (tens system)
0       0       0 =  000  =  0
0       0       1 =  001  =  1
0       1       1 =  011  =  3
1       0       0 =  100  =  4
1       0       1 =  101  =  5
1       1       0 =  110  =  6
1       1       1 =  111  =  7
```

In computers we have to have decide before hand how high we want to count. We then asign a set of 0s and 1s in our computers for that number. We can't just grow the number of bits (`0`s and `1`s) we use for a number (if say we decide we want to be able to count higher) because the neighboring `0`s are probably being used for something else!

Now that we can count using binary we'll use those numbers and map them to specific symbols and characters. The ASCII standard is very old but is still used today by programming languages like the C programming language. C actually lets us manipulate the `0`s and `1`s, but we'll get to that another time.

Here is a short list of some ASCII symbols you might be familiar with.

(For full list see the Notes)

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
(taken from https://theasciicode.com.ar/ascii-codes.txt)

Every ASCII symbol uses 8 bits. This lets gives us 256 possible symbols since with 8 bits we can only count from 0 to 255.

ASCII only supports latin characters (latin symbols cover spanish, english, french and others). If we want more rare characters then we are out of luck when it comes to ASCII. As a result a new standard was made called Unicode.

Unicode has several levels of "transform formats". UTF-8 (Unicode Transform Format 8) givews us 8 bits, and is backwards compatible with ASCII.

UTF-16 uses 16 bits, and gives us 16^2 (16 to the power of 2) possible characters. There is also UTF-32 and possibly a UTF-64, but I don't think anyone uses UTF-64 since UTF-32 still has room for new symbols (at the time of writing).

Further reading (feel free to contribute to this list)
- https://theasciicode.com.ar/ascii-codes.txt

# Colors
For color we use lights in our computer. Each "pixel" is made up of a combination of three smaller LEDs (Light Emiting Diodes). These smaller LEDS are Red Green and Blue. We mix different amounts of each color to make all the colors you see on your screen.

RGB-24 is a format that uses 3 numbers for Red Green and Blue, with each number using 8 bits. This results in having numbers between 0 and 255.

If the number for Red is 0, then the LED for 0 is turned off. If the number for Red is 255, then the LED is fully on.

For example the numbers 249, 255, 0, make the color yellow.

![yellow color](/Assets/yellow_color.png)


In memroy the RGB values look like this

```
11111001 11111111 00000000
```

Why are all the smallest numbers using 8 bits? To make making accessing memory faster, modern computers store memory in blocks of 8 bits. Since this is ubiquitous (so common that it is seen everywhere) we call these blocks of memory a "byte". A byte also refers to 8 bits, like dollars refer to 100 pennies.

This may be slightly incorrect, and I think some computers store information in 32 bits or 86 bits. Computers these days are pretty confusing.

Resources
- Very good explanation of RGB http://paulbourke.net/dataformats/bitmaps/ 

# Pictures
The simplest picture is a bitmap picture. Bitmap pictures just store each pixel as an RGB value.

Using bitmaps for pictures tends to take up a lot of space.

Resources (also link to other courses that are relevant)
- Very good explanation of bitmaps http://paulbourke.net/dataformats/bitmaps/

# Audio
Yeah, I have no idea. There are many, many audio formats. I wonder if there is a simple one we could talk about...

# File systems
You migh have wondered how your computer can have files and folders if the only things the computers understand is bits (`0`s and `1`s).

There is a program on your computer that manages presenting the information in your computer as yfiles and folders. Not interestingly these programs are called a "file system".
