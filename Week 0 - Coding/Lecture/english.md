# Intro
Computers have a language that they understand, positive `+` and negative `-` electric signals. We usually use the symbol `1` to represent positive and `0` to represent negative. Computer nerds like to say that these two symbols are enough to make a language and a number system. That language and number system is called "binary". 

How does "binary" live in the computer? Millions and millions of switches, representing on (a positive electric charge) or off (a negative electric charge). Each electric charge is called a "bit", standing for "binary digit".

When we are "coding" it just means we are writing instructions for a computers "processor" (a processor takes tons of `off` and `on` signals and "processes" them). In coding we put a bunch of instructions into a file in the form of bits (binary digits) or binary. We call these files a "program". A simple program could tell the computer to display the word "hello" on the screen.

If we wanted to write a program we could use binary, the 0's and 1's language... That would be really hard. Thankfully though some smart people made a *program* that took some *word* based instructions from a file and turned them into binary instructions in another file for us!

The programs that turn our word based instructions into binary instructions are called "Compilers" because they "compile" our word based instructions into binary that the computer can understand.

These compilers could only understand instructions if they were written in a specific way. We call this "specific way" of writing instructions "syntax". The english language has syntax as well, if I just said "wnfkwebf enfwwen234ef +Bbqew *wqefb11" you wouldn't be able to understand it. So we have rules about how to layout words. The same is true for the word based instructions a compiler understands.

When a computers processor is made it comes with a few builtin instructions. In english we have thousands of instructions, but processors can only understand a few limited instructions. Those few processor instructions are called "Assembly" instructions and they are written in binary (Assembly is very hard to code in). The compiler has to figure out how to convert our words to those few Assembly binary instructions. Compilers can more easily compile a programming language (turn the words into functioning binary instructions) if the programming language has strict rules.

You can think of these "word" based programming languages as if you were looking from a very high mountain at a pasture of rocks. From your perspective those rocks are in the shape of some words! But if you looked at them up close you would see that they are rocks. Because of this word based programming languages are often called "high level" languages because they don't make us look really closely at the bits (AKA 0's and 1's), while a language like binary is called a "low level" programming language.

