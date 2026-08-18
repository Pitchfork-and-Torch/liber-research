# Liber Primus columnar transposition pass 1

Date: 2026-08-14 (America/New_York)
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo.
Parser/constants: reused from `box-only desk parser (not in this repo)` (`GP`, `LATIN`, `R2I`, `RUNESET`, `parse_pages`, `page_runes`, `ioc`, `to_latin`). Atbash / Vigenere / totient match `box-only running-key runner (not in this repo)` and `box-only periodic runner (not in this repo)`.
Method family: **regular columnar transposition only**. Write-by-rows/read-by-columns and the inverse write-by-columns/read-by-rows, each with column direction LTR/RTL and row direction TTB/BTT (8 variants). Widths 5 through 60 inclusive (56 = traditional LP2 page count is inside that range). Two scopes: the whole unsolved stream as one block, and each unsolved rune page separately.
Not polyalphabetic. Not Wave 1. Not book-index. Not running-key from AN END/PARABLE. Not periodic Vigenere/Beaufort. Not SHA-512. Not YOUR INNOCENCE pad. Not INSTAR JPEGs. Not a W! column-order brute.

Honesty rail: no claimed solve unless calibration replays and a decode lifts a *readable window* to 3301 English. Global IOC cannot lift under a permutation. A single crib collision in a 12k stream is not a solve.

## Calibration

Known methods replayed on this transcription. Attack proceeds only if all four pass.

### A_WARNING: ok=True

- method: Atbash p = 28-c on parse_pages[0] / rtkd[0]
- n_runes: 184
- preview: `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX PERIENCE YOUR DEATH DO NOT EDIT O R CHANGE THIS BOOC OR THE MESSAGE CONTAINED WITHIN EITHER THE WO RDS OR THEI`
- note: GP spelling WARNNG/BELIEUE/NOTHNG/BOOC is the known plaintext, not a miss

### WELCOME: ok=True

- method: Vigenere DIVINITY; consume F at 5 and 14 (M in each WELCOME title) and F at 47 (O of OF); skip remaining F as interrupter. Title F that is M is not skipped.
- n_runes: 515
- preview: `WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EASY TRIP BUT FOR THOSE WHO FIND THEIR WAY HERE IT IS A NECESSARY ONE A LONG THE WAY YOU WILL FIND AN EN D TO AFNG NGYUBYSFE THAEU E`
- note: Opening through ALONG THE WAY YOU WILL FIND AN END TO A is the known WELCOME plaintext (GP: THNGS). Middle then breaks; later recovers ARE A LAW UNTO YOURSELF EACH INTELLIGENCE IS HOLY. Middle gap is the known INNOCENCE/ILLUSIONS region and is not treated as method failure.

### AN_END: ok=True

- method: totient p=(c-(prime-1)) mod 29; skip F at page-local index 56 (the OF interrupter). Community 'index 202' does not exist on this 85-rune page; skip-202 is a no-op and leaves DUTY OOE.
- n_runes: 85
- preview: `AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PILGR IM TO SEEC OUT THIS PAGE`

### PARABLE: ok=True

- method: direct Gematria Primus
- n_runes: 95
- preview: `PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND TH E DIUINITY WITHIN AND EMERGE`

CALIBRATION_PASS True

WELCOME title-only no-skip (parse_pages[1], consume the F that is M): ok=True, head=`WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTO`.

## Target

Unsolved LP2 0-55 rune stream = `parse_pages` indices 15..69. The hex-only rtkd page inside that span is dropped by the rune-page parser, so this is **55 rune pages**, **12956 runes**, raw IOC = **0.03448** (1/29 = 0.03448). Traditional label "LP2 0-55" counts 56 pages including the hex page; width 56 is still in the 5..60 grid.

Work is in rune indexes / GP Latin, not UTF-8 bytes. Direct Gematria (no extra cipher) is the only readout after untranspose: the untransposed index stream mapped through `LATIN`.

