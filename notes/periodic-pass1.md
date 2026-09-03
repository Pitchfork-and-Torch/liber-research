# Liber Primus periodic Vigenere / Beaufort pass 1

Date: 2026-08-14 (America/New_York)
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo.
Parser/constants: reused from `box-only desk parser (not in this repo)` (`GP`, `LATIN`, `R2I`, `RUNESET`, `parse_pages`, `page_runes`, `ioc`, `to_latin`) plus totient/Vigenere/Atbash matching `box-only book-cipher helpers (not in this repo)` / `box-only running-key runner (not in this repo)`.
Method family: periodic Vigenere `p=(c-k) mod 29` and Beaufort `p=(k-c) mod 29` only. Key recovered from English-on-29 frequencies (solved LP1 + AN END + PARABLE rune distribution) and/or a DJUBEI plaintext crib. No Wave 1, no book-index, no SHA-512, no YOUR INNOCENCE pad, no AN END/PARABLE running key.

## Calibration

Known methods replayed on this transcription. Attack proceeds only if all four pass.

### A_WARNING: ok=True

- method: Atbash (28-i) on rtkd[0] / parse_pages[0]
- n_runes: 184
- preview: `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX PERIENCE YOUR DEATH DO NOT EDIT O R CHANGE THIS BOOC OR THE MESSAGE CONTAINED WITHIN EITHER THE WO RDS OR THEI`
- note: GP spelling WARNNG/BELIEUE/NOTHNG/BOOC is the known plaintext, not a miss

### WELCOME: ok=True

- method: Vigenere DIVINITY; skip-every-F gives WELCOF; title works without skipping that F (no-skip)
- n_runes: 251
- preview: `WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ OLN FM DA FRS EEA THEAG WCNW WRF EAOAE THAEEAJ DUO LUOG EAGB HSL LCIX DB UN W AEAUTHTGETP NCTH AE JYR EA OHIA BYP DTTR LIDW IN RAE H TB HGL UOEULMGE IA`
- note: skip-every-F head=WELCOF; no-skip head=WELCOME. pages[1]+[2] no-skip starts `WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTO` then garbles (known INNOCENCE region / later F-interrupters). Title does not skip the F that is M.

### AN_END: ok=True

- method: totient (c-(p-1)) mod 29; skip only index 202 (no-op if n<=202)
- n_runes: 85
- preview: `AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OOE TAXTHT EAGETHM RN XEA NIEOEA EAAH IATHC JXREO`
- note: F positions=[35, 47, 51, 56, 74]. skip-202 is a no-op on this 85-rune page. skip-F@56 (if present) gives: AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY O

### PARABLE: ok=True

- method: direct Gematria Primus
- n_runes: 95
- preview: `PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND TH E DIUINITY WITHIN AND EMERGE`

CALIBRATION_PASS True

## Target

Unsolved LP2 0-55 = `parse_pages` indices 15..69 (hex-only rtkd page dropped by the rune-page parser). **12956 runes**, raw IOC = **0.03448** (1/29 = 0.03448).

DJUBEI = D J U B E I = indexes `[23, 11, 1, 17, 18, 10]` = `DJUBEI`. Hits at global **6555** and **12950**. Distance = 6395 = 5 x 1279. 7, 11, 29, 43 do **not** divide 6395, so Kasiski from this 6-gram does not nominate those periods.

- hit 6555: page-local context pre=`HGUIAHUBF` crib=`DJUBEI` post=`AEFPAEPTHRMLC`
- hit 12950: pre=`THOECEAIMCX` crib=`DJUBEI` post=`` (end of stream)
- non-F consume-index at 6555: 6319 (skip-F column = that mod L)
- non-F consume-index at 12950: 12492

## English-on-GP target distribution

Built from decrypted solved-page rune indexes (not Latin A-Z). Mixed corpus used for the 64-trial grid: n=2705, IOC=0.05577 (includes the half-garbled WELCOME page IOC 0.039 and CIRCUMFERENCE page IOC 0.039, and counts AN END twice: skip-202 and skip-F@56). Laplace +0.5 used only inside chi-squared; table is raw counts.

A cleaner subset (drop those two mixed pages, AN END once) is n=2143, IOC=**0.06186**. That cleaner distribution is what the synthetic self-test uses. It cannot change the LP2 verdict: column IOC is shift-invariant and already flat, so no target distribution can turn these columns into English.

Source pieces:

| piece | n | IOC | head |
|---|---|---|---|
| LP1-0-atbash | 184 | 0.06403 | `AWARNNGBELIEUENOTHNGFROMTHIS` |
| LP1-1-vig-DIVINITY-noskip | 251 | 0.03917 | `WELCOMEWELCOMEPILGRIMTOTH` |
| LP1-3-direct | 157 | 0.05251 | `SOMEWISDOMTHEPRIMESARESAC` |
| LP1-4-atbash-plus3 | 209 | 0.07090 | `ACOANAMANDECIDEDTOGOANDS` |
| LP1-5-atbash-plus3 | 210 | 0.06161 | `DAGAINTHEMANTHOUGHTFORAMOM` |
| LP1-6-atbash-plus3 | 218 | 0.06570 | `OAREYOUWHOWISHESTOSTUDYH` |
| LP1-7-atbash-plus3 | 141 | 0.05613 | `BUTHECOULDNOTTHINCOFANYTHNG` |
| LP1-8-direct | 187 | 0.06567 | `THELOSSOFDIUINITYTHECIRCUM` |
| LP1-9-direct | 207 | 0.06768 | `WEHAUEWHATWEHAUENOWBYLUC` |
| LP1-10-direct | 192 | 0.05874 | `MOSTTHNGSARENOTWORTHPRESERU` |
| LP1-11-direct | 169 | 0.05558 | `CETHATHAUEUSLOSEOURPRIMAL` |
| LP1-12-13-fir-noskip-p12 | 226 | 0.03925 | `ACOANDURNGALESSONTHEMASTER` |
| LP1-14-direct | 89 | 0.05746 | `ANINSTRUCTIANCWESTIANALLTHNG` |
| ANEND-totient-skip202noop | 85 | 0.05518 | `ANENDWITHINTHEDEEPWEBTHEREE` |
| ANEND-totient-skipF56 | 85 | 0.07003 | `ANENDWITHINTHEDEEPWEBTHEREE` |
| PARABLE-direct | 95 | 0.06271 | `PARABLELICETHEINSTARTUNNE` |

