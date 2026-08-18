# Liber Primus Playfair / two-square / four-square pass 1

Date: 2026-08-14 18:52 EDT
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo.
Parser/constants: reused from `box-only desk parser (not in this repo)` (`GP`, `LATIN`, `R2I`, `RUNESET`, `parse_pages`, `page_runes`, `ioc`, `to_latin`). Atbash / Vigenere / totient match `box-only columnar runner (not in this repo)`.
Method family: **Playfair, two-square (horizontal and vertical), four-square only**.
Not outguess. Not book-index. Not running-key. Not periodic Vigenere. Not columnar. Not word-unit. Not acrostic. Not homophonic/zkdecrypto. Not SHA-512. Not YOUR INNOCENCE. No sexagesimal, no line-acrostic, no hash grind. No public post. No INSTAR paste of LP pages.

Honesty rail: solved pages are Atbash / Vigenere DIVINITY / totient / direct - they are **not** Playfair. Decrypting A WARNING ciphertext with Playfair and expecting A WARNING is the wrong test. Success on the engine is: encrypt a full solved-page English with a crib keyword, decrypt with the same engine, title readable. Success on LP2 is readable 3301-style English and/or IOC lift of the decrypt toward English-on-29 (~0.06+). Score-only mush is FAIL. Isolated THE/OF or a 4-gram is not a solve. Seeing DJUBEI in ciphertext is not a decrypt.

---

## Grid (29-fit, documented)

Gematria Primus is 29 runes. Classic Playfair is 5x5 (25). Collapsing 29 to 25 would drop runes. That was not done.

Primary lane: **6 rows x 5 columns = 30 cells, one NULL pad** (sentinel index 29, not a GP rune). Fill is row-major: unique keyword runes first, then remaining GP 0..28 in alphabet order, NULL in the last empty cell (cell (5,4) for these short cribs).

Rules:

- Same letter pair: identity (leave unchanged). Classic encrypt inserts filler X (GP 14) between doubles and pads odd length; decrypt of a *real* stream does not insert fillers - it pairs as-is.
- NULL is a first-class 30th cell. Wrap is modulo 5 columns / 6 rows. Synthetic CT may contain the pad; it is stripped for the title check. Real LP2 CT has no pad.
- Same row / same column: shift +1 (encrypt) or -1 (decrypt) with wrap, landing on NULL if that is the next cell. Rectangle: other two corners (may be NULL).
- Two-square horizontal: first letter in left square, second in right. Same row -> shift in each square; else corners.
- Two-square vertical: same column -> shift in each square; else corners.
- Four-square: plaintext squares are sequential GP (empty keyword); ciphertext squares are key1 (top-right) and key2 (bottom-left).

Second lane (documented, not a silent collapse of the 29-rune grid): **Latin-after-GP (26)**. Each rune expands to its `LATIN` spelling (TH, EO, NG, OE, AE, IA, EA become two letters). Classic 5x5 Playfair, I=J, no hole. This lane exists because 29 is not a rectangle; it is not a substitute for the 6x5.

F / interrupter: two variants, both documented.

- `f_normal`: F (index 0) is a regular letter and is paired.
- `f_skip`: F is copied through unpaired (interrupter). Remaining letters are paired. Same rule on the Latin-26 lane for the letter F.

Pairing offset 0 and 1 (first kept letter left raw, then pairs). Odd leftover copied raw.

---

## Parser replay (not the Playfair test)

Known methods on this transcription, so the synthetic plaintext is real solved-page English.

### A_WARNING: ok=True

- method: Atbash p=28-c on parse_pages[0]
- n_runes: 184
- preview: `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX PERIENCE YOUR DEATH DO NOT EDIT O R CHANGE THIS BOOC OR THE MESSAGE CONTAINED WITHIN EITHER THE WO RDS OR THEI`

### WELCOME: ok=True

