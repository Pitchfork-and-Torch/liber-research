# Liber Primus Mobius direction-reversal pass 1 (onion 15-22)

Date: 2026-09-12 (America/New_York). Gauntlet cycle 3.
Source: public Liber Primus rune transcription, fetched fresh for this pass from two independent public copies (rtkd master transcription with `%` page and `/` line delimiters; scream314 `liber_primus.md`). Full rune dump is not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts). Atbash / Vigenere / totient replays match the earlier passes in this repo.
Method family: **section-wide direction-reversal transposition** on the Mobius section (onion 15-22) read as one ciphertext. The marginalia hint is taken literally: a Mobius strip has one side and a half twist, so the family is "reverse the reading direction somewhere" - whole stream, per page, per line, per word, at a midpoint, in blocks, or as a half-twist interleave. Readout is direct Gematria after the permutation.
Not rail-fence (height-measured rail on 0-2 is already NULL_ATTACK, 2026-09-12). Not regular columnar (burned in `notes/transposition-pass1.md`). Not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not pad/hash-chain, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, WELCOME, AN END, PARABLE and a decode then yields continuous readable 3301-style English. Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd parses to **72 rune pages**. The first page starting `SHEOGMIAF` is rune-page 15 = onion 0. Onion 15-22 are therefore rune-pages 30-37. Heads and lengths against the Steward box extract:

| onion | rtkd page | n | lines | words | head (rtkd) | Steward head | match |
|---|---|---|---|---|---|---|---|
| 15 | 30 | 159 | 8 | 42 | `FULMAEAYOEALUNGNCU` | `FULMAEAYOEALUINGNCU` | yes (see note) |
| 16 | 31 | 267 | 12 | 69 | `EDAAETOEAEEAXCEATOD` | `EDAAETOEAEEAXCEATOD` | yes |
| 17 | 32 | 273 | 12 | 79 | `LTHPDTHEOBIAABANMCN` | `LTHPDTHEOBIAABANMCN` | yes |
| 18 | 33 | 260 | 12 | 68 | `EAAJEOEALRGSWOBIEAC` | `EAAJEOEALRGSWOBIEAC` | yes |
| 19 | 34 | 271 | 12 | 74 | `NOOENFOIFUSNDWEAEOP` | `NOOENFOIFUSNDWEAEOP` | yes |
| 20 | 35 | 269 | 12 | 71 | `PJUBGIEOPXYPOETHDRE` | `PJUBGIEOPXYPOETHDRE` | yes |
| 21 | 36 | 273 | 12 | 60 | `CAEEADCGOIEONOEGYCT` | `CAEEADCGOIEONOEGYCT` | yes |
| 22 | 37 | 131 | 6 | 32 | `NGMIGJGCOTHETHJYFT` | `INGMIGJGCOTHETHJYFT` | yes (see note) |

Note: the only text difference is the rune ᛝ glossed `ING` in the Steward heads and `NG` here. Same rune, same index 21. Not a transcription disagreement.

Cross-check: scream314 groups 15-22 as one block and moves the page-15 rubric `FULM AEAYOEA` into its own "15.jpg" section with the number square. Rubric (9 runes) + block (1894 runes) = 1903 runes, **identical rune-for-rune** to the rtkd concatenation of pages 30-37. Two public sources agree, so the ciphertext used below is not invented. **PASS_ALIGN.**

Section stream: **n = 1903**, raw IOC **0.03450** (1/29 = 0.03448). Drop-F: n = 1831 (72 F, 3.78%), IOC 0.03574. Per-page raw IOC 0.03354-0.03598, all flat.

## Calibration

Known methods replayed on the fresh fetch. Attack proceeds only if all four pass.

### A_WARNING: ok=True

- method: Atbash p = 28-c on rune-page 0
- n_runes: 184, IOC 0.06403
- preview: `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX PERIENCE Y`

### WELCOME: ok=True

- method: Vigenere DIVINITY (DIUINITY) on rune-page 1; consume F at 5, 14 (M of each WELCOME) and 47 (O of OF); skip remaining F as interrupter
- n_runes: 251
- preview: `WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EASY TRIP BUT FOR THOSE WHO FIND THEIR WAY HERE IT IS A NECESSARY ONE A LONG THE WAY YOU WILL FIND AN EN D TO`
- no-skip title head: `WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTO`