Ranked frequencies (raw, solved-page runes):

| rank | rune | idx | count | p |
|---|---|---|---|---|
| 1 | E | 18 | 326 | 0.1205 |
| 2 | O | 3 | 228 | 0.0843 |
| 3 | A | 24 | 179 | 0.0662 |
| 4 | R | 4 | 177 | 0.0654 |
| 5 | S | 15 | 164 | 0.0606 |
| 6 | T | 16 | 161 | 0.0595 |
| 7 | N | 9 | 153 | 0.0566 |
| 8 | I | 10 | 141 | 0.0521 |
| 9 | U | 1 | 125 | 0.0462 |
| 10 | TH | 2 | 107 | 0.0396 |
| 11 | D | 23 | 102 | 0.0377 |
| 12 | W | 7 | 93 | 0.0344 |
| 13 | L | 20 | 91 | 0.0336 |
| 14 | C | 5 | 88 | 0.0325 |
| 15 | H | 8 | 83 | 0.0307 |
| 16 | M | 19 | 81 | 0.0299 |
| 17 | Y | 26 | 71 | 0.0262 |
| 18 | B | 17 | 55 | 0.0203 |
| 19 | P | 13 | 47 | 0.0174 |
| 20 | F | 0 | 44 | 0.0163 |
| 21 | G | 6 | 43 | 0.0159 |
| 22 | NG | 21 | 31 | 0.0115 |
| 23 | EA | 28 | 27 | 0.0100 |
| 24 | IA | 27 | 22 | 0.0081 |
| 25 | J | 11 | 19 | 0.0070 |
| 26 | X | 14 | 18 | 0.0067 |
| 27 | AE | 25 | 17 | 0.0063 |
| 28 | EO | 12 | 6 | 0.0022 |
| 29 | OE | 22 | 6 | 0.0022 |

## Self-test of the recovery method

If chi-squared / correlation cannot recover a known periodic key on clean English-on-29, it cannot be trusted on LP2. Three classes: a mixed real page, clean monoalphabetic pages, and a synthetic Vigenere/Beaufort of the clean solved-page stream.

### WELCOME page, Vigenere period 8 (true key DIVINITY = DIUINITY) - does not recover

This is a negative control, not a method failure. Known-key no-skip decrypt of parse_pages[1] has IOC 0.03917 (not English). The title is WELCOME; the rest of the 251-rune page garbles under a single no-skip DIVINITY (later F-interrupters). Column IOC under the true period is mixed [0.05242, 0.05645, 0.03024, 0.03871, 0.03011, 0.04516, 0.04086, 0.04301]. Frequency recovery on that mixed page:

- recovered chi2 key: `AEIIAIIIII` match 3/8
- recovered corr key: `NIOAIATI` match 2/8
- decrypt contains WELCOME: False
- decrypt head: `CEDCTHMADTLHOEEMYEGWI`
- chi2 margins: [6.642, 32.729, 4.857, 4.004, 6.26, 4.484, 12.586, 7.799] (small vs synthetic below)

Do not read this as "the engine cannot find DIVINITY". It cannot find a period-8 key on a page that is not period-8 English.

### Clean monoalphabetic pages - recovers

- A WARNING ciphertext, Beaufort period 1 (Atbash = k=28): k_chi2=28 k_corr=28 margin_chi2=130.13. Decrypt head `AWARNNGBELIEUENOTHNGFROMTHIS`. Page IOC 0.06403.
- PARABLE (already plaintext), Vigenere period 1: k_chi2=0 k_corr=0 margin=170.93. Identity key recovered.
- A WARNING plaintext, Vigenere period 1: k_chi2=0 k_corr=0 margin=451.88.

### Synthetic Vigenere / Beaufort of the clean solved stream - recovers DIVINITY 8/8

Clean solved-page runes only (drop the mixed WELCOME and CIRCUMFERENCE pages; AN END once via totient skip-F@56): n=2143, IOC=0.06186 (true English-on-29).

Encrypt that stream with repeating DIVINITY (`[23, 10, 1, 10, 9, 10, 16, 26]`):

- synthetic Vigenere CT IOC=0.04144 (period mixes the alphabet, as it should)
- column IOC at L=8: [0.07239, 0.06188, 0.06048, 0.05897, 0.06370, 0.05822, 0.06431, 0.05900] - all English-like
- chi2 key = corr key = `[23, 10, 1, 10, 9, 10, 16, 26]` = DIUINITY, 8/8
- chi2 margins: [1329, 2090, 2767, 1673, 1892, 2550, 1666, 1679] (orders of magnitude above the WELCOME-page margins)
- decrypt head: `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWHATYOUCNOWTOB`
- synthetic Beaufort with the same key: also 8/8

