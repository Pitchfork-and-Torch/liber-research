# Liber Primus - zkdecrypto-lite pass 1 (homophonic)

Date: 2026-08-14 16:35 EDT
Worker: Liber Cook executor (Linux box only)
Honesty rail: no fake solve. No public post. No homophonic solver written here.
Steward: zkdecrypto / ahomophonic only.

---

## Upstream

Used the official Google Code export of **zkdecrypto-lite** (Dan Umanovskis CLI of zkdecrypto), not a toy rewrite.

| Item | Value |
|---|---|
| Project | zkdecrypto-lite - "A command-line homophonic cipher solver" |
| Archive URL | https://storage.googleapis.com/google-code-archive-source/v2/code.google.com/zkdecrypto-lite/source-archive.zip |
| Project JSON | https://storage.googleapis.com/google-code-archive/v2/code.google.com/zkdecrypto-lite/project.json |
| License | GPL-2.0 |
| Commit | `652611d98ade82dfc95d1726f60d4153c15dd718` |
| Commit subject | Removing logging |
| Author | Daniels Umanovskis \<daniels.umanovskis@gmail.com\> |
| Commit date | 2013-07-09 16:52:50 +0200 |

Also cloned (not used for the attack run):

- https://github.com/glurk/zkdecrypto @ `fbc552117d469f48335290d25a2b9b8b80c62f6d` (2010-01-18). Win32 GUI (`zodiac.vcproj` / `.dsp`). No Linux Makefile. Headless Linux cannot run it. Prefer lite CLI, as the brief said.
- https://github.com/umanovskis/lgp-decrypto @ `95b6229d77ad3b7cea4304eb847267c7d47a164a` - depends on lite; vendors a library-ized copy of the same CLI under `src/zkd/` (`zkd_main_file`, empty CMakeLists). Not built.
- https://github.com/umanovskis/homophonic-solver @ `323d901766075502af74642b5846794526eaa905` - README: "Barebones solver". Hardcoded 5s / 44000. Treated as a toy; **not used**.

Official Linux binary `zkd-lite-0.15-linux.zip` is listed on the Google Code downloads JSON (sha1 `e586364daf4ab188f57d5d11b88bef1af81feb9b`). Source built, so the binary was not required. Auto-review also blocked that download on the first try.

Documented usage (zodiackillerciphers.com/zkdecrypto-lite-edition/):  
`./zkdecrypto-lite cipher.txt [-t n \| -s n \| -i n]`; default 2 minutes; Z408 readable near score 44000.

---

## Build

Commands (headless Debian 13; installed `g++` `cmake` `make` via apt):

```
cd box-only zkdecrypto-lite source tree (not in this repo)
mkdir -p build && cd build
cmake ..
make -j$(nproc)
```

Result: **BUILD OK**

- Binary: `box-only zkdecrypto-lite binary (not in this repo)`
- ELF 64-bit LSB pie, x86-64, dynamically linked, not stripped
- One compile warning only: `z340.cpp:429` `memcpy` 208 bytes from `float unigraphs[26]` (104). Upstream, unmodified. Linked anyway.
- CMake 3.31.6 warned that `cmake_minimum_required()` is missing. Upstream CMakeLists is two lines. Ignored.

`--help` / no-args usage (exact):

```
Usage:
.../zkdecrypto-lite filename [(-t | -s | -i) n]
-t n limits runtime to n seconds
-s n limits solution score to n
-i n limits solution to n iterations
If no limit options are given, solver will run for 2 minutes
```

Must be run with CWD = source tree so `language/eng/{uni,bi,tri,tetra,penta}graphs.txt` resolve.