Page lengths: min 66, max 277. Per-page raw IOC range 0.02844-0.03789 (all flat). Lengths: 0:262, 1:266, 2:201, 3:217, 4:261, 5:263, 6:196, 7:208, 8:255, 9:268, 10:263, 11:273, 12:261, 13:272, 14:137, 15:159, 16:267, 17:273, 18:260, 19:271, 20:269, 21:273, 22:131, 23:213, 24:270, 25:273, 26:265, 27:234, 28:269, 29:277, 30:263, 31:269, 32:121, 33:214, 34:261, 35:271, 36:238, 37:228, 38:228, 39:240, 40:231, 41:273, 42:272, 43:274, 44:273, 45:270, 46:270, 47:274, 48:271, 49:66, 50:92, 51:263, 52:179, 53:232, 54:76.

DJUBEI = D J U B E I = indexes `[23, 11, 1, 17, 18, 10]`. Rune-stream hits at global **6555** and **12950**. Both are a **6-gram split across two 3-rune words**: `DJU` | `BEI` (page 27 local 28-33; page 54 local 70-75, end of stream). Compact-Latin hits at AZ offsets 8187 and 16125 (Latin is longer than the rune count because of TH/NG/EO/OE/IA/AE/EA). The test this pass can actually make is whether an untranspose glues that split into one word, or produces any other 3301 word. It did neither.

## Method

Grid shape: width W, `nrows = ceil(n/W)`, last row short on the right. Reversing columns or rows reverses **iteration order** only; the ragged edge stays on the right. That is 2 fills x 2 column dirs x 2 row dirs = **8 variants per width**, not W!.

| fill | meaning |
|---|---|
| `rows_cols` | write by rows, read by columns (standard columnar *encrypt*) |
| `cols_rows` | write by columns, read by rows (standard columnar *decrypt* / inverse) |

Self-test invertibility on random streams (n in 10..277, W in 5..56, all 8 flags): **ok=True**.

Positive control: take PARABLE (direct English, n=95, IOC=0.06271) and A WARNING plaintext (Atbash, n=184, IOC=0.06403), columnar-encrypt (`rows_cols`), then decrypt (`cols_rows`) at W=5,7,8,13,17 x 4 direction flags. Recover-all=True. IOC of ciphertext equals IOC of plaintext in every trial (`ioc_invariant=True`). Encrypt breaks the readable head; decrypt restores it. The machinery works on known English.

## Frequency invariance (why global IOC cannot be the success meter)

Transposition is a permutation of the same 29-rune multiset. `sum n_i(n_i-1) / (N(N-1))` does not change. The raw stream is already **0.03448 = 1/29**. Therefore:

- If LP2 0-55 were *English written in a grid and read by columns* (no substitution), the **raw** global IOC would already be ~0.06. It is not. Direct Gematria of the raw stream is not English.
- Untranspose cannot lift whole-stream IOC toward 0.06. Unrounded IOC is identical on every trial (checked on W=5,17,29,48,56,60: delta 0.0, same multiset). A first-draft `round(ioc,5) - raw` counter reported 448 "changes"; that was 1e-6 rounding noise, not a lift. Displayed IOC stays **0.03448**.
- The real test is a *window* (page, or 50-200 runes) becoming readable 3301 English after untranspose, or DJUBEI / known words lining up as words rather than a 6-gram. A lone crib in 12k runes is not that.

Direct Gematria after untranspose is the same operation as reading the untransposed indexes as GP Latin. There is no second cipher in this pass.

## Baseline (no transposition)

Whole-stream direct Gematria:

- n=12956, IOC=0.03448
- head: `SHEOGMIAFSYENGCTHJGAEFJOEONTHNEWBASOEEOINGUNAEGITHHBNIAPBNEOJ`
- long cribs in compact Latin: DJUBEI@[8187, 16125]
- DJUBEI rune positions: [6555, 12950]
- word-aligned DJUBEI under the original hyphen/dot cuts: **none** (raw cut is `DJU` + `BEI`, two 3-rune words)
- 3301 word-runs (3+ tokens, >=12 compact letters): none

Chance shorties in compact Latin (not scored as cribs): THE appears in the raw AZ stream; AND/YOU/THIS at 1-4 hits. Expected junk in 16k GP letters.

Best raw sliding-window IOC (step 1):

