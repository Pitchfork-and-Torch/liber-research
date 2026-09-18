# Liber Primus cross-height rail-fence pass 1 (onion 0-2)

Date: 2026-09-17 (America/New_York), desk work archived from gauntlet cycle 2 (2026-09-12).
Source: public Liber Primus rune transcription (`liber-primus-rtkd.txt` on the cook box; scream314 / rtkd delimiters). Full rune dump and page JPEGs are not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts).
Method family: **height-measured rail-fence** on the Sign-post / Cross section (onion 0-2). Rail count and start-rail are taken from the measured vertical offset of the two patriarchal crosses, not from the already-tried small rails 2/3/4.

Not Mobius direction-reversal (burned, `notes/mobius-direction-reversal-pass1.md`). Not sexagesimal block as key or transposition (burned, `notes/sexagesimal-block-*-pass1.md`). Not Mayfly GP-direction (burned, `notes/mayfly-numbers-direction-pass1.md`). Not regular columnar, not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, WELCOME, AN END, PARABLE and then yields continuous 3301-style English. Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd first page starting `SHEOGMIAF` is onion 0. Onion 0-2 are rtkd pages whose heads match SHEOGMIAF / AIMSNSOERUWSL / OEMUHTBEOLDHBM.

| onion | n | head (GP Latin) | raw IOC |
|---|---|---|---|
| 0 | 262 | `SHEOGMIAF...` | 0.03431 |
| 1 | 266 | `AIMSNSOERUWSL...` | ~1/29 |
| 2 | 201 | `OEMUHTBEOLDHBM...` | ~1/29 |
| 0-2 concat | 729 | (flat) | ~1/29 |

**PASS_ALIGN.**

## Calibration

Solved pages are Atbash / Vigenere DIVINITY / totient / direct. They are **not** rail-fence. Decrypting A WARNING ciphertext with a rail and expecting A WARNING is the wrong test.

### Parser replay

| Title | ok | method |
|---|---|---|
| A WARNING | True | Atbash p=28-c |
| WELCOME | True | Vigenere DIVINITY, skip-F |
| AN END | True | totient, skip F |
| PARABLE | True | direct Gematria |

### Engine self-test

Encrypt each solved-page plaintext with rail-fence (rails 2,3,5,7,8,12,13,17 × start 0..min(3,rails-1) × down/up). Decrypt with the same parameters. Success = exact invert **and** title readable.

**232 / 232 ok.** **PASS_CALIB.**

## Definition of the family

All three onion JPEGs are 2400×3600. Left/right third ink boxes are polluted by red rubric, so raw top-of-ink delta is a 25–31 px lie. The usable signal is the first fat-bar peak on each side:

| onion | left first bar y | right first bar y | bar0 Δ px | line_h px |
|---|---|---|---|---|
| 0 | 2212 | 986 | **1226** | 44 |
| 1 | 2211 | 987 | **1224** | 41 |
| 2 | 2207 | 987 | **1220** | 46 |

Offset is stable across the section (~1220–1226 px). Derived rails kept (2 ≤ r ≤ 40): **1226/44 ≈ 28**, n_right_bars=5, height-diff/line_h, left-bar-gap/line_h, plus ±2 neighbors. Union actually run as primary: **5–10, 12–16, 23–33**. Start-rail = 0 and (Δ mod rails). Both zigzag directions. Both decode (CT as row-read of a fence) and encode (CT already in reading order). Control rails 2/3/4 on onion 0 only (already FAIL in inventory; negative control).

Targets: onion 0, onion 1, onion 2, and the concatenated 0–2 stream. **1924** trials.

## Results

IOC stayed **0.03431** on onion 0 (permutation-invariant; if this were English in a fence the raw IOC would already be ~0.06). Same structural fact as the burned columnar pass.

3301 cribs of length ≥6: **0**. Four-word 3301 runs: **0**. Isolated THE / DEATH / NGTH fragments are 3-rune chance, not counted.

**NULL_ATTACK.** No readable 3301-style English.

## Falsify

This family dies if any of the following hold (several already do):

1. The engine cannot invert a known rail of solved-page English. **Did not die** (232/232).
2. The measured offset is unstable across onion 0–2. **Did not die** (~1220–1226 px).
3. A rail / start taken from that offset yields continuous 3301 English on 0, 1, 2, or 0–2. **Died.** 1924 nulls.
4. Raw IOC on these pages is ~0.06 (English already sitting in a fence). **Died.** IOC is 1/29, so rail-fence as the *only* layer cannot be the cipher.

What would reopen it: a new independent measurement that the two crosses encode a *different* integer than the ones tested, **and** that integer is a rail of English that also calibrates. Do not recook the same Δ/line_h neighborhood.

## Score

**PASS_CALIB / NULL_ATTACK**

Height-measured rail on onion 0–2 is burned. Do not recook.
