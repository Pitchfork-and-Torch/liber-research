# Liber Primus word-as-unit book-cipher pass 1

Date: 2026-08-14 (America/New_York)
Worker: executor subagent
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo. Linux box only. No public post.
Honesty rail: no claimed solve. Isolated book words (THE, A, YOU) are contamination.
Method: each ciphertext *word* (rtkd delimiter `-`) is a coordinate into solved
LP1 *English words*, as (page, word) or (word-in-book).
Not used: letter indexes, Gematria prime-sum indexes, running-key, periodic
Vigenere, columnar, SHA-512, YOUR INNOCENCE, INSTAR JPEGs.
Reuse: GP / page split / LP1 decrypts from `lp_analyze.py`,
`liber-bookcipher-pass1.py`, `lp_bookcipher_core.py`.
Script: `box-only word-unit runner (not in this repo)` (audit JSON: `box-only word-unit audit (not in this repo)`).

## 1. Parse and split

Runes = 29-letter Gematria Primus. Word break = `-` (also `. & $ sect / %`, so a
line-break does not glue two words).
GP order: `F U TH O R C G W H N I J EO P X S T B E M L NG OE D A AE Y IA EA`.
1-based first/last-rune-index = GP index + 1 (F=1 ... EA=29).

rtkd raw `%-parts`: 74 -> 73 content parts after dropping a trailing section-mark.
`parse_pages` from `lp_analyze.py` keeps 72 rune-bearing pages (drops the hex-only part).

| Block | rtkd parts | Count | Notes |
|---|---|---|---|
| LP1 solved rune pages | 0-14 | 15 | WARNING, WELCOME, WISDOM, KOAN, LOSS OF DIVINITY, INSTRUCTION |
| LP2 0-55 unsolved | 15-70 | 56 | one page is hex-only, 0 runes / 0 words |
| LP2 56 AN END | 71 | 1 | totient (c-(p-1)) mod 29; 85 runes |
| LP2 57 PARABLE | 72 | 1 | direct gematria |

Unsolved LP2 0-55: 55 rune-bearing pages, **12956 runes**, **3316 words**,
IOC29 = **0.03448** (flat / 1/29).
Word lengths: min=1 median=3 max=14; <=8: 3184/3316; <=13 (book page count): 3314/3316.
Almost every unsolved word-length is a legal page number in a 13-page book.
That is why in-range lookups are cheap and not evidence.

## 2. Known-method calibration (must pass)

| Target | Method | ok | n runes / words | preview |
|---|---|---|---|---|
| A_WARNING | Atbash 28-i on rtkd[0] | True | 184 / 50 | A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE |
| WELCOME | Vigenere DIVINITY **no-skip-F** on rtkd[1] only | True | 251 / 70 | WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ OLN FM DA FRS EEA THE |
| AN_END | totient (c-(p-1)) mod 29; 85 runes so skip-202 is a no-op | True | 85 / 28 | AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OOE TAXTHT |
| PARABLE | direct Gematria Primus | True | 95 / 23 | PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND |

All four titles replay from this transcription: **True**.

Notes vs requested operators:

- Atbash 28-i on rtkd[0] -> A WARNNG / BELIEUE / BOOC / CNOW (GP spelling of WARNING).
- Vigenere DIVINITY **skip-every-F** on rtkd[1] -> WELCOF (fail). The 6th rune is F
  and must consume the key to become M. **No-skip-F** -> WELCOME WELCOME PILGRIM
  TO THE GREAT JOURNEY TOWARD THE END, then the page goes to garbage
  (`OG HFJ OLN...`). rtkd[2] under the same key is garbage (1/70 dictionary hits).
- AN END is 85 runes. scream314 skip-F-at-202 does not apply. `(c-(p-1)) mod 29`
  with no F-skip reproduces AN END / DEEP WEB / HASHES TO. totient-every-F is
  the weaker / wrong variant (breaks at HASHES).
- PARABLE is direct gematria (LICE = LIKE; TUNNELNG = TUNNELING).

Known pages are Atbash / Vigenere DIVINITY / totient / direct. They are **not**
a word-unit book cipher. The next section asks whether they *could* be, by
feeding their ciphertext words into the LP1 book.