So the frequency engine does recover a period-8 Vigenere/Beaufort key when the plaintext is English-on-29. LP2 0-55 is not that.

## Kasiski / column IOC

Wave 1 reported mean column IOC ~0.0347 for periods 2-40. Confirmed here, and extended to 43. Column IOC is shift-invariant: it does not depend on Vigenere vs Beaufort. A correct period on English-on-29 should lift each column toward ~0.06. Column IOC lift alone is not a solve.

### Periods 2-40 and 43, no-skip (full stream)

| L | col n | mean IOC | min | max | n>=0.045 | n>=0.055 |
|---|---|---|---|---|---|---|
| 2 | 6478-6478 | 0.03448 | 0.03448 | 0.03449 | 0 | 0 |
| 3 | 4318-4319 | 0.03450 | 0.03442 | 0.03460 | 0 | 0 |
| 4 | 3239-3239 | 0.03451 | 0.03441 | 0.03456 | 0 | 0 |
| 5 | 2591-2592 | 0.03451 | 0.03438 | 0.03468 | 0 | 0 |
| 6 | 2159-2160 | 0.03451 | 0.03428 | 0.03476 | 0 | 0 |
| 7 | 1850-1851 | 0.03458 | 0.03448 | 0.03474 | 0 | 0 |
| 8 | 1619-1620 | 0.03453 | 0.03433 | 0.03477 | 0 | 0 |
| 9 | 1439-1440 | 0.03441 | 0.03407 | 0.03471 | 0 | 0 |
| 10 | 1295-1296 | 0.03456 | 0.03427 | 0.03480 | 0 | 0 |
| 11 | 1177-1178 | 0.03450 | 0.03406 | 0.03501 | 0 | 0 |
| 12 | 1079-1080 | 0.03454 | 0.03397 | 0.03535 | 0 | 0 |
| 13 | 996-997 | 0.03457 | 0.03427 | 0.03523 | 0 | 0 |
| 14 | 925-926 | 0.03461 | 0.03415 | 0.03490 | 0 | 0 |
| 15 | 863-864 | 0.03471 | 0.03429 | 0.03529 | 0 | 0 |
| 16 | 809-810 | 0.03455 | 0.03404 | 0.03525 | 0 | 0 |
| 17 | 762-763 | 0.03437 | 0.03391 | 0.03495 | 0 | 0 |
| 18 | 719-720 | 0.03452 | 0.03381 | 0.03534 | 0 | 0 |
| 19 | 681-682 | 0.03444 | 0.03396 | 0.03498 | 0 | 0 |
| 20 | 647-648 | 0.03463 | 0.03397 | 0.03531 | 0 | 0 |
| 21 | 616-617 | 0.03452 | 0.03380 | 0.03548 | 0 | 0 |
| 22 | 588-589 | 0.03450 | 0.03351 | 0.03529 | 0 | 0 |
| 23 | 563-564 | 0.03453 | 0.03375 | 0.03528 | 0 | 0 |
| 24 | 539-540 | 0.03452 | 0.03376 | 0.03541 | 0 | 0 |
| 25 | 518-519 | 0.03462 | 0.03387 | 0.03554 | 0 | 0 |
| 26 | 498-499 | 0.03465 | 0.03380 | 0.03602 | 0 | 0 |
| 27 | 479-480 | 0.03422 | 0.03328 | 0.03533 | 0 | 0 |
| 28 | 462-463 | 0.03474 | 0.03329 | 0.03611 | 0 | 0 |
| 29 | 446-447 | 0.03451 | 0.03345 | 0.03562 | 0 | 0 |
| 30 | 431-432 | 0.03481 | 0.03346 | 0.03613 | 0 | 0 |
| 31 | 417-418 | 0.03453 | 0.03325 | 0.03532 | 0 | 0 |
| 32 | 404-405 | 0.03462 | 0.03351 | 0.03619 | 0 | 0 |
| 33 | 392-393 | 0.03449 | 0.03344 | 0.03577 | 0 | 0 |
| 34 | 381-382 | 0.03445 | 0.03328 | 0.03575 | 0 | 0 |
| 35 | 370-371 | 0.03458 | 0.03359 | 0.03579 | 0 | 0 |
| 36 | 359-360 | 0.03451 | 0.03309 | 0.03647 | 0 | 0 |
| 37 | 350-351 | 0.03471 | 0.03318 | 0.03659 | 0 | 0 |
| 38 | 340-341 | 0.03444 | 0.03297 | 0.03626 | 0 | 0 |
| 39 | 332-333 | 0.03456 | 0.03329 | 0.03636 | 0 | 0 |
| 40 | 323-324 | 0.03476 | 0.03335 | 0.03778 | 0 | 0 |
| 43 | 301-302 | 0.03459 | 0.03329 | 0.03626 | 0 | 0 |

### Skip-F columns (F does not enter a column)

Dropping F from the raw stream, with no key, already lifts IOC from 0.03448 to 0.03571. Skip-F column means sit on that artifact (~0.0356-0.0359), not on English.

