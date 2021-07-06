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
ascii code	0	 NULL	(Null character)			
ascii code	1    SOH	(Start of Header)			
ascii code	2	 STX	(Start of Text)			
ascii code	3	 ETX	(End of Text)			
ascii code	4	 EOT	(End of Transmission)			
ascii code	5	 ENQ	(Enquiry)			
ascii code	6	 ACK	(Acknowledgement)			
ascii code	7	 BEL	(Bell)			
ascii code	8	 BS	    (Backspace)			
ascii code	9	 HT	    (Horizontal Tab)			
ascii code	10	 LF	    (Line feed)			
ascii code	11	 VT	    (Vertical Tab)			
ascii code	12	 FF	    (Form feed)			
ascii code	13	 CR	    (Carriage return)			
ascii code	14	 SO	    (Shift Out)			
ascii code	15	 SI	    (Shift In)			
ascii code	16	 DLE	(Data link escape)			
ascii code	17	 DC1	(Device control 1)			
ascii code	18	 DC2	(Device control 2)			
ascii code	19	 DC3	(Device control 3)			
ascii code	20	 DC4	(Device control 4)			
ascii code	21	 NAK	(Negative acknowledgement)			
ascii code	22	 SYN	(Synchronous idle)			
ascii code	23	 ETB	(End of transmission block)			
ascii code	24	 CAN	(Cancel)			
ascii code	25	 EM	    (End of medium)			
ascii code	26	 SUB	(Substitute)			
ascii code	27	 ESC	(Escape)			
ascii code	28	 FS	    (File separator)			
ascii code	29	 GS	    (Group separator)			
ascii code	30	 RS	    (Record separator)			
ascii code	31	 US	    (Unit separator)			
						
