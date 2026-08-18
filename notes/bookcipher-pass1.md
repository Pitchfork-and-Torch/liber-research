# Liber Primus book-cipher pass 1

Date: 2026-08-14 (America/New_York)
Worker: executor subagent
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo. No other crib file.
Honesty rail: no claimed solve unless calibration replays A WARNING, WELCOME, AN END, PARABLE
and a book-cipher then yields a 29-rune IOC lift **and** new 3301-style English.
Not rerun on unsolved 0-55: Atbash, Caesar, totient, Vigenere DIVINITY / CIRCUMFERENCE,
LP1 running key, 15.jpg stream, page-0 column-read, skip-13.

## 1. Parse and split

Runes = the 29 Anglo-Saxon futhorc characters of Gematria Primus.
Delimiters: `-` word, `.` clause, `&` paragraph, `$` segment, `sect` chapter, `/` line, `%` page.

Gematria Primus order (indexes 0-28):
`F U TH O R C G W H N I J EO P X S T B E M L NG OE D A AE Y IA EA`
Atbash: `28-i`. Primes: `2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 101 103 107 109`.

The file has 73 `%` markers -> 74 raw parts. The last part is a lone `sect` and was dropped.
73 content parts remain. Onion LP1 00 (title) and LP1 02 (Chapter I Intus) are not in the rune stream.
rtkd therefore has 15 LP1 rune pages, not 17.

| Block | rtkd parts | Count | Notes |
|---|---|---|---|
| LP1 solved rune pages | 0-14 | 15 | WARNING, WELCOME, WISDOM, KOAN, LOSS OF DIVINITY, INSTRUCTION |
| LP2 0-55 unsolved | 15-70 | 56 | one page (rtkd 65) is hex-only, 0 runes |
| LP2 56 AN END | 71 | 1 | totient (c-(p-1)) mod 29; 85 runes, skip-202 is a no-op |
| LP2 57 PARABLE | 72 | 1 | direct gematria |

Unsolved LP2 0-55: 55 rune-bearing pages, 12956 runes, IOC29 = 0.03448 (flat / 1/29).

## 2. Calibration (must pass)

| Target | Method | ok | n | preview |
|---|---|---|---|---|
| A_WARNING | Atbash 28-i on rtkd[0] | True | 184 | A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE |
| WELCOME | Vigenere DIVINITY no-skip-F on rtkd[1-1] | True | 354 | WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ OLN FM DA FRS EEA THE |
| AN_END | totient (c-(p-1)) mod 29; page has 85 runes so skip-index-202 is a no-op | True | 85 | AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OOE TAXTHT  |
| PARABLE | direct Gematria Primus | True | 95 | PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND |

All four titles/openings replay from this transcription. Calibration passed.

Notes on the requested methods vs this file:
- Atbash 28-i on rtkd[0] -> A WARNNG / BELIEUE / BOOC / CNOW (GP spelling of WARNING).
- Vigenere DIVINITY **skip-every-F** on rtkd[1] -> WELCOF (fail). The 6th rune is F and
  must consume the key to become M. **No-skip-F** -> WELCOME WELCOME PILGRIM TO THE GREAT
  JOURNEY TOWARD THE END O... (51+ letters). Skip-every-F is not the operator on this page.
- AN END is 85 runes. scream314 skip-F-at-202 does not apply (no index 202).
  `(c-(p-1)) mod 29` with no F-skip reproduces AN END / DEEP WEB / HASHES TO.
  totient-every-F is the weaker / wrong variant, as specified.
- PARABLE is direct gematria (LICE = LIKE; TUNNELNG = TUNNELING).

## 3. LP1 book (solved English, decoded from rtkd)

Book size: 15 pages, 772 words, 3061 letters.
First words: A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX

Per-page decode used only to build the book (not applied to LP2 0-55):

