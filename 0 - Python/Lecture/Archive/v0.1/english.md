# Intro
Computers have a language that they understand, positive `+` and negative `-` electric signals. We usually use the symbol `1` to represent positive and `0` to represent negative. Computer nerds like to say that these two symbols are enough to make a language and a number system. That language and number system is called "binary". 

How does "binary" live in the computer? Millions and millions of switches, representing on (a positive electric charge) or off (a negative electric charge). Each electric charge is called a "bit", standing for "binary digit".

When we are "coding" it just means we are writing instructions for a computers "processor" (a processor takes tons of `off` and `on` signals and "processes" them).

In coding we put a bunch of instructions into a file in the form of bits, binary digits, aka a single `1` or `0`. We call these files of `0` and `1` instructions a "program". A simple program could tell the computer to display the word "hello" on the screen.

If we wanted to write a program we could use binary, the 0's and 1's language... But that would be really hard! Thankfully though some smart people made a *program* that took some *word* based instructions from a file and turned them into binary instructions in another file for us!

The programs that turn our word based instructions into binary instructions are called "Compilers" because they "compile" our word based instructions into binary instruction files that the computer can understand.


TODO Save for once we introduce C

These compilers could only understand instructions if they were written in a specific way. We call this "specific way" of writing instructions "syntax". The english language has syntax as well, if I just said "wnfkwebf enfwwen234ef +Bbqew *wqefb11" you wouldn't be able to understand it. So, we have to have rules about how to layout english words. The same is true for the word based instructions we write for a compiler.

When a computers processor is made it comes with a few builtin instructions, binary instrctions. In english we have thousands of instructions, but processors can only understand a few limited instructions. 

Those few processor instructions are called "Assembly" instructions. Assembly instructions small little memory control instructions written as words, that get compiled into binary.

The compiler has to figure out how to convert our words to those few Assembly binary instructions. And then that Assembly is compiled or "assembled" into binary by an "Assembler".

Compilers can more easily compile a programming language (turn the words into functioning assembly instructions) if the programming language has strict rules.

You can think of these "word" based programming languages as if you were looking from a very high mountain at a pasture of rocks. From your perspective those rocks are in the shape of some words! But if you looked at them up close you would see that they are rocks. Because of this word based programming languages are often called "high level" languages because they don't make us look really closely at the bits (AKA 0's and 1's), while a language like binary is called a "low level" programming language.