# Scratch, your first language
Lets use a program*ing* language (that will be compiled into 0's and 1's by a compiler) to get the computer to say the word "Hello!" (Well ok, *this* programming language doesn't get converted to 0's and 1's because it is running in the browser).

We will use a programming language called scratch, that automatically makes sure we write our programs with correct syntax, because getting used to a programming languages syntax can take a long time (remember syntax makes it so that the compiler can figure out how to convert our instructions into 0's and 1's). Scratch runs in your Browser so you don't have to download anything! Just go to (scratch.mit.edu)[https://scratch.mit.edu/] and and click on the "Create" or "Start Creating" button highlighted in the picture.

![create first scratch project](/Assets/create_first_scratch_project.png)

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
(binary) 0, 1, 10 and...
(decimal) 0, 1, 2...
```

Interesting we carry the 1 over once the number system reaches its "base" number, so once we try to reach the number 2 in binary we have to move the 1 over, because 2 is binary's base number. In the decimal system we move the 1 over only if we reach ten.

Now how about counting past three? How do we carry that over? Well we need another digit. If we maxed out the tens system `99 + 1 = 100` we have to grow, move the 1 over, and add another 0.

```
binary  (4) + (2) + (1)
         1  +  0  +  0    = 100 = 4 (four)

decimal (100) + (10) + (1)
         1    +  0   +  0       = 100 (one hundred)
```

In the decimal system, every time we carry a 1 over we increase the number by a multiple of ten (10, 100, 1000, 10000). But in binary, we increase the number by a multiple of two.

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
--->   16  =   10   =        10000 (16)
       17  =   11   =        10001 (16 + 1)
```
(It took me 30 miutes to figure out the binary equivalents)

People find hexadecimal more easy than binary because it can represent larger numbers with less digits. Also you will notice that hexadecimal lines up pretty well with binary since 16 is a multiple of 2 (binary has a base of 2).

# Numbers represent letters
Now that we can use binary (0's and 1's) to represent numbers we can use those numbers to represent letters. For example the letter "H" could be represented by "16", or in hexadecimal "F". 

If we want to tell the computer to say "Hello!", or actually just the letter "H", all we have to do is tell the computer *when* the number 16 should represent "H".

Now we just need to make a large list of numbers that represent letters. As you might have guessed there is already a "standard" that us nerds have made. Its called ASCII which stands for American Standard Code for Information Interchange. Below is the ASCII "encoding" of latin based characters letters and symbols

```
       number   letter/symbol
ascii code	0	NULL	(Null character)			
ascii code	1	SOH	(Start of Header)			
ascii code	2	STX	(Start of Text)			
ascii code	3	ETX	(End of Text)			
ascii code	4	EOT	(End of Transmission)			
ascii code	5	ENQ	(Enquiry)			
ascii code	6	ACK	(Acknowledgement)			
ascii code	7	BEL	(Bell)			
ascii code	8	BS	(Backspace)			
ascii code	9	HT	(Horizontal Tab)			
ascii code	10	LF	(Line feed)			
ascii code	11	VT	(Vertical Tab)			
ascii code	12	FF	(Form feed)			
ascii code	13	CR	(Carriage return)			
ascii code	14	SO	(Shift Out)			
ascii code	15	SI	(Shift In)			
ascii code	16	DLE	(Data link escape)			
ascii code	17	DC1	(Device control 1)			
ascii code	18	DC2	(Device control 2)			
ascii code	19	DC3	(Device control 3)			
ascii code	20	DC4	(Device control 4)			
ascii code	21	NAK	(Negative acknowledgement)			
ascii code	22	SYN	(Synchronous idle)			
ascii code	23	ETB	(End of transmission block)			
ascii code	24	CAN	(Cancel)			
ascii code	25	EM	(End of medium)			
ascii code	26	SUB	(Substitute)			
ascii code	27	ESC	(Escape)			
ascii code	28	FS	(File separator)			
ascii code	29	GS	(Group separator)			
ascii code	30	RS	(Record separator)			
ascii code	31	US	(Unit separator)			
						
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

Its pretty long. But even still it doesn't cover all the possibility's! This is because we only use 8 bits (eight 0's and 1's) to for our ASCII encoding. Using only 8 bits for our binary number only lets us count from 0 to 255. Remember everything in computers is really just binary.

Why 8 bits? and not 7? or 3? Modern computers store everything in sets of 8 bits, that we call a "byte". A byte is 8 bits.

What about emoji's? ASCII doesn't support emoji's. According to Wikipedia the ASCII encoding was invented in 1963! 

A new modern encoding called Unicode is based off of the ASCII encoding with the encoding for the numbers 0 to 255 being the same as ASCII except that Unicode adds another byte (8 bits). 

Unicode has several encodings, one is called UTF-8 which uses 1 byte (8 bits). UTF stand for Unicode Transform Format. Another popular Unicode encoding that adds more characters that aren't in ASCII is UTF-16, it uses (You guesssed it!) 16 bits (or 2 bytes). There is also a UTF-32 but that is not used often.

The goal for Unicode was to make an encoding that could cover every written or electronic language. This is achieved by leaving the ASCII encoding in UTF-8 but adding more characters in UTF-16, and then even more rare encoding's in UTF-32.

The crying face emoji is the number 128,512, which is technically a pattern of bits 000000011111011000000010.

# Color
Emoji's are colored pictures, and that may make you wonder, how are colors represented in a computer? Well we jsut have to find a way to map 0's and 1's to colors. RGB is the most popular format, standing for Red Green Blue. It turns out that by only using Red Green and Blue lights we can make every color of the rainbow, and this is exactly what the pixels on your screen are doing. They are mixing different amounts of Red Green and Blue light to make different colors!

We use 1 byte for each color and this gives us numbers ranging from 0 to 255. If we store three bytes each being 8 bits we end up with a total of 24 bits. We can represent the color yellow with 72, 73, 33.

!(yellow color)[]

