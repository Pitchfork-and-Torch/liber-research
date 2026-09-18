# Liber Primus sexagesimal block as running key on the cuneiform section (onion 32-39), pass 1

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (rtkd `liber-primus__transcription--master.txt`, fetched fresh). The 256-value sexagesimal block from three public copies: scream314 `assets/2014/stage11/49.txt 50.txt 51.txt` (the page numerals), scream314 `stage11/ky2khlqdf7qdznac.onion/decimal.txt` (the 2014 onion listing), and rtkd `byte-strings` String 4 ("Matrix from pages 49-51 converted to hexadecimal"). None of these files are added to this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts). Atbash / Vigenere / totient replays match the earlier passes in this repo.
Method family: **the 256-value block used as a running key (additive mod 29) over the rune pages that carry it and the cuneiform section that follows**, in every reading of the numerals (byte, base-60 digit pair, low digit, high digit, hex nibbles), every block ordering (row-major, column-major, column-major per page), both additive laws plus Beaufort, with and without the "clear-text F is not encrypted" rule, tiled over the section or applied once at any offset. Secondary check in the other direction: section runes as key over the 256 bytes.
Not outguess, not book-index, not periodic Vigenere key recovery, not columnar, not Mobius reversal (NULL_ATTACK, PR #2), not SHA-512 preimage. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, WELCOME, AN END, PARABLE and a decode then yields continuous readable 3301-style English. Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Hypothesis

H1: the 256-value block printed on onion 32-34 is the key stream for the runes around it. Concretely, some reading of the numerals, subtracted from (or added to, or Beaufort against) the rune indexes of onion 32-39, with or without the Cicada F rule, gives English-on-Gematria-Primus, either tiled across the section or as a single 256/512-rune keyed run.

Prediction if H1 is true: at the correct cell the decrypt IOC lands in the English-on-GP band (whole section about 0.060-0.062; a 256-rune window mean 0.0628, sd 0.0048, min 0.0541 over 270 solved-page windows) and long cribs appear (positive controls below give 36-65).
Prediction if H1 is false: every cell stays inside the distribution produced by random 256-byte blocks pushed through the identical grid, and no long cribs beyond chance.

## Alignment

### Block provenance (PASS_ALIGN)

- The numerals on onion 32, 33, 34 are two-place base 60 written with the digit alphabet `0-9 A-Z a-x` (60 symbols): 10 + 13 + 9 = 32 rows of 8 = **256 values**. `3N` = 3*60 + 23 = 203, `3p` = 3*60 + 51 = 231, `2l` = 167, `36` = 186, `1b` = 97, matching the 2014 onion decimal list value for value.
- scream314 page reading = scream314 onion decimal list = the 256-byte `sexagesimal.bin`, exactly. Call this **K1**.
- rtkd String 4 (**K2**) differs from K1 at 10 of 256 positions (25, 45, 50, 165, 170, 172, 175, 182, 199, 246). Every difference is a glyph slip inside the digit alphabet: `l`/`L` (47 vs 21, 107 vs 81, 167 vs 141), `i`/`I` (224 vs 198, 44 vs 18), `s`/`S` (174 vs 148), `l`/`I` (47 vs 18), leading `3`/`4` (194 vs 254). K1 is the better-attested block (two independent renderings agree); K2 is carried as a robustness variant.
- Block statistics: min 0, max 255, 161 distinct values (uniform expectation about 162), entropy 7.17 bits/byte, high base-60 digit 0-4 with 4 appearing 17 times (uniform expectation 16). The numerals encode **bytes**, not rune indexes (which would stop at 28) and not base-60 digits with a small range. 256 bytes = 2048 bits. Read straight as runes (byte mod 29, direct GP) the block is flat: IOC 0.03692, head `FEAOEEOICINCBJMSRNNCEASRSNGUFOENGEAAECHAEBEAIADIAEO`.

### Runes (PASS_ALIGN)

rtkd parses to 72 rune pages; onion n = rune-page n+15 (onion 0 head `SHEOGMIAF`, as in the earlier passes). rtkd index entry 0.10.1 `ᛞᛇ ᛉᚳᚠᛁᚪᚹᚻᚷ (50/33)` matches the head of rune-page 48, so onion 33 = rune-page 48. The cuneiform section proper (rtkd 0.11, title `ᛝᚦᛇ ᛁᚠᚳᛟᛇ`) starts mid-page on onion 33 at rune 91 after a `&`/`$` break and runs to the end of onion 39; the sub-title `ᛡᚳᛋ` sits on onion 39 at rune 119.

| onion | rune page | n | lines | words | head | raw IOC |
|---|---|---|---|---|---|---|
| 32 | 47 | 121 | 6 | 26 | `LTHAEWAEUPIACWNGHWBMSOEE` | 0.0342 |
| 33 | 48 | 214 | 11 | 61 | `DEOXCFIAWHGEOOEFTEOEEAAI` | 0.0331 |
| 34 | 49 | 261 | 12 | 71 | `MBNHEODHMLIEANIAEEUTTHEO` | 0.0334 |
| 35 | 50 | 271 | 12 | 71 | `NGTCAEAYGCTHENUIAEIUIAWL` | 0.0350 |
| 36 | 51 | 238 | 11 | 58 | `YNUWNGHGYROILNXNOPFEAAEA` | 0.0360 |
| 37 | 52 | 228 | 11 | 60 | `NYEXNUXINGTPWSYTEAPXAIJS` | 0.0334 |
| 38 | 53 | 228 | 11 | 53 | `UAECEOCYIAAETECFSHSRUTHI` | 0.0352 |
| 39 | 54 | 240 | 12 | 64 | `SWTHNSIHBXEANGBULOEUNUTH` | 0.0358 |

Target stream: onion 32-39 concatenated, **n = 1801**, raw IOC 0.03437 (1/29 = 0.03448). Scored spans: T1 = section 0.11 (runes 212-1801, n = 1589, 412 words, 75 lines, IOC 0.03435); T2 = onion 33-39 (n = 1680, IOC 0.03436); T3 = the three matrix host pages onion 32-34 (n = 596, IOC 0.03448); ALL (n = 1801).

## Calibration

Known methods replayed on the fresh fetch. Attack proceeds only if all four pass.

- A_WARNING ok=True: Atbash p = 28-c on rune-page 0, n 184, IOC 0.06403, `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWHATYOUCNOWTOBETRUETES`
- WELCOME ok=True: Vigenere DIVINITY (DIUINITY) on rune-page 1, consume F at 5, 14, 47, skip the rest; n 251, `WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTOWARDTHEENDOFALLTHNGSITISNOTANEASYTRIPBUT`
- AN_END ok=True: totient p = (c-(prime-1)) mod 29 on rune-page 70, skip F at page-local 56; n 85, IOC 0.07003, `ANENDWITHINTHEDEEPWEBTHEREEXISTSAPAGETHATHASHESTOITISTHEDUTYOFEUERYPILGRIMTOSEEC`
- PARABLE ok=True: direct on rune-page 71, n 95, IOC 0.06271, `PARABLELICETHEINSTARTUNNELNGTOTHESURFACEWEMUSTSHEDOUROWNCIRCUMFERENCESFINDTHEDIU`

**PASS_CALIB.**

### Engine positive controls

English-on-GP plaintext (A WARNING, PARABLE, AN END, LP1 direct pages 3/8/9/10/11/14, LP1 Atbash+3 pages 4-7; IOC 0.0618, 65 long cribs at n = 1801) was pushed forward through the cipher and the full grid was asked to find it.

| control | planted cell | grid top cell | top IOC | cribs | 2nd-best cell | median cell |
|---|---|---|---|---|---|---|
| A tiled, F encrypted normally | row, byte mod 29, sub, phase 0 | same | 0.06180 | 65 | 0.06180 (its Beaufort twin) | 0.03649 |
| B tiled, clear-text F not encrypted | row, byte mod 29, sub, F rule, phase 0 | same | 0.06005 | 60 | 0.06005 | 0.03517 |
| C one keyed run of 512 planted at offset 700 inside the real ciphertext | col_all, base-60 digits, add, offset 700 | same | 0.06160 | 36 | 0.04507 | 0.04017 |

Control B needed one honest fix: with the F rule, a non-F plaintext that encrypts to F would be misread as an interrupter on decrypt and desynchronise the key. The solved pages never produce that case; the control forces the same by leaving such a plaintext rune as clear F (3.4% of positions, plaintext IOC 0.0601 instead of 0.0618). A first version of the control without that fix failed, and the attack table below was not read until all three controls passed. **CONTROL_OK.**

## Definition of the grid

| axis | values |
|---|---|
| block | K1 (scream314 pages = onion list), K2 (rtkd hex) |
| ordering | row-major (as printed); column-major over the whole 32x8; column-major within each page (10, 13, 9 rows) |
| reading | byte mod 29 (L 256); base-60 digit pair hi,lo each mod 29 (L 512); low digit mod 29 (L 256); high digit 0-4 (L 256); hex nibbles hi,lo (L 512) |
| law | sub p = c-k; add p = c+k; Beaufort p = k-c |
| F | none (every rune consumes key); F rule (ciphertext F is clear-text F and consumes no key) |
| tiled | key repeated over the whole 1801-rune stream at every phase 0..L-1; IOC scored on T1, T2, T3, ALL |
| one-shot | key applied once starting at every offset 0..1801-L; IOC scored on the L keyed runes |

900 cells; **517,896 distinct decrypts** for the two blocks (tiled: 3 orderings x 5 readings x 3 laws x 2 F x (256 or 512) phases x 2 blocks; one-shot: the same with 1546 or 1290 offsets). Beaufort and sub give identical IOC at the same phase (negation permutes symbols), so the effective count is two-thirds of that.

## Scoring and null

- IOC of the decrypt on the scored span. English-on-GP about 0.062; a 256-rune English window has mean 0.0628, sd 0.0048, minimum 0.0541 over 270 windows of the solved corpus; a 256-rune uniform window has mean 0.0345, sd 0.0010, max 0.0397 over 2000 draws.
- Long cribs: GP rune sequences of length >= 4 from the same 48-word list used in the earlier passes (K->C, V->U, ING->ᛝ, digraphs greedy).
- Null: **60 random uniform 256-byte blocks** pushed through the identical grid (all orderings, readings, laws, F modes, phases, offsets, spans). The statistic compared is the grid maximum, so the null is a grid maximum too.
- Crib null: random blocks through the hex-nibble reading (the only reading that produced any 2-crib cell), 6 blocks x 9216 decrypts.

## Attack table

### Tiled (key repeated over the section)

| span | n | best IOC K1 | cell | null tiled grid-max (60 blocks) |
|---|---|---|---|---|
| T1 section 0.11 | 1589 | 0.03612 | col_page, low digit, add, F rule, phase 126 | min 0.03807 mean 0.03865 max 0.03992 |
| T2 onion 33-39 | 1680 | 0.03611 | row, low digit, add, F rule, phase 213 | (same) |
| T3 onion 32-34 | 596 | 0.03841 | col_page, hex nibbles, add, F rule, phase 415 | (same) |
| ALL onion 32-39 | 1801 | 0.03620 | col_all, hex nibbles, add, F rule, phase 66 | (same) |

Real K1 tiled maximum 0.03841. **45 of 60 random blocks beat it.** Control B, the same construction with a real key, reads 0.06005 at phase 0.

### One-shot (key applied once at the best offset)

| rank | block | cell | offset | IOC (256 runes) | cribs | head |
|---|---|---|---|---|---|---|
| 1 | K1 | col_page, low digit, sub, F rule | 847 | 0.04403 | 0 | `UBGNEXEADFMNGOJWEORNUYSTHYIPEWSFPMAEEDNGFI` |
| 1' | K1 | same, Beaufort (IOC twin) | 847 | 0.04403 | 0 | `EAEODLJSUGFIHYEOEBAELEAOXIAOMTJOEXFTIRJGHFM` |
| 2 | K2 | col_page, low digit, sub, F rule | 847 | 0.04381 | 0 | `UBGNEXEADFMNGOHWEOWNUYSTHYIPEWSFPMAEEDNGFI` |
| 3 | K1 | col_all, byte mod 29, add, F rule | 6 | 0.04301 | 0 | `POIFLUEAIAECMYFRHLFEYYCACFFSTHTHTHTEARGLXH` |
| 4 | K1 | col_all, low digit, sub, F rule | 1064 | 0.04240 | 0 | `PFBOETHAOPGEEOOENGPNFWHPCDEFXMBDJFNGDLFMEEA` |
| 5 | K1 | row, low digit, add, F rule | 74 | 0.04213 | 0 | `SHIASDYEFYCXEOENFFAEGOEEDNMUEAFTHPRRCHEOOERNG` |

Real grid maximum **0.04403**. Null grid maximum over 60 random blocks: min 0.04090, mean 0.04193, max 0.04439; **2 of 60 random blocks reach or beat the real value (p about 0.05)**. Against the H1 band the same number is 3.9 sd below the English 256-window mean and below the minimum of all 270 English windows. Control C, a real planted run in the same ciphertext, reads 0.06160 with 36 cribs and its runner-up cell is 0.04507.

### Cribs

- Top 12 cells by IOC: 0 long cribs in every one.
- Full K1 tiled crib census (32,256 decrypts): maximum 2 long cribs in any decrypt. Hex-nibble reading: 10 decrypts with 2 cribs, mean 0.045 per decrypt; six random blocks through the same reading give 6-12 such decrypts, mean 0.041-0.052, max 2. Inside the null.
- Random-block crib rate for byte mod 29: mean 0.035 per decrypt, max 1 over 256 phases.

### Secondary check: runes as key, block as ciphertext

Key material: the whole LP2 0-55 rune stream (12,956 runes, so any alignment is covered, the section itself sits at 7839-9640), as rune index 0-28 and as the Gematria Primus prime value 2-109. Operations: byte minus key, byte plus key, byte xor key, mod 256, at every offset (76,206 trials). Score: fraction of printable ASCII in the 256 output bytes, plus a search for PGP, `3301`, `.onion`, `http`, PNG/JPEG/PDF/gzip/zip/ELF/RAR headers.

| key | op | real sweep max printable | matched null sweep max (40 random rune streams) |
|---|---|---|---|
| GP prime | sub | 0.4766 at offset 2916 | min 0.4688 mean 0.4779 max 0.4922 |
| GP prime | add | 0.4531 at offset 5846 | min 0.4492 mean 0.4607 max 0.4766 |
| GP prime | xor | 0.4414 at offset 8616 | min 0.4336 mean 0.4401 max 0.4531 |
| rune index | sub | 0.4297 | min 0.4258 mean 0.4311 max 0.4336 (20 streams) |
| rune index | add | 0.4297 | min 0.4258 mean 0.4289 max 0.4375 |
| rune index | xor | 0.4062 | 0.4062 in every null stream (xor with 0-28 only touches the low five bits) |

The real sweep maxima sit at or below the null mean. The only "magic" hits are the two-byte gzip header `1f 8b` appearing somewhere in 256 bytes, which is expected by chance hundreds of times over 76k trials. The best candidate has byte entropy 7.158 against the block's 7.162, so nothing was removed from it.

## What kills the family

1. **Tiled keying is dead outright.** With the block repeated over the section, no reading, ordering, law, F rule or phase lifts IOC above 0.0384; three quarters of random blocks do better. The same engine reads 0.060 when a real key is planted.
2. **One-shot keying is dead against both bars.** The best 256-rune window (0.0440) is what the extreme value of random keys produces (2/60 random blocks match or exceed it) and is below the worst of 270 genuine English windows (0.0541). It carries zero long cribs and its head is flat GP Latin. The grid found a planted one-shot run at the right offset with IOC 0.0616 and 36 cribs, so the statistic has the power to see what H1 predicts.
3. **The block is uniform bytes.** 161 distinct values, entropy 7.17, hi digit 4 at its uniform rate: it looks like 2048 bits of key or ciphertext material, not like a 29-symbol or 60-symbol text. Reading it as runes directly is flat (0.0369).
4. **Nothing comes out of the other direction.** Un-keying the bytes with the section runes (or any LP2 offset) never rises above the random-rune-key sweep maximum and never exposes a file header or ASCII.
5. **Transcription is not the excuse.** K1 and K2 differ at 10 positions and give the same result to within 0.0003 at the same cells; the top one-shot cell is the same offset for both.

## What was not run

- The block as a key for pages outside onion 32-39 (any other section, or all of 0-55 at every offset). Cheap; not done because H1 was about the pages that carry the block.
- The block as a transposition key (values as column order or skip pattern) rather than an additive key.
- The block as a 2048-bit RSA object (modulus, signature, ciphertext) against the 2014 Cicada public keys. That is not a Liber Primus text attack and needs the key material, not runes.
- Combining the block key with a monoalphabetic layer (Atbash/Caesar before or after). An additive key composed with a Caesar is the same key shifted, which the phase and law sweep covers; Atbash after the key is not covered.
- Image work on the cuneiform pages (page JPEGs not used).

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

The 256-value block on onion 32-34 is a well-attested, uniform 256-byte object (two independent public readings agree; rtkd's copy has ten glyph slips). Used as a running key mod 29 over the pages that carry it and the cuneiform section that follows, in five readings, three orderings, three laws, both F rules, tiled at every phase and applied once at every offset (517,896 decrypts), it produces nothing that 60 random blocks through the same grid do not also produce, and nothing within reach of the English band that three positive controls hit. Used the other way round, the section runes do not turn the block into anything with structure. No solve. LP2 0-55 unsolved.

## Next experiment

Keep the block, drop the additive assumption. The one remaining text-side reading of "cuneiform as base 60" that this pass did not touch is **the block as a transposition instruction**: the 256 values (or their 512 base-60 digits, or the 32x8 grid shape itself) as a column order, skip schedule or grid write-in/read-out for the cuneiform section. That is a permutation family, so it is only worth running after a substitution layer is fixed (IOC is permutation-invariant, as the Mobius pass showed); the concrete falsifiable test is column-IOC lift under a period equal to a block-derived width (8, 32, 60, 256) on onion 33-39 alone. If that is flat too, the block should be treated as binary key material for something that is not the rune text, and the rune-side work should move on.

No public post. Box files only: `notes/sexagesimal-block-key-pass1.md`. Attack script, decoded block copies and per-cell JSON stayed in the VM and are not committed.
