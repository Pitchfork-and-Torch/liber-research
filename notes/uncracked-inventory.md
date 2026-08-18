# Cicada 3301 / Liber Primus - uncracked-page work
Date: 2026-08-14 (America/New_York)
Worker: executor subagent
Honesty rail: no claimed solve unless a method first replays A WARNING, WELCOME, AN END, PARABLE and then yields readable 3301-style English. None of the new trials met that bar.

Sources used (local, not uploaded):
- local liber-archive (page images and rune dump not in this repo)
- local INSTAR checkout (separate public school; LP pages were not copied into it)
- liber-archive notes: WHAT-IS-SOLVED.txt, ATTACK-LOG.txt, NEXT-MOVES.txt, 00-START-HERE.txt
- Archived cloud agent "Unsolved cicada 3301 puzzles" (bc-019ffec2) final: [4,9,4,8] = YOUR INNOCENCE YOUR ILLUSIONS; pads at word 245/1791/2063 differ; 155 Vigenere/totient/hash-chain/autokey/tiled-pad trials NULL. Treated as burned.
- Community status: cicadasolvers.com LP2 sections; scream314 / rtkd numbering

INSTAR is a puzzle school. It is not Liber Primus and was not used as a crib source beyond the public fact that molt 7 uses Futhorc sound values, not Gematria Primus.

---

## 1. Inventory of still-uncracked pages

Community split (onion-7 names, the names 3301 used in the May 2014 dump):

### Solved (calibration only - do not "re-solve")
| Pages | Why solved |
|---|---|
| LP1 00 | English title: Liber Primus |
| LP1 01 | Atbash / reversed Gematria: A WARNING |
| LP1 02 | English: Chapter I Intus |
| LP1 03-04 | Vigenere DIVINITY, skip F: WELCOME |
| LP1 05 | Direct Gematria + number square: SOME WISDOM |
| LP1 06-09 | Shift 3 down reversed: A KOAN |
| LP1 10-13 | Direct Gematria: THE LOSS OF DIVINITY |
| LP1 14-15 | Vigenere CIRCUMFERENCE (FIRFUMFERENFE after F-skip): A KOAN / sway |
| LP1 16 | Direct Gematria: AN INSTRUCTION |
| LP2 56.jpg | (c - (p-1)) mod 29, skip F at index 202: AN END + 512-bit deep-web hash |
| LP2 57.jpg | Direct Gematria: PARABLE |

An End (solved, not a new find):
  AN END
  WITHIN THE DEEP WEB THERE EXISTS A PAGE THAT HASHES TO
  36367763ab73783c7af284446c59466b4cd653239a311cb7116d4618dee09a8425893dc7500b464fdaf1672d7bef5e891c6e2274568926a49fb4f45132c2a8b4
  IT IS THE DUTY OF EUERY PILGRIM TO SEEK OUT THIS PAGE

Parable (solved, not a new find):
  PARABLE
  LIKE THE INSTAR TUNNELING TO THE SURFACE
  WE MUST SHED OUR OWN CIRCUMFERENCES
  FIND THE DIVINITY WITHIN AND EMERGE

### Unsolved
LP2 onion pages **0.jpg through 55.jpg** (56 pages, ~12956 runes).
Why they are still uncracked:
- Index of coincidence sits on 1/29 (0.03448). That is flat / random on a 29-rune alphabet. English-on-29 is ~0.06+.
- The known Cicada family (identity, Atbash, Caesar, totient+F, primes, Fibonacci, Vigenere/Beaufort on DIVINITY / CIRCUMFERENCE / 2016 phrases, LP1 running key, 15.jpg square stream) was closed locally on 2026-08-13/14 (ATTACK-LOG wave 1). Kasiski column IOC stays ~0.0347 for periods 2-40.
- DJUBEI is the longest repeated 6-gram inside 0-55. It is a crib, not a key.
- The page-56 512-bit locator has never been retrieved. Hash-preimage and "hash as ciphertext" catalogs were already run (waves 2-7). Not repeated here.
- rtkd transcription has 72 rune-bearing pages vs 75 complete-book images. Three images are art/Latin-only or otherwise not in the rune stream. rtkd LP2 has 57 pages (0-56) vs onion 58 (0-57): one LP2 page is missing or merged in rtkd. An End is rtkd's second-to-last rune page; Parable is last. Treat rtkd index vs onion index as possibly off-by-one after ~page 15.

