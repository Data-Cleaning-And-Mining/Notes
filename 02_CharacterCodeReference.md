# Character Codes And Uses

## Formulas

**=CODE(_Text_)**

Will reveal the character code for a character within a string of text. It can be used with one of the =LEFT(), =MID(), or =RIGHT() functions to reveal troublesome characters in a string of text, including leading and trailing whitespace that may be such things as line breaks, carriage returns, or non-breaking spaces

A | B | C
-----|-----|-----
Text | Formula | Result
A String of Text | =CODE(LEFT(A1,1)) | 65
A String of Text | =CODE(MID(A2,2,1)) | 32
&nbsp;Leading non-breaking space | =CODE(LEFT(A3,1)) | 160
 
 **=CHAR(_Number_)**
 
 Will insert the proper character using the correct ASCII code provided. Useful in combination with =SUBSTITUTE() for removing special characters that cannot otherwise be specified within paranthesis, such as carriage returns and non-breaking spaces.
 
 A | B | C
 -----|-----|-----
 Text Description | Formula | Result
 Capital A | =CHAR(65) | A
 Breaking space | =CHAR(32) |   
 Breaking Space | =CHAR(160) |  
 A String of Text | =SUBSTITUTE(A4,CHAR(65),"") |  String of Text
 A String of Text | =SUBSTITUTE(A5,CHAR(32),"") | AStringofText
 &nbsp;Leading non-breaking space | =SUBSTITUTE(A6,CHAR(160),"") |Leading non-breaking space
 
 ## Use Case
 
 A common use case for =CODE() and =CHAR() is troubleshooting and cleaning data pasted from a PDF file or other converted file. These files often contain encoding issues and non-breaking spaces that require manipulating the names and other information with a variety of =CLEAN(), =TRIM(), and =SUBSTITUTE() to strip the special characters away and make the data compatible with the other data in the spreadsheet. =CODE() and =CHAR() come in handy in identifying and specifiying which special characters are causing issues with the data.
 
 Original document - Notice this document contains both leading white space and trailing white space in front of and behind the names. Our task is to properly identify what kind of white space this is so that we can use the proper formula or combination of formulas to remove that white space. 
 A | B 
 -----|-----
 Name | 
 &nbsp;JOHN DOE   |
 &nbsp;JOHN JR DOE     |     
 &nbsp;JANE DOE  |
 
 Before Cleaning - To identify problematic white space we can also use the =LEN() function to determine the number of characters in a string of text within a cell. For example, we would expect the name "JOHN DOE" to contain 8 characters "J", "O", "H", "N", "Space", "D", "O", and "E". If =LEN() returns something greater than 8 characters in length, then we know we have some cleanup to perform on that cell.
 
 A | B | C | D | E | F | G
 -----|-----|-----|-----|----|-----|-----
 Name | Length Code | Len Result | Code for revealing leading whitespace | Result of Leading Whitespace | Code for revealing trailing whitespace | Result for trailing whitespace
 &nbsp;JOHN DOE   |=LEN(A1) | 12|=CODE(LEFT(A1,1)) | 160 |=CODE(MID(A1,10,1)) | 32
 &nbsp;JOHN JR DOE     |=LEN(A2) | 17|=CODE(LEFT(A2,1)) | 160 |=CODE(MID(A2,13,1)) | 32
 &nbsp;JANE DOE  |=LEN(A3) | 11|=CODE(LEFT(A3,1)) | 160 |=CODE(MID(A3,10,1)) | 32
 
 
 Cleaning - To clean we will use both =TRIM() to handle the trailing breaking spaces and =SUBSTITUTE() in combination with =CHAR(160) to replace the non-breaking spaces with an empty parenthesis "". We will also wrap the function in =CLEAN() to handle the existence of any nonprinting characters that may exists but not have been caught in our initial review of the data. Finally, we will include =PROPER() to make sure the names are converted to proper casing. We can do this in steps, or we can nest all the formulas together for efficiency.
 
  A | B | C | D | E | F | G
 -----|-----|-----|-----|-----|-----|-----
 Name | Clean Formula | Trim Formula | Proper Formula | Substitute Formula | Nested Formula | Result 
 &nbsp;|Removes nonprinting spaces | Removes Char 32 breaking spaces | Applies proper casing| Deletes Char 160 non-breaking spaces | 
 &nbsp;JOHN DOE   |=CLEAN(A1)  | =TRIM(B1)  | =PROPER(C1)  | =SUBSTITUTE(D1,CHAR(160),"")  | =CLEAN(TRIM(PROPER(SUBSTITUTE(A1,CHAR(160),""))))|John Doe  
 &nbsp;JOHN JR DOE     |=CLEAN(A2)| =TRIM(B2)| =PROPER(C2)| =SUBSTITUTE(D2,CHAR(160),"")| =CLEAN(TRIM(PROPER(SUBSTITUTE(A2,CHAR(160),""))))|John Jr Doe
 &nbsp;JANE DOE  |=CLEAN(A3)| =TRIM(B3)| =PROPER(C3)| =SUBSTITUTE(D3,CHAR(160),"")| =CLEAN(TRIM(PROPER(SUBSTITUTE(A3,CHAR(160),""))))| John Doe
 