| window | IOC | start | head |
|---|---|---|---|
| 50 | 0.06204 | 9463 | `GRIEOYOOEUNGRGMTGBPGMTMYWBT` |
| 100 | 0.04485 | 31 | `INGUNAEGITHHBNIAPBNEOJTHANGYXBD` |
| 200 | 0.03824 | 3542 | `XNGXTHEADCBGXWNGUXDPXIAPOENIAFIA` |

Null: 8 random permutations of the same stream, max window IOC:

| window | null mean | null min | null max |
|---|---|---|---|
| 50 | 0.06245 | 0.05714 | 0.0702 |
| 100 | 0.04679 | 0.04525 | 0.04889 |
| 200 | 0.04029 | 0.03965 | 0.04136 |

A transposition that merely matches this null is rearrangement noise, not English.

## Whole-stream results

Trials: **448** (56 widths x 8 variants).

Non-DJUBEI compact cribs: **35** trials, and they are weak:
- **COAN** (GP for KOAN, 4 Latin letters / 4 runes): 29 trials. Raw stream has 0. Expected junk in 16k GP letters; 4-grams are not a solve.
- **EUERY** (GP for EVERY, 5 letters): 6 trials, all at W=48 or 49. Context e.g. `...THMUEUERYIALGS...` - not a sentence. Raw stream has 0 EUERY runes.
Variants that still contain a DJUBEI 6-gram: **0** (every non-degenerate grid splits the two raw hits).
Word-aligned recut hits: isolated `THNGS` / `DEATH` / one `THREE` / one `THINGS` (3-4 runes). Those are short CONTENT words landing on the original 3316 hyphen cuts; no cluster, no DJUBEI word.
3301 word-runs (3+ tokens): **0**.
Whole-stream trials with max-window-100 above the 8-shuffle null max (0.04889): **38**, best **0.05273**.
Whole-stream trials with max-window-200 above the 8-shuffle null max (0.04136): **20**, best **0.04221**.
Eight shuffles are a thin null. 0.053 on a 100-rune window is not English-on-29 (~0.06) and the window heads are unreadable. Treat as clump noise.

### Extra long cribs (whole stream)

| W | variant | cribs | head |
|---|---|---|---|
| 5 | `rows_cols_ltr_ttb` | COAN@[10351] | `SMEGOWEOAEBNNGPGFNGBNGHYTHITYFINGYBFEABI` |
| 5 | `rows_cols_ltr_btt` | COAN@[7136] | `SHIANGAENBIGNEOYEFPXUAEXFAIAHENTHEADCMJX` |
| 5 | `rows_cols_rtl_ttb` | COAN@[10350] | `SMEGOWEOAEBNNGPGFNGBNGHYTHITYFINGYBFEABI` |
| 5 | `rows_cols_rtl_btt` | COAN@[7135] | `HIANGAENBIGNEOYEFPXUAEXFAIAHENTHEADCMJXD` |
| 8 | `cols_rows_ltr_btt` | COAN@[8703] | `SIAOAEHJXAOEEDJEPYEOTPOIOMMXDJLAGDFCIAOI` |
| 16 | `cols_rows_ltr_ttb` | COAN@[1233] | `SSIAYONGAEIAOEOEPGLEAIUHNJGXAEAJTOJJIAEA` |
| 16 | `cols_rows_ltr_btt` | COAN@[1249] | `SSIAYONGAEIAOEOEPGHNJGXAEAJTOJJLEAIUEWPO` |
| 23 | `cols_rows_ltr_ttb` | COAN@[11345] | `SUTHEAEUDCOEXPCJYWWCICEGNGYHTHANGEAAEWBD` |
| 23 | `cols_rows_ltr_btt` | COAN@[11322] | `SUTHEAEUDHTHANGEAAEWCOEXPCJYWWCICEGNGYEH` |
| 29 | `cols_rows_ltr_ttb` | COAN@[597] | `SSCJEOCMYBPEATHOEENGAELSOEYHLHFGAEAYHNAE` |
| 29 | `cols_rows_ltr_btt` | COAN@[587] | `SSCJEOCMYBPEATHOEENGAELSOEYHHNAEIATEAUUO` |
| 29 | `cols_rows_rtl_ttb` | COAN@[847] | `SWCEABMFCAORINGPSEORRWTXEAFYEAWGAEGHSYAP` |
| 29 | `cols_rows_rtl_btt` | COAN@[838] | `CAORINGPSEORRWTXEAFYEAWGAEGSWCEABMFTEGIA` |
| 31 | `rows_cols_ltr_btt` | COAN@[10401] | `SOEGFTHTHLEAOAEHTHGIAGJALHJFEADUTIMDHTIN` |
| 39 | `rows_cols_ltr_ttb` | COAN@[9354] | `SHOEODNTLHTHXSCMEDEXEAHREAEOTIEONGTOEUSX` |
| 39 | `rows_cols_ltr_btt` | COAN@[6004] | `SSJXNGLEAUPSFFFIAUPTFCCYMYHIAEANGUGBIBNG` |
| 39 | `rows_cols_rtl_ttb` | COAN@[9346] | `SHOEODNTLHTHXSCMEDEXEAHREAEOTIEONGTOEUSX` |
| 39 | `rows_cols_rtl_btt` | COAN@[5995] | `SJXNGLEAUPSFFFIAUPTFCCYMYHIAEANGUGBIBNGN` |
| 42 | `rows_cols_ltr_ttb` | COAN@[5669] | `SIAAEEAPBFXEAOERWXEIAPLAWEOTXEAIAGEOERXD` |
| 42 | `rows_cols_ltr_btt` | COAN@[14116] | `SOSEOJAEYSHXFIPPHTHNGCRLHIEAJOEJSATHFAEO` |
| 42 | `rows_cols_rtl_ttb` | COAN@[5649] | `SIAAEEAPBFXEAOERWXEIAPLAWEOTXEAIAGEOERXD` |
| 42 | `rows_cols_rtl_btt` | COAN@[14109] | `OSEOJAEYSHXFIPPHTHNGCRLHIEAJOEJSATHFAEOU` |
| 43 | `cols_rows_rtl_ttb` | COAN@[8756] | `SOEOCEOELNLJSMLMOEFAECTDXBOEBSNOELWNYEOE` |
| 43 | `cols_rows_rtl_btt` | COAN@[8772] | `YEOENDAOEEADSJOXSOEOCEOELNLJSMLMOEFAECTD` |