Section map (cicadasolvers marginalia, onion numbers):

| Onion pages | Section | Status |
|---|---|---|
| 0-2 | Sign post and Cross (offset patriarchal crosses, infinity marks, red incipit on 0) | Unsolved |
| 3-7 | Spirals | Unsolved |
| 8-14 | Branches | Unsolved |
| 15-22 | Mobius | Unsolved |
| 23-26 | Mayfly | Unsolved |
| 27-32 | Wing and Tree | Unsolved |
| 33-39 | Cuneiform | Unsolved |
| 40-53 | Spiral Branches | Unsolved |
| 54-55 | Spiral and Dead Tree | Unsolved |
| 56 | Deep-web hash | Solved (AN END) |
| 57 | Parable | Solved |

Also still open, but not "uncracked pages":
- The 512-bit deep-web page (never retrieved). Do not grind preimages.
- Sexagesimal 256-byte block (high entropy, no file magic).
- Passworded outguess on LP JPEGs that have no nopass dump.

---

## 2. Pages picked

Picked **LP2 0.jpg** (Sign-post / Cross, first unsolved, red rubric, two offset crosses, 6-dot and 4-dot clusters) and **LP2 15.jpg** (Mobius section start, also red rubric).

Why these, and not the burned pad:
- Page 0 is the door of the unsolved book. Layout (cross height offset, 12 lines, red incipit, 6-dot cluster) suggests transposition / skip / rail, not another Vigenere key.
- Page 15 opens a new marginalia section. A section-start page is the usual place for a method change in this book (LP1 does that).
- Explicitly **not** reused: SHA-512 preimage; YOUR INNOCENCE YOUR ILLUSIONS local-pad recovery; Caesar / Atbash / DIVINITY / CIRCUMFERENCE / totient on all of 0-55; full LSB redo (local wave 4 already: 0 hits).

rtkd alignment used: first page whose runes start SHEOGMIAF = onion 0 (262 runes, 65 words, 12 lines). Fifteenth LP2 rune page = 159 runes, 42 words, 8 lines (Mobius neighborhood; rtkd may be off-by-one vs onion 15 if the missing rtkd page is before it). Image work used the actual onion files 0.jpg and 15.jpg.

Direct Gematria of the two pages (not a solve; this is the ciphertext as Latin):
- LP2-0 rubric (red): SHEOGMIAF SYENGC THJGAE FJOE
- LP2-0 direct IOC: 0.03431
- LP2-15 rubric: FULM AEAYOEA LUNGN CU
- LP2-15 direct IOC: 0.03598

---

## 3. Methods tried and results

Format: page, method, result, next.

### LP2 0.jpg