Bundled Z408 self-test (Dan's documented command):

```
cd box-only zkdecrypto-lite source tree (not in this repo)
./build/zkdecrypto-lite cipher/408.zodiac.solved.txt -s 44000
```

Result in 0.38s, score **44107**:

```
IDIHEHILDINGPEOPLEBECAUSEITISSOMUCHFUNITIUMORETUNTHANHILLINGWIDDGAMEINTHEFORREST...
```

That is the Zodiac 408 plaintext (I LIKE KILLING PEOPLE...) with the usual leftover substitutions. **Z408 self-test OK.**

---

## Calibration (hard stop)

Plaintext came from existing desk parsers only (`lp_analyze.parse_pages` / `page_runes` / `to_latin`; `liber-transposition-pass1.py` atbash / Vigenere DIVINITY / totient). C/K U/V as the desk already prints. No recook of burned families.

Known-good recoveries (sanity, not a new find):

| Page | Method | A-Z len | Title in stream |
|---|---|---|---|
| A WARNING | atbash 28-i on `parse_pages[0]` | 199 | AWARNNG |
| WELCOME | Vigenere DIVINITY, consume F at <=47, skip later F, pages[1]+[2] | 586 | WELCOME (opening English; middle is the known pad/F-skip mush) |
| AN END | totient `(c-(p-1)) mod 29`, skip F@56, pages[70] | 91 | ANEND |
| PARABLE | identity / direct gematria, pages[71] | 100 | PARABLE |

Encoder (not a solver): multiple ciphertext symbols per A-Z letter, allocated from English unigram weights, seed 3301, printable ASCII 0x21-0x7E. Fed to the **unmodified** binary.

### Attempt 1 - WELCOME pages[1]+[2] (586 letters, 62 symbols)

Rejected as a pass/fail oracle. The desk Vigenere recovers the WELCOME opening and the later "A REAL LAW UNTO YOURSELF / EACH INTELLIGENCE IS HOLY", but the middle is the already-burned YOUR INNOCENCE region (n-gram mush under this key). A 120s lite run scored 49246 and printed English-ish mush with **no title**. That is a bad test vector, not a solver failure.

### Attempt 2 - full A WARNING + full PARABLE (299 letters, 49 symbols)

This is the calibration the brief asked for: full solved-page English, not the 7-letter title, enough length, clean plaintext.

Command:

```
./build/zkdecrypto-lite box-only synthetic calibration file (not in this repo) -t 120
```

CWD = lite source tree. 120.3s. Score **33823**. Output (preview):

```
AWARNNGBEVIEUENOTHNGFROMTHISBOOCELCEPTWHATYOUCNOWTOBETRUETESTTHECNOWLEDGEFINDYOURTRUTHELPERIENCEYOURDEATHDONOTEDITORCHANGETHISBOOCORTHEMESSAGECONTAINEDWITHINEITHERTHEWORDSORTHEIRNUMBERSFORALLISSACREDPARABLELICETHEINSTARTUNNELNGTOTHESURFACEWEMUSTSHEDOUROWNCIRCUMFERENCESFINDTHEDIUINITYWITHINANDEMERGE
```

Titles **AWARNNG** and **PARABLE** are readable. Body is the known GP spelling (BELIEUE/BEVIEUE, BOOC, CNOW, LICE=LIKE, TUNNELNG, DIUINITY) with two leftover substitutions (V for L in BELIEUE, L for X in EXCEPT). That is a working homophonic recover, same class as the Z408 self-test.

**CALIBRATION OK.**

---

## LP2 0-55 - one run

After calibration passed: one 120s run. No second try.

Stream: rtkd rune pages from first `SHEOGMIAF` (`parse_pages[15]`, onion LP2-0) through the page before AN END (`parse_pages[69]`). 55 rtkd pages (desk already noted rtkd vs onion can be off-by-one; one LP2 image is missing or merged). **12956 runes, 29 symbols, IOC 0.03448.** Matches the brief.

Map: GP index 0..28 -> `A`-`Z` plus `1`,`2`,`3`. One ASCII symbol per rune. File: `box-only LP2 mapping file (not in this repo)`.

Command:

```
./build/zkdecrypto-lite box-only LP2 mapping file (not in this repo) -t 120
```

Score **634767** (length x n-gram; do not treat as a solve). Preview:

```
CGURNTNHCOUFDTENHHEARATAUMESCAWSFLAHNSTGEANIEAWETSFOEERIUNHENHCITHILFOFENOGELNRIFHTSHGETINOHFDETSTSFSNOGWTGHNEOULFDHAWTESTTIOFIOAUOREFMEDEREHTTAUIEAENEENTOSRSFNTEOREWOTISTREAGEIHEHINEHEMWTHHNAT...
```

- 3301 cribs (WELCOME, PARABLE, INSTAR, DIVINITY, PILGRIM, CIRCUMFERENCE, INNOCENCE, CICADA, ANEND, DEEPWEB, ...): **none**
- Function-word counts in 12956 letters: THE 25, AND 6, NOT 11, FOR/THAT/THIS/FROM 1, YOU/WITH 0. That is n-gram mush, not English (real English at this length would drown in THE).
- IOC of the input stayed 0.03448. A 29-symbol flat stream is what a homophonic-English solver is supposed to fail on if the page is not a homophonic of English.

**Not a solve.**

---

## Verdict

| Gate | Result |
|---|---|
| Build | OK |
| Z408 self-test | OK (score 44107, readable) |
| Calibration | OK (AWARNNG + PARABLE readable on synthetic) |
| LP2 0-55 | one run; n-gram mush; no 3301 English |

**VERDICT: LP2 NOT SOLVED (calibration passed; homophonic-English attack on the 29-symbol IOC-0.03448 stream failed).**

Idle-ok on a claimed plaintext. Do not post, tweet, onion, or INSTAR-paste LP pages.

---

## Artifacts (box only)

- `notes/homophonic-zkd-pass1.md` (this file)
- `box-only zkdecrypto audit (not in this repo)`
- `box-only zkdecrypto-lite source tree (not in this repo)/` (source + `build/zkdecrypto-lite`)
- `box-only synthetic calibration file (not in this repo)`
- `box-only calibration audit (not in this repo)`
- `box-only LP2 mapping file (not in this repo)`
- `box-only LP2 audit (not in this repo)`

Not used for the attack: AZDecrypt, Zenith, colossus, any 100-line hill-climb, SHA-512, YOUR INNOCENCE pad, book-index, word-unit, running-key, periodic Vigenere, columnar, acrostic.