### AN_END: ok=True

- method: totient p = (c-(prime-1)) mod 29 on rune-page 70; skip F at page-local 56 (the OF interrupter)
- n_runes: 85, IOC 0.07003
- preview: `AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PILGR IM TO SEEC OUT THIS PAGE`

### PARABLE: ok=True

- method: direct Gematria Primus on rune-page 71
- n_runes: 95, IOC 0.06271
- preview: `PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND TH E DIUINITY WITHIN AND EMERGE`

**PASS_CALIB.**

### Engine self-test

Every variant is built as an explicit permutation array `p` (output[i] = input[p[i]]), so the inverse is exact. 98 variants on the 1903-token stream:

- every `p` is a permutation of 0..1902: ok
- random stream through `p` then `inv(p)` returns the input for all 98: ok (0 failures)
- positive control: PARABLE + A WARNING plaintext + AN END plaintext (364 runes, English-on-GP, IOC 0.06593, 26 long-crib hits) pushed forward through each variant, then back through the inverse: plaintext restored in **all** variants; IOC of the forward output is **0.06593 in every trial** (permutation-invariant); the forward output keeps all 26 long cribs in only 5/96 variants (the three segment-swap variants that leave long runs contiguous), and destroys them elsewhere. So the machinery does move text and does undo itself.

Variants that are involutions (plain reversals) are tried once; the rest are tried as both forward and inverse, since it is unknown whether 3301 would have applied the operation as encrypt or decrypt.

## Definition of the family (concrete grid)

One stream = onion 15..22 concatenated in page order (rtkd word and line cuts kept as token metadata). Three F modes: `none`, `before` (drop every F, then permute), `after` (permute, then drop F). Duplicate outputs across modes/variants were removed.

| group | variants |
|---|---|
| whole stream | reverse whole stream |
| page level | page order 22->15; each page reversed in place; odd pages (15,17,19,21) reversed; even pages (16,18,20,22) reversed; page order 22->15 with odd or even pages reversed |
| line level (rtkd `/` cuts) | line order reversed within each page; each line reversed, order kept; line order reversed and each line reversed; boustrophedon (every other line reversed, even or odd start) |
| word level (rtkd `-`/`.` cuts) | word order reversed within page; within line; across the whole section; each word reversed; every other word reversed |
| half twist at 1/2 | second half reversed; first half reversed; halves swapped; halves swapped + second reversed; interleave A[i],revB[i]; interleave revB[i],A[i]; plain interleave A[i],B[i] |
| midpoints 1/3, 2/3, thirds | tail reversed / head reversed / segments swapped at 1/3 and at 2/3; thirds with every reverse mask (7); thirds in order 3,2,1 forward and each reversed |
| blocks | block size 2..16, each block reversed; block size 2..16, alternate blocks reversed |
| page-wise | blocks of 2,3,4,5,6,7,8,12,16 restarting at each page; per-page second-half reversed; per-page half-twist interleave; per-page halves swapped |
| compositions | reverse whole stream then blocks of 3,5,7,8 |

98 permutations x 3 F modes = 294 runs, **261 unique outputs**. Well inside the 500-2000 cap. Not rail-fence, not columnar.

## Scoring