| Method | Result | Next |
|---|---|---|
| Direct Gematria | Fail. SHEOGMIAF SYENGC ... IOC 0.03431. Two accidental dictionary hits (I, AS) from digraph noise. | Do not treat rubric as plaintext. |
| Reverse runes / reverse words | Fail. No English. | - |
| First-of-word acrostic | Fail. SSTHFONNHPEOABESYBGNGIAE... | Try first-of-word after a real decrypt, not on ciphertext. |
| Last-of-word acrostic | Fail. | - |
| First-of-line acrostic | Fail. SOPSAEIAEBOENGEOT (12 lines). | - |
| Prime-indexed runes (0- and 1-based) | Fail. | - |
| Skip 2,3,5,7,11,13,17,19,23,29 and off-by-1 | Fail as a page decrypt. Weak fragment only: skip-13-off1 = HJABBPPNGTTHDEATHFNGDNGHWW. "DEATH" is 3 GP runes (D, EA, TH) inside 21 runes. Expected by chance. Not a solve. | If anyone cribs DEATH here, demand the rest of the skip reading as English. It is not. |
| Skip 4 and 6 (4-dot diamond / 6-dot cluster on the JPEG) | Fail. SGSCAEOESNGGBB... / SIACJEEOGIATHDG... | Visual dot-counts are not a working skip. |
| Odd / even runes | Fail. | - |
| Rail-fence encode and decode, 2/3/4 rails (motivated by the two offset crosses) | Fail. IOC did not lift; no English. | A height-measured rail (count pixel rows between the two cross tops) was not computed. That is a possible next, still a long shot. |
| Drop every F then direct | Fail. IOC 0.03533. F-skip without a key does nothing. | - |
| Book cipher A: solved-page English first letters pick unsolved words | Fail. IOC rose only because the same words were re-picked (repeat artifact). Preview YFNGCJ SPTFPUNGYNGXIA... | Do not reuse this selector. |
| Book cipher B: walk unsolved runes by solved-word lengths | Fail. | - |
| Book cipher from LP1 number squares (instruction 434/1311/..., wisdom 272/138/..., 15.jpg 3258/3222/...) as mod / mod-1 / digit-sum indexes into page 0 | Fail. Examples: JHNGAEPMBLJNYANAYNJLBMPAENGHJ ; EDDXJNFJXDDE ; COSDWIYDEBGCSNGLW. No English. | A new number rule that is *internal* to 0-55 is still the 2016 "numbers are the direction" reading. These published squares are not it. |
| An End 64-byte hex used as indexes (not a preimage) | Fail. DDJNGDFIGTHUXNGIA... | If 0-55 ever yields plaintext, use *that* as a key on the 64 bytes. The reverse direction (hash bytes -> page 0) is closed. |
| Musical / page-number skips (5,7,8,12) and pentatonic keep/drop on a 12-line page | Fail. Same strings as ordinary skips. | - |
| Column read (down the 12 lines, then across) | **Weak fragment, not a solve.** Slice: ...DGLFDNG **ONEOF THE X THEAR** NGUGEJ... "ONE OF THE" is real English but sits in garbage, has no word breaks, and does not continue. "CAPEALOSS" later in the same string is also a tease (LOSS is an LP1 word). Column-reverse has AMILY / HEAMILY - not FAMILY. | Re-try column read only after a substitution that lifts IOC. On raw ciphertext this is coincidence. |
| Image: crop guides | Fail. 20 px borders are clean white (dark fraction 0). Ink bbox rows 871-2858, cols 211-2188. No crop ticks. | - |
| Image: color channels | Red incipit is real paint (55144 redish pixels, bbox 602,668-1443,1163). G and B track each other. R-G difference is the visible red, not a hidden plane. | Do not upload the JPEG. |
| Image: LSB (spot-check only; wave 4 already burned this) | LSB p1 ~ 0.90 on all channels. That is JPEG near-white landing on odd values, not a 50/50 payload. Local wave 4 already: no PGP/onion in first 4 KB of LSB planes. | Passworded outguess is still open if outguess is installed. LSB is closed. |
| Image: ICC | 2576-byte ICC_PROFILE. Already identified as a standard APP2 marker, not a payload. | - |

### LP2 15.jpg (Mobius start)

| Method | Result | Next |
|---|---|---|
| Direct Gematria | Fail. FULM AEAYOEA LUNGN CU ... IOC 0.03598. | - |
| Reverse / acrostics / prime-index / skips / rails / drop-F | Fail. Line acrostic FLGATHIAIAIA (high IOC is a small-n artifact: 8 runes, three IA). Skip-29 = FUISHI (not English). | - |
| Book ciphers (same family as page 0) | Fail. Same repeat artifact on selector A. Number-square indexes: HXXUNEATYSEOFJUJFEOSYTEANUXXH etc. | - |
| Musical skips including page-number 15 | Fail. UNXNTWILSOEN and friends. | - |
| Column read | Fail. FLGATHIAIAIAUUXCARHX... No English phrase. | - |
| Image: crop guides | Fail. Borders clean. Ink cols 769-1755 (narrower than page 0; Mobius art, not a full-width text block). | - |
| Image: color channels | Red rubric present (64301 redish pixels). Same R-vs-GB pattern as page 0. | - |
| Image: LSB / ICC | Same JPEG-white LSB bias (~0.945). ICC 2576. Not a payload. | - |