### DJUBEI after untranspose

Raw: the 6-gram is **already split** as `DJU` | `BEI` at both hits (words 1666-1667 and 3314-3315). After a width-W columnar rewrite those six consecutive runes become a column (or a broken column). Survivors of the 6-gram itself: **0**. Survivors of DJUBEI as a single recut word: **0**. Untranspose does not glue the split.

Word-length recut (original 3316 word lengths applied to the untransposed stream) produced only stray 3-4 rune CONTENT tokens (`THNGS`, `DEATH`, once `THREE`, once `THINGS`). Not a clustered word, not DJUBEI.

### Top window-50 IOC

| W | variant | win50 IOC | start | global IOC | cribs | head |
|---|---|---|---|---|---|---|
| 17 | `cols_rows_ltr_btt` | 0.08 | 8662 | 0.03448 | - | `SPHNIAEILWNPAEPAHXDTHEOEYBIAETEAGLXA` |
| 52 | `cols_rows_ltr_btt` | 0.07592 | 7884 | 0.03448 | - | `SOEFNMIAIADHLJADEODBEOYUTHSXDBRNIYYO` |
| 48 | `cols_rows_ltr_btt` | 0.07429 | 5356 | 0.03448 | - | `SUEASOETIAXSYAEPOAECNGEDAEAERIAWROEN` |
| 42 | `rows_cols_ltr_btt` | 0.07347 | 11106 | 0.03448 | COAN@[14116] | `SOSEOJAEYSHXFIPPHTHNGCRLHIEAJOEJSATH` |
| 17 | `cols_rows_ltr_ttb` | 0.07265 | 5384 | 0.03448 | - | `SPIAEILWNPAEPAHXDTHEOHNBIAETEAGLXAEA` |
| 42 | `rows_cols_rtl_ttb` | 0.07265 | 4311 | 0.03448 | COAN@[5649] | `SIAAEEAPBFXEAOERWXEIAPLAWEOTXEAIAGEO` |
| 36 | `cols_rows_rtl_ttb` | 0.07102 | 6730 | 0.03448 | - | `SFFYGNXWTNGLECNGAEJHOTDWHNGNNGCHPEOY` |
| 39 | `rows_cols_ltr_ttb` | 0.07102 | 159 | 0.03448 | COAN@[9354] | `SHOEODNTLHTHXSCMEDEXEAHREAEOTIEONGTO` |