- method: Vigenere DIVINITY; skip F after index 47
- n_runes: 515
- preview: `WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EASY TRIP BUT FOR THOSE WHO FIND THEIR WAY HERE IT IS A NECESSARY ONE A LONG THE WAY YOU WILL FIND AN EN D TO AFNG NGYUBYSFE THAEU E`

### AN_END: ok=True

- method: totient skip F at 56
- n_runes: 85
- preview: `AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PILGR IM TO SEEC OUT THIS PAGE`

### PARABLE: ok=True

- method: direct Gematria Primus
- n_runes: 95
- preview: `PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND TH E DIUINITY WITHIN AND EMERGE`

PARSER_REPLAY True

---

## Engine self-test (the actual calibration)

Take full A WARNING plaintext (Atbash of parse_pages[0], 184 runes) and full PARABLE plaintext (direct parse_pages[71], 95 runes). Encrypt with a crib keyword. Decrypt with the same engine. Success = title readable (`AWARNNG` / `PARABLE`). Fillers may remain; that is classic Playfair. Latin-26 recovers `AWARNXNG` (X inserted between the double N that NG-expansion creates); title is readable after stripping the filler.

Trials: **50**. Recovered title: **50/50**.

| kind | lane | n | title-ok | sample back head |
|---|---|---|---|---|
| playfair29 | 29 | 14 | 14/14 | `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWH` |
| twosqH29 | 29 | 6 | 6/6 | `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWH` |
| twosqV29 | 29 | 6 | 6/6 | `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWH` |
| foursq29 | 29 | 6 | 6/6 | `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWH` |
| playfair26 | 26 | 6 | 6/6 | `AWARNXNGBELIEUENOTHNGFROMTHISBOXOCEXCEPT` |
| twosqH26 | 26 | 4 | 4/4 | `AWARNXNGBELIEUENOTHNGFROMTHISBOXOCEXCEPT` |
| twosqV26 | 26 | 4 | 4/4 | `AWARNXNGBELIEUENOTHNGFROMTHISBOXOCEXCEPT` |
| foursq26 | 26 | 4 | 4/4 | `AWARNXNGBELIEUENOTHNGFROMTHISBOXOCEXCEPT` |

ENGINE_SELFTEST True

Engine recovers its own synthetic. Titles readable. Calibration passes. Attack proceeds.

---

## Target

Unsolved LP2 0-55 rune stream = `parse_pages` indices 15..69. Hex-only rtkd page inside that span is dropped by the rune-page parser, so this is **55 rune pages**, **12956 runes**, raw IOC = **0.03448** (1/29 = 0.03448).

Latin-after-GP expansion: **16131** letters, raw IOC26 = **0.06874** (1/26 ~ 0.03846; English-on-26 ~ 0.066).

That 0.06874 is **expansion bias, not English**. TH/NG/EO/OE/AE/IA/EA runes inject T,H,N,G,E,O,A,I into a 26-letter stream, so monogram IOC already sits at English-ish before any decrypt. A 26-lane decrypt that lands at 0.05x is a **drop** from 0.06874, not a lift toward 0.06. Do not treat Latin-26 IOC as the success meter.

Work is in rune indexes / GP Latin, not UTF-8 bytes.

Same-letter ciphertext pairs (Playfair CT almost never has these if pairing is correct): **37** at offset 0, **49** at offset 1. That is evidence the raw 0-55 stream is not a standard Playfair ciphertext under either pairing, independent of key.

---

## DJUBEI pairing (not a decrypt)

DJUBEI = D J U B E I = indexes `[23, 11, 1, 17, 18, 10]`. Rune-stream hits at global **6555** and **12950**. Both are a 6-gram in the *ciphertext*. Seeing DJUBEI in CT is not a decrypt. The only question this pass can answer is whether Playfair pairing **glues** the 6-gram as three digraphs (DJ|UB|EI) or **splits** it (prev+D | JU | BE | I+next).