- rtkd[00] `atbash` - A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE
- rtkd[01] `vig-DIVINITY-noskipF` - WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ O
- rtkd[02] `vig-DIVINITY-noskipF` - AET AETH TRBXNGH BYF PARNGRAEG NGO SIT OEC FHNYR OTLFECXR S IAEH OSB M
- rtkd[03] `direct` - SOME WISDOM THE PRIMES ARE SAC RED THE TOTIENT FUNCTIAN IS SA CRED ALL
- rtkd[04] `atbash-caesar-3 hits=38` - A COAN A MAN DECIDED TO GO AND STUDY WITH A MASTE R HE WENT TO THE DOO
- rtkd[05] `atbash-caesar-3 hits=34` - D AGAIN THE MAN THOUGHT FOR A MOMENT AND REPLIED I AM A PROFESSOR THAT
- rtkd[06] `atbash-caesar-3 hits=31` - O ARE YOU WHO WISHES TO STUDY HERE ASCED THE MASTE R AGAIN AFTER A MOM
- rtkd[07] `atbash-caesar-3 hits=13` - BUT HE COULD NOT THINC OF ANYTHNG ELSE TO SAY SO HE TRA ILED OFF AFTER
- rtkd[08] `direct` - THE LOSS OF DIUINITY THE CIRCU MFERENCE PRACTICES THRE E BEHAUIARS WHI
- rtkd[09] `direct` - WE HAUE WHAT WE HAUE N OW BY LUCC AND WE WILL NOT BE STRONG ENOUGH LAT
- rtkd[10] `direct` - MOST THNGS ARE NOT WORTH PRESERU NG ADHERENCE WE FOLLOW DOGMA SO THAT 
- rtkd[11] `direct` - CE THAT HAUE US LOSE OUR PRIMAL ITY AND THUS OUR DIUINITY SOME WISDOM 
- rtkd[12] `vig-FIRFUMFERENFE-noskip hits=10` - A COAN DURNG A LESSON THE MAS TER EXPLAINED THE I THE I IS THE UOICE O
- rtkd[13] `atbash-caesar-3 hits=1` - EEOE FA EOYNGHAOEC OOEW YWOR JR UINGTN FGAE LEOEOY WWOH AAU OEBU A EI 
- rtkd[14] `direct` - AN INSTRUCTIAN CWESTIAN ALL THNGS DISCOUER TRUTH INSIDE YOURSELF FOLLO

## 4. DJUBEI 6-grams in LP2 0-55

Target rune sequence D-J-U-B-E-I = indexes `23 11 1 17 18 10`.
Hits in unsolved 0-55: **2**.

| # | LP2 page | rtkd | rune offset | global | 10 runes left (Latin) | DJUBEI | 10 runes right (Latin) |
|---|---|---|---|---|---|---|---|
| 0 | 27 | 42 | 28 | 6555 | PNHGUIAHUBF | DJUBEI | AEFPAEPTHRMLC |
| 1 | 55 | 70 | 70 | 12950 | ESTHOECEAIMCX | DJUBEI |  |

Neighbor rune indexes and gematria primes (used as book-cipher coordinates):

- hit 0 LP2 27 off 28:
  - left idx [13, 9, 8, 6, 1, 27, 8, 1, 17, 0] primes [43, 29, 23, 17, 3, 107, 23, 3, 61, 2]
  - right idx [25, 0, 13, 25, 13, 2, 4, 19, 20, 5] primes [101, 2, 43, 101, 43, 5, 11, 71, 73, 13]
- hit 1 LP2 55 off 70:
  - left idx [18, 15, 2, 22, 5, 28, 10, 19, 5, 14] primes [67, 53, 5, 83, 13, 109, 31, 71, 13, 47]
  - right idx [] primes []

## 5. Book-cipher tests (small)

Book = LP1 solved English only. Coordinates from DJUBEI neighbors and from the 0-55 stream:
rune index (0-28), gematria prime, and those values mod book length.
Lookups: word; letter; (word, letter); (page, word, letter).
Also: unsolved word gematria-sums as word indexes; DJUBEI-neighbor values as a repeating
(word, letter) key over the whole 0-55 stream.

Scoring: 8+ letter English stretch, or 29-rune IOC lifting from ~0.0345 toward 0.06+.
IOC26 of letters sampled from an English book is ~0.06 **by construction** (source bias).
That is not a break of the 29-rune cipher. IOC29 of the raw 0-55 stream stayed ~0.0345.
Re-encoding looked-up English back onto GP also inherits English-on-29 IOC; that is the
same bias, not a lift of LP2. Sequential or mod-length pointers that reprint the book
are marked `echo` and are not a solve.