# Scratch, your first language
Lets use a program*ing* language (that will be compiled into 0's and 1's by a compiler) to get the computer to say the word "Hello!" (Well ok, *this* programming language doesn't get converted to 0's and 1's because it is running in the browser).

We will use a programming language called scratch, that automatically makes sure we write our programs with correct syntax, because getting used to a programming languages syntax can take a long time (remember syntax makes it so that the compiler can figure out how to convert our instructions into 0's and 1's). Scratch runs in your Browser so you don't have to download anything! Just go to (scratch.mit.edu)[https://scratch.mit.edu/] and and click on the "Create" or "Start Creating" button highlighted in the picture.

![create first scratch project](/Assets/create_first_scratch_project.png)

(You will need to make an account on the scratch website if you want to save this project we will make)

A tutorial should pop up, feel free to follow the tutorial and then keep reading this. Or just close it and keep reading.

![close tutorial popup](/Assets/close_tutorial_popup.png)

Now click on the cat to select it and lets add some code to it (remember "code" is another way of saying "instructions").

![click on cat then add code](/Assets/click_on_cat_add_code.png)

Scratch doesn't make us type words, instead it gives us puzzle pieces with words on them. Because they are puzzle pieces they only fit together if the syntax is correct. If we were using another programming language we would have to type those words manually and make sure they are following the rules of syntax. So yeah, scrath makes it much easier so you don't have to worry about "syntax". But scrathc still lets us see how syntax would work if we were typing it manually.

Go to the "looks" tab and drag the code block that says "say Hello!" onto the code area. You can change the word "Hello!" to whatever you want.

![add say code block](/Assets/scratch_add_code.png)

Now click the green flag to see the cat say "hello!"! Wait why didn't the cat say hello!?... The problem is that we didn't tell the computer "when" to say hello. Yes, computers only do EXACTLY what we tell them.

So we need to tell the computer when the cat should say hello? How about *in a robotic voice* "When. green. flag. clicked. say. hello.". Sounds good, and scratch gives us a code block called "When green flag clicked" in the "Events" tab. Drag the "When green flag clicked" block into the code area and attatch the "Say Hello!" block under it.

![scratch first working code](/Assets/scratch_first_working_code.png)

Now if we click the green flag the cat will say hello!

# Conclusion
What have we learned? Computers understand everything in binary (0's and 1's) but writing instructions for a computer in binary is hard. So some people made Compilers that take word based instructions and turn them into binary. We often call our word based instructions (that the compiler turns into binary) a programming language. Programming languages have to follow strict syntax rules so that the compiler can turn the words into the few binary instructions that our computer processors understand.

# Binary
How do we represent letters and numbers using this mysterious language called binary? Lets start by learning how we can represent numbers using only two symbols, `0` and `1`.

In the "decimal" (tens) number system we have ten symbols to work with, `0, 1, 2, 3, 4, 5, 6, 7, 8, 9`. This is why people will say the decimal number system has a "base" of ten.

We will make a number system like the tens system except using binary.

In binary we only have two symbols `0, 1` and that is why number represented in binary are said to have a base of 2.

In binary we can have `0` represent the value 0, and `1` represent the value 1.

But that doesn't get us very far! To solve this, we can look at how the decimal (tens) system counts farther than 9.

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

But how do we count to three? Well what do we do in the decimal (tens) system when we reach ten? We move the one over!...

```
1
2
3
...
8
9
10
100?
```

Uhhh, no! We increase the zero, AKA the ones place.

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
11
12
13
14
15
16
17
18
19
```


```
DECIMAL SYSTEM (0, 1, 2, 3, 4, 5, 6, 7, 8, 9) (10 is not a symbol but two, 1 and 0)

base ---> (100) + (10) + (1) <- multiply by the base
(decimal)  0    +  0   +  4  =  0 + 0 + 4  = 4
(decimal)  0    +  0   +  5  =  0 + 0 + 5  = 5
(decimal)  0    +  0   +  6  =  0 + 0 + 6  = 6
(decimal)  0    +  0   +  7  =  0 + 0 + 7  = 7
(decimal)  0    +  0   +  8  =  0 + 0 + 8  = 8
(decimal)  0    +  0   +  9  =  0 + 0 + 9  = 9
(decimal)  0    +  1   +  0  =  0 + 10 + 0  = 10
(decimal)  0    +  1   +  1  =  0 + 10 + 1  = 11
(decimal)  0    +  1   +  2  =  0 + 10 + 2  = 12
```

```
BINARY (0, 1) SYSTEM

base ---> (4) + (2) + (1) <- multiply by the base
(binary)   0  +  0  +  1  =  0 + 0 + 1
(binary)   0  +  1  +  0  =  0 + 2 + 0
(binary)   0  +  1  +  1  =  0 + 2 + 1
(binary)   1  +  0  +  0  =  4 + 0 + 0
(binary)   1  +  0  +  1  =  4 + 0 + 1
(binary)   1  +  1  +  0  =  4 + 2 + 0
(binary)   1  +  1  +  1  =  4 + 2 + 1
```

To count further you want to add another base number. Because binary has a "base" of 2 every base number will be a multiple of 2, although we start the base with 1, otherwise we wouldn't be able to have odd numbers (AKA 3, 5, 7...). Here are some of the base numbers for binary `1, 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048...`.

Another name you could call the binary system is "duo-decimal".

# hexadecimal
Lets add another number system to the mix.

the symbols it uses are `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F`. We use the decimal symbols for 0 to 9 and then the alphabetical symbols for 10 (A) to 15 (F). Hexadecimals base is 16 (sixteen).

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
(hexadecimal)  0    +  0   +  0   +  0   +  F  =  0 + 0 + 0 + 15  =  15 <--- up to 15 without extra digits
(hexadecimal)  0    +  0   +  0   +  1   +  0  =  0 + 0 + 16 + 1  =  16
(hexadecimal)  0    +  0   +  0   +  1   +  1  =  0 + 0 + 16 + 2  =  17
(hexadecimal)  0    +  0   +  0   +  1   +  2  =  0 + 0 + 16 + 3  =  18
```

We can make a chart showing each number systems values side-by-side.

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

People find hexadecimal more easy than binary because it can represent larger numbers with less digit, so often you will see hexadecimal in place of binary. Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (which is binary's base).

If you are really geeking out right now try to make a number system with a base of 8, or 5, or 6! 

There is a number system called trinary that has a base of 3. Quantum computer use trinary because the switches in a quantum computer can be on, off, or half way. You could use the symbols 1 (on) -1 (off) and 0 (half way) for trinary... or really any symbols.

# Numbers can represent letters
Now that we can use binary (`0`'s and `1`'s) to represent numbers, we can use those numbers to represent letters! For example the letter "H" could be represented by the number "15", or in hexadecimal "F".

If we want to tell the computer to say "Hello!", or actually just the letter "H", all we have to do is tell the computer *when* the number 15 should represent "H". In binary then "H" would be `1111` -> (8 + 4 + 2 + 1).

Now we just need to make a long list of what numbers should map to what letters. As you might have guessed there is already a "standard" that us nerds have made. Its called ASCII which stands for American Standard Code for Information Interchange. Below is the ASCII "encoding" of latin based characters letters and symbols

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

The crying face emoji is represented by the number 128,512, which is technically a pattern of bits 000000011111011000000010.

# Color
Emoji's are colored pictures, and that may make you wonder, how are colors represented in a computer? Well we just have to find a way to map 0's and 1's to colors, or actually we can use numbers and map them to colors.

RGB is the most popular format, standing for Red Green Blue. The reason for this is that by only using Red Green and Blue lights we can make every color of the rainbow! This is what the pixels on your screen are doing right now. They are mixing different amounts of Red Green and Blue light to make colors!

We can use 1 byte for each color giving us numbers ranging from 0 to 255. As with Unicode, RGB also has RGB-16 and RGB-32.

By mixing the right amount of Red Green and Blue we can represent the color yellow with 72, 73, and 33.

TODO ![yellow color](/Assets/yellow_color.png)

Pictures are typically made up of thousands of pixels, this results in a lot of memory being used. For 512 x 512 pixels we end up with 512 x 512 x 3 bytes. For such large memmory sizes we have other names such as kilobyte, megabyte, and gigabyte. 

A kilobyte is 1024 bytes, a megabyte is 1024 kilobytes, and a gigabyte is 1024 megabytes. A typical computer usally has a couple hundred gigabytes aroung 128 to 512 gigabytes. Some computers even have 1024 gigabytes, which is 1 terrabyte.