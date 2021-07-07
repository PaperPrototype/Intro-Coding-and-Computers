# Intro
Computers have a language that they understand, positive `+` and negative `-` electric signals. How does a computer store all those electric signals? Millions and millions of switches, containing a positive electric charge, or a negative electric charge. 

Each electric charge is called a "bit". But the idea of using 0s and 1s to represent everything is refered to as "binary". "bi" meaning 2, because there are only two symbols in a computers alphabet.

We usually use the symbol `1` to represent positive charges and `0` to represent negative charges.

We **won't** go into the details of how a computers "processor" can take tons of `+` and `-` signals and process them. Instead we will focus on how we can represent numbers, letters, and everything you see on a computer, using only 0s and 1s (aka electric signals).

When we are "coding" it just means we are writing thousands of instructions for a computers "processor" using binary. We put those instructions in a file. Those files of instructions are called a "program" or "app". 

But we don't want to code using 0s and 1s!

Thankfully some smart people made a *program* (using binary!) that took text (aka letter) based instructions from a file and turned them into binary instructions for us!

But how can you represent letters using binary?

# Binary
Lets start by learning how to represent numbers using only two symbols, `0` and `1`.

In the "decimal" ("dec" meaning ten) number system we have ten symbols to work with, `0, 1, 2, 3, 4, 5, 6, 7, 8, 9`. This is why people will say the decimal number system has a "base" of ten.

We will make a number system like the tens system except using using only two symbols, `0` and `1`.

In binary we only have two symbols `0, 1` and that is why number represented in binary are said to have a base of 2.

In binary we can have `0` represent the value 0, and `1` represent the value 1.

But that doesn't get us very far! 

```
0
1
2 ?
```

To solve this, we can look at how the decimal (tens) system counts farther than its last symbol -> 9.

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

If we copy the decimal (tens) system we can go beyond the number of symbols we have by moving the `1` over and continuing to count.

```
(binary) 0, 1, 10...
(decimal) 0, 1, 2...
```

Weird huh? But, this is exactly what we do with the decimal (tens) number system! How do we count to 3 in binary?

```
(binary) 0, 1, 10, 11...
(decimal) 0, 1, 2, 3...
```

Why did we increase the zero to a one? Because that is exactly what we do in the tens system.

```
1
2
3
4
5
6
7
8
9
10 
11 <--
12
13
14
15
16
17
18
19
```

Except in binary we don't have ten symbols, so this doesn't represent the decimal number 11. Instead it represents the decimal number 3.

In the decimal number system, every time we carry the one we increase the number by a multiple of ten.


```
DECIMAL SYSTEM (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

multiple (base) -> (100) + (10) + (1)  <- multiply number below by its base
(decimal)           0    +  0   +  4  =  0 + 0 + 4  = 4
(decimal)           0    +  0   +  5  =  0 + 0 + 5  = 5
...
(decimal)           0    +  1   +  0  =  0 + 10 + 0  = 10
(decimal)           0    +  1   +  1  =  0 + 10 + 1  = 11
(decimal)           0    +  1   +  2  =  0 + 10 + 2  = 12
```

This is because the tens system has a base of ten. Can you see it now?

But in binary we have a base of two, so every time we move the 1 over we increase the number by a multiple of two.

```
BINARY (0, 1) SYSTEM

multiple -> (4) + (2) + (1)    (decimal equivalent)
(binary)     0  +  0  +  1  =  0 + 0 + 1
(binary)     0  +  1  +  0  =  0 + 2 + 0
(binary)     0  +  1  +  1  =  0 + 2 + 1
(binary)     1  +  0  +  0  =  4 + 0 + 0
(binary)     1  +  0  +  1  =  4 + 0 + 1
(binary)     1  +  1  +  0  =  4 + 2 + 0
(binary)     1  +  1  +  1  =  4 + 2 + 1
```

To count further than the number of digits you have, you have to add another base number. In the examples above we were only using three digits to count `digit + digit + digit`.

Because binary has a "base" of 2 every base number will be a multiple of 2. 

Although, ee start the base with 1, otherwise you wouldn't be able to represent the number 1, or any odd numbers (AKA 3, 5, 7...). 

Here are the base numbers for binary `1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048...`.

Here are the base numbers for the tens system `1, 10, 100, 1000`. You will notice that the decimal (tens) number system works well with the symbols we have, since, wuite literally, the symbols were designed to work with a base of 10.