Baseline best-50 = 0.06204; null max-50 = 0.0702.

### Top window-100 IOC

| W | variant | win100 IOC | start | global IOC | cribs | head |
|---|---|---|---|---|---|---|
| 58 | `rows_cols_ltr_ttb` | 0.05273 | 8602 | 0.03448 | - | `SFNHHDLIAYLETIANGWHIJAEPPDETHEANGXHD` |
| 58 | `rows_cols_ltr_btt` | 0.05273 | 3691 | 0.03448 | - | `STHNGDNGMHGEAFHEODFRBCXGNSIDYHYTYRPO` |
| 58 | `rows_cols_rtl_ttb` | 0.05273 | 8582 | 0.03448 | - | `SFNHHDLIAYLETIANGWHIJAEPPDETHEANGXHD` |
| 58 | `rows_cols_rtl_btt` | 0.05273 | 3674 | 0.03448 | - | `THNGDNGMHGEAFHEODFRBCXGNSIDYHYTYRPON` |
| 53 | `cols_rows_rtl_ttb` | 0.05172 | 4327 | 0.03448 | - | `SSJHEANGOIAYEODGAJDUTEAIAOGPPOFSOFDA` |
| 34 | `cols_rows_ltr_ttb` | 0.05091 | 4366 | 0.03448 | - | `SAENJIJAETHIBLWWLNEAPEAERPIAAMHWXDDO` |
| 51 | `rows_cols_ltr_ttb` | 0.0503 | 9790 | 0.03448 | - | `SYYTHMROEGTHEAFRYXAYMTDMTHNGLPOELDNG` |
| 51 | `rows_cols_ltr_btt` | 0.0503 | 9282 | 0.03448 | - | `SEBEOIXDHFCFGHSWJSLREOXUWSEYFSTHOJAA` |
| 51 | `rows_cols_rtl_ttb` | 0.0503 | 9788 | 0.03448 | - | `SYYTHMROEGTHEAFRYXAYMTDMTHNGLPOELDNG` |
| 51 | `rows_cols_rtl_btt` | 0.0503 | 9280 | 0.03448 | - | `EBEOIXDHFCFGHSWJSLREOXUWSEYFSTHOJAAR` |
| 51 | `cols_rows_rtl_ttb` | 0.0503 | 3346 | 0.03448 | - | `SMFIAEONGRWLYOEHFWDAADNTHAENGUUTHEEM` |
| 24 | `rows_cols_ltr_ttb` | 0.0501 | 5815 | 0.03448 | - | `SETHIAAIEPMEOOEMBHEASSTHGEAAXOEEOEAS` |

Baseline best-100 = 0.04485; null max-100 = 0.04889.

### Top window-200 IOC

