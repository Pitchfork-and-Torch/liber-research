# Liber Primus LP2 - passworded outguess pass 2

Date: 2026-08-14 15:39 ET  
Tool: outguess 0.4 (`/usr/bin/outguess`) on the Linux box  
Rule: honest only. No fake solves. No public post. No SHA-512 grind. No YOUR INNOCENCE YOUR ILLUSIONS pad.

## Verdict

**No real extract.** 38 no-dump onion7 pages run. 0 hits under the strict ECC+English/magic test. Raw nonempty dumps are DCT / LSB noise (same key -> same size and head on many different covers). Combined with pass 1, all 40 intended no-dump onion7 JPEGs have now been tested. Still nothing that looks like 3301 English or a real file.

## Pages run

Zip: `local JPEG zip (not in this repo)` (17,528,265 bytes) unzipped to `box-only JPEG workdir (not in this repo)` without recompressing. Zip inventory: 40 JPEGs named `1.jpg`-`3.jpg`, `5.jpg`-`25.jpg`, `27.jpg`-`39.jpg`, `49.jpg`, `50.jpg`, `55.jpg`. No `0.jpg` in the zip.

SKIP (as requested):

- onion7 `0.jpg` / complete 17 - has nopass; not in this zip
- onion7 `1.jpg` / complete 18 - already failed passworded outguess (`LP2 page 1 JPEG (not in this repo)`, md5 `b300a52bd5dca6c98deea695c94769e8`, identical to zip `1.jpg`)
- onion7 `15.jpg` / complete 32 - already failed passworded outguess (`LP2 page 15 JPEG (not in this repo)`, md5 `4e37370df1178f3296569467080b3f57`, identical to zip `15.jpg`)

RAN (38 files): onion7 **2, 3, 5-14, 16-25, 27-39, 49, 50, 55**  
Complete-number mapping for this set is onion7 + 17 (onion7 2 = complete 19, ..., onion7 55 = complete 72).

## Passwords

Same 62-key crib as pass 1. Each key tried raw and `-e`. Plus one passwordless retrieve per page (raw and `-e`) to confirm no nopass dump. Wordlist was not widened.

`3301`, `1033`, `761`, `DIVINITY`, `CIRCUMFERENCE`, `FIRFUMFERENFE`, `INSTAR`, `WELCOME`, `PARABLE`, `ANEND`, `AN END`, `LIBERPRIMUS`, `LIBER PRIMUS`, `AWARNING`, `A WARNING`, `INTUS`, `KOAN`, `THELOSSOFDIVINITY`, `INSTRUCTION`, `EUERY`, `PILGRIM`, `7A35090F`, `wearethemusicmakers`  
and lower / Title / UPPER of those same strings only.

Total: **4788** runs (38 pages x 63 keys including empty x 2 modes). Elapsed 42.1s, 7 workers.

## Success test (strict)

- Hit only if: ECC nonempty AND (printable >= 0.70 OR known magic PGP/PEM/PNG/JPEG/ZIP/PDF) AND looks like 3301 English or a real file.
- Raw nonempty binary with printable 0.36-0.42 and key-dependent length is DCT noise. **Not a hit.** Especially when the same key yields the same size/head on two different covers.
- A real extract would be labeled **CANDIDATE**, not a solve, until it is readable 3301 English.

## Results

| class | count | what it was |
|---|---|---|
| ECC (`-e`) nonempty | **0 / 2394** | all failed (rc 1). `decode_data: padding is incorrect` / `wrong data len: 0`. Correct reject of garbage. |
| passwordless raw nonempty | **0 / 38** | empty. Confirms no nopass payload on these pages. |
| passwordless ECC nonempty | **0 / 38** | empty. rc 1. |
| raw `-k` nonempty | **1691 / 2356** | **binary noise, not a find** (printable 0.298-0.451; 1674/1691 in 0.36-0.42) |
| strict hits (ECC + English/magic) | **0** | - |
| raw file-like watches | **0** | no PNG/JPEG/ZIP/PDF/PGP/PEM; no printable >= 0.70 |

Kinds: empty 3097, binary 1691. Zero `text` / `file`. Zero `english` flags.

Cross-cover identical raw dumps (same key + size + first 16 bytes on >=2 pages): **53** signatures, **1653** page-hits. **31** of those signatures are identical on **all 38** covers. A real hidden message would not do that across dozens of unrelated keys and every page.

Example (not a find - identical noise on every run page, and the same heads as pass 1 on onion7-1 / onion7-15):