Note:
- There exist other number systems, and we could actually make our own, but one popukar one is hexadecimal (it has a base of 16), and octodecimal (it has a base of 8).

- Another name you could call the binary system is "duo-decimal", to be more consistent with the naming of other number systems.

# hexadecimal
Lets add another number system to the mix.

It has sixteen symbols we can use, The symbols are `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. We use the decimal symbols for 0 to 9 and then the alphabetical symbols for A to F, for 10 to 16.

So we can count up to 15 without needing to add another digit.

```
HEXADECIMAL SYSTEM

base ------>  (128) + (64) + (32) + (16) + (1) <--- multiply by the base
(hexadecimal)  0    +  0   +  0   +  0   +  1  =  0 + 0 + 0 + 1  =  1
(hexadecimal)  0    +  0   +  0   +  0   +  2  =  0 + 0 + 0 + 2  =  2
...
(hexadecimal)  0    +  0   +  0   +  0   +  9  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  A  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  B  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  C  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  D  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  E  =  0 + 0 + 0 + 2  =  2
(hexadecimal)  0    +  0   +  0   +  0   +  F  =  0 + 0 + 0 + 15  =  15 <--- up to 15
...
(hexadecimal)  0    +  0   +  0   +  1   +  0  =  0 + 0 + 16 + 1  =  16
(hexadecimal)  0    +  0   +  0   +  1   +  1  =  0 + 0 + 16 + 2  =  17
(hexadecimal)  0    +  0   +  0   +  1   +  2  =  0 + 0 + 16 + 3  =  18
```

We can make a chart showing each number systems values and symbol systems side-by-side.

```
    decimal  hexadecimal   binary
    0   =    0    =        0     (0)
    1   =    1    =        1     (1)
    2   =    2    =        10    (2 + 0)
    3   =    3    =        11    (2 + 1)
    4   =    4    =        100   (4 + 0 + 0)
    5   =    5    =        101   (4 + 0 + 1)
    6   =    6    =        110   (4 + 2 + 0)
    7   =    7    =        111   (4 + 2 + 1)
    8   =    8    =        1000  (8 + 0 + 0 + 0)
    9   =    9    =        1001  (8 + 0 + 0 + 1)
    10  =    A    =        1010  (8 + 0 + 2 + 0)
    11  =    B    =        1011  (8 + 0 + 2 + 1)
    12  =    C    =        1100  (8 + 4 + 0 + 0)
    13  =    D    =        1101  (8 + 4 + 0 + 1)
    14  =    E    =        1110  (8 + 4 + 2 + 0)
    15  =    F    =        1111  (8 + 4 + 2 + 1)
    16  =    10   =        10000 (16 + 0 + 0 + 0 + 0)
    17  =    11   =        10001 (16 + 0 + 0 + 0 + 1)
