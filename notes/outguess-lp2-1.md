# Liber Primus LP2 page 1 - outguess receipt (honest fail)

**Page:** LP2 page 1 (scream314 complete 18.jpg / onion7 1.jpg; page image not in this repo). First unsolved page; no prior nopass dump.
**Image:** JPEG JFIF 1.01, 400x400 DPI, baseline 8-bit, 2400x3600, 3 components, 667228 bytes.
**Method:** OutGuess 0.4 (`/usr/bin/outguess`). Retrieve only (`-r`). No embed. No fake solve.
**Usable bits (this JPEG):** 687226.
**LP2 passworded run:** already completed this session into `box-only outguess pass-1 workdir (not in this repo)` (126 rows in `results.json` for this page: 63 keys x raw/ECC). **Not rerun.** Parent confirmation: 96 extract files, all H~8, printable <=0.41, no PGP/magic. Independent nopass recheck this session: FPE, empty file.
**Judge rule:** 3301-style English / PGP / known 2012 leftover = hit. High-entropy binary with printable ~0.38-0.41 and `file`=`data` = outguess false-positive (wrong key still emits a seed+len). Empty / FPE / "datalen too long" = no payload.

## Verdict

**LP2 page 1 outguess (nopass + listed keys, raw and ECC) is an honest fail: empty/FPE or H~8 binary noise - no English, no PGP, no 2012 leftover.**

## LP2 page 1 - requested keys (raw, no ECC)

Source: `box-only outguess pass-1 log (not in this repo)` (lp2-1.jpg, `ecc=false`). ECC twin of every key: empty, `decode_data: padding is incorrect`, `wrong data len: 0`. None marked interesting.

| key | rc | size | kind | printable | seed / claimed len | judge |
|---|---:|---:|---|---:|---|---|
| *(nopass)* | -8 FPE | 0 | empty | 0.000 | 41408 / 58152 | empty (FPE after retrieve header). Rechecked: `box-only empty retrieve (not in this repo)` is 0 bytes. |
| 3301 | 0 | 54051 | binary | 0.394 | 62079 / 54051 | noise. prefix md5-16 `7ff223d396026018ae5f0dc6e826fd8c`. not PGP/English. |
| 1033 | 0 | 21717 | binary | 0.393 | 63451 / 21717 | noise. |
| 761 | 0 | 45224 | binary | 0.393 | 7240 / 45224 | noise. |
| DIVINITY | 0 | 51011 | binary | 0.390 | 23534 / 51011 | noise. |
| CIRCUMFERENCE | 0 | 19957 | binary | 0.394 | 40275 / 19957 | noise. |
| FIRFUMFERENFE | 0 | 9474 | binary | 0.386 | 41002 / 9474 | noise. |
| WELCOME | -8 FPE | 0 | empty | 0.000 | 49160 / 64446 | empty (FPE). |
| PARABLE | 0 | 8778 | binary | 0.390 | 29223 / 8778 | noise. |
| INTUS | 0 | 17696 | binary | 0.394 | 21253 / 17696 | noise. |
| INSTAR | 0 | 7553 | binary | 0.395 | 34964 / 7553 | noise. |
| LIBERPRIMUS | 0 | 53258 | binary | 0.389 | 42565 / 53258 | noise. |
| ANEND | 0 | 5222 | binary | 0.387 | 41940 / 5222 | noise. |
| A WARNING | 0 | 28617 | binary | 0.388 | 58772 / 28617 | noise. |
| wearethemusicmakers | 0 | 56927 | binary | 0.390 | 47252 / 56927 | noise. |

Broader same-run set (case/spacing variants + extra 2012 words, still this page only): 54 nonempty raw dumps, printable 0.379-0.417, **zero** PGP/`-----BEGIN`/English prefixes, **zero** interesting flags, all H~8. Extract binaries were under `box-only extracts (deleted after scoring; not in this repo)` and are gone; the JSON receipt remains. First-200 hex of those dumps is not restated here because the files were not rerun.

This is the expected wrong-key outguess signature, not a hidden message.

---

## INSTAR public JPEGs (separate corpus - do not mix with LP)

Same tool, **this session only**, outputs in `box-only INSTAR outguess workdir (not in this repo)/`. Keys: nopass, `3301`, `DIVINITY`, `INSTAR`. No Liber Primus plaintext was written into these files.

Sources:

| file | JPEG |
|---|---|
| `public INSTAR JPEG og.jpg (not copied here)` | JFIF 1.01, 1200x630, 102941 B, usable 112139 bits |
| `public INSTAR JPEG seal.jpg (not copied here)` | JFIF 1.01, 1024x1024, 352177 B, usable 355615 bits |
| `public INSTAR JPEG hero-soil.jpg (not copied here)` | JFIF 1.01, 1280x720, 266739 B, usable 272742 bits |
| `public INSTAR JPEG wing-src.jpg (not copied here)` | JFIF 1.01, 1152x864, 277811 B, usable 265790 bits |

### og.jpg

| key | rc | size | magic | H | printable | judge |
|---|---:|---:|---|---:|---:|---|
| nopass | 1 | 0 | - | - | - | empty. claimed len 41708 > 14018 |
| 3301 | 1 | 0 | - | - | - | empty. claimed len 55447 > 14018 |
| DIVINITY | 1 | 0 | - | - | - | empty. claimed len 19275 > 14018 |
| INSTAR | 1 | 0 | - | - | - | empty. claimed len 17612 > 14018 |

### seal.jpg

| key | rc | size | magic | H | printable | judge |
|---|---:|---:|---|---:|---:|---|
| nopass | 1 | 0 | - | - | - | empty. claimed len 57923 > 44452 |
| 3301 | 0 | 4656 | data | 7.961 | 0.382 | noise. seed 11780. not PGP/English. |
| DIVINITY | -8 FPE | 0 | - | - | - | empty (FPE after seed 33971 / len 35148) |
| INSTAR | 1 | 0 | - | - | - | empty. claimed len 62888 > 44452 |

seal / 3301 first-200 hex omitted (DCT noise; not a payload).

### hero-soil.jpg

| key | rc | size | magic | H | printable | judge |
|---|---:|---:|---|---:|---:|---|
| nopass | 0 | 19219 | data | 7.990 | 0.385 | noise. seed 42171. |
| 3301 | 0 | 11659 | data | 7.985 | 0.377 | noise. seed 61174. |
| DIVINITY | 1 | 0 | - | - | - | empty. claimed len 60965 > 34093 |
| INSTAR | 0 | 21985 | data | 7.992 | 0.384 | noise. seed 52392. |

hero-soil first-200 hex dumps omitted (DCT noise; not a payload).

### wing-src.jpg

| key | rc | size | magic | H | printable | judge |
|---|---:|---:|---|---:|---:|---|
| nopass | 0 | 5482 | data | 7.968 | 0.372 | noise. seed 17791. |
| 3301 | 1 | 0 | - | - | - | empty. claimed len 59911 > 33224 |
| DIVINITY | 0 | 15939 | data | 7.988 | 0.384 | noise. seed 24017. |
| INSTAR | 1 | 0 | - | - | - | empty. claimed len 35156 > 33224 |

wing-src first-200 hex dumps omitted (DCT noise; not a payload).

### INSTAR section verdict

No payload. og.jpg: all four keys empty (claimed length > capacity). seal / hero-soil / wing-src: empty, FPE, or H~8 `data` with printable 0.37-0.38. Same false-positive signature as LP2 page 1. Not 3301 English, not PGP, not a known leftover.

Machine-readable INSTAR rows: `box-only INSTAR outguess log (not in this repo)`.