- IOC vs 0.03448 baseline (reported, but see the invariance note).
- Long cribs: GP rune sequences of length >= 4 runes for DIVINITY, PILGRIM, BELIEVE, WELCOME, WARNING, INSTAR, CIRCUMFERENCE, TRUTH, WISDOM, PRIMES, SACRED, EMERGE, SURFACE, MASTER, STUDENT, INNOCENCE, ILLUSIONS, JOURNEY, TOWARD, CONSUME, ENLIGHTEN, KNOWLEDGE, EXPERIENCE, NOTHING, EVERY, WITHIN, THINGS, DEATH, THAT, THEIR, THERE, WHICH, SHED, KOAN, GREAT, HOLY, UNTO, YOUR, FROM, THIS, WITH, DUTY, SEEK, PAGE, DEEP, BOOK, FIND, LOSS (encoded the way 3301 writes them: K->C, V->U, ING->ᛝ, digraph runes greedy, so DEATH = D-EA-TH is 3 runes and lands in the short list).
- Short cribs (2-3 runes): THE, AND, YOU, ARE, NOT, FOR, ALL, ONE, WHO, LAW, END, WEB, OUR, OWN, WAY, OUT plus the 3-rune long-list words. Counted, not scored as evidence.
- Best sliding-window IOC at 50 and 100 runes.
- Null: 300 random shuffles of the same stream (and of the F-dropped stream).
- Word-aligned dictionary check for the word-preserving variants: 180 GP word tuples (len >= 2) taken from the solved pages.

### Baseline and null

| stream | n | IOC | long cribs | short cribs | best win50 | best win100 |
|---|---|---|---|---|---|---|
| raw 15-22 | 1903 | 0.03450 | 0 | 4 | 0.05224 | 0.04121 |
| raw drop-F | 1831 | 0.03574 | 0 | 4 | - | - |
| null, 300 shuffles | 1903 | 0.03450 | mean 0.03 (291 at 0, 9 at 1, max 1) | mean 3.67, 0-11 | mean 0.0549, max 0.0784 | mean 0.0433, max 0.0523 |
| null, 300 shuffles drop-F | 1831 | 0.03574 | mean 0.05 (max 2) | mean 3.70, 0-11 | mean 0.0561, max 0.0743 | mean 0.0445, max 0.0552 |

Word-cut dictionary hits: raw 3 of 495 words (`WE EX IM`); each-word-reversed 4 (`BY IM CE OF`); null over 200 shuffles mean 2.94, max 9.

## Attack table

| family | unique trials | F modes | long cribs | short-crib range | best win100 |
|---|---|---|---|---|---|
| reverse whole stream | 2 | none, before | 0 | 2-2 | 0.04283 |
| page-order / per-page reversal | 12 | none, before | 0 | 2-4 | 0.04242 |
| line-order / boustrophedon | 8 | none, before | 0 | 2-5 | 0.04303 |
| word-order / within-word | 11 | none, before, after | 0 | 1-6 | 0.04343 |
| half-twist 1/2 (reverse / swap / interleave) | 36 | none, before, after | 0 | 1-6 | 0.04525 |
| midpoints 1/3, 2/3, thirds | 36 | none, before, after | 0 | 2-4 | 0.04343 |
| blocks 2..16 (each / alternate) | 90 | none, before, after | 0 | 0-6 | 0.04505 |
| page-wise blocks 2..16 | 27 | none, before, after | 0 | 1-4 | 0.04444 |
| page-wise half-twist / swap | 15 | none, before, after | 0 | 1-6 | 0.04909 |
| reverse whole then blocks | 24 | none, before, after | 0 | 2-7 | 0.04485 |
| **total** | **261** | | **0** | **0-7** | **0.04909** |

For structural reversals (page, line, word) the `after` F mode collapses onto `before`, because dropping F commutes with reversing whole groups; those duplicates were removed.

Top rows (there is nothing to rank by long cribs, so the highest short-crib counts and highest window-100 are shown):