```
(It took me 30 miutes to figure out the binary equivalents)

People find hexadecimal more easy than binary because it can represent larger numbers with less digit, and you don't have to carry 1 over so many times resulting in less digits. 

Often you will see hexadecimal in place of binary. Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (which is binary's base number).

If you are really geeking out right now try to make a number system with a base of 8, or 5, or 3!

There is a number system called trinary that has a base of 3. Quantum computers use it because the switches in a quantum computer can be on, off, or half way, giving 3 possible symbols. You could use the symbols 1 (on) -1 (off) and 0 (half way) for trinary... or really any symbols.

# Numbers can represent letters
Now that we can use binary (`0`'s and `1`'s) to represent numbers, we can use those numbers to represent letters! For example the letter "H" could be represented by the number "15", or in binary "1111", or in hexadecimal "F".

If we want to tell the computer to say "Hello!", or actually just the letter "H", all we have to do is tell the computer *when* the number 15 should represent "H".

Now all thats left is to make a long list of what numbers should map to what letters. As you might have guessed there is already a "standard" that us nerds have made. Its called ASCII which stands for American Standard Code for Information Interchange. Below is the ASCII "encoding" of latin based characters letters and symbols

```
ASCII ENCODING

    num  letter/symbol
	0	 NULL	(Null character)			
	1    SOH	(Start of Header)			
	2	 STX	(Start of Text)			
	3	 ETX	(End of Text)			
	4	 EOT	(End of Transmission)			
	5	 ENQ	(Enquiry)			
	6	 ACK	(Acknowledgement)			
	7	 BEL	(Bell)			
	8	 BS	    (Backspace)			
	9	 HT	    (Horizontal Tab)			
	10	 LF	    (Line feed)			
	11	 VT	    (Vertical Tab)			
	12	 FF	    (Form feed)			
	13	 CR	    (Carriage return)			
	14	 SO	    (Shift Out)			
	15	 SI	    (Shift In)			
	16	 DLE	(Data link escape)			
	17	 DC1	(Device control 1)			
	18	 DC2	(Device control 2)			
	19	 DC3	(Device control 3)			
	20	 DC4	(Device control 4)			
	21	 NAK	(Negative acknowledgement)			
	22	 SYN	(Synchronous idle)			
	23	 ETB	(End of transmission block)			
	24	 CAN	(Cancel)			
	25	 EM	    (End of medium)			
	26	 SUB	(Substitute)			
	27	 ESC	(Escape)			
	28	 FS	    (File separator)			
	29	 GS	    (Group separator)			
	30	 RS	    (Record separator)			
	31	 US	    (Unit separator)			
						
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
						
	128	Ç	(Majuscule C-cedilla )			
	129	ü	(letter "u" with umlaut or diaeresis ; "u-umlaut")			
	130	é	(letter "e" with acute accent or "e-acute")			
	131	â	(letter "a" with circumflex accent or "a-circumflex")			
	132	ä	(letter "a" with umlaut or diaeresis ; "a-umlaut")			
	133	à	(letter "a" with grave accent)			
	134	å	(letter "a"  with a ring)			
	135	ç	(Minuscule c-cedilla)			
	136	ê	(letter "e" with circumflex accent or "e-circumflex")			
	137	ë	(letter "e" with umlaut or diaeresis ; "e-umlaut")			
	138	è	(letter "e" with grave accent)			
	139	ï	(letter "i" with umlaut or diaeresis ; "i-umlaut")			
	140	î	(letter "i" with circumflex accent or "i-circumflex")			
	141	ì	(letter "i" with grave accent)			
	142	Ä	(letter "A" with umlaut or diaeresis ; "A-umlaut")			
	143	Å	(letter "A"  with a ring)			
	144	É	(Capital letter "E" with acute accent or "E-acute")			
	145	æ	(Latin diphthong "ae")			
	146	Æ	(Latin diphthong "AE")			
	147	ô	(letter "o" with circumflex accent or "o-circumflex")			
	148	ö	(letter "o" with umlaut or diaeresis ; "o-umlaut")			
	149	ò	(letter "o" with grave accent)			
	150	û	(letter "u" with circumflex accent or "u-circumflex")			
	151	ù	(letter "u" with grave accent)			
	152	ÿ	(letter "y" with diaeresis)			
	153	Ö	(letter "O" with umlaut or diaeresis ; "O-umlaut")			
	154	Ü	(letter "U" with umlaut or diaeresis ; "U-umlaut")			
	155	ø	(slashed zero or empty set)			
	156	£	(Pound sign ; symbol for the pound sterling)			
	157	Ø	(slashed zero or empty set)			
	158	×	(multiplication sign)			
	159	ƒ	(function sign ; f with hook sign ; florin sign )			
	160	á	(letter "a" with acute accent or "a-acute")			
	161	í	(letter "i" with acute accent or "i-acute")			
	162	ó	(letter "o" with acute accent or "o-acute")			
	163	ú	(letter "u" with acute accent or "u-acute")			
	164	ñ	(letter "n" with tilde ; enye)			
	165	Ñ	(letter "N" with tilde ; enye)			
	166	ª	(feminine ordinal indicator )			
	167	º	(masculine ordinal indicator)			
	168	¿	(Inverted question marks)			
	169	®	(Registered trademark symbol)			
	170	¬	(Logical negation symbol)			
	171	½	(One half)			
	172	¼	(Quarter or  one fourth)			
	173	¡	(Inverted exclamation marks)			
	174	«	(Guillemets or  angle quotes)			
	175	»	(Guillemets or  angle quotes)			
	176	░				
	177	▒				
	178	▓				
	179	│	(Box drawing character)			
	180	┤	(Box drawing character)			
	181	Á	(Capital letter "A" with acute accent or "A-acute")			
	182	Â	(letter "A" with circumflex accent or "A-circumflex")			
	183	À	(letter "A" with grave accent)			
	184	©	(Copyright symbol)			
	185	╣	(Box drawing character)			
	186	║	(Box drawing character)			
	187	╗	(Box drawing character)			
	188	╝	(Box drawing character)			
	189	¢	(Cent symbol)			
	190	¥	(YEN and YUAN sign)			
	191	┐	(Box drawing character)			
	192	└	(Box drawing character)			
	193	┴	(Box drawing character)			
	194	┬	(Box drawing character)			
	195	├	(Box drawing character)			
	196	─	(Box drawing character)			
	197	┼	(Box drawing character)			
	198	ã	(letter "a" with tilde or "a-tilde")			
	199	Ã	(letter "A" with tilde or "A-tilde")			
	200	╚	(Box drawing character)			
	201	╔	(Box drawing character)			
	202	╩	(Box drawing character)			
	203	╦	(Box drawing character)			
	204	╠	(Box drawing character)			
	205	═	(Box drawing character)			
	206	╬	(Box drawing character)			
	207	¤	(generic currency sign )			
	208	ð	(lowercase "eth")			
	209	Ð	(Capital letter "Eth")			
	210	Ê	(letter "E" with circumflex accent or "E-circumflex")			
	211	Ë	(letter "E" with umlaut or diaeresis ; "E-umlaut")			
	212	È	(letter "E" with grave accent)			
	213	ı	(lowercase dot less i)			
	214	Í	(Capital letter "I" with acute accent or "I-acute")			
	215	Î	(letter "I" with circumflex accent or "I-circumflex")			
	216	Ï	(letter "I" with umlaut or diaeresis ; "I-umlaut")			
	217	┘	(Box drawing character)			
	218	┌	(Box drawing character)			
	219	█	(Block)			
	220	▄				
	221	¦	(vertical broken bar )			
	222	Ì	(letter "I" with grave accent)			
	223	▀				
	224	Ó	(Capital letter "O" with acute accent or "O-acute")			
	225	ß	(letter "Eszett" ; "scharfes S" or "sharp S")			
	226	Ô	(letter "O" with circumflex accent or "O-circumflex")			
	227	Ò	(letter "O" with grave accent)			
	228	õ	(letter "o" with tilde or "o-tilde")			
	229	Õ	(letter "O" with tilde or "O-tilde")			
	230	µ	(Lowercase letter "Mu" ; micro sign or micron)			
	231	þ	(capital letter "Thorn")			
	232	Þ	(lowercase letter "thorn")			
	233	Ú	(Capital letter "U" with acute accent or "U-acute")			
	234	Û	(letter "U" with circumflex accent or "U-circumflex")			
	235	Ù	(letter "U" with grave accent)			
	236	ý	(letter "y" with acute accent)			
	237	Ý	(Capital letter "Y" with acute accent)			
	238	¯	(macron symbol)			
	239	´	(Acute accent)			
	240	¬	(Hyphen)			
	241	±	(Plus-minus sign)			
	242	‗	(underline or underscore)			
	243	¾	(three quarters)			
	244	¶	(paragraph sign or pilcrow)			
	245	§	(Section sign)			
	246	÷	(The division sign ; Obelus)			
	247	¸	(cedilla)			
	248	°	(degree symbol )			
	249	¨	(Diaeresis)			
	250	•	(Interpunct or space dot)			
	251	¹	(superscript one)			
	252	³	(cube or superscript three)			
	253	²	(Square or superscript two)			
	254	■	(black square)			
	255	nbsp	(non-breaking space or no-break space)
