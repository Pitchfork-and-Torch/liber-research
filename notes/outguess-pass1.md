# Liber Primus LP2 - passworded outguess pass 1

Date: 2026-08-14 15:32 ET  
Tool: outguess 0.4-2 (Debian) on the Linux box  
Rule: honest only. No fake solves. No public post.

## Verdict

**No real extract.** Nothing that looks like 3301 English, a known file type, or a structured payload.  
This is a **partial** pass: the Windows host disconnected before the 40 no-dump JPEGs could be copied. Only two eligible pages were already on the box.

## Pages that already had nopass dumps (SKIP)

From the local kit (not in this repo), scream314 complete numbering already has passwordless outguess dumps for:

`00-04, 06-13, 17, 21, 43, 57-65, 68-71`

Many of those dumps are 58152 bytes and look like the same repeated extract (junk). `08.jpg.txt` is 150 bytes. Those pages were not re-run.

`onion7/0.jpg` ~ complete `17.jpg` is in that skip set. `LP2 page 0 JPEG (not in this repo)` (695525 bytes) was already on the box and was **not** attacked.

## Intended target set (no nopass dump)

Complete numbering -> onion7:

| complete | onion7 |
|---|---|
| 18-20 | 1-3 |
| 22-42 | 5-25 |
| 44-56 | 27-39 |
| 66-67 | 49-50 |
| 72 | 55 |

40 JPEGs. Sources on the host (verified present, then host dropped):

- `local onion7 JPEG set (not in this repo)`
- zip staged at `local no-dump JPEG zip (not in this repo)` (17,528,265 bytes)
- CopyToBox of that zip **timed out**; file never landed on the box
- Host then disconnected. No further ExternalShell / CopyToBox.

## Pages actually run

Only files already on the box (page images not in this repo):

| box file | size | md5 | mapping | ran? |
|---|---|---|---|---|
| `lp2-0.jpg` | 695525 | f179ae5b4a77f6eacca698dfadda23d8 | onion7-0 / complete-17 | SKIP (has nopass) |
| `lp2-1.jpg` | 667228 | b300a52bd5dca6c98deea695c94769e8 | onion7-1 / complete-18 | YES |
| `lp2-15.jpg` | 512272 | 4e37370df1178f3296569467080b3f57 | onion7-15 / complete-32 | YES |

Both run pages are 2400x3600 JFIF 1.01, 400 DPI, baseline JPEG.

## Passwords

Small crib from solved 3301 / Liber Primus material only, plus case variants of the **same** tokens (outguess keys are case-sensitive). 62 keys.

`3301`, `1033`, `761`, `DIVINITY`, `CIRCUMFERENCE`, `FIRFUMFERENFE`, `INSTAR`, `WELCOME`, `PARABLE`, `ANEND`, `AN END`, `LIBERPRIMUS`, `LIBER PRIMUS`, `AWARNING`, `A WARNING`, `INTUS`, `KOAN`, `THELOSSOFDIVINITY`, `INSTRUCTION`, `EUERY`, `PILGRIM`, `7A35090F`, `wearethemusicmakers`  
and lower / Title / UPPER of those same strings.

Not used: `YOUR INNOCENCE YOUR ILLUSIONS` (explicitly excluded).  
`SOURCES.txt` (`local SOURCES.txt (not in this repo)`) listed no extra 2012-2014 outguess passwords beyond the crib / PGP id `7A35090F`. INSTAR is noted there as a separate ARG; it was still tried because it was on the requested crib.

Each key was tried twice: raw retrieve, and `-e` (error-correcting). Passwordless retrieve was also run once per page to confirm the "no nopass dump" status.

Total: 252 runs (2 pages x 63 keys including empty x 2 modes).

## Results

| class | count | what it was |
|---|---|---|
| ECC (`-e`) nonempty | 0 / 126 | all failed (rc 1). Correct reject of garbage. |
| passwordless raw | 0 / 2 | empty. rc -8. Confirms no nopass payload on these two. |
| passwordless ECC | 0 / 2 | empty. rc 1. |
| raw `-k` nonempty | 96 / 124 | **binary noise, not a find** |
| interesting (text / magic / 3301 English) | **0** | - |

Raw nonempty dumps:

- kind = binary every time
- printable fraction 0.37-0.42 (random-byte range)
- no PNG / JPEG / PDF / ZIP / GZIP / PEM / `-----BEGIN` magic
- prefixes are high-entropy junk, not English
- **41** key+mode pairs produced the **same size and same first 16 bytes on both different JPEGs**. A real hidden message would not do that across two covers for dozens of unrelated keys.

Example (not a find - identical noise on two pages):

- key `1033` raw -> 21717 bytes, magic `dbf7d554d782c7475b49...` on both onion7-1 and onion7-15
- key `761` raw -> 45224 bytes, magic `481ca8b034c260c8a844...` on both

Outguess 0.4 without `-e` will often emit a "successful" retrieve of cover LSB noise seeded by the key. That is what 96 nonempty files were. They were deleted after scoring so they are not mistaken for dumps.

Failed retrieves still logged `Steg retrieve: seed: ..., len: 58152` in several cases. That matches the 58152-byte repeated nopass junk in the kit. Same artifact family, not a payload.

## Light JPEG marker check (not LSB)

Both run pages:

- APP0 JFIF 16 bytes (`JFIF 1.01`, 400x400 density)
- APP2 ICC_PROFILE 2592 bytes (standard `mntr RGB XYZ` profile)
- no COM comment
- no EXIF APP1
- no other APP markers

Nothing hidden in comments / EXIF / APP. Raw LSB bit0/bit1 / R-only was already 0 hits on 79 JPEGs in the 2026-08-14 attack log and was not re-done.

## Blockers / remaining work

1. **Host disconnect.** 38 of 40 no-dump onion7 JPEGs never reached the box (`2-3, 5-14, 16-25, 27-39, 49-50, 55`).
2. Zip is on the Windows side only: `local no-dump JPEG zip (not in this repo)`.
3. When the host is back: CopyToBox that zip (or the individual JPEGs), extract, rerun the same 62-key x raw+ecc script. Do not widen the wordlist. Do not grind SHA-512. Do not rerun the 155 NULL pad / YOUR INNOCENCE path. Do not treat a 64-byte page-56 hash re-encoding as a find.
4. A later pass should treat **ECC nonempty + English/file-magic** as the only success test. Raw nonempty binary is not a hit.

## Machine notes

- outguess installed on the box: `/usr/bin/outguess` (1:0.4-2)
- run log JSON: `box-only outguess pass-1 log (not in this repo)`
- this report: `notes/outguess-pass1.md`

**No solve. Two pages tested, zero real extracts. 38 pages not tested (host down).**