- hit 6555: offset0_glues=False, offset1_glues=True, skipF_offset0_glues=False, skipF_offset1_glues=True, n_nonF_before=6319. offset0 SPLITS (prev+D | JU | BE | I+next).
- hit 12950: offset0_glues=True, offset1_glues=False, skipF_offset0_glues=True, skipF_offset1_glues=False, n_nonF_before=12492. offset0 GLUES as DJ|UB|EI.

6555 is odd, so offset-0 stream pairing **splits** DJUBEI; offset-1 **glues** it. 12950 is even, so offset-0 **glues** it and offset-1 **splits** it. Both offsets were run. Neither treatment of the 6-gram is a plaintext claim.

---

## Attack

Keywords (Playfair, one square): A WARNING, WARNING, WELCOME, AN END, PARABLE, DIVINITY, CIRCUMFERENCE.
Two-square / four-square pairs: each title primary x second-square keywords DIVINITY / CIRCUMFERENCE / INSTAR, plus DIVINITY+CIRCUMFERENCE. INSTAR is a second-square keyword only. No new family.

Each key x {Playfair | two-square H | two-square V | four-square} x {F normal, F skip} x {offset 0, 1}. Same matrix on the Latin-26 lane. **440 trials** total.

### 29-rune lane

- trials: **220**
- IOC min / median / max: **0.03461 / 0.03566 / 0.03693**
- IOC >= 0.045: **0**. IOC >= 0.06: **0**
- readable 3301 (runs or 2+ titles or 3+ long cribs): **0**
- trials with any extra crib (not DJUBEI): **5** (all **COAN**, a 4-gram; same chance shorty the columnar pass already saw). Isolated THE/OF counts are TH-rune + E collisions, not English.

Top IOC (heads are mush):

| kind | key | skipF | off | IOC | extra cribs | head |
|---|---|---|---|---|---|---|
| twosqV | AWARNING+CIRCUMFERENCE | True | 0 | 0.03693 | [] | `HNDFEOIFLHMIAAENTHCYFHDUOUTHMGEOBHSG` |
| twosqV | WELCOME+CIRCUMFERENCE | True | 0 | 0.03687 | [] | `XJOEJCFOEHNGIBICTHMLFNALOUTHYEALXDPC` |
| playfair | WELCOME | True | 0 | 0.03683 | [] | `PIWCMWFEAXNGYDERIMBFNALJUIWOADXDSGOE` |
| playfair | WARNING | True | 1 | 0.03679 | [] | `SCLFEOLYFXIAPWJNGHCFEACDTHEANWOEIPRX` |
| playfair | CIRCUMFERENCE | True | 0 | 0.03679 | [] | `HNFTHEOCFOEHNGILIUTHFLFHDTHENEIEEOBH` |
| twosqV | WARNING+CIRCUMFERENCE | True | 0 | 0.03676 | [] | `HNDFEOIFLHMIWAENTHCYFHDUOUTHMGEOBHSG` |
| foursq | AWARNING+DIVINITY | True | 0 | 0.03669 | [] | `EEODCJNGFEABAENGCINPJYFXDHRHOOEISMOE` |
| playfair | AWARNING | True | 1 | 0.03666 | [] | `SCLFEOLYFXIAPAJNGHCFEACDTHEANAOEIXRP` |
| twosqV | PARABLE+CIRCUMFERENCE | True | 0 | 0.03666 | [] | `EOEOOFNIFNGHMITRBTHCYFEONGUOUTHFGLDE` |
| playfair | PARABLE | True | 1 | 0.03665 | [] | `SCTHFNNGYFJUTHEGFFYIDTHHOCOHRLJNGXEO` |
| foursq | AWARNING+INSTAR | True | 1 | 0.03663 | [] | `SXBGXOEYFTIAOELPCJPFIAHOHREOTTHFLETH` |
| twosqV | ANEND+CIRCUMFERENCE | True | 0 | 0.03663 | [] | `XJFNJCFLHMIBURWULFHAEROENHOELXDPCSEA` |

Skip-F is the high side of this band (~+0.002 over raw 0.03448). Same interrupter artifact as running-key / periodic. Not language.

### Latin-after-GP 26 lane