| L | col n | mean IOC | min | max | n>=0.045 | n>=0.055 |
|---|---|---|---|---|---|---|
| 2 | 6249-6249 | 0.03572 | 0.03569 | 0.03575 | 0 | 0 |
| 5 | 2499-2500 | 0.03565 | 0.03564 | 0.03567 | 0 | 0 |
| 7 | 1785-1786 | 0.03563 | 0.03543 | 0.03574 | 0 | 0 |
| 11 | 1136-1137 | 0.03578 | 0.03536 | 0.03641 | 0 | 0 |
| 13 | 961-962 | 0.03573 | 0.03543 | 0.03602 | 0 | 0 |
| 17 | 735-736 | 0.03559 | 0.03508 | 0.03600 | 0 | 0 |
| 19 | 657-658 | 0.03562 | 0.03480 | 0.03603 | 0 | 0 |
| 29 | 430-431 | 0.03585 | 0.03478 | 0.03745 | 0 | 0 |
| 31 | 403-404 | 0.03590 | 0.03470 | 0.03762 | 0 | 0 |
| 37 | 337-338 | 0.03581 | 0.03471 | 0.03759 | 0 | 0 |
| 43 | 290-291 | 0.03576 | 0.03427 | 0.03782 | 0 | 0 |

Per-column IOC for the four target periods (no-skip):

- L=7: [0.03453, 0.03451, 0.03465, 0.03448, 0.03474, 0.03458, 0.03453]
- L=11: [0.03459, 0.03459, 0.03435, 0.03459, 0.03406, 0.03432, 0.03459, 0.0344, 0.03501, 0.03453, 0.0345]
- L=29: [0.03419, 0.03356, 0.03482, 0.03403, 0.03464, 0.0351, 0.03452, 0.03562, 0.03526, 0.03517, 0.03505, 0.0345, 0.03363, 0.03414, 0.03486, 0.03452, 0.03543, 0.03415, 0.03509, 0.03453, 0.03457, 0.03466, 0.03436, 0.0345, 0.03356, 0.03383, 0.03345, 0.03452, 0.03445]
- L=43: [0.03417, 0.0347, 0.03472, 0.03481, 0.03459, 0.0345, 0.03478, 0.03562, 0.03373, 0.03551, 0.03481, 0.03604, 0.03417, 0.03475, 0.03362, 0.03362, 0.03626, 0.03513, 0.03437, 0.0359, 0.03402, 0.03526, 0.03367, 0.03406, 0.03466, 0.03386, 0.03426, 0.03367, 0.03475, 0.034, 0.03477, 0.03422, 0.03329, 0.0357, 0.0338, 0.03504, 0.03493, 0.03342, 0.03462, 0.03473, 0.03446, 0.03422, 0.03612]

Per-column IOC for the four target periods (skip-F):

- L=7: [0.0356, 0.03559, 0.03568, 0.03567, 0.03543, 0.03571, 0.03574]
- L=11: [0.03641, 0.03542, 0.0363, 0.03586, 0.03542, 0.03616, 0.03554, 0.03567, 0.03582, 0.03536, 0.03559]
- L=29: [0.03648, 0.03593, 0.03616, 0.03478, 0.03693, 0.03648, 0.03636, 0.03542, 0.03605, 0.0349, 0.03539, 0.03535, 0.03576, 0.03544, 0.03534, 0.03622, 0.03559, 0.0355, 0.03678, 0.03555, 0.03596, 0.03496, 0.03709, 0.03745, 0.03573, 0.03614, 0.03513, 0.03549, 0.0352]
- L=43: [0.035, 0.03567, 0.03586, 0.03517, 0.03486, 0.03541, 0.03557, 0.03782, 0.03467, 0.0356, 0.03534, 0.03564, 0.03553, 0.03666, 0.03477, 0.03524, 0.03481, 0.03515, 0.03574, 0.03453, 0.03631, 0.03515, 0.03733, 0.03522, 0.03583, 0.03673, 0.0359, 0.03626, 0.0357, 0.03572, 0.03558, 0.03687, 0.03587, 0.03615, 0.03646, 0.03654, 0.0373, 0.03427, 0.03527, 0.03589, 0.0367, 0.03537, 0.03618]

## Attack grid

4 periods x 2 ciphers x 2 skip modes x 4 crib modes = 64 trials.

Crib modes:

- `freq`: every key digit from chi-squared vs English-on-GP
- `6555` / `12950` / `both`: pin key digits implied by treating DJUBEI as **plaintext** at that ciphertext offset, then fill the rest by frequency

Because the ciphertext at those offsets *is* DJUBEI, Vigenere + PT=DJUBEI pins those columns to **k=0**. Beaufort pins k=(2c) mod 29. Isolated 2-letter dictionary hits are not English. Success requires IOC toward 0.06+ **and** readable 3301 phrases.

- trials: 64
- success (IOC>=0.06 and 3301 English): 0
- IOC min / median / max: 0.03447 / 0.03481 / 0.03637
- trials with IOC >= 0.05: 0
- trials with any listed 3301 phrase in the compact stream: 0
- trials with >=1 content word (len>=4) in word-broken decrypt: 19

### Top 20 by IOC