- key `1033` raw -> 21717 bytes, head `dbf7d554d782c7475b49fcb50867e680` on all 38 pages (same as pass 1)
- key `761` raw -> 45224 bytes, head `481ca8b034c260c8a84484afd94c5725` on 35 pages (same as pass 1; missing 14, 23, 32 where that retrieve FPE'd / failed)
- key `7A35090F` raw -> 17115 bytes, head `6fc7db42aa1ce9a332b8a6e8d13a6441` on all 38 pages
- key `ANEND` raw -> 5222 bytes, head `d4a366144580c76aee19390eabc53708` on all 38 pages

Eight crib keys produced **no** raw extract on any page (all empty / FPE): `KOAN`, `Parable`, `THELOSSOFDIVINITY`, `WELCOME`, `circumference`, `instruction`, `intus`, `pilgrim`. That is still not a signal - just keys whose claimed length crashed or failed.

17 raw dumps sit slightly outside printable 0.36-0.42. All 17 are key `Awarning`, 235 bytes, printable 0.298-0.451, binary, shared head prefix `07c3eb00e125f572...` on multiple pages. Still DCT noise. Not a candidate.

Failed passwordless retrieves still logged `Steg retrieve: seed: 41408, len: 58152` on every page (page 32 also: `Extracted datalen is too long: 58152 > 49172`). Same 58152-byte claimed-length artifact as pass 1 and the kit's repeated nopass junk. Not a payload. Extracts were not kept.

## Candidates

None.

## Passwordless confirm (no nopass dump)

Every page: raw empty, ECC empty. 37/38 raw rc -8 (FPE after the 58152 header). Page 32 raw rc 1 (claimed length longer than usable bits).

| onion7 | complete | raw rc | raw size | ecc rc | ecc size |
|---|---:|---:|---:|---:|---:|
| 2 | 19 | -8 | 0 | 1 | 0 |
| 3 | 20 | -8 | 0 | 1 | 0 |
| 5 | 22 | -8 | 0 | 1 | 0 |
| 6 | 23 | -8 | 0 | 1 | 0 |
| 7 | 24 | -8 | 0 | 1 | 0 |
| 8 | 25 | -8 | 0 | 1 | 0 |
| 9 | 26 | -8 | 0 | 1 | 0 |
| 10 | 27 | -8 | 0 | 1 | 0 |
| 11 | 28 | -8 | 0 | 1 | 0 |
| 12 | 29 | -8 | 0 | 1 | 0 |
| 13 | 30 | -8 | 0 | 1 | 0 |
| 14 | 31 | -8 | 0 | 1 | 0 |
| 16 | 33 | -8 | 0 | 1 | 0 |
| 17 | 34 | -8 | 0 | 1 | 0 |
| 18 | 35 | -8 | 0 | 1 | 0 |
| 19 | 36 | -8 | 0 | 1 | 0 |
| 20 | 37 | -8 | 0 | 1 | 0 |
| 21 | 38 | -8 | 0 | 1 | 0 |
| 22 | 39 | -8 | 0 | 1 | 0 |
| 23 | 40 | -8 | 0 | 1 | 0 |
| 24 | 41 | -8 | 0 | 1 | 0 |
| 25 | 42 | -8 | 0 | 1 | 0 |
| 27 | 44 | -8 | 0 | 1 | 0 |
| 28 | 45 | -8 | 0 | 1 | 0 |
| 29 | 46 | -8 | 0 | 1 | 0 |
| 30 | 47 | -8 | 0 | 1 | 0 |
| 31 | 48 | -8 | 0 | 1 | 0 |
| 32 | 49 | 1 | 0 | 1 | 0 |
| 33 | 50 | -8 | 0 | 1 | 0 |
| 34 | 51 | -8 | 0 | 1 | 0 |
| 35 | 52 | -8 | 0 | 1 | 0 |
| 36 | 53 | -8 | 0 | 1 | 0 |
| 37 | 54 | -8 | 0 | 1 | 0 |
| 38 | 55 | -8 | 0 | 1 | 0 |
| 39 | 56 | -8 | 0 | 1 | 0 |
| 49 | 66 | -8 | 0 | 1 | 0 |
| 50 | 67 | -8 | 0 | 1 | 0 |
| 55 | 72 | -8 | 0 | 1 | 0 |

## Per-page raw nonempty key count

Noise only. A real payload would not spray dozens of unrelated keys, and would not repeat the same bytes on every cover.

| onion7 | complete | raw nonempty keys | ECC nonempty |
|---|---:|---:|---:|
| 2 | 19 | 44 | 0 |
| 3 | 20 | 44 | 0 |
| 5 | 22 | 54 | 0 |
| 6 | 23 | 43 | 0 |
| 7 | 24 | 43 | 0 |
| 8 | 25 | 47 | 0 |
| 9 | 26 | 52 | 0 |
| 10 | 27 | 49 | 0 |
| 11 | 28 | 45 | 0 |
| 12 | 29 | 46 | 0 |
| 13 | 30 | 49 | 0 |
| 14 | 31 | 39 | 0 |
| 16 | 33 | 44 | 0 |
| 17 | 34 | 43 | 0 |
| 18 | 35 | 43 | 0 |
| 19 | 36 | 43 | 0 |
| 20 | 37 | 43 | 0 |
| 21 | 38 | 43 | 0 |
| 22 | 39 | 42 | 0 |
| 23 | 40 | 39 | 0 |
| 24 | 41 | 54 | 0 |
| 25 | 42 | 53 | 0 |
| 27 | 44 | 44 | 0 |
| 28 | 45 | 43 | 0 |
| 29 | 46 | 43 | 0 |
| 30 | 47 | 43 | 0 |
| 31 | 48 | 43 | 0 |
| 32 | 49 | 32 | 0 |
| 33 | 50 | 43 | 0 |
| 34 | 51 | 43 | 0 |
| 35 | 52 | 44 | 0 |
| 36 | 53 | 42 | 0 |
| 37 | 54 | 42 | 0 |
| 38 | 55 | 43 | 0 |
| 39 | 56 | 43 | 0 |
| 49 | 66 | 52 | 0 |
| 50 | 67 | 44 | 0 |
| 55 | 72 | 45 | 0 |

## Machine notes

- images: `box-only JPEG workdir (not in this repo)`
- runner: `box-only outguess runner (not in this repo)`
- run log JSON: `box-only outguess pass-2 log (not in this repo)`
- jsonl: `box-only outguess pass-2 jsonl (not in this repo)`
- candidates dir: `box-only candidates dir (empty; not in this repo)` (empty)
- this report: `notes/outguess-pass2.md`
- elapsed: 42.1s, workers: 7
- pass 1 (onion7 1 and 15): `notes/outguess-pass1.md`

**No solve. 38 pages tested, zero real extracts. Hit count: 0.**