## 3. LP1 book (calibrated English words only)

Book used for lookups: **13 pages, 675 words** (GP orthography, not a canned paste).
First 24: `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX`

Per-page decode is book-building only. It is not applied to LP2 0-55.
Koan pages are included only when they decrypt to readable English; garbage is skipped.

| rtkd | section | method | hits/words | keep | preview |
|---|---|---|---|---|---|
| 00 | WARNING | atbash | 43/50 | INCLUDE | A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE |
| 01 | WELCOME | vig-DIVINITY-noskipF | 9/70 | INCLUDE (opening only is English) | WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ... |
| 02 | WELCOME-cont | vig-DIVINITY-noskipF | 1/70 | **SKIP** | AET AETH TRBXNGH BYF PARNGRAEG... |
| 03 | WISDOM | direct | 15/34 | INCLUDE | SOME WISDOM THE PRIMES ARE SAC RED THE TOTIENT FUNCTIAN IS SA CRED |
| 04 | KOAN | atbash-caesar3 | 50/68 | INCLUDE | A COAN A MAN DECIDED TO GO AND STUDY WITH A MASTE R HE WENT TO THE DOOR |
| 05 | KOAN | atbash-caesar3 | 43/63 | INCLUDE | D AGAIN THE MAN THOUGHT FOR A MOMENT AND REPLIED I AM A PROFESSOR |
| 06 | KOAN | atbash-caesar3 | 39/63 | INCLUDE | O ARE YOU WHO WISHES TO STUDY HERE ASCED THE MASTE R AGAIN AFTER |
| 07 | KOAN | atbash-caesar3 | 22/40 | INCLUDE | BUT HE COULD NOT THINC OF ANYTHNG ELSE TO SAY SO HE TRA ILED OFF |
| 08 | LOSS OF DIVINITY | direct | 24/44 | INCLUDE | THE LOSS OF DIUINITY THE CIRCU MFERENCE PRACTICES THRE E BEHAUIARS |
| 09 | LOSS OF DIVINITY | direct | 47/60 | INCLUDE | WE HAUE WHAT WE HAUE N OW BY LUCC AND WE WILL NOT BE STRONG ENOUGH |
| 10 | LOSS OF DIVINITY | direct | 42/52 | INCLUDE | MOST THNGS ARE NOT WORTH PRESERU NG ADHERENCE WE FOLLOW DOGMA |
| 11 | LOSS OF DIVINITY | direct | 32/42 | INCLUDE | CE THAT HAUE US LOSE OUR PRIMAL ITY AND THUS OUR DIUINITY SOME WISDOM |
| 12 | KOAN2 | vig-FIRFUMFERENFE-noskip | 15/70 | INCLUDE (opening; tail is garbage) | A COAN DURNG A LESSON THE MAS TER EXPLAINED THE I THE I IS THE UOICE |
| 13 | KOAN2 | atbash-caesar3 | 1/27 | **SKIP** | EEOE FA EOYNGHAOEC OOEW YWOR JR... |
| 14 | INSTRUCTION | direct | 17/19 | INCLUDE | AN INSTRUCTIAN CWESTIAN ALL THNGS DISCOUER TRUTH INSIDE YOURSELF FOLLO |

rtkd[2] and rtkd[13] are garbage and are not in the book.
rtkd[1] and rtkd[12] have a clean opening and a garbage tail; the whole decoded
token list was kept for the run (675 words). That makes contamination *easier*,
not harder: more English tokens to hit by chance. Calibration still failed.

A 675-word English book makes THE / A / YOU / WELCOME / KOAN cheap hits.
Any in-range coordinate can land on a function word. That is not a solve.

## 4. Word-unit scheme calibration (the method itself)

Question: using a *solved* page's ciphertext words as coordinates into the LP1
book, does any scheme recover **that page's own title**
(A WARNING / WELCOME / AN END / PARABLE)?

If not, the scheme fails as a method. Isolated book words do not count.
Recovering a *different* title because the book contains WELCOME twice at the
start of page 1 is contamination, not calibration.

Schemes (word-level features only - no gematria sums, no letter streams):

