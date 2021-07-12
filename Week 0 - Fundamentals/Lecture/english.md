# Introduction
The language that computers understand are positive `+` and negative `-` electric charges, because they literally only have electric currents to work with (from a battery or being pluged in to an electric outlet). How does a computer *store* all those electric charges? Millions and millions of switches, containing a positive electric charge, or a negative electric charge. 

Each electric charge is called a "bit". A bit can be either positive, or negative. We use the symbol `1` to represent positive charges and `0` to represent negative charges. This is always the case.

The formal name for the *language* of 0s and 1s "binary".

In case your wondering how a computers "processor" can take tons of `+` and `-` signals and "process" them, we **won't** be covering that because THAT is not the focus of this course. Instead, we will focus on how we can represent numbers, letters, and everything you see on a computer, using only 0s and 1s (aka electric signals) to be able to code, and understand how that code is able to create images and text files (such as your reading right now; when you click on a letter there is litterally a computer code of 0's and 1's in the background for each letter or symbol).

When we are "coding" it just means we are writing thousands of instructions for a computers processor using binary. We put those instructions in a file. Those files of instructions are called a "program" or "app". 

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

So how do we count past 9 in decimal? We add another column!

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

If we copy the decimal system, we can go beyond the number of symbols we have by moving the `1` over and continuing to count.

```
2s | 1s
0    0
0    1
1    0 <- represents 2
```

You'll notice in binary we have a 1s place and a 2s place, but in decimal we have a 1s place and a 10s place. Since we have 10 symbols to work with we can count up to 9. In binary we only have 2 symbols to work with so we can count up to 1.

In both systems when we add another column when we run out of symbols. The next column continues where the last was not able to count to, so we have a 2s place in binary because that is where we were not able to count to.

```
2s | 1s
0    0
0    1
1    0 <- represents 2
```

Here are the "base" (aka places) numbers for binary `1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048...`.

```
8s | 4s | 2s | 1s  =  decimal
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

You will notice that the decimal (tens base) number system works well with the symbols we have, since, quite literally, the standard symbols were designed to work with a "base" of 10.

Note:
- There exist other number systems, and we could actually make our own! A popular one is hexadecimal (it has a base of 16), and octodecimal (it has a base of 8).

# lesson 1: HEXADECIMAL
Lets add another number system to the mix.

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
0      0     f
0      1     0  <- 16
```

Every number system has a 1s place, otherwise we wouldn't be able to represent 1.

We can make a chart showing each number system's values and symbol's side-by-side.