- trials: **220**
- IOC26 min / median / max: **0.04602 / 0.05068 / 0.05861**
- IOC26 >= 0.045: **220** (the expanded baseline is already 0.06874; this threshold is meaningless here). IOC26 >= 0.06: **0**
- readable 3301: **0**
- trials with any extra crib: **11** (KOAN/COAN 4-grams only; not a title, not a sentence).
- raw expanded IOC26 is **0.06874**; every decrypt is **below** that (max 0.05861). Not a lift.

Top IOC26 (heads are mush):

| kind | key | skipF | off | IOC | extra cribs | head |
|---|---|---|---|---|---|---|
| foursq | AWARNING+INSTAR | True | 1 | 0.05861 | [] | `SPGRLLEFCAZIBOICLBKAFFEUFRASPEIBGCAU` |
| playfair | ANEND | True | 1 | 0.05817 | [] | `SGDMHPGFEQXDEFHQGHCEFBGMDLDODANZNEQM` |
| playfair | CIRCUMFERENCE | True | 1 | 0.0581 | [] | `SGNPDUCFUKWAEHMOGRKEFIWPFQFQLEFZEUKP` |
| playfair | CIRCUMFERENCE | True | 0 | 0.05805 | [] | `QKFPLIUEFKSFEDIQLWENFFCPFPBQNRIPANQT` |
| foursq | DIVINITY+CIRCUMFERENCE | True | 1 | 0.05804 | [] | `SMHRMRAFIRGFBOKTMCOGFGERGSGCPBIZHIRR` |
| foursq | AWARNING+INSTAR | True | 0 | 0.05789 | [] | `SOGUFQEEFTYGEHFSPBPEFFBUGUDDMBGZKBRT` |
| foursq | WARNING+INSTAR | True | 1 | 0.05778 | [] | `SPGRLLEFCBZIBOICLBKAFFEUFRASPEIBFCBU` |
| playfair | ANEND | True | 0 | 0.05744 | [] | `TGDMEGCBFTXNAFIODHFBNFHPDMDRFDNXDBTM` |
| foursq | DIVINITY+CIRCUMFERENCE | True | 0 | 0.0574 | [] | `XLFUPBDGFYVHKLBCPBMGGFARFUETNHGZIHVQ` |
| foursq | WARNING+INSTAR | True | 0 | 0.05724 | [] | `SOGUFQEEFTYGEHFSPBPEGFBUGUDDMBGZKBRT` |
| foursq | WARNING+DIVINITY | True | 1 | 0.05704 | [] | `SPGRLMEFAWZIBOKCMBGFFGEUFTASPEICFAWU` |
| playfair | AWARNING | False | 1 | 0.05699 | [] | `SMBFAEZUGLSDIEBPMAEIGMATGSAPMIDVWNOT` |

---

## Verdict

**FAIL**

Calibration passed (parser replay True; engine self-test 50/50, titles readable on synthetic A WARNING and PARABLE). One pass on LP2 0-55 (12956 runes, IOC 0.03448). 29-lane 220 trials, IOC max **0.03693** (no lift to 0.06; readable=0). 26-lane 220 trials, IOC26 max **0.05861**, which is a drop from the expanded baseline 0.06874, not a lift. No 3301-style English sentence. The only extra cribs are COAN/KOAN 4-grams. Isolated THE/OF are TH-rune collisions. Score-only mush is FAIL. DJUBEI stays a ciphertext 6-gram; pairing glues or splits it by offset and is not a decrypt.

Do not recook this family with a longer crib list. Do not treat a lone 4-gram or isolated THE/OF as a solve. Do not invent a 5x5 collapse that drops runes and call it the same pass. Do not treat Latin-26 IOC near 0.06 as English (the raw expansion is already 0.06874). Do not paste LP pages or claimed plaintext to INSTAR.

No public post.

This report: `notes/playfair-pass1.md`
Numbers: `box-only Playfair numbers (not in this repo)`
Engine: `box-only Playfair runner (not in this repo)`