| IOC | lift | L | cipher | skip | crib | key | phrases | content | crib PT | preview |
|---|---|---|---|---|---|---|---|---|---|---|
| 0.03637 | +0.00189 | 7 | beaufort | skipF | freq | `EOEOOEOEEOEOEO` | - | DEATH,WITH | {'6555': 'EUJAREO', '12950': 'EUJADEO'} | `YRRMGOEXFYSRUWIUGTFJFNOIODSCBYMFTHUNGOTG` |
| 0.03632 | +0.00184 | 29 | vigenere | skipF | freq | `WBIAADNUWAUWBOWTDWWBBWWWWGWWSB` | - | THAT | {'6555': 'TAEPIUEO', '12950': 'TRAIJA'} | `HLLHEOIYFHTHBXBEARMTHFRSSNGATHJFJBHWAORO` |
| 0.03631 | +0.00183 | 7 | vigenere | skipF | freq | `WWBBWBW` | - | - | {'6555': 'GRDIUOE', '12950': 'TDDIJOE'} | `HUUSEATHLFHMURIAXREAEFDCAENGATHJMFBIASCO` |
| 0.03631 | +0.00183 | 11 | vigenere | skipF | freq | `NWWWWWBWUBW` | - | DEATH | {'6555': 'TDDTUO', '12950': 'TIPINO'} | `GUJAEEAEOIFHAEUXAEAREAEFRCAEHXTHNFIBHSAO` |
| 0.03628 | +0.00180 | 43 | vigenere | skipF | freq | `SBBWHBOEUEBTUBWBWRWPDWWWEWWBWBFBJYBHWAEWWBSRW` | - | - | {'6555': 'MRSFUO', '12950': 'TOEDIUO'} | `FLUAEIATHCFXHUCRXREEFWSMSATHJEIBIASAIRME` |
| 0.03617 | +0.00169 | 29 | beaufort | skipF | freq | `EOOEHPIAMFEOFGEOAEHNGJEAEOEOOEOEFEOXEAJEOEOEAIA` | - | - | {'6555': 'EBYARIA', '12950': 'LBIADE'} | `YXMINGFTHFYOBLLGICOFUMMPIAOAENGDBYGSTHUW` |
| 0.03610 | +0.00162 | 43 | beaufort | skipF | freq | `EOOEXJONGIACEAOEEOAEOEEOOEMJIAEAEOJEOEOOENGEJEOOEFOEWOEFEOEONGBOEHHEOEO` | - | - | {'6555': 'EUJCAEU', '12950': 'EJLUOETH'} | `YXAEHYTHFFMTHRLLLUTDFFCAEONODSRDAEMIMUGP` |
| 0.03607 | +0.00158 | 7 | beaufort | skipF | 12950 | `CWLOEBOETH` | - | - | {'6555': 'EALRMTHEO', '12950': 'DJUBEI'} | `MEATHMJORFMITHUEOLLEAJFNFXPFAEEPCOEWNOEY` |
| 0.03603 | +0.00155 | 7 | beaufort | skipF | both | `THCWLBBOE` | - | - | {'6555': 'DJUBEI', '12950': 'DGNGXTY'} | `TYEBJIAAFTHEEAEOSJAENFAEIAXHLOETFOOETHFM` |
| 0.03597 | +0.00149 | 11 | beaufort | skipF | freq | `MEOEOFEOEOOEOEHOEEO` | - | THIS | {'6555': 'EJNGLRTH', '12950': 'EAYNGAUTH'} | `RRDYGOEAFWJRLXIUDTFUFMEALOUCACYMIEOTNGOD` |
| 0.03595 | +0.00147 | 43 | beaufort | skipF | 12950 | `EOOEXJONGIACEAOEEOAEOEEOOEMJIAEAEOJEOBOETHCWLOEFOEWOEFEOEONGBOEHHEOEO` | - | - | {'6555': 'EUJCAEU', '12950': 'DJUBEI'} | `YXAEHYTHFFMTHRLLLUTDFFCAEONOEASXINGIAIMU` |
| 0.03595 | +0.00147 | 29 | beaufort | skipF | 6555 | `CWLPIAMFEOFGEOAEHNGJEAEOEOOEOEFEOXEAJEOBOETH` | - | - | {'6555': 'DJUBEI', '12950': 'LBIAEAEO'} | `MEATHINGFTHFYOBLLGICOFUMMPIAOAENGDBTHFMA` |
| 0.03593 | +0.00145 | 29 | beaufort | skipF | 12950 | `EOOEHPIAMFEOFGEOAEHNGJEAEOEOOEOEFEOBOETHCWLIA` | - | - | {'6555': 'PNYARIA', '12950': 'DJUBEI'} | `YXMINGFTHFYOBLLGICOFUMMPIAOEASXINGIASTHU` |
| 0.03592 | +0.00144 | 7 | beaufort | skipF | 6555 | `THCWLEOBOE` | - | - | {'6555': 'DJUBEI', '12950': 'EGNGXTY'} | `TYEBGIAAFTHEEAWSJAENFAEIANHLOETFOBTHFMAS` |
| 0.03592 | +0.00144 | 43 | beaufort | skipF | 6555 | `THCWLONGIACEAOEEOAEOEEOOEMJIAEAEOJEOEOOENGEJEOOEFOEWOEFEOEONGBOEHHBOE` | - | - | {'6555': 'DJUBEI', '12950': 'EJLUOETH'} | `TYEBYTHFFMTHRLLLUTDFFCAEONODSRDAEMIMUGPR` |
| 0.03585 | +0.00137 | 29 | beaufort | skipF | both | `CWLPIAMFEOFGEOAEHNGJEAEOEOOEOEFEOBOETHCBOETH` | - | - | {'6555': 'DJUBEI', '12950': 'DJUBEAEO'} | `MEATHINGFTHFYOBLLGICOFUMMPIAOEASXITHFMAS` |
| 0.03580 | +0.00132 | 43 | beaufort | skipF | both | `THCWLONGIACEAOEEOAEOEEOOEMJIAEAEOJEOBOETHCWLOEFOEWOEFEOEONGBOEHHBOE` | - | - | {'6555': 'DJUBEI', '12950': 'DJUBEI'} | `TYEBYTHFFMTHRLLLUTDFFCAEONOEASXINGIAIMUG` |
| 0.03580 | +0.00132 | 43 | vigenere | skipF | 12950 | `SBBWHBOEUEBTUBWBWRWPDWWFFFFFFBFBJYBHWAEWWBSRW` | - | - | {'6555': 'MRSFUO', '12950': 'DJUBEI'} | `FLUAEIATHCFXHUCRXREEFWSMSATHEWBASOEAIRME` |
| 0.03577 | +0.00129 | 43 | vigenere | skipF | 6555 | `FFFFHBOEUEBTUBWBWRWPDWWWEWWBWBFBJYBHWAEWWBSFF` | - | - | {'6555': 'DJUBEI', '12950': 'TOEDIUO'} | `SHEOIATHCFXHUCRXREEFWSMSATHJEIBIASAIRMEO` |
| 0.03576 | +0.00128 | 11 | beaufort | skipF | 6555 | `MEOEOFEOBOETHCWL` | - | - | {'6555': 'DJUBEI', '12950': 'HDGOUTH'} | `RRDYGIAAFTHEEAXIUDTFGFEAAECJUCACYAINGPGJ` |