```
     decimal  hexadecimal  binary
     0  =     0   =        00000                  (0)
     1  =     1   =        00001                  (1)
     2  =     2   =        00010              (2 + 0)
     3  =     3   =        00011              (2 + 1)
     4  =     4   =        00100          (4 + 0 + 0)
     5  =     5   =        00101          (4 + 0 + 1)
     6  =     6   =        00110          (4 + 2 + 0)
     7  =     7   =        00111          (4 + 2 + 1)
     8  =     8   =        01000      (8 + 0 + 0 + 0)
     9  =     9   =        01001      (8 + 0 + 0 + 1)
    10  =     A   =        01010      (8 + 0 + 2 + 0)
    11  =     B   =        01011      (8 + 0 + 2 + 1)
    12  =     C   =        01100      (8 + 4 + 0 + 0)
    13  =     D   =        01101      (8 + 4 + 0 + 1)
    14  =     E   =        01110      (8 + 4 + 2 + 0)
    15  =     F   =        01111      (8 + 4 + 2 + 1)
    16  =    10   =        10000 (16 + 0 + 0 + 0 + 0)
    17  =    11   =        10001 (16 + 0 + 0 + 0 + 1)
```
(I took away the zero's in front of hexadecimal and decimal to make it easier to read)

People find hexadecimal more easy than binary because it can represent larger numbers with less digit (don't have to carry the 1 over so many times resulting in less digits).

Often you will see hexadecimal in place of binary. Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (which is binary's "base" number).

If you are really geeking out right now try to make a number system with a base of 8, or 5, or 3!

There is a number system called trinary that has a base of 3. Quantum computers use it because the switches in a quantum computer can be on, off, or half way, giving 3 possible symbols. You could use the symbols 1 (on) -1 (off) and 0 (half way) for trinary... or really any symbols.

# lesson 2: Numbers can represent letters
Now that we can use binary (`0`'s and `1`'s) to represent numbers, we can use those numbers to represent letters! For example the symbol "H" could be represented by the number "15", or in binary "1111" (or in hexadecimal "F").

If we want to tell the computer to say "Hello!", or actually just the letter "H", all we have to do is tell the computer ***when*** the number 15 should represent the symbol "H".

All thats left is to make a long list of what numbers map to what symbols. As you might have guessed there is already a "standard" that exists that every computer uses. Its called ASCII which stands for American Standard Code for Information Interchange. Below is the ASCII "encoding" of latin based characters letters and symbols.

(**Don't** read this whole list... skip over most of it)

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

Its pretty long. But even still it doesn't cover all the possibility's! This is because we only use 8 bits (eight columns of 0's and 1's). 

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

The code for binary search would look something like this>

```

```

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
Lets jump into actually learning coding so that we can make these algorithms, and some games (In the tutorials of this week).

We will used a programmig language called Python. Python is a program (a file of instructions written in binary (0s and 1s)). 

It reads text files, and as it reads them it figures out how to translate our text code into binary instructions the computer can understand. 

We call this type of *programming language* an "interpreted" language because it gets "interpreted" by a program, whereas other coding languages actually get converted to binary instructions by a program called a "compiler"! (but that is for next week).

Although we know that text files are also actually just binary *encoded* in the ASII or Unicode format, so really this "interpreter" program, is reading in binary as Unicode, and then figuring out what we mean, and running the instructions as it figures them out.

Lets make some simple interpreted code that prints (aka displays) the phrase "Hello World" on the screen.

We will use an online coding tool for editing the code. Open [this link](https://replit.com/) to go to the online text editor we will use, this way you don't have to download anything.

Then click the "Start Coding" button.

![start coding](/Assets/start_coding.png)

It will ask you to make an account (We're sorry about this! If you have any issues contact us in our Discord, or through the repository Issues).

Once you've made an account click the "New repl" button to create a new repl program.

![new repl](/Assets/new_repl.png)

(If you don't see it click the three lines in top left corner)

Select the Python programming language, and call the project "HelloWorld". Then click the "Create repl" button (currently hidden by the dropdown menu for picking a language).

![create repl](/Assets/create_repl.png)

Now we can write some code in replit's IDE.

![replit ide](/Assets/replit_ide.png)

IDE stands for Integerated Development Environment. It just means we get an editing tool for editing the code, much like Google Docs, or Microsoft Word. 

IDE's usually also have a "file viewer", currently there is only a single file called `hello.py`. That file is a text file. We end the files name as `.py` so that the computer can know that the file has text "code" that is for the Python programming language.

In *python* there is some code written for us that automatically figures out the exact 0s and 1s for print words onto the screen. We can simply type in the following code.

```py
print("Hello world")
```

And then click the green arrow to run the code. You will see the phrase "Hello world" printed in the "console" (the black box on the right).

The word "print" is the name of a group of code that figures out how to print words onto the screen for us. We call these groups of code "functions", because a function implements "functionality". Functions take an input and then do something with it. The `print` functions take in input through the parenthesis `()`. Then in the parenthesis it takes in two words "Hello world".

Why do we have the quotation marks `"`? Well, say we took them away. How is the computer going to know the difference between numbers, and words we want to print? What if we put a sentence with code that adds two numbers together?

```py
print(Hello I am 12 + 13)
```

How will we now if something is a sentence vs some numbers being added?

Well, in coding, we have a "specific way" of writing or "format"ing how to write words, so that the computer can know when we are trying to write a sentence, vs trying to write some code (aka adding numbers together). That format is to put the `"` around words or phrases.

We call this format the "syntax" of a programming language. Syntax is a specific way of coding so that the computer can understand it.

If you ran the `print("Hello world")` code (by clicking the green arrow) you will have seen the black "console" (the black box on the right) with the phrase "Hello world" somewhere on it.

That console is how the print function is able to display the phrase "Hello world".

# Variables
Now lets make it so that the code can get input from us and then print it out again.

How can we do that? Well there is a function that gets input from the console, and when we call the function (aka the code in the function gets run) it prints a message and then waits for us to type something.

```py
input("Type in your name: ")
```

The `input` function will print the words we in it to the console, then wait for the you to type in some words. When you hit enter, the code will stop running... and nothing happens. 

We need to be able to get access to the words you typed in.

Well, we can make a code-word (like a function) that refer's to the words the `input` function gives us. Change the code to the following.

```py
myName = input("Type in your name: ")

print(myName)
```

So what is `myName`? It gets the words that the `input` function got from the console (Or really, it gets the *output* that the `input` function gave us).

We call these referers "variables". For a clearer example make a *variable* that holds a number. And then print the variable.

```py
variable = 12

print(variable)
```

If you hit play you should see `12` get printed. Pretty cool right?

We can also add together a variable and some words.

```py
variable = 12

print("hello " + variable)
```

and you will get "hello 12".

Notice that we put a space at the end of "hello ". If we didn't put a space the word *hello* and the number *12* will be mashed together like this "hello12".

# Functions
What about functions? How can we make one ourselves? Type in the following.

```py
def say_hello_to_name():
    myName = input("Type in your name: ")

    print("Hello, " + myName)
```

If you run this nothing will happen because a function simply groups code, if we want the code in the function to run we have to *call* it... we'll get to that.

When we make a function we use the the special `def` "keyword". A keyword is a special word that lets python know that we are about to type in a function, so you can't go using `def` as the name for a *variable* as python (the coding language we are using) will think you are trying to make a *function*.

After `def` we write the name we will use to refer to the function `say_hello_to_name`. Then we put the `()` for any input (also called parameters) that the functin takes in. Currently the function takes no input so they are empty (note: you have to put the parenthesis even if it takes in no input).

(We usually refer to the "input" of a function as the function's "parameters")

You will also notice that the `:` after the two parenthesis `():`. This tells Python (the coding language we are using) that any code after the `:` is *inside* of the function. 

...But, all the code inside of the function also has to have a 2 or 4 spaces (click the `tab` key) in front of it. 

This is mostly for the you, the programmer, to be able to tell what code is in a function, and what code is not. We usually refer to adding a tab in front of code as "indenting" the code.

If we go ahead and write our code without adding any *indenting* in front...

```py
def say_hello_to_name():
myName = input("Type in your name: ")

print("Hello, " + myName)
```

...You can see it is hard to tell what code is *inside* of the function, and what code is *outside* of it. We call this idea of writing our code in a certain way "syntax". We have to have *syntax* so that we type things in a way that Python can understand what we are trying to tell it to do.

If you click the green arrow to run the code you won't see anything happen! This is because a *function* simply groups code. To *run the function* or refer to the function and have it run the code inside of it, you have to type its name followed by parenthesis ("run" simply means to have the computer load the code and read the intructions and do them).

```py
def say_hello_to_name():
  myName = input("Type in your name: ")

  print("Hello, " + myName)

# We "call" the function. 
say_hello_to_name()
```

We simply type in the name of the function `say_hello_to_name` followed by parenthesis `say_hello_to_name()` and this calls *upon  our glroies function* and *runs* it.

Notice when we are *calling* the function we don't indent it because we don't want to call a function inside of a function! THat would give us an endless loop of function running over and over (and might crash the computer, but go ahead and see what happens).

We don't have to put anything in the parenthesis since the function didn't need any input.

If you run this the function gets called and runs our code. You get asked for input, then it prints `Hello, <insert name here>`.

How do we give a function parameters (aka input)? Remember variables? We just make a variable for a function.

```py
def hello_to(name):
  print("Hello, " + name)
```

And then we can "call" the function and give it input

```py
def hello_to(name):
  print("Hello, " + name)

hello_to("Bob")
```

Now what if we want to make a function that takes many paremeters (aka inputs)? To add more parameters we simply separate them using a comma `,`

```py
def hello_to(name, age):
  print("Hello, " + name + " you are " + age)
```

# Lists?
What if we want to make a list of things? In python this is super easy.

Here is a list of numbers

```py
[1, 23, 5]
```

Here is a list of letters and words
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
myList[0]
```

By using square brackets `[]` after the variable we can access each item of the variables list, based on the items position in the list. So `myList[0]` gets item 0, which is the first item "A".

"What do you mean item `0`? Shouldn't it be `[1]` to get the first item?"

Yes your right, but an interesting thing about computers is that they always start counting from 0. 

This also applies getting things from a lists of items, so if we want to access the first item in a list we have to use `0` to access the first item.

Remember when we talked about how computer represent numbers? They use 0s and 1s. So how would we represent zero? we just use the symobl `0`. If we didn't count zero as a number we would end up representing zero as `1` in binary.

And honestly, we need the number 0.

# Loops
What if we want to print "hello" 3 times? We can just write `print("hello")` 3 times.

```py
print("hello")
print("hello")
print("hello")
```

But what if we want it to change the words to "Hello world"? We can just change them all.

```py
print("Hello world")
print("Hello world")
print("Hello world")
```

But that is kinda annoying, even with copy paste. Instead we can using a "loop" to run the same code a certain number of times.

```py
for item in [0, 1, 2]:
    print("Hello world")
```

This code prints "Hello world" 3 times.

What is the `for variable in [0, 1, 2]`? The word `for` is a keyword as well as the keyword `in`. They are saying, quite literally, "for every item in the list".

We store each item that we access from the list in a variable called "item".

Then you'll notice the `:`, this does the same thing as a function, we have to indent our code after the `:` to show that it is inside of the loop.

The code inside of the loop will run once for every item, every loop it stores a reference to the number in the variable "item".

We aren't using the variable item, but we could if we changed the code to the following.

```py
for item in [0, 1, 3]:
  print("Hello world")
  print(item)
```

This still prints "Hello world" 3 times, but it also prints the item.

When we print a variable we are accessing what it represents. We call the thing a variable represents its "value". So really variables just give us references to values.

# Comments
As a programmer can leave human written comments in the code for other programmers to read, this is important to do as it helps others understand what the code is doing. In Python you put a hash `#` before human comments. 

```py
# This is a comment
# Comments don't affect code
print("This is code")
```

By putting the hash in front the Python programming language can tell comments apart from the code.

# If, then?
What if we want to compare two names and see if they are the same? Or compare two numbers?

Most programming languages have a keyword called "if". It works like this.

```py
if 12 == 12:
    print("They are equal")
```

We have to use the the double equal sign "==" so that python doesn't confuse it with the single equal sign "=" since the *single* equal sign is for "assigning" variables. 

```py
myVariable = 12
myVariable = myVariable + 12
# equals 24
```

When we say `if 12 == 12` the "==" will give us a bool. This is because if "statements" have to know if something is True or False. We call if statements "conditions" because they make our code only run if their *condition* is True.

We call a True or False variable a "bool" because the guy who made them was named "George Boole".

Also a bool (True or False variable) in Python requires us to uppercase the first letter, so saying `true` will not work, instead you have to use `True`.

In the Tutorials folder you will find tutorials on how to implement the search algorithms we talked about earlier. If you need any help you can join our Discord to ask questions and get help from me https://discord.gg/QhqTE4t2tR

And that is it for week 0! Have fun! There is also a tutorial on making a simple game, but just remember, the more tutorials you do after each lecture the better you will get at coding!