| F | variant | n | IOC | long | short | win100 | head |
|---|---|---|---|---|---|---|---|
| before | reverse whole then blocks of 5 | 1831 | 0.03574 | - | 7 | 0.04283 | `EONGEANXTHSNBTHPGNGBIATOEWBEOXYAGEOOEEAE` |
| none | word order reversed within each page | 1903 | 0.03450 | - | 6 | 0.04061 | `XMBOEAPEANNGRTHLFBHAEJIAIIAXYOEYALTOLLXN` |
| none | word order reversed within each line | 1903 | 0.03450 | - | 6 | 0.04202 | `AEAYOEAFULMUOEAEJFAEIUIUBNTFNGCULUNGNNOE` |
| none | half-twist interleave A[i],revB[i] | 1903 | 0.03450 | - | 6 | 0.04101 | `FXUNLFMEAANGEAEOYFOETHABLNUSNGFNTHCIAUBB` |
| none | blocks of 10 alternate reversed | 1903 | 0.03450 | - | 6 | 0.04101 | `LAOEYEAAMLUFUNGNCUBNTFNGUAEFJAEOEUIUIGXE` |
| before | page-wise half-twist: second half of each page reversed | 1831 | 0.03574 | - | 3 | 0.04909 | win100 head `AAELTRIAAEDNGJOIAEAXAIAHRBIDIAJA` |
| after | page-wise half-twist: second half of each page reversed | 1831 | 0.03574 | - | 3 | 0.04889 | win100 head `LTRIAAEDNGJOIAEAXAIAHRBIDIAJAPRS` |
| after | plain interleave A[i],B[i] [inverse] | 1831 | 0.03574 | - | 4 | 0.04525 | win100 head `UTHLGEOEAAXATEBGBTHSBNGUMEAOELNG` |

Max short-crib count 7 vs null max 11. Max window-100 IOC 0.04909 vs null max 0.0523 (0.0552 drop-F). Max window-50 0.06286 vs null max 0.0784. Every head is flat GP Latin; no head reads as English.

## What kills the family

1. **Frequency invariance.** A direction reversal is a permutation of the same 29-rune multiset. IOC took exactly two values across all 261 trials: 0.03450 (no F-skip) and 0.03574 (F dropped). The section unigram counts are 50-77 per rune against a flat expectation of 65.6. English-on-GP from the solved pages has IOC ~0.062 with E about 12% and EO/OE under 1%. Onion 15-22 is not English-on-GP in any order, so **no permutation alone can read out as English**. This is the same wall the columnar pass hit on the whole book; it holds for this section too.
2. **Monoalphabetic substitution commutes with any permutation.** "Reverse then Atbash / Caesar / direct" equals "Atbash / Caesar / direct then reverse". Those monoalphabetic readouts of 0-55 are already burned (wave 1), so this pass cannot be rescued by bolting one on. Only a position-dependent cipher (Vigenere, totient, running key) would interact with a reversal, and those are burned families not rerun here.
3. **No crib survives.** 0 long cribs in 261 trials; the 300-shuffle null itself produces one by chance 3% of the time, so even a single hit would not have counted. Short-crib counts (0-7) sit inside the null (0-11).
4. **Window IOC never leaves the null.** Best 100-rune window 0.04909 < null max 0.0523. Best 50-rune window 0.06286 < null max 0.0784.
5. **Word cuts do not help.** Word-order reversals keep the word multiset (3 dictionary hits, same as raw). Reversing each word gives 4; the null mean is 2.94, max 9.
6. **Two public transcriptions agree** on the 1903 runes, so this is not a transcription miss.

## What was not run

- Rail-fence (any rail count) on 15-22: kept out on purpose; the rail family is NULL_ATTACK on 0-2 as of 2026-09-12 and this pass is not a rail.
- Reversal followed by Vigenere / Beaufort / totient / running key (burned families). HYPOTHESIS only: a reversed stream would change which key digit meets which rune, so a totient-style position cipher on a reversed section is technically distinct from the burned run. Not tested here; it would need the same calibration rail and a fresh receipt.
- Reversal on any section other than 15-22.
- Image work on the Mobius marginalia (page JPEGs not used; no pixel measurement).

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, attack null).

Onion 15-22 concatenate to a 1903-rune stream that two public sources agree on. The four calibration pages replay. The reversal engine inverts exactly and restores known English in the positive control. On the real section, 261 unique direction-reversal readouts (whole, page, line, word, half-twist, thirds, blocks 2-16, page-wise, with and without F-skip) produced zero long cribs, short-crib and window-IOC values inside a 300-shuffle null, and no readable head. IOC is permutation-invariant at 1/29, so the family is structurally unable to produce English from this section without a substitution layer, and the monoalphabetic layers commute with it and are already burned. No solve. LP2 0-55 unsolved.

No public post. Box files only: `notes/mobius-direction-reversal-pass1.md`. Attack script and per-trial JSON stayed in the VM and are not committed.