```
(taken from https://theasciicode.com.ar/ascii-codes.txt)

Its pretty long. But even still it doesn't cover all the possibility's! This is because we only use 8 bits (eight 0's and 1's). Using only 8 bits for our binary number only lets us count from 0 to 255, giving us 256 possible symbols! 

Why 8 bits? and not 7 or 3 bits? Modern computers store everything in sets of 8 bits so that every memory location will hold 8 bits instead of just 1. Doing this increases the speed we can access memeory by 8x.

There is a short name for "8 bits" called a "byte". Whenever someone says "byte" they are just refering to a block of memory that is 8 bits long. This is very common as litterally every computer these days stores memory in bytes (AKA a set of 8 bits).

What about emoji's? The ASCII encoding doesn't include emoji's! This is probably because (according to Wikipedia) the ASCII encoding was invented in 1963! [1]

A new modern mapping system called Unicode is based off of ASCII with the mapping for the numbers 0 to 255 being the same as ASCII's.

Unicode offers several formats each one storing twice as many symbols and letters as the previous one. Each Unicode variant is called a Unicode Transform Format, or more commonly UTF. The first format is called UTF-8, the "8" stands for the number of bits it uses so UTF-8 takes up 1 byte (remember 1 byte is 8 bits) of space for each symbol.

How is Unicode different from ASCII? Well, with Unicode, if you add another byte you get UTF-16 which adds support for many more letters and symbols. And then UTF-32 adds even more support for symbols.

The original goal of Unicode was to cover every possible letter and symbol, this includes emoji's. UTF-8 lets us use a small amount of space if we only need the most common (latin / english) letters and symbols. And then for the less common symbols UTF-16. Then UTF-32 for even rarer symbols. There is even a UTF-64, but nobody uses it since we haven't even finished mapping UTF-32.

The crying face emoji is represented by the number 128,512, which is technically a pattern of bits 00000001 11110110 00000010 <- this may not be the correct sequence.

# Color
Emoji's are represresented by a number, but we render them as colored pictures. That may make you wonder, how are colors represented in a computer? Well we just have to find a way to map 0's and 1's to colors, or actually we can use numbers and map them to colors.

RGB is the most popular format, standing for Red Green Blue. The reason for this is that by only using Red Green and Blue lights we can make every color of the rainbow! This is what the pixels on *your* screen are doing right now. They are mixing different amounts of Red Green and Blue light to make colors!

We can use 1 byte for each color giving us numbers ranging from 0 to 255. As with Unicode, RGB also has RGB-16 and RGB-32.

By mixing the right amount of Red Green and Blue we can represent the color yellow with 249, 255, and 0.

TODO ![yellow color](/Assets/yellow_color.png)

Pictures are typically made up of thousands of pixels, this results in a lot of memory being used. For a picture of 512 x 512 pixels we end up with 512 x 512 x 3 bytes. For such large memory sizes we have other names such as kilobyte, megabyte, and gigabyte. 

A kilobyte is 1024 bytes, a megabyte is 1024 kilobytes, and a gigabyte is 1024 megabytes. A typical computer usally has a couple hundred gigabytes aroung 128 to 512 gigabytes. Some computers even have 1024 gigabytes, which is 1 terrabyte.

# Audio?
For audio... Well we also use numbers. We can have a number representing the frequency (aka deep rumble vs squeaky squeak), and then another number representing the loudness, and then another representing bass. Then we can just store a bunch of these numbers one after the other to make a sound or store music. You get the idea

Hopefully now computers make more sense! If you still don't understand something you can Join our Discord (here's an invite link https://discord.gg/QhqTE4t2tR) to ask questions from me and other students!

# Algorithms
TODO:
    first expain both algorithm
    then edxplain O(n) notation
    then go back to video to explain black box as input -> [box] -> output
    then 

In your phone you probably have a bunch of contacts to people you call or text. How does your phone find that contact, using only instructions?

Say we have 1000 contacts and we want to find someone with the name of Johnny. How can we make some instructions about how to find Johnny for the computer? Lets make some simple example code for that.

```
1|  open first page
2|  if johnny is on page
3|    return (give back) johnny's info
4|  else if johnny not on page
5|    open next page
6|    go back to line 2
```

First we tell the computer to open the first contact, if johnny is on it then, show his information. But, if johnny is not on the page, keep going and move to the next page.

Once we move to the next page, we go back to line 2 (You will notie each line of code has a number in front) and start over, checking if Johnny is on the page, then if not going back to line 2, and so on. 

This code will run over and over, "looping" as we call it, until it finds johnny. This "algorithm" (way of solving something througha specific set of steps) is what we call a "linear" search algorithm because we go over every single contact "linearly".

There is one more problem, what if we don't find johnny? Well, the code would try to just keep searching, or crash your computer or you will get an endless loading screen. We call this a "bug". You'll hear the word "bug" used to refer to these kinds of programmer errors.

To fix this we add 2 more lines of code

```
1|  open first page
2|  if johnny is on page
3|    return (give back) johnny's info
4|  else if johnny not on page
5|    open next page
6|    go back to line 2
7|  else
8|    exit
```

This algorithm for searching seems pretty dumb though. If we had say 1000 contacts, in a worst case scenario it would take 1000 page turns, or "loops", to find johnny if he was the last contact on the list. What if there was a super shortcut to make the code run faster?

We can exploit the fact that your in your phone contacts are sorted alphabetically. Rather than starting at the beginning of the contacts list we can start right smack in the center. This makes us the closest to every possible contact (if you think about it, this is literally the exact average position of all the contacts).

Lets say we land at Samuel's contact. Well, since all the contacts are in alphabetical order, we know that Johnny will be somewhere before Samuels contact (Since J comes before S in the alphabet).

![binary search 0](/Assets/binary_search_0.png)

But here's the coolest part, now we can literally just ignore all the contacts below Samuel, and eliminate half of the contacts that need searched!

![binary search 1](/Assets/binary_search_1.png)

Remember the linear search code was "looping" once for every contact in the worst case scenario. But now, for every loop we eliminate half of the remaining work!

Lets keep going with this. We start in the center of the remaining contacts. Say we land at Dexter's contact.

![binary search 2](/Assets/binary_search_2.png)

Now we know that the top half of the contacts (that remain) are not going to have Johnny (notice that we also include Dexter's contact in the removal).

![binary search 3](/Assets/binary_search_3.png)

And we've split our work in half again! We could keep doing this until we founnd Johnny. This algorithm is called "binary search" (rather than linear search). The name comes from the fact we always split our work in two (aka half), hence "bi" which stands for two.

Its also because some later algorithms will use a `1` to represent choosing the right, and `0` to represent shoosing the left when searching.

There exists a method for graphing the number of iterations the above algorithms have to take to solve a problem. 

The first algorithm, the one we called "linear search", in its worst case scenario, takes 1000 iterations (loops) to find Johhny for 1000 contacts (If say Johnny was the last contact). So, we can say if there are N number of contacts then it will take N number of iterations, in the worst case scenario, to find Johnny using linear search. For example, N in this case is 1000 (since there are 1000 contacts), and it will take us 1000 steps to find Johnny (Yeah ok, its actually 999 steps to find Johnny in the worst case scenario. As "worst case scenarios" go a small difference of 1 is really not that relevant).

It takes pretty long to say "for the worst case scenario" so computer scientists (like you) made something called "Big O notation". 

In big O notation we write and `O`represents the worst case scenario, with some parenthesis after it `O()` holding a number representing the number of steps or iterations we have to go through to solve the problem. In our case, `O(1000)`. If we say a symbol like `N` stands for the number of contacts, then we could change the big O notation to `O(N)` since, for every contact, we add a step to the search algorithm.

We can graph linear search as, quite literally, a line

![graph linear search](/Assets/graph_linear_search.png)

This because as the number of contacts increases so does the number of steps, or iterations, it will take to find Johnny. A 1 to 1 relationship makes the line on the graph very straight, and as the problem to solve gets bigger, so does the amount of work.

What about "binary search"? Binary search in the worst case scenario is `O(log N)`. `log` just means for every iteration we go through, divide the number `N` in half. So obviously by reducing the number in half, each loop, we end up with way less steps for binary search. But just how much faster is binary search?

If we graph the binary search algorithm it looks like this

![graph binary search](/Assets/graph_binary_search.png)

As the size of the problem grows, the amount of work it takes us to solve it will barely grow!

So how could we turn this into pseudo-code? (pseudo-cde just means fake english readable example code, that only illustrates a concept and how the code "might" look). Read through the following code line by line.

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

And all we are doing is making algorithms, that is all of code, game developers focus on making the code super fast, web developers focus on making it look nice. You get the point.

For reference here is the two algorithms plotted next to each other.

![graph both search](/Assets/graph_both_search.png)

# Your first code
Lets jump into actually learning coding so that we can make these algorithms, and some games.

Hey there, I'm am still writing this lecture!

THIS IS NOT PART OF THE LECTURE BUT NOTES FOR ME:

How do we take those instructions and make something like a video game?

Lets think about how we can make instructions for simple gravity in a game. Gravity moves you down as time passes (if time stopped we would stop falling).

TODO: what is a position? x? y? huh? whats position.x?

So all we have to do is move the players position down all the time. We can write this as english instructions

```
forever
    position.y - 1
```

This code says, decrease the players y position forever.