### 5a. Whole-stream 29-IOC after re-encoding book letters to GP

| trial | n | IOC29 | vs unsolved 0.0345 |
|---|---|---|---|
| u55-idx-letter-mod | 12356 | 0.06661 | source-bias if English book |
| u55-prime-letter-mod | 12215 | 0.09159 | source-bias if English book |
| u55-idx-WL-mod | 6142 | 0.06573 | source-bias if English book |
| u55-prime-WL-mod | 6279 | 0.07632 | source-bias if English book |
| u55-idx-PWL-mod | 4066 | 0.05408 | source-bias if English book |
| u55-gematria-sum-letter-mod | 3118 | 0.05629 | source-bias if English book |

### 5b. Trials with any 8+ letter stretch or 3301 phrase

Trials run: 72. With a stretch/phrase/high-IOC26: 33 (non-echo 33, book-echo 0).

| trial | n | IOC26 | stretches (first) | phrases | echo | preview |
|---|---|---|---|---|---|---|
| dj0-LP227-idx-word-0b | 81 | 0.06327 | TRUEYOUWHAT, EDITWHAT, FROMYOURTRUTHTHIS | - | False | TRUEYOUWHATBOOCWARNNGEDITWHATWARNNGNOWLE |
| dj0-LP227-idx-word-1b | 66 | 0.05967 | WHATEXCEPTTHIS, NOTEXCEPT, FINDYOURFROM | - | False | BEWHATEXCEPTTHISANOTEXCEPTACDEATHBEDEATH |
| dj0-LP227-idx-word-mod | 81 | 0.06327 | TRUEYOUWHAT, EDITWHAT, FROMYOURTRUTHTHIS | - | False | TRUEYOUWHATBOOCWARNNGEDITWHATWARNNGNOWLE |
| dj0-LP227-prime-word-0b | 106 | 0.08374 | THEIRTHIS | - | False | THEIRRYOURNOWLEDGENOTHNGONUYOURNOTHNGEND |
| dj0-LP227-prime-word-1b | 90 | 0.07765 | - | - | False | OROPERIENCECBELIEUECYRDJBOEDYPERIENCEBEL |
| dj0-LP227-prime-word-mod | 106 | 0.08374 | THEIRTHIS | - | False | THEIRRYOURNOWLEDGENOTHNGONUYOURNOTHNGEND |
| dj1-LP255-idx-word-0b | 43 | 0.06977 | NOWYOURTHISTEST | - | False | FINDTHEBELIEUEPERIENCETHISOCNOWYOURTHIST |
| dj1-LP255-idx-word-1b | 43 | 0.05537 | FROMEDITYOUFINDFROMTRUE | - | False | NOWLEDGETESTWARNNGEXFROMEDITYOUFINDFROMT |
| dj1-LP255-idx-word-mod | 43 | 0.06977 | NOWYOURTHISTEST | - | False | FINDTHEBELIEUEPERIENCETHISOCNOWYOURTHIST |
| u55-idx-letter-mod | 12956 | 0.07457 | - | - | False | OENRGGSAOINRNAEGHAEORLALNBHTOOUIRWLHGIAE |
| u55-idx-letter-0b | 12956 | 0.07457 | - | - | False | OENRGGSAOINRNAEGHAEORLALNBHTOOUIRWLHGIAE |
| u55-prime-letter-mod | 12956 | 0.10493 | - | - | False | TMWBHGNATTWUENTHEATUBONOWGTOTUTCUROEHCNM |
| u55-prime-letter-0b | 12956 | 0.10493 | - | - | False | TMWBHGNATTWUENTHEATUBONOWGTOTUTCUROEHCNM |
| u55-idx-word-mod-first | 12956 | 0.10763 | - | - | False | TWFNBYEATNFETBTBDATPNYBYFENDTPBCEWYDBCBW |
| u55-prime-word-mod-first | 12956 | 0.11302 | - | - | False | GYFENWOBGYFDTTWNBBWNERTRFYEIGNRTDNRBNTTY |
| u55-idx-word-mod | 51593 | 0.0768 | EXPERIENCE, EXPERIENCE, EXPERIENCE | - | False | THEWHATFINDNOTHNGBOOCYOUREDITATHENOTFIND |
| u55-prime-word-mod | 55901 | 0.07124 | - | - | False | GRIMYOURFRSEXCEPTNOWLEDGEWRFONUBELIEUEGR |
| u55-idx-WL-mod | 6478 | 0.07935 | - | - | False | EDCEEIITDTHLDNHBXOOEODOEIEEODABHCREEIHWO |
| u55-idx-WL-1b-mod | 6478 | 0.07351 | - | - | False | TWITEERNHNERGCEOTWHACNCTGTTEWHSTEBTTOPAU |
| u55-prime-WL-mod | 6478 | 0.08005 | - | - | False | MREUMRRNBNTHRNMDBRESDNDDHBIRSUWMWIBBNOGX |
| u55-idx-PWL-mod | 4318 | 0.0684 | - | - | False | AEAEEAOHEGIOSISTAATAORAEITARWIEAISANEDDU |
| u55-prime-PWL-mod | 4318 | 0.07327 | - | - | False | UGNIROOUHDTGDIHLYBCGNJWEAROUTACUNCHHLOCU |
| u55-idx-PWL-1b-mod | 4318 | 0.06884 | - | - | False | ENRBAEWLIETWEASWJWAYWEARWMBAYGNAAEHEITAA |
| u55-gematria-sum-word-mod | 13396 | 0.06374 | CONTAINED, CONTAINED, CONTAINED | WELCOME | False | YOURREPLIEDYBXTRBXNGHRDSTHNGSEFWBUOIDMEA |
| u55-gematria-sum-word-1b | 13596 | 0.06524 | CONTAINED, CONTAINED, CONTAINED | WELCOME | False | ONLYARELAEDUMRAETHWOMOSTJNGANALOGOSBAEAU |
| u55-gematria-sum-letter-mod | 3316 | 0.07099 | - | - | False | LEHTTARTHUCSDEBCWFCYNOCRNDEUNWDTSNCRETET |
| u55-wordlen-letter-mod | 3316 | 0.18673 | - | - | False | ENNRRENNRRNRGEAARRWGNEARWARRNARAANGNNWRN |
| u55-repkey-dj0-idx-as-word-ct-as-letter | 12956 | 0.08251 | - | - | False | EUACWTTWEADARDEERYRIEYAOWTHWEADAROREOUUT |
| u55-repkey-dj0-ct-as-word-idx-as-letter | 12956 | 0.09225 | - | - | False | HHFNOREAENIEHEOODATNOYEYIENEEPECXAODBWEH |
| u55-repkey-dj0-sum-letter-mod | 12956 | 0.07215 | - | - | False | BHILBNEWEIORNSTEOGCSTNIOGCHHEOTICIOSIOOE |
| u55-repkey-dj1-idx-as-word-ct-as-letter | 12956 | 0.09314 | - | - | False | DEEIIOWYSSNTURSONYSSDTLEIONYSSFHBEHOOUIT |
| u55-repkey-dj1-ct-as-word-idx-as-letter | 12956 | 0.08119 | - | - | False | TTNNOYIAETNXIEOBDAOCNYLOIPWHECBWENUDOWUA |
| u55-repkey-dj1-sum-letter-mod | 12956 | 0.07459 | - | - | False | XMFHEOTGFAPPBTTCEGTPRTNCMESOFPOHMMNTTOBO |

Neighbor-only dumps are 10-20 symbols. A short dump can spell a book word by chance
because the coordinates are small (0-28 or primes <=109) and the book is short.
Whole-stream word-mod lookups reprint LP1 vocabulary in cipher-driven order; that is
a bag of known words, not a sentence.

## 6. Verdict

- Real 29-rune IOC lift (not English-source bias): **False**
- New 3301 English (not a book echo): **False**

Neither bar was met. DJUBEI is still a repeated 6-gram crib, not a key.
Neighbor indexes / primes do not address a readable (page, word, letter) message in the LP1 book.
Using the unsolved stream as coordinates into that book does not produce 3301 English.

**VERDICT: FAIL: no IOC lift of the 29-rune stream and no new 3301 English (book-cipher pass 1)**