1. `(len, 1-based first-rune-index)` -> (LP1 page, word-on-page); also word-in-book = first-index or `len*29+first`
2. `(len, 1-based last-rune-index)` -> (page, word); also word-in-book = last-index
3. successive pairs `(len1, len2)` -> (page, word); also overlapping pairs
4. `(word-count-so-far-on-page, len)` -> (page, word); also word-in-book = count
5. `(ciphertext page number, word-index)` -> LP1 page `p mod n`, word `i mod n_words`
6. DJUBEI pair DJU+BEI as a (page, word) crib; neighbors under `(len, first)`

Variants (structured, not a grind): 1-based/0-based x nowrap/mod.

### Echoes (not credited)

| variant | what it actually does |
|---|---|
| s5 `p mod n`, `i mod n_words` | reprints book page `p` in word order |
| s4 `book-count-1b` / `book-count-1b-mod` | word *i* -> book word *i* = the book from the start (A WARNNG BELIEUE...) |
| s1/s2 `book-first1b` / `book-last1b` | rune-index 1-29 -> first 29 words of A WARNING, which are all English |

Those three families always emit LP1 vocabulary. They are the burned
"small index into a short book" family with word-level coordinates.
They are **not** title recovery.

### Non-echo results on solved pages

| page | scheme | variant | own title? | longest English run | preview (first ~70) |
|---|---|---|---|---|---|
| A_WARNING | s1 | 1b-nowrap | no | 6 | FROM YOU HE THE STUDY OBSCURA MASTE MASTE WHO THE YO OG END |
| A_WARNING | s1 | book-first1b | echo | 18 | FROM EX TO YOUR O NOT TO CNOW EX BELIEUE YOUR BE TO BE BE NOT |
| A_WARNING | s3 | 1b-nowrap | no | 13 | FROM NOT A TO A COAN GRIM COAN EXCEPT MAN COAN DIUINITY WISDOM PRIMES |
| A_WARNING | s4 | 0b-nowrap | no (hits WELCOME) | 5 | WELCOME SAC AND THOUGHT WISHES NOT THE OW WORTH US LESSON... |
| A_WARNING | s4 | book-count-1b | echo | 16 | A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW |
| WELCOME | s1 | 1b-nowrap | no | 7 | HE THINC SOME THE EAGB LCIX THE SHADOWS TO A GRIM FORM WELCOME |
| WELCOME | s3 | overlap-1b | no | bag of KOAN/WELCOME | book words in cipher-driven order, not WELCOME WELCOME PILGRIM |
| AN_END | s3 | 1b-nowrap | no | 7 | PIL AGAIN A BELIEUE O A GRIM WELCOME WELCOME COAN THOUGHT WELCOME A PRIMES |
| AN_END | s1 | 1b-nowrap | no | 6 | LUOG AETHEREAL NOT GRIM TO THE TEST PRIMES THE TRUTH YO SAC |
| PARABLE | s1 | 1b-nowrap | no | 9 | ILED MASTER PIL MASTE C ARE DA PIL AFTER JOU THE TO PRIMES PRIMES |
| PARABLE | s3 | 1b-nowrap | no | 6 | NOT THE THIS WELCOME HE MAN THE BE A EXCEPT THE |

The one "WELCOME" opening on A_WARNING s4 0b-nowrap is `(count=1, len=1)` as
0-based `(1, 1)` = book page 1 word 1, which is the second WELCOME we put there.
That is a coordinate collision with a 13-page book, not A WARNING decrypting
as WELCOME.

The WELCOME WELCOME pair on AN_END s3 is the same collision: book page 1
starts WELCOME WELCOME, so any `(page, word)` pair that lands on (1, 0) and
(1, 1) reprints the title of a *different* page in the middle of a salad.

**No non-echo variant recovered a page's own title from that page's ciphertext words.**

Scheme-level own-title recovery: s1=False, s2=False, s3=False, s4=False, s5=echo.
**Word-unit scheme calibration: FAIL.**

Known pages remain Atbash / Vigenere / totient / direct. Treating their words
as (page, word) pointers into the LP1 book does not replay their titles.
The method is not calibrated.