### Also checked, not a third-page attack
- LP2 1.jpg (same Cross section) is true grayscale: R=G=B exactly, 0 redish pixels, 0 channel difference. No hidden color channel on that page.
- Calibration pages in rtkd still read as known plaintext when treated as direct / Atbash / etc. The alphabet used here is the standard 29-rune Gematria Primus. The new methods fail *because they are wrong*, not because the alphabet is wrong.

---

## 4. Candidate plaintext

**No genuine new English plaintext.**

Do not promote these to solves:

1. LP2-0 column-read fragment `ONE OF THE` (then `X THEAR`). Not in the public solved-page list as a page decrypt. Surrounding text is not English. **Not flagged as a solve.**
2. LP2-0 skip-13-off1 fragment `DEATH`. Three runes. Chance. **Not a solve.**
3. Rubrics `SHEOGMIAF SYENGC` and `FULM AEAYOEA LUNGN CU` are ciphertext, not titles.

If a later pass ever gets a real page, the test is: replay A WARNING / WELCOME / AN END / PARABLE with the same rules, then show IOC lift on 0-55, then show continuous 3301-style English.

---

## 5. What is burned (do not repeat as the main attack)

- SHA-512 / constructed-page / extra-512-bit-algo preimage of the An End hash
- YOUR INNOCENCE YOUR ILLUSIONS skeleton at word indices 245 / 1791 / 2063 (rune 1107 / 7911 / 9090); 155 pad trials; three different pads; IOC ~1.00
- Caesar / Atbash / DIVINITY / CIRCUMFERENCE / totient / Fibonacci / 15.jpg stream on all of 0-55
- Hash-as-ciphertext catalog (XOR / RC4 / AES / ChaCha on the 64 bytes)
- nopass LSB / R-only on the LP JPEG set
- Treating a re-encoding of the 64 bytes (onion / magnet / IPFS / Freenet / I2P / Windows-1252) as a find

---

## 6. Honest next methods (not tried, or only sketched)

1. Passworded outguess on pages with no scream314 nopass dump. Keys to try: 3301, 1033, 761, DIVINITY, CIRCUMFERENCE, and phrases from solved pages. Needs an outguess binary (not on PATH in the local kit).
2. A number rule *taken from the unsolved runes themselves* (2016: "their numbers are the direction"), not from LP1 squares. Unknown.
3. Section-wide transposition: treat 0-2 / 15-22 / etc. as one ciphertext, using marginalia as the permutation hint (cross offset in pixels; Mobius as a direction-reversal; cuneiform as a base-60 read against the sexagesimal block).
4. Height-measured rail on pages 0-2: measure the vertical offset of the two crosses and use that as rail count or starting rail. Not done; pixel measurement only sketched.
5. If any of 0-55 ever yields verified plaintext, immediately use those bytes / SHA-512 / rune indexes as XOR and AES on payloads/page56-hash.bin and test the v2-prefix rule.
6. Hash algos the local kit did not run: original BLAKE-512, Streebog, Groestl, JH, LSH, CubeHash, MD6, FNV-512 (tweqx/3301-hash-alarm). Secondary to a book decrypt.

---

## 7. Notes file path

`notes/uncracked-inventory.md`

Local images used (copied into the box for analysis, not uploaded, not written into INSTAR):
- LP2 page 0 JPEG (not in this repo)
- LP2 page 1 JPEG (not in this repo)
- LP2 page 15 JPEG (not in this repo)
- the public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo
- box-only desk parser / dump / scratch (not in this repo)