Character|Code|Character Name|CHAR Function|CHAR Symbol|Category
-----|-----|-----|-----|-----|-----
32	| Space	| =CHAR(32) | 		| Punctuation
33	| Exclamation mark	| =CHAR(33) | 	!	| Punctuation
34	| Double quotes (or speech marks) | =CHAR(34) | 	“	| Punctuation
35	| Number	| =CHAR(35) | 	#	| Punctuation
36	| Dollar	| =CHAR(36) | 	$	| Punctuation
37	| Per cent sign	| =CHAR(37) | 	%	| Punctuation
38	| Ampersand	| =CHAR(38) | 	&	| Punctuation
39	| Single quote	| =CHAR(39) | 	‘	| Punctuation
40	| Open parenthesis (or open bracket) | =CHAR(40) | 	(	| Punctuation
41	| Close parenthesis (or close bracket) | =CHAR(41) | 	) | 	Punctuation
42	| Asterisk	| =CHAR(42) | 	*	| Punctuation
43	| Plus	| =CHAR(43) | 	+	| Punctuation
44	| Comma	| =CHAR(44) | 	,	| Punctuation
45	| Hyphen	| =CHAR(45) | 	–	| Punctuation
46	| Period, dot or full stop	| =CHAR(46) | 	.	| Punctuation
47	| Slash or divide	| =CHAR(47) | 	/	| Punctuation
48	| Zero	| =CHAR(48) | 	0	| Numbers
49	| One	| =CHAR(49) | 	1	| Numbers
50	| Two	| =CHAR(50) | 	2	| Numbers
51	| Three	| =CHAR(51) | 	3	| Numbers
52	| Four	| =CHAR(52) | 	4	| Numbers
53	| Five	| =CHAR(53) | 	5	| Numbers
54	| Six	| =CHAR(54) | 	6	| Numbers
55	| Seven	| =CHAR(55) | 	7	| Numbers
56	| Eight	| =CHAR(56) | 	8	| Numbers
57	| Nine	| =CHAR(57) | 	9	| Numbers
58	| Colon	| =CHAR(58) | 	:	| Special Characters
59	| Semicolon	| =CHAR(59) | 	;	| Special Characters
60	| Less than (or open angled bracket) | =CHAR(60) | 	<	| Special Characters
61	| Equals	| =CHAR(61) | 	=	| Special Characters
62	| Greater than (or close angled bracket) | =CHAR(62) | 	>	| Special Characters
63	| Question mark	| =CHAR(63) | 	?	| Special Characters
64	| At symbol	| =CHAR(64) | 	@	| Special Characters
65	| Uppercase A	| =CHAR(65) | 	A	| Letters (Upper Case)
66	| Uppercase B	| =CHAR(66) | 	B	| Letters (Upper Case)
67	| Uppercase C	| =CHAR(67) | 	C	| Letters (Upper Case)
68	| Uppercase D	| =CHAR(68) | 	D	| Letters (Upper Case)
69	| Uppercase E	| =CHAR(69) | 	E	| Letters (Upper Case)
70	| Uppercase F	| =CHAR(70) | 	F	| Letters (Upper Case)
71	| Uppercase G	| =CHAR(71) | 	G	| Letters (Upper Case)
72	| Uppercase H	| =CHAR(72) | 	H	| Letters (Upper Case)
73	| Uppercase I	| =CHAR(73) | 	I	| Letters (Upper Case)
74	| Uppercase J	| =CHAR(74) | 	J	| Letters (Upper Case)
75	| Uppercase K	| =CHAR(75) | 	K	| Letters (Upper Case)
76	| Uppercase L	| =CHAR(76) | 	L	| Letters (Upper Case)
77	| Uppercase M	| =CHAR(77) | 	M	| Letters (Upper Case)
78	| Uppercase N	| =CHAR(78) | 	N	| Letters (Upper Case)
79	| Uppercase O	| =CHAR(79) | 	O	| Letters (Upper Case)
80	| Uppercase P	| =CHAR(80) | 	P	| Letters (Upper Case)
81	| Uppercase Q	| =CHAR(81) | 	Q	| Letters (Upper Case)
82	| Uppercase R	| =CHAR(82) | 	R	| Letters (Upper Case)
83	| Uppercase S	| =CHAR(83) | 	S	| Letters (Upper Case)
84	| Uppercase T	| =CHAR(84) | 	T	| Letters (Upper Case)
85	| Uppercase U	| =CHAR(85) | 	U	| Letters (Upper Case)
86	| Uppercase V	| =CHAR(86) | 	V	| Letters (Upper Case)
87	| Uppercase W	| =CHAR(87) | 	W	| Letters (Upper Case)
88	| Uppercase X	| =CHAR(88) | 	X	| Letters (Upper Case)
89	| Uppercase Y	| =CHAR(89) | 	Y	| Letters (Upper Case)
90	| Uppercase Z	| =CHAR(90) | 	Z	| Letters (Upper Case)
91	| Opening bracket	| =CHAR(91) | 	[	| Special Characters
92	| Backslash	| =CHAR(92) | 	\	| Special Characters
93	| Closing bracket	| =CHAR(93) | 	]	| Special Characters
94	| Caret – circumflex	| =CHAR(94) | 	^	| Special Characters
95	| Underscore	| =CHAR(95) | 	_	| Special Characters
96	| Grave accent	| =CHAR(96) | 	`	| Special Characters
97	| Lowercase a	| =CHAR(97) | 	a	| Letters (Lower Case)
98	| Lowercase b	| =CHAR(98) | 	b	| Letters (Lower Case)
99	| Lowercase c	| =CHAR(99) | 	c	| Letters (Lower Case)
100	| Lowercase d	| =CHAR(100) | 	d	| Letters (Lower Case)
101	| Lowercase e	| =CHAR(101) | 	e	| Letters (Lower Case)
102	| Lowercase f	| =CHAR(102) | 	f	| Letters (Lower Case)
103	| Lowercase g	| =CHAR(103) | 	g	| Letters (Lower Case)
104	| Lowercase h	| =CHAR(104) | 	h	| Letters (Lower Case)
105	| Lowercase i	| =CHAR(105) | 	i	| Letters (Lower Case)
106	| Lowercase j	| =CHAR(106) | 	j	| Letters (Lower Case)
107	| Lowercase k	| =CHAR(107) | 	k	| Letters (Lower Case)
108	| Lowercase l	| =CHAR(108) | 	l	| Letters (Lower Case)
109	| Lowercase m	| =CHAR(109) | 	m	| Letters (Lower Case)
110	| Lowercase n	| =CHAR(110) | 	n	| Letters (Lower Case)
111	| Lowercase o	| =CHAR(111) | 	o	| Letters (Lower Case)
112	| Lowercase p	| =CHAR(112) | 	p	| Letters (Lower Case)
113	| Lowercase q	| =CHAR(113) | 	q	| Letters (Lower Case)
114	| Lowercase r	| =CHAR(114) | 	r	| Letters (Lower Case)
115	| Lowercase s	| =CHAR(115) | 	s	| Letters (Lower Case)
116	| Lowercase t	| =CHAR(116) | 	t	| Letters (Lower Case)
117	| Lowercase u	| =CHAR(117) | 	u	| Letters (Lower Case)
118	| Lowercase v	| =CHAR(118) | 	v	| Letters (Lower Case)
119	| Lowercase w	| =CHAR(119) | 	w	| Letters (Lower Case)
120	| Lowercase x	| =CHAR(120) | 	x	| Letters (Lower Case)
121	| Lowercase y	| =CHAR(121) | 	y	| Letters (Lower Case)
122	| Lowercase z	| =CHAR(122) | 	z	| Letters (Lower Case)
123	| Opening brace	| =CHAR(123) | 	{	| Special Characters
124	| Vertical bar	| =CHAR(124) |	\| | Special Characters
125	| Closing brace	| =CHAR(125) | 	}	| Special Characters
126	| Equivalency sign – tilde	| =CHAR(126) | 	~	| Special Characters
127	| Delete	| =CHAR(127) | 		| Special Characters
128	| Euro sign	| =CHAR(128) | 	€	| Special Characters
130	| Latin small letter f with hook	| =CHAR(130) | 	‚	| Special Characters
131	| Double low-9 quotation mark	| =CHAR(131) | 	ƒ	| Special Characters
132	| Horizontal ellipsis	| =CHAR(132) | 	„	| Special Characters
133	| Dagger	| =CHAR(133) | 	…	| Special Characters
134	| Double dagger	| =CHAR(134) | 	†	| Special Characters
135	| Modifier letter circumflex accent	| =CHAR(135) | 	‡	| Special Characters
137	| Per mille sign	| =CHAR(137) | 	‰	| Special Characters
138	| Latin capital letter S with caron	| =CHAR(138) | 	Š	| Special Characters
139	| Single left-pointing angle quotation	| =CHAR(139) | 	‹	| Special Characters
140	| Latin capital ligature OE	| =CHAR(140) | 	Œ	| Special Characters
142	| Latin capital letter Z with caron	| =CHAR(142) | 	Ž	| Special Characters
145	| Left single quotation mark	| =CHAR(145) | 	‘	| Special Characters
146	| Right single quotation mark	| =CHAR(146) | 	’	| Special Characters
147	| Left double quotation mark	| =CHAR(147) | 	“	| Special Characters
148	| Right double quotation mark	| =CHAR(148) | 	”	| Special Characters
149	| Bullet	| =CHAR(149) | 	•	| Special Characters
150	| En dash	| =CHAR(150) | 	–	| Special Characters
151	| Em dash	| =CHAR(151) | 	—	| Special Characters
152	| Small tilde	| =CHAR(152) | 	˜	| Special Characters
153	| Trade mark sign	| =CHAR(153) | 	™	| Special Characters
154	| Latin small letter S with caron	| =CHAR(154) | 	š	| Special Characters
155	| Single right-pointing angle quotation mark	| =CHAR(155) | 	›	| Special Characters
156	| Latin small ligature oe	| =CHAR(156) | 	œ	| Special Characters
158	| Latin small letter z with caron	| =CHAR(158) | 	ž	| Special Characters
159	| Latin capital letter Y with diaeresis	| =CHAR(159) | 	Ÿ	| Special Characters
160	| Non-breaking space	| =CHAR(160) | 		| Special Characters
161	| Inverted exclamation mark	| =CHAR(161) | 	¡	| Special Characters
162	| Cent sign	| =CHAR(162) | 	¢	| Special Characters
163	| Pound sign	| =CHAR(163) | 	£	| Special Characters
164	| Currency sign	| =CHAR(164) | 	¤	| Special Characters
165	| Yen sign	| =CHAR(165) | 	¥	| Special Characters
166	| Pipe, Broken vertical bar	| =CHAR(166) | 	¦	| Special Characters
167	| Section sign	| =CHAR(167) | 	§	| Special Characters
168	| Spacing diaeresis – umlaut	| =CHAR(168) | 	¨	| Special Characters
169	| Copyright sign	| =CHAR(169) | 	©	| Special Characters
170	| Feminine ordinal indicator	| =CHAR(170) | 	ª	| Special Characters
171	| Left double angle quotes	| =CHAR(171) | 	«	| Special Characters
172	| Not sign	| =CHAR(172) | 	¬	| Special Characters
173	| Soft hyphen	| =CHAR(173) | 	­	| Special Characters
174	| Registered trade mark sign	| =CHAR(174) | 	®	| Special Characters
175	| Spacing macron – overline	| =CHAR(175) | 	¯	| Special Characters
176	| Degree sign	| =CHAR(176) | 	°	| Special Characters
177	| Plus-or-minus sign	| =CHAR(177) | 	±	| Special Characters
178	| Superscript two – squared	| =CHAR(178) | 	²	| Special Characters
179	| Superscript three – cubed	| =CHAR(179) | 	³	| Special Characters
180	| Acute accent – spacing acute	| =CHAR(180) | 	´	| Special Characters
181	| Micro sign	| =CHAR(181) | 	µ	| Special Characters
182	| Pilcrow sign – paragraph sign	| =CHAR(182) | 	¶	| Special Characters
183	| Middle dot – Georgian comma	| =CHAR(183) | 	·	| Special Characters
184	| Spacing cedilla	| =CHAR(184) | 	¸	| Special Characters
185	| Superscript one	| =CHAR(185) | 	¹	| Special Characters
186	| Masculine ordinal indicator	| =CHAR(186) | 	º	| Special Characters
187	| Right double angle quotes	| =CHAR(187) | 	»	| Special Characters
188	| Fraction one quarter	| =CHAR(188) | 	¼	| Special Characters
189	| Fraction one half	| =CHAR(189) | 	½	| Special Characters
190	| Fraction three quarters	| =CHAR(190) | 	¾	| Special Characters
191	| Inverted question mark	| =CHAR(191) | 	¿	| Special Characters
192	| Latin capital letter A with grave	| =CHAR(192) | 	À	| Upper Case Latin-1 Letters
193	| Latin capital letter A with acute	| =CHAR(193) | 	Á	| Upper Case Latin-1 Letters
194	| Latin capital letter A with circumflex	| =CHAR(194) | 	Â	| Upper Case Latin-1 Letters
195	| Latin capital letter A with tilde	| =CHAR(195) | 	Ã	| Upper Case Latin-1 Letters
196	| Latin capital letter A with diaeresis	| =CHAR(196) | 	Ä	| Upper Case Latin-1 Letters
197	| Latin capital letter A with ring above	| =CHAR(197) | 	Å	| Upper Case Latin-1 Letters
198	| Latin capital letter AE	| =CHAR(198) | 	Æ	| Upper Case Latin-1 Letters
199	| Latin capital letter C with cedilla	| =CHAR(199) | 	Ç	| Upper Case Latin-1 Letters
200	| Latin capital letter E with grave	| =CHAR(200) | 	È	| Upper Case Latin-1 Letters
201	| Latin capital letter E with acute	| =CHAR(201) | 	É	| Upper Case Latin-1 Letters
202	| Latin capital letter E with circumflex	| =CHAR(202) | 	Ê	| Upper Case Latin-1 Letters
203	| Latin capital letter E with diaeresis	| =CHAR(203) | 	Ë	| Upper Case Latin-1 Letters
204	| Latin capital letter I with grave	| =CHAR(204) | 	Ì	| Upper Case Latin-1 Letters
205	| Latin capital letter I with acute	| =CHAR(205) | 	Í	| Upper Case Latin-1 Letters
206	| Latin capital letter I with circumflex	| =CHAR(206) | 	Î	| Upper Case Latin-1 Letters
207	| Latin capital letter I with diaeresis	| =CHAR(207) | 	Ï	| Upper Case Latin-1 Letters
208	| Latin capital letter ETH	| =CHAR(208) | 	Ð	| Upper Case Latin-1 Letters
209	| Latin capital letter N with tilde	| =CHAR(209) | 	Ñ	| Upper Case Latin-1 Letters
210	| Latin capital letter O with grave	| =CHAR(210) | 	Ò	| Upper Case Latin-1 Letters
211	| Latin capital letter O with acute	| =CHAR(211) | 	Ó	| Upper Case Latin-1 Letters
212	| Latin capital letter O with circumflex	| =CHAR(212) | 	Ô	| Upper Case Latin-1 Letters
213	| Latin capital letter O with tilde	| =CHAR(213) | 	Õ	| Upper Case Latin-1 Letters
214	| Latin capital letter O with diaeresis	| =CHAR(214) | 	Ö	| Upper Case Latin-1 Letters
215	| Multiplication sign	| =CHAR(215) | 	×	| Upper Case Latin-1 Letters
216	| Latin capital letter O with slash	| =CHAR(216) | 	Ø	| Upper Case Latin-1 Letters
217	| Latin capital letter U with grave	| =CHAR(217) | 	Ù	| Upper Case Latin-1 Letters
218	| Latin capital letter U with acute	| =CHAR(218) | 	Ú	| Upper Case Latin-1 Letters
219	| Latin capital letter U with circumflex	| =CHAR(219) | 	Û	| Upper Case Latin-1 Letters
220	| Latin capital letter U with diaeresis	| =CHAR(220) | 	Ü	| Upper Case Latin-1 Letters
221	| Latin capital letter Y with acute	| =CHAR(221) | 	Ý	| Upper Case Latin-1 Letters
222	| Latin capital letter THORN	| =CHAR(222) | 	Þ	| Upper Case Latin-1 Letters
223	| Latin small letter sharp s – ess-zed	| =CHAR(223) | 	ß	| Lower Case Latin-1 Letters
224	| Latin small letter a with grave	| =CHAR(224) | 	à	| Lower Case Latin-1 Letters
225	| Latin small letter a with acute	| =CHAR(225) | 	á	| Lower Case Latin-1 Letters
226	| Latin small letter a with circumflex	| =CHAR(226) | 	â	| Lower Case Latin-1 Letters
227	| Latin small letter a with tilde	| =CHAR(227) | 	ã	| Lower Case Latin-1 Letters
228	| Latin small letter a with diaeresis	| =CHAR(228) | 	ä	| Lower Case Latin-1 Letters
229	| Latin small letter a with ring above	| =CHAR(229) | 	å	| Lower Case Latin-1 Letters
230	| Latin small letter ae	| =CHAR(230) | 	æ	| Lower Case Latin-1 Letters
231	| Latin small letter c with cedilla	| =CHAR(231) | 	ç	| Lower Case Latin-1 Letters
232	| Latin small letter e with grave	| =CHAR(232) | 	è	| Lower Case Latin-1 Letters
233	| Latin small letter e with acute	| =CHAR(233) | 	é	| Lower Case Latin-1 Letters
234	| Latin small letter e with circumflex	| =CHAR(234) | 	ê	| Lower Case Latin-1 Letters
235	| Latin small letter e with diaeresis	| =CHAR(235) | 	ë	| Lower Case Latin-1 Letters
236	| Latin small letter i with grave	| =CHAR(236) | 	ì	| Lower Case Latin-1 Letters
237	| Latin small letter i with acute	| =CHAR(237) | 	í	| Lower Case Latin-1 Letters
238	| Latin small letter i with circumflex	| =CHAR(238) | 	î	| Lower Case Latin-1 Letters
239	| Latin small letter i with diaeresis	| =CHAR(239) | 	ï	| Lower Case Latin-1 Letters
240	| Latin small letter eth	| =CHAR(240) | 	ð	| Lower Case Latin-1 Letters
241	| Latin small letter n with tilde	| =CHAR(241) | 	ñ	| Lower Case Latin-1 Letters
242	| Latin small letter o with grave	| =CHAR(242) | 	ò	| Lower Case Latin-1 Letters
243	| Latin small letter o with acute	| =CHAR(243) | 	ó	| Lower Case Latin-1 Letters
244	| Latin small letter o with circumflex	| =CHAR(244) | 	ô	| Lower Case Latin-1 Letters
245	| Latin small letter o with tilde	| =CHAR(245) | 	õ	| Lower Case Latin-1 Letters
246	| Latin small letter o with diaeresis	| =CHAR(246) | 	ö	| Lower Case Latin-1 Letters
247	| Division sign	| =CHAR(247) | 	÷	| Lower Case Latin-1 Letters
248	| Latin small letter o with slash	| =CHAR(248) | 	ø	| Lower Case Latin-1 Letters
249	| Latin small letter u with grave	| =CHAR(249) | 	ù	| Lower Case Latin-1 Letters
250	| Latin small letter u with acute	| =CHAR(250) | 	ú	| Lower Case Latin-1 Letters
251	| Latin small letter u with circumflex	| =CHAR(251) | 	û	| Lower Case Latin-1 Letters
252	| Latin small letter u with diaeresis	| =CHAR(252) | 	ü	| Lower Case Latin-1 Letters
253	| Latin small letter y with acute	| =CHAR(253) | 	ý	| Lower Case Latin-1 Letters
254	| Latin small letter thorn	| =CHAR(254) | 	þ	| Lower Case Latin-1 Letters
255	| Latin small letter y with diaeresis	| =CHAR(255) | 	ÿ	| Lower Case Latin-1 Letters