## 5. Unsolved LP2 0-55 inventory (not a solve)

Same schemes, same book. Whole-stream = all 3316 unsolved words in rtkd order.
Per-page rows were kept only when a long dictionary-run or a title *string* appeared.

s1 whole-stream in-range (3316 coords):

| variant | in-range | miss | longest dict-run | why it is not a solve |
|---|---|---|---|---|
| 1b-nowrap | high (len <=13 almost always) | low | short | bag of book words; no 3301 sentence |
| 1b-mod | 3316/3316 | 0 | long | wrap reprints the short book |
| 0b-nowrap / 0b-mod | same pattern | | | same |
| book-first1b | 3316/3316 (indexes 1-29) | 0 | 18-34 | first 29 book words *are* A WARNING English |
| book-len29+first-1b | mostly miss without mod | | | out of range; mod = wrap echo |

Typical non-echo previews (s1 1b-nowrap stream) are shuffles of the book:
`FROM YOU HE THE STUDY OBSCURA MASTE...` - LP1 vocabulary in cipher-driven order.
That is a bag of known words, not a sentence.

A first-pass scorer that treated "8 dictionary words in a row" as success
reported hundreds of hits. Those runs are `DO KNOW KNOW BE KNOW YOUR KNOW THIS`
and `A WARNING BELIEVE NOTHING FROM THIS BOOK` from the echo variants.
They are **not** 3301 English. Isolated THE / A / YOU / KNOW / THIS in a
675-word book are contamination, as specified.

**Unsolved 8+ word stretch that is readable 3301 English: none.**
No PROGRAM YOUR MIND, no AN END WITHIN THE DEEP WEB, no LIKE THE INSTAR,
no BELIEVE NOTHING FROM THIS BOOK except as a book-order echo.

## 6. DJUBEI pair crib

DJU+BEI is a real *word pair* (rtkd `-`), not only a 6-gram, in two places:

| kind | LP2 | rtkd | words | neighbors (Latin ciphertext) |
|---|---|---|---|---|
| word-pair + 6-gram | 27 | 42 | i=6,7 DJU BEI | N HGUIAHU BF \| DJU BEI \| AEF P AEPTH |
| word-pair + 6-gram | 55 | 70 | i=17,18 DJU BEI | THOE CEAIM CX \| DJU BEI \| (end of page) |

Crib coordinates tried: `(len,len)=(3,3)`, `(len, first of BEI)`,
`(first, first)`, `(first, len)`, `(len, last)`. Neighbors looked up with
scheme 1 `(len, first)`. 1b/0b x nowrap/mod.

Best neighbor run: **4** words (`QUESTION YOU THE SAY` on LP2 27, 0b-mod).
That is four book tokens, not a sentence. LP2 55 has no right-hand neighbors
(pair is at end of page).

**DJUBEI-neighbor 8+ word English: none.**
DJUBEI remains a repeated 6-gram / two-word crib. It is not a (page, word) key.

## 7. What would have counted

Success required either:

- a stretch of **8+ recovered words** that is 3301 English (readable Cicada prose,
  not THE/A/YOU contamination and not a book-order reprint), or
- a **title recovery on a solved page** (that page's own title, non-echo)
  **plus** readable unsolved English.

Neither bar was met.

Scheme 5 is tautological: it reprints an LP1 page in word order.
`book-count` and `book-first/last` (rune-index 1-29 into a 675-word book)
are the same small-index contamination the gematria-sum family already burned.
They were run as inventory and not credited.

## 8. Verdict

- Known-method calibration (A WARNING, WELCOME, AN END, PARABLE): **True**
- Word-unit scheme recovers a page's own title from that page's words: **False**
- Unsolved 8+ word 3301 English stretch: **False**
- DJUBEI-neighbor 8+ word English: **False**

The word-as-unit book cipher does not calibrate. Solved pages do not encrypt
their titles as (page, word) or word-in-book pointers into the LP1 English.
Unsolved 0-55 lookups return a bag of those book words. That is inventory,
not a break.

**VERDICT: FAIL: word-unit scheme did not recover a title from any solved page (A WARNING / WELCOME / AN END / PARABLE). Unsolved lookup is inventory only.**