### IOC matrix (freq-only, noskip / skipF)

| L | vig noskip | vig skipF | beau noskip | beau skipF |
|---|---|---|---|---|
| 7 | 0.03456 | 0.03631 | 0.03456 | 0.03637 |
| 11 | 0.03460 | 0.03631 | 0.03462 | 0.03597 |
| 29 | 0.03476 | 0.03632 | 0.03477 | 0.03617 |
| 43 | 0.03493 | 0.03628 | 0.03492 | 0.03610 |

### Chi2/corr agreement and margins (freq-only)

| L | cipher | skip | agree/L | mean chi2 margin | mean corr margin | key_chi |
|---|---|---|---|---|---|---|
| 7 | vigenere | noskip | 1/7 | 139.09 | 140.77271 | `LHOEDJGOE` |
| 7 | vigenere | skipF | 1/7 | 272.52 | 309.57436 | `WWBBWBW` |
| 7 | beaufort | noskip | 2/7 | 125.92 | -28.08965 | `AEPMMTNGB` |
| 7 | beaufort | skipF | 2/7 | 273.88 | -72.99327 | `EOEOOEOEEOEOEO` |
| 11 | vigenere | noskip | 0/11 | 66.57 | -9.77527 | `YPMMXNGAXDOEG` |
| 11 | vigenere | skipF | 5/11 | 174.28 | -263.46162 | `NWWWWWBWUBW` |
| 11 | beaufort | noskip | 2/11 | 134.18 | 91.03489 | `MEAYMYFMRUJ` |
| 11 | beaufort | skipF | 4/11 | 156.58 | -412.92052 | `MEOEOFEOEOOEOEHOEEO` |
| 29 | vigenere | noskip | 5/29 | 45.80 | 5.77136 | `ALNGMPSHEOIAUBOEDOETHYBPGJJCTHEXAEWPT` |
| 29 | vigenere | skipF | 9/29 | 54.45 | -46.80865 | `WBIAADNUWAUWBOWTDWWBBWWWWGWWSB` |
| 29 | beaufort | noskip | 6/29 | 49.01 | -41.74715 | `FOYXTHTTHBCEOHIAUOITHJJUFFIASMFEOHNG` |
| 29 | beaufort | skipF | 9/29 | 66.54 | -13.20192 | `EOOEHPIAMFEOFGEOAEHNGJEAEOEOOEOEFEOXEAJEOEOEAIA` |
| 43 | vigenere | noskip | 12/43 | 37.42 | -31.37904 | `SEAIAHJLRUAEADOENOJNEOEOTLTHNGDOEHNAEIBDLOXBSYIEOXOMNGX` |
| 43 | vigenere | skipF | 14/43 | 37.99 | -49.39914 | `SBBWHBOEUEBTUBWBWRWPDWWWEWWBWBFBJYBHWAEWWBSRW` |
| 43 | beaufort | noskip | 6/43 | 35.12 | 6.37046 | `LGHUTFNGAFPEAHAHUXTHODUCMWYPAEFEAGEAENGFUJTHEMGNGAEMM` |
| 43 | beaufort | skipF | 13/43 | 33.03 | -41.67266 | `EOOEXJONGIACEAOEEOAEOEEOOEMJIAEAEOJEOEOOENGEJEOOEFOEWOEFEOEONGBOEHHEOEO` |

### Crib-pin summary

For Vigenere, PT=DJUBEI on CT=DJUBEI forces k=0 on the columns those positions consume. For Beaufort, k=2c. The two hits sit in different columns for every target L (6395 != 0 mod L), so `both` pins up to 12 digits, or fewer when a column is hit twice.