ascii code	32	 	(space)			
ascii code	33	!	(exclamation mark)			
ascii code	34	"	(Quotation mark)			
ascii code	35	#	(Number sign)			
ascii code	36	$	(Dollar sign)			
ascii code	37	%	(Percent sign)			
ascii code	38	&	(Ampersand)			
ascii code	39	'	(Apostrophe)			
ascii code	40	(	(round brackets or parentheses)			
ascii code	41	)	(round brackets or parentheses)			
ascii code	42	*	(Asterisk)			
ascii code	43	+	(Plus sign)			
ascii code	44	,	(Comma)			
ascii code	45	-	(Hyphen)			
ascii code	46	.	(Full stop , dot)			
ascii code	47	/	(Slash)			
ascii code	48	0	(number zero)			
ascii code	49	1	(number one)			
ascii code	50	2	(number two)			
ascii code	51	3	(number three)			
ascii code	52	4	(number four)			
ascii code	53	5	(number five)			
ascii code	54	6	(number six)			
ascii code	55	7	(number seven)			
ascii code	56	8	(number eight)			
ascii code	57	9	(number nine)			
ascii code	58	:	(Colon)			
ascii code	59	;	(Semicolon)			
ascii code	60	<	(Less-than sign )			
ascii code	61	=	(Equals sign)			
ascii code	62	>	(Greater-than sign ; Inequality) 			
ascii code	63	?	(Question mark)			
ascii code	64	@	(At sign)			
ascii code	65	A	(Capital A )			
ascii code	66	B	(Capital B )			
ascii code	67	C	(Capital C )			
ascii code	68	D	(Capital D )			
ascii code	69	E	(Capital E )			
ascii code	70	F	(Capital F )			
ascii code	71	G	(Capital G )			
ascii code	72	H	(Capital H )			
ascii code	73	I	(Capital I )			
ascii code	74	J	(Capital J )			
ascii code	75	K	(Capital K )			
ascii code	76	L	(Capital L )			
ascii code	77	M	(Capital M )			
ascii code	78	N	(Capital N )			
ascii code	79	O	(Capital O )			
ascii code	80	P	(Capital P )			
ascii code	81	Q	(Capital Q )			
ascii code	82	R	(Capital R )			
ascii code	83	S	(Capital S )			
ascii code	84	T	(Capital T )			
ascii code	85	U	(Capital U )			
ascii code	86	V	(Capital V )			
ascii code	87	W	(Capital W )			
ascii code	88	X	(Capital X )			
ascii code	89	Y	(Capital Y )			
ascii code	90	Z	(Capital Z )			
ascii code	91	[	(square brackets or box brackets)			
ascii code	92	\	(Backslash)			
ascii code	93	]	(square brackets or box brackets)			
ascii code	94	^	(Caret or circumflex accent)			
ascii code	95	_	(underscore , understrike , underbar or low line)			
ascii code	96	`	(Grave accent)			
ascii code	97	a	(Lowercase  a )			
ascii code	98	b	(Lowercase  b )			
ascii code	99	c	(Lowercase  c )			
ascii code	100	d	(Lowercase  d )			
ascii code	101	e	(Lowercase  e )			
ascii code	102	f	(Lowercase  f )			
ascii code	103	g	(Lowercase  g )			
ascii code	104	h	(Lowercase  h )			
ascii code	105	i	(Lowercase  i )			
ascii code	106	j	(Lowercase  j )			
ascii code	107	k	(Lowercase  k )			
ascii code	108	l	(Lowercase  l )			
ascii code	109	m	(Lowercase  m )			
ascii code	110	n	(Lowercase  n )			
ascii code	111	o	(Lowercase  o )			
ascii code	112	p	(Lowercase  p )			
ascii code	113	q	(Lowercase  q )			
ascii code	114	r	(Lowercase  r )			
ascii code	115	s	(Lowercase  s )			
ascii code	116	t	(Lowercase  t )			
ascii code	117	u	(Lowercase  u )			
ascii code	118	v	(Lowercase  v )			
ascii code	119	w	(Lowercase  w )			
ascii code	120	x	(Lowercase  x )			
ascii code	121	y	(Lowercase  y )			
ascii code	122	z	(Lowercase  z )			
ascii code	123	{	(curly brackets or braces)			
ascii code	124	|	(vertical-bar, vbar, vertical line or vertical slash)			
ascii code	125	}	(curly brackets or braces)			
ascii code	126	~	(Tilde ; swung dash)			
ascii code	127	DEL	(Delete)			
						
ascii code	128	Ç	(Majuscule C-cedilla )			
ascii code	129	ü	(letter "u" with umlaut or diaeresis ; "u-umlaut")			
ascii code	130	é	(letter "e" with acute accent or "e-acute")			
ascii code	131	â	(letter "a" with circumflex accent or "a-circumflex")			
ascii code	132	ä	(letter "a" with umlaut or diaeresis ; "a-umlaut")			
ascii code	133	à	(letter "a" with grave accent)			
ascii code	134	å	(letter "a"  with a ring)			
ascii code	135	ç	(Minuscule c-cedilla)			
ascii code	136	ê	(letter "e" with circumflex accent or "e-circumflex")			
ascii code	137	ë	(letter "e" with umlaut or diaeresis ; "e-umlaut")			
ascii code	138	è	(letter "e" with grave accent)			
ascii code	139	ï	(letter "i" with umlaut or diaeresis ; "i-umlaut")			
ascii code	140	î	(letter "i" with circumflex accent or "i-circumflex")			
ascii code	141	ì	(letter "i" with grave accent)			
ascii code	142	Ä	(letter "A" with umlaut or diaeresis ; "A-umlaut")			
ascii code	143	Å	(letter "A"  with a ring)			
ascii code	144	É	(Capital letter "E" with acute accent or "E-acute")			
ascii code	145	æ	(Latin diphthong "ae")			
ascii code	146	Æ	(Latin diphthong "AE")			
ascii code	147	ô	(letter "o" with circumflex accent or "o-circumflex")			
ascii code	148	ö	(letter "o" with umlaut or diaeresis ; "o-umlaut")			
ascii code	149	ò	(letter "o" with grave accent)			
ascii code	150	û	(letter "u" with circumflex accent or "u-circumflex")			
ascii code	151	ù	(letter "u" with grave accent)			
ascii code	152	ÿ	(letter "y" with diaeresis)			
ascii code	153	Ö	(letter "O" with umlaut or diaeresis ; "O-umlaut")			
ascii code	154	Ü	(letter "U" with umlaut or diaeresis ; "U-umlaut")			
ascii code	155	ø	(slashed zero or empty set)			
ascii code	156	£	(Pound sign ; symbol for the pound sterling)			
ascii code	157	Ø	(slashed zero or empty set)			
ascii code	158	×	(multiplication sign)			
ascii code	159	ƒ	(function sign ; f with hook sign ; florin sign )			
ascii code	160	á	(letter "a" with acute accent or "a-acute")			
ascii code	161	í	(letter "i" with acute accent or "i-acute")			
ascii code	162	ó	(letter "o" with acute accent or "o-acute")			
ascii code	163	ú	(letter "u" with acute accent or "u-acute")			
ascii code	164	ñ	(letter "n" with tilde ; enye)			
ascii code	165	Ñ	(letter "N" with tilde ; enye)			
ascii code	166	ª	(feminine ordinal indicator )			
ascii code	167	º	(masculine ordinal indicator)			
ascii code	168	¿	(Inverted question marks)			
ascii code	169	®	(Registered trademark symbol)			
ascii code	170	¬	(Logical negation symbol)			
ascii code	171	½	(One half)			
ascii code	172	¼	(Quarter or  one fourth)			
ascii code	173	¡	(Inverted exclamation marks)			
ascii code	174	«	(Guillemets or  angle quotes)			
ascii code	175	»	(Guillemets or  angle quotes)			
ascii code	176	░				
ascii code	177	▒				
ascii code	178	▓				
ascii code	179	│	(Box drawing character)			
ascii code	180	┤	(Box drawing character)			
ascii code	181	Á	(Capital letter "A" with acute accent or "A-acute")			
ascii code	182	Â	(letter "A" with circumflex accent or "A-circumflex")			
ascii code	183	À	(letter "A" with grave accent)			
ascii code	184	©	(Copyright symbol)			
ascii code	185	╣	(Box drawing character)			
ascii code	186	║	(Box drawing character)			
ascii code	187	╗	(Box drawing character)			
ascii code	188	╝	(Box drawing character)			
ascii code	189	¢	(Cent symbol)			
ascii code	190	¥	(YEN and YUAN sign)			
ascii code	191	┐	(Box drawing character)			
ascii code	192	└	(Box drawing character)			
ascii code	193	┴	(Box drawing character)			
ascii code	194	┬	(Box drawing character)			
ascii code	195	├	(Box drawing character)			
ascii code	196	─	(Box drawing character)			
ascii code	197	┼	(Box drawing character)			
ascii code	198	ã	(letter "a" with tilde or "a-tilde")			
ascii code	199	Ã	(letter "A" with tilde or "A-tilde")			
ascii code	200	╚	(Box drawing character)			
ascii code	201	╔	(Box drawing character)			
ascii code	202	╩	(Box drawing character)			
ascii code	203	╦	(Box drawing character)			
ascii code	204	╠	(Box drawing character)			
ascii code	205	═	(Box drawing character)			
ascii code	206	╬	(Box drawing character)			
ascii code	207	¤	(generic currency sign )			
ascii code	208	ð	(lowercase "eth")			
ascii code	209	Ð	(Capital letter "Eth")			
ascii code	210	Ê	(letter "E" with circumflex accent or "E-circumflex")			
ascii code	211	Ë	(letter "E" with umlaut or diaeresis ; "E-umlaut")			
ascii code	212	È	(letter "E" with grave accent)			
ascii code	213	ı	(lowercase dot less i)			
ascii code	214	Í	(Capital letter "I" with acute accent or "I-acute")			
ascii code	215	Î	(letter "I" with circumflex accent or "I-circumflex")			
ascii code	216	Ï	(letter "I" with umlaut or diaeresis ; "I-umlaut")			
ascii code	217	┘	(Box drawing character)			
ascii code	218	┌	(Box drawing character)			
ascii code	219	█	(Block)			
ascii code	220	▄				
ascii code	221	¦	(vertical broken bar )			
ascii code	222	Ì	(letter "I" with grave accent)			
ascii code	223	▀				
ascii code	224	Ó	(Capital letter "O" with acute accent or "O-acute")			
ascii code	225	ß	(letter "Eszett" ; "scharfes S" or "sharp S")			
ascii code	226	Ô	(letter "O" with circumflex accent or "O-circumflex")			
ascii code	227	Ò	(letter "O" with grave accent)			
ascii code	228	õ	(letter "o" with tilde or "o-tilde")			
ascii code	229	Õ	(letter "O" with tilde or "O-tilde")			
ascii code	230	µ	(Lowercase letter "Mu" ; micro sign or micron)			
ascii code	231	þ	(capital letter "Thorn")			
ascii code	232	Þ	(lowercase letter "thorn")			
ascii code	233	Ú	(Capital letter "U" with acute accent or "U-acute")			
ascii code	234	Û	(letter "U" with circumflex accent or "U-circumflex")			
ascii code	235	Ù	(letter "U" with grave accent)			
ascii code	236	ý	(letter "y" with acute accent)			
ascii code	237	Ý	(Capital letter "Y" with acute accent)			
ascii code	238	¯	(macron symbol)			
ascii code	239	´	(Acute accent)			
ascii code	240	¬	(Hyphen)			
ascii code	241	±	(Plus-minus sign)			
ascii code	242	‗	(underline or underscore)			
ascii code	243	¾	(three quarters)			
ascii code	244	¶	(paragraph sign or pilcrow)			
ascii code	245	§	(Section sign)			
ascii code	246	÷	(The division sign ; Obelus)			
ascii code	247	¸	(cedilla)			
ascii code	248	°	(degree symbol )			
ascii code	249	¨	(Diaeresis)			
ascii code	250	•	(Interpunct or space dot)			
ascii code	251	¹	(superscript one)			
ascii code	252	³	(cube or superscript three)			
ascii code	253	²	(Square or superscript two)			
ascii code	254	■	(black square)			
ascii code	255	nbsp	(non-breaking space or no-break space)
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
    first expain algorithm
    then go back to video to explain black box as input -> [box] -> output

In your phone you probably have a bunch of contacts to people you call or text. How does your phone find that contact, using only instructions?

Say we have 1000 contacts and we want to find someone with the name of Johnny. How can we make some instructions about how to find Johnny for the computer? Lets make some simple example code for that.

```
1|  open first page
2|  if johnny is on page
3|    return (give back) johnny's info
4|  else if johnny not on page
5|    open next page
6|    go to line 2
```

First we tell the computer to open the first contact, if johnny is on it then, show his information. But, if johnny is not on the page, keep going and move to the next page.

Once we move to the next page, we go back to line 2 (You will notie each line of code has a number in front) and start over, checking if Johnny is on the page, then if not going back to line 2, and so on. 

This code will run over and over, "looping" as we call it, until it finds johnny.

Now there is something we have forgotten to add to the code. What if we don't find johnny? Well, the code would try to just keep searching... but we've run out of pages! So your computer will crash or you will get an endless loading screen. We call this a "bug", and you'll hear the word "bug" used to refer to these kinds of programmer errors, that cause our programs to crash.

So we have to add one last "condition".

```
1|  open first page
2|  if johnny is on page
3|    return (give back) johnny's info
4|  else if johnny not on page
5|    open next page
6|    go to line 2
7|  else
8|    exit
```

Now the code should theoretically work.

Although this seems pretty dumb though. And it would take a while for your computer to find johnny (Well ok, only if you have like 1 Million contacts).

If we had say 1000 contacts, it would take 1000 page turns, or steps, to find johnny. A 1 to 1 relationship


# Instructions for video games?
How do we take those instructions and make something like a video game?

Lets think about how we can make instructions for simple gravity in a game. Gravity moves you down as time passes (if time stopped we would stop falling).

So all we have to do is move the players position down all the time. We can write this as english instructions

```
forever
    position.y - 1
```

This code says, decrease the players y position forever.