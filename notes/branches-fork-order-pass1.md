# Liber Primus Branches binary-fork pass 1 (onion 8-14)

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (`liber-primus-rtkd.txt` on the cook box; scream314 / rtkd delimiters). Full rune dump is not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts).
Method family: **binary-fork / L-R half-merge / heap-tree path** transposition on the Branches section (onion 8-14). Motivated by the section art (branch / fork marginalia), not by Mobius, sexagesimal, Mayfly, Wing-and-Tree leaf-order, Spirals spiral-order, or cross-height rail. The rule is a page-layout fork read, not a substitution key.

Not Mobius direction-reversal (burned, `notes/mobius-direction-reversal-pass1.md`). Not sexagesimal block as key or transposition (burned, `notes/sexagesimal-block-*-pass1.md`). Not Mayfly GP-direction (burned, `notes/mayfly-numbers-direction-pass1.md`). Not cross-height rail on 0-2 (burned, `notes/cross-height-rail-pass1.md`). Not Wing-and-Tree leaf-order on 27-32 (burned, `notes/wing-tree-leaf-order-pass1.md`). Not Spirals spiral/ring on 3-7 (burned, `notes/spirals-order-pass1.md`). Not regular columnar, not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, AN END, PARABLE (and the method would need continuous 3301-style English). Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd parses to **72 rune pages**. First page starting `SHEOGMIAF` is rtkd index **15** = onion 0. Onion 8-14 are therefore rtkd **23-29**.

| onion | rtkd | n | lines | words | head (GP Latin) | raw IOC |
|---|---|---|---|---|---|---|
| 8 | 23 | 255 | 12 | 56 | `XIXMUXMCTHPOBIANTE` | 0.03428 |
| 9 | 24 | 268 | 12 | 66 | `YWAEGJNGMAWPAUNPIA` | 0.03346 |
| 10 | 25 | 263 | 12 | 73 | `CXUPTSUEGTHIALESEA` | 0.03352 |
| 11 | 26 | 273 | 12 | 62 | `IASCEWBNLNGTHNIEAB` | 0.03504 |
| 12 | 27 | 261 | 12 | 72 | `CIRCWEAEOTTHCHUIAW` | 0.03395 |
| 13 | 28 | 272 | 12 | 69 | `GTHFJGCBIMLEOEAWNA` | 0.03343 |
| 14 | 29 | 137 | 7 | 34 | `TJFOLDNGCLGMEATHUO` | 0.03381 |

Section stream: **n = 1729**, raw IOC **0.03446** (1/29 = 0.03448). Flat. **PASS_ALIGN.**

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

Fork / heap-path ops are explicit permutations of line-grid indices (ragged rows skip empty cells, not a new rune). Each forward op on PARABLE keeps length `n` and drops long cribs present in the raw direct readout (PARABLE / INSTAR / TUNNELNG class), so the op moves text. Odd leftover multiset fill (if any) restores exact `n` with no silent truncation.

## Definition of the family

Targets: whole Branches concat (per-page then join), and each onion page alone.
F modes: `none`, `drop_before` (drop every F, then apply).

Modes (layout-motivated fork / tree reads; reverse-rows kept as a near-sibling control):

| mode | rule |
|---|---|
| identity | control |
| fork_lr_concat | split each line at midpoint; emit all left halves, then all right |
| fork_rl_concat | same split; emit all right halves, then all left |
| fork_interleave | per line: left half then right half, walk lines in order |
| fork_zip_chars | per line: interleave left/right chars |
| dfs_preorder | treat row-major cells as a binary heap; DFS preorder |
| dfs_inorder | binary-heap DFS inorder |
| bfs_heap | binary-heap BFS from root |
| cols_alt_zigzag | column-major with alternating down/up (branch zigzag) |
| reverse_rows | reverse line order, keep within-line order |

Total cells: 7 pages x 10 modes x 2 F + concat x 10 modes x 2 F = **160** trials.

Scoring: 3301 crib list, GP spelling, length >= 5, non-overlapping search on the continuous Latin string. Random control: 40 random permutations of the 1729-rune stream (seed 3301).

## Results

Identity on the raw Branches stream: **0** cribs >= 5 (expected for flat CT).

Every fork / heap / sibling cell also scored **0** cribs >= 5. IOC stayed in the 0.033-0.037 band (drop-F raises IOC slightly by shrinking `n`; permutations do not lift toward English-on-29 ~0.06).

Random permutations of the same stream: crib count mean **0.0**, max **0**. The attack grid never beat identity.

Strict improvements over identity crib count: **0 / 144** non-identity cells.

## What kills the family (this grid)

1. **No English.** Zero cribs >= 5 across the full fork/tree grid.
2. **No structure lift.** IOC remains ~1/29 under every fork permutation.
3. **Section cut is not the excuse.** Per-page and whole-stream grids agree.
4. **Calibration is not the excuse.** A WARNING / AN END / PARABLE replay on the same parser.

## What was not run

- Whole LP2 0-55 under the same fork family (would be a longer null of the same family; not needed to burn the Branches cut).
- Pixel-measured branch pitch from the JPEG art (image work stays out of this repo; layout used transcription line grids only).
- Mobius / Mayfly / Wing-and-Tree / Spirals / sexagesimal / cross-height rail reruns.
- Spiral Branches onion 40-53 (separate section; not this pass).

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

On onion 8-14, reading the Branches section as a binary fork / L-R half-merge / heap-tree path (or near-sibling zigzag / reverse-rows) does not yield continuous 3301-style English. No solve. LP2 0-55 unsolved.