| W | variant | win200 IOC | start | global IOC | cribs | head |
|---|---|---|---|---|---|---|
| 43 | `cols_rows_rtl_btt` | 0.04221 | 1782 | 0.03448 | COAN@[8772] | `YEOENDAOEEADSJOXSOEOCEOELNLJSMLMOEFA` |
| 44 | `rows_cols_ltr_ttb` | 0.04181 | 3606 | 0.03448 | - | `SBPXEAGMHPYIYOEJDDOGNGCLEAJCEABGSWEW` |
| 44 | `rows_cols_ltr_btt` | 0.04181 | 10669 | 0.03448 | - | `SOTIAGNGOERBIAOWXEOFEDUMWCIEAOEFBCEA` |
| 44 | `rows_cols_rtl_ttb` | 0.04181 | 3594 | 0.03448 | - | `SBPXEAGMHPYIYOEJDDOGNGCLEAJCEABGSWEW` |
| 44 | `rows_cols_rtl_btt` | 0.04181 | 10662 | 0.03448 | - | `OTIAGNGOERBIAOWXEOFEDUMWCIEAOEFBCEAE` |
| 5 | `rows_cols_ltr_ttb` | 0.04161 | 10617 | 0.03448 | COAN@[10351] | `SMEGOWEOAEBNNGPGFNGBNGHYTHITYFINGYBF` |
| 5 | `rows_cols_ltr_btt` | 0.04161 | 8026 | 0.03448 | COAN@[7136] | `SHIANGAENBIGNEOYEFPXUAEXFAIAHENTHEAD` |
| 5 | `rows_cols_rtl_ttb` | 0.04161 | 10616 | 0.03448 | COAN@[10350] | `SMEGOWEOAEBNNGPGFNGBNGHYTHITYFINGYBF` |
| 5 | `rows_cols_rtl_btt` | 0.04161 | 8025 | 0.03448 | COAN@[7135] | `HIANGAENBIGNEOYEFPXUAEXFAIAHENTHEADC` |
| 58 | `rows_cols_ltr_ttb` | 0.04161 | 4576 | 0.03448 | - | `SFNHHDLIAYLETIANGWHIJAEPPDETHEANGXHD` |
| 58 | `rows_cols_rtl_btt` | 0.04161 | 12604 | 0.03448 | - | `THNGDNGMHGEAFHEODFRBCXGNSIDYHYTYRPON` |
| 58 | `cols_rows_ltr_ttb` | 0.04161 | 8731 | 0.03448 | - | `SUNLNCYCUOEYDCDTEPBDTHANGPOGEFOTNTMT` |

Baseline best-200 = 0.03824; null max-200 = 0.04136.

None of those heads is 3301 English. The best 100-rune window (0.05273 at W=58 `rows_cols_*`) is a few thousandths above a thin 8-shuffle null and still reads as `SFNHHDLIAYLETIANGWHI...`. Not a lift to readable English.

## Per-page results

Trials: **24640** (55 rune pages x widths 5..60 with W < page length x 8 variants). Per-page **global** IOC is also invariant (same runes). Pages are 66-277 runes, so a 50-200 window is most of a page; "window IOC" here is local clumpiness, not a new alphabet.

DJUBEI lives on rune-pages 27 local=[28], 54 local=[70].

### Page trials that grew a long crib or 3301 run

