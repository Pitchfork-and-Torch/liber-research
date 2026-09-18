# Liber Primus sexagesimal block as a transposition instruction on onion 33-39, pass 1

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (rtkd `liber-primus__transcription--master.txt`, fetched fresh). The 256-value sexagesimal block from the same three public copies as the running-key pass: scream314 `assets/2014/stage11/49.txt 50.txt 51.txt` (page numerals), scream314 `stage11/<2014 onion mirror dir>/decimal.txt` (2014 onion listing), rtkd `byte-strings` String 4 (hex). None of these files are added to this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts). Atbash / Vigenere / totient replays match the earlier passes.
Method family: **the 256-value block used as a transposition instruction** (column order, cell permutation, skip schedule, 32x8 grid shape) over onion 33-39, scored by **column IOC at block-derived widths (8, 32, 60, 256)**, with a period sweep 2-64 as context. This is the next experiment named at the end of `notes/sexagesimal-block-key-pass1.md`.
Not additive keying (NULL_ATTACK, PR #3), not Mobius reversal (NULL_ATTACK, PR #2), not plain columnar on the whole stream (FAIL, `notes/transposition-pass1.md`), not outguess, not book-index, not periodic key recovery. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, WELCOME, AN END, PARABLE and a decode then yields continuous readable 3301-style English. Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Hypothesis

H1: the cuneiform section is a periodic substitution (period tied to the block: 8 columns, 32 rows, base 60, or 256 cells) whose ciphertext was then transposed under an instruction read off the block. Undoing the right transposition should make the residue classes at the true period monoalphabetic again.

Why column IOC and not global IOC: a permutation cannot change the global IOC (already 1/29 on this section), and a pure transposition of English-on-GP would already read 0.06 raw. The section is flat, so the only transposition model that is still alive is transposition on top of a substitution. Under that model the falsifiable quantity is the mean IOC of the W residue classes after untransposing: English-on-GP at n = 1680 gives about 0.060-0.064 at W = 8, 32, 60, 256 (positive controls below), a flat stream gives 0.0343 with a shuffle spread that widens as W grows.

Prediction if H1 is true: some block-derived untranspose lifts column IOC at one of the block widths into the 0.06 band, well outside what random 256-byte blocks driving the same instruction set produce.
Prediction if H1 is false: every cell stays inside the random-block distribution and no cell carries words.

## Alignment

Block: K1 (scream314 page reading = onion decimal list, checked value for value) and K2 (rtkd hex, ten glyph slips at 25, 45, 50, 165, 170, 172, 175, 182, 199, 246), as in the running-key pass. **PASS_ALIGN.**

Runes: rtkd parses to 72 rune pages; onion n = rune-page n+15. Heads and lengths of onion 32-39 match the table in the running-key note exactly (onion 33 = rune-page 48, head `DEOXCFIAWHGEOOEFTEOEEAAI`, n 214).

| span | what | n | raw IOC |
|---|---|---|---|
| T2 | onion 33-39 (the primary target this note was asked for) | 1680 | 0.03436 |
| T1 | section 0.11 (onion 33 rune 91 to end of onion 39) | 1589 | 0.03435 |

## Calibration

- A_WARNING ok=True: Atbash on rune-page 0, n 184, IOC 0.06403, `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWHATYOUCNOWTOBETRUETES`
- WELCOME ok=True: Vigenere DIVINITY on rune-page 1, consume F at 5, 14, 47, skip the rest; n 251, `WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTOWARDTHEENDOFALLTHNGSITISNOTANEASYTRIPBUT`
- AN_END ok=True: totient p = (c-(prime_k - 1)) mod 29 on rune-page 70, skip F at page-local 56; n 85, IOC 0.07003, `ANENDWITHINTHEDEEPWEBTHEREEXISTSAPAGETHATHASHESTOITISTHEDUTYOFEUERYPILGRIMTOSEEC`
- PARABLE ok=True: direct on rune-page 71, n 95, IOC 0.06271

**PASS_CALIB.** (A first draft wrapped the prime list at 29 entries and broke AN END after EXISTS; the k-th prime runs on past 109. Fixed before anything else was read.)

## Definition of the grid

Every instruction is a permutation P of the n target positions. Both P and its inverse are applied (the model does not say which direction the setter used). Block readings: byte (0-255), low base-60 digit, high base-60 digit (0-4), and the 512 base-60 digits interleaved; each in row-major (as printed) and column-major (down the 8 printed columns) order.

| family | definition | cells per block |
|---|---|---|
| `colorder W` | keyed columnar at W in {8, 32, 60, 256}; column read order = stable rank of the first W block values | 4 W x 8 readings x 2 dirs = 64 |
| `perm256` / `perm512` | the block as a permutation of its own cells (stable rank of all 256 values, or all 512 digits), applied to each consecutive 256- or 512-rune chunk of the target | 8 readings x 2 dirs = 16 |
| `skip` | read-out order by stepping: pos = pos + (v mod r) + 1, next free cell on collision, v walking the block; r in {none, 8, 32, 60} | 6 readings x 4 r x 2 dirs = 48 |
| `shape` | block-independent grid shapes: plain columnar at W in {8, 32, 60, 256} on the whole target; 32x8 written per 256-rune chunk read by columns and by rows | 12 |

128 block-dependent cells per block plus 12 shape cells. Run on K1 and K2, on T2 and T1: **536 distinct untranspositions** of the real text. Each is scored on column IOC at W = 8, 32, 60, 256 and on the maximum over the sweep W = 2..64.

## Positive controls

English-on-GP (A WARNING, PARABLE, AN END, LP1 direct pages 3/8/9/10/11/14, LP1 Atbash+3 pages 4-7; 2143 runes, first 1680 used; IOC 0.06179) was encrypted with a periodic Vigenere whose key is the first `period` block values mod 29, then transposed with one instruction from the grid, then handed to the full grid.

| control | period | planted transposition | colIOC at period: after Vigenere / after transposition / grid top | expected cell found |
|---|---|---|---|---|
| A | 8 | `colorder W=32 row byte fwd` | 0.06228 / 0.03621 / 0.06228 | rank 1, alone |
| B | 32 | `perm256 row byte fwd` | 0.06157 / 0.03718 / 0.06157 | rank 1, alone |
| C | 8 | `skip raw row byte fwd` | 0.06228 / 0.03616 / 0.06228 | rank 1, alone; runner-up 0.04208 |
| D | 60 | `skip mod32 col lo inv` | 0.06376 / 0.03664 / 0.06376 | rank 1, alone; runner-up 0.04200 |
| E | 60 | `colorder W=8 col lo inv` | 0.06376 / 0.03884 / 0.06376 | tied at top with `colorder W=8 row hi fwd` |

The tie in E is structural, not a bug: 8 divides 1680, so any permutation of the 8 columns maps each residue class mod 60 onto another residue class, and column IOC at 60 cannot tell two W=8 column keys apart. Every control puts the planted cell at the top with the grid median at 0.036-0.039. Pure English transposed with no substitution reads 0.060-0.063 at every width (permutation invariance, as expected). **CONTROL_OK.**

## Null

- Shuffle null for the raw target: 2000 random permutations of T2 (and of T1), column IOC at each width and sweep maximum.
- Block null for the grid: **60 random uniform 256-byte blocks** driving the identical 128 block-dependent cells on each span (15,360 untranspositions). The statistic compared is the grid maximum per width, so the null is a grid maximum too. Shape cells are block-independent and are reported on their own.
- Crib null: 20 random blocks through the same cells, and 3000 random permutations of T1, scored on a 3301 word list (GP spelling, length >= 5).

## Attack table

### Raw target, no untranspose (block-derived period test)

| span | W | raw colIOC | shuffle mean (sd) | shuffle max | frac of shuffles >= raw |
|---|---|---|---|---|---|
| T2 | 8 | 0.03407 | 0.03435 (0.00040) | 0.03591 | 0.755 |
| T2 | 32 | 0.03553 | 0.03434 (0.00086) | 0.03759 | 0.080 |
| T2 | 60 | 0.03514 | 0.03432 (0.00121) | 0.03876 | 0.252 |
| T2 | 256 | 0.03344 | 0.03437 (0.00265) | 0.04330 | 0.638 |
| T2 | sweep 2-64 | 0.03643 at W=54 | max-of-sweep mean 0.03670 | 0.03954 | 0.651 |
| T1 | 8 / 32 / 60 / 256 | 0.03397 / 0.03532 / 0.03490 / 0.03378 | same nulls | | 0.807 / 0.135 / 0.334 / 0.581 |

Per-column at W=8 on T2: 0.0324-0.0358, every column flat. W=32 columns scatter 0.026-0.052 on 52-53 runes each, which is what 52-rune samples of a flat stream do. Nothing to untranspose toward.

### Block-driven untranspose, K1 grid maxima against the random-block null

| span | W | real K1 grid-max (cell) | null grid-max min / mean / max | random blocks >= real |
|---|---|---|---|---|
| T2 | 8 | 0.03525 (`colorder W=60 row byte inv`) | 0.03513 / 0.03544 / 0.03603 | 47 / 60 |
| T2 | 32 | 0.03687 (`perm256 col lo fwd`) | 0.03573 / 0.03656 / 0.03871 | 13 / 60 |
| T2 | 60 | 0.03792 (`skip mod32 col lo inv`) | 0.03593 / 0.03746 / 0.03889 | 6 / 60 |
| T2 | 256 | 0.03977 (`skip mod8 row byte fwd`) | 0.03873 / 0.04109 / 0.04435 | 54 / 60 |
| T2 | sweep 2-64 | 0.03865 | 0.03784 / 0.03864 / 0.04039 | 22 / 60 |
| T1 | 8 | 0.03561 | 0.03520 / 0.03554 / 0.03615 | 18 / 60 |
| T1 | 32 | 0.03687 | 0.03590 / 0.03669 / 0.03809 | 18 / 60 |
| T1 | 60 | 0.03755 | 0.03681 / 0.03813 / 0.03993 | 52 / 60 |
| T1 | 256 | 0.04170 (`colorder W=60 row hi fwd`) | 0.03899 / 0.04155 / 0.04602 | 25 / 60 |
| T1 | sweep 2-64 | 0.03852 | 0.03810 / 0.03892 / 0.03998 | 41 / 60 |

K2 grid maxima: T2 0.03558 / 0.03647 / 0.03695 / 0.03947, T1 0.03546 / 0.03646 / 0.03801 / 0.04170 at W = 8 / 32 / 60 / 256. Same picture within 0.001; the ten glyph slips change nothing.

Shape cells (no block values): T2 grid-max 0.03520 / 0.03508 / 0.03638 / 0.03783; T1 0.03517 / 0.03531 / 0.03808 / 0.03828. All flat.

Reading the table: the largest real value anywhere is 0.0417 at W=256 on T1, where each "column" is six or seven runes and the shuffle sd is 0.0028; 25 of 60 random blocks beat it. The one width where the real block is in the upper tail (T2, W=60, 6/60) sits at 0.0379 against an English-on-GP expectation of 0.0638 for that width and sample size, is not repeated on T1 (52/60), and is the 60th-width cell of a five-statistic table. The band the controls hit (0.0616-0.0638 at the planted period, runner-up 0.042) is never approached.

### Top cells by any-width column IOC (K1, T2)

| cell | colIOC 8 / 32 / 60 / 256 | head |
|---|---|---|
| `skip mod8 row byte fwd` | 0.03408 / 0.03413 / 0.03373 / 0.03977 | `FFGNAEXUHTHINWWJSNGEOCUNDWCFSBPOCTXBEOIA` |
| `skip raw row byte fwd` | 0.03392 / 0.03387 / 0.03461 / 0.03932 | `HMANGPIARAGYFGTFUTHHNIAEONGAFBBGMNGDEOTP` |
| `colorder W=256 row byte fwd` | 0.03428 / 0.03409 / 0.03338 / 0.03899 | `GCTBCIAUNAEYHOETEOCPWITJOEWAETHIBGHLAEDB` |
| `skip raw col digits fwd` | 0.03409 / 0.03463 / 0.03549 / 0.03880 | `FIAWTHJJGJAPWMAHNAESWOAESPTMEATJPUAFDTHH` |

Flat GP Latin in every head.

### Cribs

3301 word list, GP spelling, length >= 5, non-overlapping matches over the whole untransposed span.

- Raw T2 and T1: 0 cribs.
- K1 cells: T2 mean 0.156 per decrypt, max 1; T1 mean 0.102, max 3. K2: 0.164 / 0.086, max 1 / 3.
- Random blocks (20): mean 0.103-0.108 per decrypt, max 2 in one decrypt.
- The English control text at n = 1680 carries 53.
- The single 3-crib cell, `colorder W=8 row lo inv` on T1: `DEATH` at 243, `NOTHNG` at 439, `THNGS` at 1863, each surrounded by GP noise (`...RIOERCDEATHDEOFWSBEOX...`, `...BNGBINOTHNGTAEOEURUE...`), column IOC 0.0348 / 0.0343 / 0.0354 / 0.0380 at the four widths. Three short cribs land in 3 of 3000 random permutations of T1; over 512 real block-dependent decrypts that is about half an expected event. Chance.

## What kills the family

1. **There is no period to expose.** The raw section shows no column-IOC lift at 8, 32, 60, 256 or anywhere in 2-64; the W=32 value (0.0355, 8% of shuffles higher) is the best of five statistics and is 0.028 short of the English band.
2. **No block-derived untranspose creates one.** Across 536 untranspositions the best column IOC at any block width is 0.0417, on six-rune columns, beaten by 25 of 60 random blocks. At the informative widths (8, 32, 60) the real maxima are 0.0353-0.0379 and random blocks reach 0.0360-0.0399. The same grid put a planted period-8/32/60 substitution-plus-transposition at the top of the table at 0.062-0.064 five times out of five.
3. **No words.** Crib density in the real cells equals the random-block rate; the top IOC cells carry none.
4. **Transcription is not the excuse.** K1 and K2 agree to within 0.001 at every width; the shape-only cells, which do not depend on the block at all, are just as flat.
5. **What the permutation-invariance argument leaves.** A transposition with no substitution layer is excluded by the raw IOC of 1/29 (`notes/transposition-pass1.md`). A transposition over a periodic substitution at a block-derived period is excluded here. A transposition over an aperiodic substitution (running key, autokey) is not excluded by this pass or by PR #3, but column IOC cannot see it and it has two unknowns with no anchor in the block; it is noted, not attacked.

## What was not run

- Column orders drawn from block values other than the first W (for example the W column sums of the 32x8 grid, or rank of the last W values). These are more cells of the same family; the null shows what such cells produce.
- Widths not derived from the block. The sweep 2-64 covers small ones as context; large ones on a 1680-rune section are noise.
- The block as a permutation of anything other than the rune text (byte strings, page images, the SHA-512 hex page).

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

Used as a transposition instruction in four families, eight readings and both directions (536 untranspositions of onion 33-39 and of section 0.11), the sexagesimal block does not lift column IOC at any block-derived width above what 60 random blocks driving the same instructions produce, and never approaches the 0.062-0.064 band that five planted controls reached. The raw section has no period at those widths to begin with. No solve. LP2 0-55 unsolved.

## Where this leaves the block

Two passes (PR #3 and this one) have now tried the two text-side readings of the 256-value block: as additive key material over the runes, and as a permutation instruction over the runes. Both are inside the null against matched controls that would have seen a real hit. The block itself is uniform bytes (161 distinct values, entropy 7.17, 2048 bits).

Conclusion for the box: **treat the block as binary key material for something that is not the rune text.** Candidates are outside the scope of this lab's rune work (a 2048-bit RSA object against the 2014 Cicada keys; a key or IV for a payload that has not been located). No third rune-side attack on the block is proposed. Rune-side work on the cuneiform section should move to a different hypothesis or a different section.

No public post. Box files only: `notes/sexagesimal-block-transposition-pass1.md`. Desk parser, attack script, per-cell JSON and the fetched block/transcription copies stayed in the VM and are not committed.