| L | cipher | skip | crib | n_pinned | conflicts | IOC | crib decrypt at 6555 / 12950 |
|---|---|---|---|---|---|---|---|
| 7 | vigenere | noskip | 6555 | 6 | 0 | 0.03448 | DJUBEI / DJHBEI |
| 7 | vigenere | noskip | 12950 | 6 | 0 | 0.03451 | DJUAEI / DJUBEI |
| 7 | vigenere | noskip | both | 7 | 0 | 0.03448 | DJUBEI / DJUBEI |
| 7 | vigenere | skipF | 6555 | 6 | 0 | 0.03450 | DJUBEI / TJUBEI |
| 7 | vigenere | skipF | 12950 | 6 | 0 | 0.03456 | DJUBEOE / DJUBEI |
| 7 | vigenere | skipF | both | 7 | 0 | 0.03448 | DJUBEI / DJUBEI |
| 7 | beaufort | noskip | 6555 | 6 | 0 | 0.03447 | DJUBEI / PNEFRNG |
| 7 | beaufort | noskip | 12950 | 6 | 0 | 0.03450 | JAEMFEAEO / DJUBEI |
| 7 | beaufort | noskip | both | 7 | 5 | 0.03448 | DJUBEI / PNUFRNG |
| 7 | beaufort | skipF | 6555 | 6 | 0 | 0.03592 | DJUBEI / EGNGXTY |
| 7 | beaufort | skipF | 12950 | 6 | 0 | 0.03607 | EALRMTHEO / DJUBEI |
| 7 | beaufort | skipF | both | 7 | 5 | 0.03603 | DJUBEI / DGNGXTY |
| 11 | vigenere | noskip | 6555 | 6 | 0 | 0.03452 | DJUBEI / DJNOERT |
| 11 | vigenere | noskip | 12950 | 6 | 0 | 0.03449 | BXBIAEI / DJUBEI |
| 11 | vigenere | noskip | both | 10 | 0 | 0.03447 | DJUBEI / DJUBEI |
| 11 | vigenere | skipF | 6555 | 6 | 0 | 0.03486 | DJUBEI / DJUBNO |
| 11 | vigenere | skipF | 12950 | 6 | 0 | 0.03492 | TDUBEI / DJUBEI |
| 11 | vigenere | skipF | both | 8 | 0 | 0.03462 | DJUBEI / DJUBEI |
| 11 | beaufort | noskip | 6555 | 6 | 0 | 0.03451 | DJUBEI / PNAEEOUD |
| 11 | beaufort | noskip | 12950 | 6 | 0 | 0.03452 | BHBWEAEO / DJUBEI |
| 11 | beaufort | noskip | both | 10 | 2 | 0.03450 | DJUBEI / PNUBEI |
| 11 | beaufort | skipF | 6555 | 6 | 0 | 0.03576 | DJUBEI / HDGOUTH |
| 11 | beaufort | skipF | 12950 | 6 | 0 | 0.03553 | EJTCPA / DJUBEI |
| 11 | beaufort | skipF | both | 8 | 4 | 0.03552 | DJUBEI / HDGOEI |
| 29 | vigenere | noskip | 6555 | 6 | 0 | 0.03463 | DJUBEI / GIAAGWC |
| 29 | vigenere | noskip | 12950 | 6 | 0 | 0.03465 | OMJROTH / DJUBEI |
| 29 | vigenere | noskip | both | 12 | 0 | 0.03456 | DJUBEI / DJUBEI |
| 29 | vigenere | skipF | 6555 | 6 | 0 | 0.03565 | DJUBEI / TRAIEI |
| 29 | vigenere | skipF | 12950 | 6 | 0 | 0.03562 | DJPIUEO / DJUBEI |
| 29 | vigenere | skipF | both | 10 | 0 | 0.03524 | DJUBEI / DJUBEI |
| 29 | beaufort | noskip | 6555 | 6 | 0 | 0.03464 | DJUBEI / BFFEOJF |
| 29 | beaufort | noskip | 12950 | 6 | 0 | 0.03465 | NSPXIANG / DJUBEI |
| 29 | beaufort | noskip | both | 12 | 0 | 0.03456 | DJUBEI / DJUBEI |
| 29 | beaufort | skipF | 6555 | 6 | 0 | 0.03595 | DJUBEI / LBIAEAEO |
| 29 | beaufort | skipF | 12950 | 6 | 0 | 0.03593 | PNYARIA / DJUBEI |
| 29 | beaufort | skipF | both | 10 | 2 | 0.03585 | DJUBEI / DJUBEAEO |
| 43 | vigenere | noskip | 6555 | 6 | 0 | 0.03481 | DJUBEI / OETTHDAEU |
| 43 | vigenere | noskip | 12950 | 6 | 0 | 0.03482 | ONNDAETH / DJUBEI |
| 43 | vigenere | noskip | both | 12 | 0 | 0.03472 | DJUBEI / DJUBEI |
| 43 | vigenere | skipF | 6555 | 6 | 0 | 0.03577 | DJUBEI / TOEDIUO |
| 43 | vigenere | skipF | 12950 | 6 | 0 | 0.03580 | MRSFUO / DJUBEI |
| 43 | vigenere | skipF | both | 12 | 0 | 0.03535 | DJUBEI / DJUBEI |
| 43 | beaufort | noskip | 6555 | 6 | 0 | 0.03478 | DJUBEI / UEEOJMX |
| 43 | beaufort | noskip | 12950 | 6 | 0 | 0.03478 | WDEMHO / DJUBEI |
| 43 | beaufort | noskip | both | 12 | 0 | 0.03468 | DJUBEI / DJUBEI |
| 43 | beaufort | skipF | 6555 | 6 | 0 | 0.03592 | DJUBEI / EJLUOETH |
| 43 | beaufort | skipF | 12950 | 6 | 0 | 0.03595 | EUJCAEU / DJUBEI |
| 43 | beaufort | skipF | both | 12 | 0 | 0.03580 | DJUBEI / DJUBEI |

## Reading