| lp2 | n | W | variant | cribs | word-aligned | head |
|---|---|---|---|---|---|---|
| 0 | 262 | 37 | `cols_rows_ltr_btt` | COAN@[148] | - | `SSAEHYFEITHNXXPYNGTHJIAIAFTHECNB` |
| 3 | 217 | 49 | `rows_cols_ltr_ttb` | - | THNGS | `LLYAEBJEACEAOEORJGXHLLSINGLCLYCE` |
| 7 | 208 | 11 | `rows_cols_ltr_btt` | - | DEATH | `HIAPTHTWEAEONGCIASYAWTAENTNGLURS` |
| 7 | 208 | 19 | `cols_rows_rtl_ttb` | - | DEATH | `HIAPTHTWEAEONGCIASYAWTAENTNGLURS` |
| 9 | 268 | 9 | `cols_rows_rtl_ttb` | - | DEATH | `YOUTHUSOESOEWDSMEEOYOENAESOECYDE` |
| 9 | 268 | 30 | `rows_cols_ltr_btt` | - | DEATH | `YDUTHUSOESOEWOSMEEOYOENAEDOECYDE` |
| 9 | 268 | 43 | `cols_rows_rtl_btt` | - | THNGS | `EONASMAEOUFRYMNOEPDOEOEHLOEIANGY` |
| 9 | 268 | 53 | `rows_cols_rtl_btt` | - | DEATH | `GRGPGJTXJGNGUYOWMSYIAAAOERGSWTHJ` |
| 11 | 273 | 5 | `rows_cols_ltr_ttb` | COAN@[228] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 5 | `rows_cols_ltr_btt` | COAN@[20] | - | `IAENGBIUCSCANXTUALCBCOANNCNGEODI` |
| 11 | 273 | 5 | `rows_cols_rtl_ttb` | COAN@[226] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 5 | `rows_cols_rtl_btt` | COAN@[18] | - | `ENGBIUCSCANXTUALCBCOANNCNGEODIAT` |
| 11 | 273 | 49 | `cols_rows_rtl_ttb` | COAN@[202] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUXE` |
| 11 | 273 | 49 | `cols_rows_rtl_btt` | COAN@[237] | - | `UXEAEOCNUTCXTUEATANGIANGHWADHLAG` |
| 11 | 273 | 50 | `cols_rows_rtl_ttb` | COAN@[204] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 50 | `cols_rows_rtl_btt` | COAN@[233] | - | `NUTCXTUEATANGIANGHWADHLAGOIABNRN` |
| 11 | 273 | 51 | `cols_rows_rtl_ttb` | COAN@[209] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 51 | `cols_rows_rtl_btt` | COAN@[232] | - | `TUEATANGIANGHWADHLAGOIABNRNNNGOE` |
| 11 | 273 | 52 | `cols_rows_ltr_ttb` | COAN@[20] | - | `IANEAIGNGRUNMTHFIACBCOANNCNGEODI` |
| 11 | 273 | 52 | `cols_rows_ltr_btt` | COAN@[34] | - | `IANEAIGNGRUNMTHFIASLBWNYXAJLANGL` |
| 11 | 273 | 52 | `cols_rows_rtl_ttb` | COAN@[215] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 52 | `cols_rows_rtl_btt` | COAN@[230] | - | `NGIANGHWADHLAGOIABNRNNNGOEAEAXLT` |
| 11 | 273 | 53 | `cols_rows_ltr_ttb` | COAN@[19] | - | `IANEAIGNGRUNXTUALCBCOANNCNGEODIA` |
| 11 | 273 | 53 | `cols_rows_ltr_btt` | COAN@[27] | - | `IANEAIGNGRUSLBWNYXANXTUALCBCOANN` |
| 11 | 273 | 53 | `cols_rows_rtl_ttb` | COAN@[219] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 53 | `cols_rows_rtl_btt` | COAN@[228] | - | `WADHLAGOIABNRNNNGOEAEAXLTHYIAIUE` |
| 11 | 273 | 54 | `cols_rows_ltr_ttb` | COAN@[19] | - | `IANEAIUCSCANXTUALCBCOANNCNGEODIA` |
| 11 | 273 | 54 | `cols_rows_ltr_btt` | COAN@[22] | - | `IANEASLBIUCSCANXTUALCBCOANNCNGEO` |
| 11 | 273 | 54 | `cols_rows_rtl_ttb` | COAN@[225] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 54 | `cols_rows_rtl_btt` | COAN@[228] | - | `AGOIABNRNNNGOEAEAXLTHYIAIUEOOFOE` |
| 11 | 273 | 55 | `cols_rows_ltr_ttb` | COAN@[228] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 55 | `cols_rows_ltr_btt` | COAN@[226] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 55 | `cols_rows_rtl_ttb` | COAN@[20] | - | `IAWNGBIUCSCANXTUALCBCOANNCNGEODI` |
| 11 | 273 | 55 | `cols_rows_rtl_btt` | COAN@[17] | - | `NGBIUCSCANXTUALCBCOANNCNGEODIATE` |
| 11 | 273 | 56 | `cols_rows_ltr_ttb` | COAN@[231] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 56 | `cols_rows_ltr_btt` | COAN@[222] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 56 | `cols_rows_rtl_ttb` | COAN@[22] | - | `IAWNGEAFNGCSCANXTUALCBCOANNCNGEO` |
| 11 | 273 | 56 | `cols_rows_rtl_btt` | COAN@[12] | - | `CSCANXTUALCBCOANNCNGEODIATEOCCAE` |
| 11 | 273 | 57 | `cols_rows_ltr_ttb` | COAN@[234] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |
| 11 | 273 | 57 | `cols_rows_ltr_btt` | COAN@[219] | - | `IABNRNNNGOEAEAXLTHYIAIUEOOFOEUOD` |

### Highest per-page window IOC after untranspose (top 16)

| lp2 | n | raw IOC | best win IOC | W | variant | cribs | head |
|---|---|---|---|---|---|---|---|
| 54 | 76 | 0.03789 | 0.05224 | 40 | `cols_rows_ltr_ttb` | - | `NGMWBMEODAEIABUREAXMCHLMDPBEOEOEAIXSSTHE` |
| 50 | 92 | 0.03273 | 0.04980 | 17 | `cols_rows_rtl_ttb` | - | `WLMTHIAUIEATNGNGOENGBAEOEOWXNAEAEAJEOEGO` |
| 43 | 274 | 0.03599 | 0.04970 | 15 | `cols_rows_rtl_btt` | - | `BAESIHGFPFRIOEOSBSYCMJLTIAOEEANGLEAJWELU` |
| 5 | 263 | 0.03553 | 0.04848 | 27 | `cols_rows_ltr_ttb` | - | `RNGOENGPERFNUEOPEOCSOIANGLGFUCRNECAEDHFX` |
| 8 | 255 | 0.03428 | 0.04848 | 57 | `cols_rows_ltr_ttb` | - | `XXOEAOGINGODYEEAUAUXPASYAEEIAXITHBCSEJOE` |
| 39 | 240 | 0.03577 | 0.04848 | 25 | `cols_rows_ltr_btt` | - | `SNGMYHBDUMPOEPCWLWBANGNGPLNGTGLGSOEXAUTP` |
| 12 | 261 | 0.03395 | 0.04808 | 50 | `cols_rows_ltr_ttb` | - | `CEOIAUARIPSOEALYWEAIAXDAIAHBBOETIAOENRYO` |
| 38 | 228 | 0.03517 | 0.04727 | 31 | `cols_rows_rtl_btt` | - | `DDNGDJBOERAIAEAUAESMNURMMTFMTLPUHSOGSEOL` |
| 21 | 273 | 0.03434 | 0.04687 | 15 | `rows_cols_ltr_ttb` | - | `CCEOTIJPFOEOBXOETNGGNGDAETHOEYGYCMDEAGOE` |
| 2 | 201 | 0.03562 | 0.04667 | 27 | `cols_rows_rtl_ttb` | - | `OELBDHHBFRIRBYLIHHEAEAWTCEAWAETDMDNLEUGN` |
| 7 | 208 | 0.03595 | 0.04667 | 38 | `cols_rows_rtl_btt` | - | `ITHWBONDAHAENCHXWMOEJHSIAAMLIIAEMOEHPEAI` |
| 26 | 265 | 0.03362 | 0.04667 | 52 | `rows_cols_ltr_btt` | - | `IAJTHCIYOYSIBTNEOBJUAEEAXSAFXOEASNAEAEAO` |
| 19 | 271 | 0.03439 | 0.04626 | 22 | `cols_rows_ltr_btt` | - | `NEAOEXCOOOEOJEUIAYBPWMGWRTINGDBFUFOEPDDA` |
| 36 | 238 | 0.03599 | 0.04606 | 41 | `cols_rows_ltr_btt` | - | `YGNEASTHIOEPXPRIAGOJIAOEHAETXINSTOEROUGI` |
| 28 | 269 | 0.0339 | 0.04586 | 11 | `cols_rows_rtl_ttb` | - | `PRDUTPIAOELPXCDXIMAFMPJCJRABSEOIBRDEATHT` |
| 35 | 271 | 0.03499 | 0.04586 | 8 | `cols_rows_ltr_ttb` | - | `NGOTHMHFIANTRLYPJOEOCOEAEOEGRHIAFCIAEEEO` |

No page became readable English. Direct Gematria of every untransposed page is still a flat 29-symbol stream.

## What would have counted as SUCCESS

IOC of a *readable* window toward ~0.06+ **and** 3301 English (WELCOME / AN END / PARABLE class: several consecutive known words, not one 5-gram). That did not happen.

Columnar-only is the wrong family for a stream whose unigram distribution is already 1/29. The positive control shows the same code *does* restore English when the input really was English written in a grid. LP2 0-55 is not that.

## Verdict

**FAIL**

Global IOC stays 0.03448 (permutation invariant). No untranspose produced readable 3301 English. DJUBEI remains a split 6-gram (`DJU`|`BEI`) and is destroyed as a 6-gram by every width. COAN / EUERY / isolated THNGS-DEATH recuts are chance shorties, not a sentence. Window-IOC bumps sit on garbage Latin and do not reach a readable English window. Not a solve.

No public post. Box files only: `notes/transposition-pass1.md` and `box-only columnar audit (not in this repo)`.
