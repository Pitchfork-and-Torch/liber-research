# Liber Primus Spirals spiral-order pass 1 (onion 3-7)

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (`liber-primus-rtkd.txt` on the cook box; scream314 / rtkd delimiters). Full rune dump is not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts).
Method family: **spiral-order / ring-order reading transposition** on the Spirals section (onion 3-7). Motivated by the section art (spiral marginalia), not by Mobius, sexagesimal, Mayfly, Wing-and-Tree, or cross-height rail. The rule is a page-layout reading order, not a substitution key.

Not Mobius direction-reversal (burned, `notes/mobius-direction-reversal-pass1.md`). Not sexagesimal block as key or transposition (burned, `notes/sexagesimal-block-*-pass1.md`). Not Mayfly GP-direction (burned, `notes/mayfly-numbers-direction-pass1.md`). Not cross-height rail on 0-2 (burned, `notes/cross-height-rail-pass1.md`). Not Wing-and-Tree leaf-order (burned, `notes/wing-tree-leaf-order-pass1.md`). Not regular columnar, not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, AN END, PARABLE (and the method would need continuous 3301-style English). Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd parses to **72 rune pages**. First page starting `SHEOGMIAF` is rtkd index **15** = onion 0. Onion 3-7 are therefore rtkd **18-22**.

| onion | rtkd | n | lines | words | head (GP Latin) | raw IOC |
|---|---|---|---|---|---|---|
| 3 | 18 | 217 | 11 | 50 | `LJEOHNGCTHTAEJTXHT` | 0.03307 |
| 4 | 19 | 261 | 12 | 70 | `LIAYPXIWMCILGFNIAC` | 0.03495 |
| 5 | 20 | 263 | 12 | 66 | `RAEXHJAEMLFCNGDING` | 0.03553 |
| 6 | 21 | 196 | 10 | 48 | `XCTHDEOXBEAAENJEAA` | 0.03234 |
| 7 | 22 | 208 | 10 | 57 | `HNGLTHBSCUCOIALCJX` | 0.03595 |

Section stream: **n = 1145**, raw IOC **0.03463** (1/29 = 0.03448). Flat. **PASS_ALIGN.**

## Calibration

### A_WARNING: ok=True

- method: Atbash p = 28-c on the early LP1 warning page
- preview head: `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWHATYOUCNOWTOBETRUETES`

### AN_END: ok=True

- method: totient p = (c-(prime-1)) mod 29 on rtkd page -2; F skipped as interrupter (parser replay; same kit as prior NULL notes)

### PARABLE: ok=True

- method: direct Gematria Primus on last rune page
- preview head: `PARABLELICETHEINSTAR`

**PASS_CALIB.**

### Engine self-test

Spiral / ring / column ops are explicit permutations of line-grid indices (ragged rows skip empty cells, not a new rune). Each forward op on PARABLE keeps length `n` and drops long cribs present in the raw direct readout (PARABLE / INSTAR / TUNNELNG class), so the op moves text. Odd leftover multiset fill (if any) restores exact `n` with no silent truncation.

## Definition of the family

Targets: whole Spirals concat, and each onion page alone.
F modes: `none`, `drop_before` (drop every F, then apply).

Modes (layout-motivated spiral / ring reads; boustrophedon and column-major kept as near-sibling controls):

| mode | rule |
|---|---|
| identity | control |
| spiral_cw | clockwise spiral on the line grid (outer ring inward) |
| spiral_ccw | counter-clockwise spiral |
| spiral_center_cw | expand rings from page center, clockwise within ring |
| spiral_center_ccw | expand rings from center, counter-clockwise within ring |
| spiral_cw_then_rev | clockwise spiral, then reverse the emitted stream |
| page_spiral_cw_concat | spiral each onion page clockwise, then concat (concat target only) |
| boustrophedon | reverse every other line, then concat |
| reverse_rows | reverse line order, keep within-line order |
| cols_then_rows | column-major read of the ragged line grid |

Total cells: 5 pages x 9 modes x 2 F + concat x 10 modes x 2 F = **110** trials.

Scoring: 3301 crib list, GP spelling, length >= 5, non-overlapping search on the continuous Latin string. Random control: 40 random permutations of the 1145-rune stream (seed 3301).

## Results

Identity on the raw Spirals stream: **0** cribs >= 5 (expected for flat CT).

Every spiral / ring / sibling cell also scored **0** cribs >= 5. IOC stayed in the 0.033-0.037 band (drop-F raises IOC slightly by shrinking `n`; permutations do not lift toward English-on-29 ~0.06).

Random permutations of the same stream: crib count mean **0.025**, max **1**. The attack grid never reached even the random max.

Strict improvements over identity crib count: **0 / 98** non-identity cells.

## What kills the family (this grid)

1. **No English.** Zero cribs >= 5 across the full spiral/ring grid.
2. **No structure lift.** IOC remains ~1/29 under every spiral permutation.
3. **Section cut is not the excuse.** Per-page and whole-stream grids agree.
4. **Calibration is not the excuse.** A WARNING / AN END / PARABLE replay on the same parser.

## What was not run

- Whole LP2 0-55 under the same spiral family (would be a longer null of the same family; not needed to burn the Spirals cut).
- Pixel-measured spiral pitch from the JPEG art (image work stays out of this repo; layout used transcription line grids only).
- Mobius / Mayfly / Wing-and-Tree / sexagesimal / cross-height rail reruns.

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

On onion 3-7, reading the Spirals section as a clockwise / counter-clockwise / center-out spiral (or near-sibling boustrophedon / column-major) does not yield continuous 3301-style English. No solve. LP2 0-55 unsolved.

## Paths

- Note: `notes/spirals-order-pass1.md`
- Desk summary JSON (cook box only, not in repo): spiral trial rollup used to fill the tables above