No trial lifted IOC from the 1/29 floor (0.03448) toward English-on-29 (~0.06). Max decrypt IOC in the 64-trial grid is **0.03637**. Max single-column IOC at L in {7,11,29,43} (no-skip) is **0.03626**. Zero trials reached IOC 0.05. Zero trials produced a listed 3301 phrase (WELCOME, WARNING, DIVINITY, INSTAR, CIRCUMFERENCE, PILGRIM, ...).

Column IOC is the prior that matters. A genuine period-L Vigenere or Beaufort of English-on-29 makes each column monoalphabetic, so column IOC jumps toward ~0.06 *before* any key is guessed (see the synthetic self-test: every period-8 column was 0.058-0.072). On LP2 0-55 it does not. Wave 1's Kasiski mean ~0.0347 for periods 2-40 is confirmed (mean-of-means **0.03455**). Period **43**, which was outside that window, is the same (mean 0.03459, max 0.03626). Frequency recovery then just Caesar-shifts already-flat columns. The "best" key is a noise maximum; chi2 and correlation agree on only a minority of digits (1/7, 0/11, 5/29, 12/43 for no-skip Vigenere).

Skip-F raises decrypt IOC by about +0.0015 to +0.0019 (max 0.03637). That is not English. Removing every ciphertext F from the raw unsolved stream (no key at all) already yields IOC **0.03571** (458 F's, 3.54% of 12956, vs English-on-GP F about 1.6%). Reinserting those F's as interrupters leaves a slightly less-flat remainder. The same artifact showed up in the burned running-key grid.

Isolated content-word hits (DEATH, THAT, THEY, WITH, THIS) are 3-rune GP words (D-EA-TH, TH-A-T, TH-E-Y, W-I-TH, TH-I-S). In a 12956-rune 29-symbol stream with the original word breaks, several 3-rune dictionary collisions are expected. They never continue. They are not a solve.

DJUBEI as a plaintext crib pins the expected columns (Vigenere -> k=0 on those columns, because CT at 6555 and 12950 *is* DJUBEI; Beaufort -> k=2c). Decrypts at the pinned site then read DJUBEI by construction. The rest of the stream stays flat. Beaufort `both` sometimes conflicts (the two hits land in different columns and the implied k=2c values collide). Distance 6395 = 5*1279 is not a multiple of 7, 11, 29, or 43, so Kasiski from the only 6-gram repeat does not nominate these periods.

Key strings in the tables are `to_latin` concatenations. Digraph runes (TH, EO, OE, NG, IA, EA, AE) glue to their neighbors, so a period-7 key can look longer than 7 letters. That is display, not a longer period.

This is an honest fail of periodic Vigenere/Beaufort key recovery at 7/11/29/43 on LP2 0-55, not a parser miss and not a broken engine: the same parser replayed A WARNING, WELCOME, AN END, and PARABLE first; the same engine recovered Atbash (k=28) from A WARNING, identity (k=0) from PARABLE, and DIVINITY 8/8 from a synthetic Vigenere *and* Beaufort of 2143 clean solved-page runes. It does not recover English from LP2 0-55 because those columns are not English.

## What was not run

- Wave 1 family (identity / Atbash / Caesar / totient / Fibonacci / DIVINITY / CIRCUMFERENCE / 2016 phrases / 15.jpg square) on 0-55
- book-index / gematria-sum lookups
- SHA-512 preimage or hash-as-ciphertext
- YOUR INNOCENCE YOUR ILLUSIONS pad
- AN END or PARABLE as a running key or autokey primer (burned in `notes/runningkey-pass1.md`)
- other periods as a full frequency attack (2-40 column IOC was confirmed only)

## Parser log

Full per-trial echo is box-only (not in this repo). Kept calibration and verdict lines:

```
content rune-pages (parse_pages): 72
LP2_START 15
KEY DIVINITY [23, 10, 1, 10, 9, 10, 16, 26] DIUINITY
CAL A_WARNING ok=True n=184 ioc_pt=0.06403 A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE
CAL WELCOME ok=True n=251 skipF=WELCOF noskip=WELCOME WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OG HFJ O
CAL AN_END ok=True n=85 Fpos=[35, 47, 51, 56, 74] AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OOE TAXTHT 
CAL PARABLE ok=True n=95 ioc=0.06271 PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND
CALIBRATION_PASS True
FREQ total n=2705 ioc=0.05577
FREQ top: E=326 O=228 A=179 R=177 S=164 T=161 N=153 I=141 U=125 TH=107
SELFTEST WELCOME period-8 Vigenere: chi=AEIIAIIIII match=3/8 corr=NIOAIATI match=2/8 WELCOME=False head=CEDCTHMADTLHOEEMYEGWI
SELFTEST A WARNING Beaufort period-1: k_chi2=28 k_corr=28 true=28 WARNING=True head=AWARNNGBELIEUENOTHNGFROMTHIS
TRIALS 64 success=0 ioc min=0.03447 max=0.03637 median=0.03481
IOC>=0.05: 0
any PHRASE hit: 0
VERDICT FAIL
CLEAN_FREQ n=2143 ioc=0.06186
SELFTEST PARABLE vig-p1 k_chi2=0 k_corr=0 true=0 margin=170.93
SELFTEST WARNING-PT vig-p1 k_chi2=0 k_corr=0 true=0 margin=451.88
SYNTH Vigenere DIVINITY rec 8/8
SYNTH Beaufort DIVINITY rec 8/8
UNSOLVED drop-F n=12498 ioc=0.03571 nF=458 pF=0.0354
```

VERDICT: FAIL
