# Liber Primus Wing-and-Tree leaf-order pass 1 (onion 27-32)

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (`liber-primus-rtkd.txt` on the cook box; scream314 / rtkd delimiters). Full rune dump is not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts).
Method family: **leaf-order / branch-order reading transposition** on the Wing and Tree section (onion 27-32). Motivated by the section art (wing panels + tree), not by Mobius, sexagesimal, Mayfly, or cross-height rail. The rule is a page-layout reading order, not a substitution key.

Not Mobius direction-reversal (burned, `notes/mobius-direction-reversal-pass1.md`). Not sexagesimal block as key or transposition (burned, `notes/sexagesimal-block-*-pass1.md`). Not Mayfly GP-direction (burned, `notes/mayfly-numbers-direction-pass1.md`). Not cross-height rail on 0-2 (burned, `notes/cross-height-rail-pass1.md`). Not regular columnar, not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, AN END, PARABLE (and the method would need continuous 3301-style English). Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd parses to **72 rune pages**. First page starting `SHEOGMIAF` is rtkd index **15** = onion 0. Onion 27-32 are therefore rtkd **42-47**.

| onion | rtkd | n | lines | words | head (GP Latin) | raw IOC |
|---|---|---|---|---|---|---|
| 27 | 42 | 248 | 11 | 61 | `EOADNGTHLIAFPMURSC` | ~1/29 |
| 28 | 43 | 231 | 10 | 58 | `THNGCWEAORLDSMIBUF` | ~1/29 |
| 29 | 44 | 255 | 12 | 64 | `IAEOULFNGPRTHMASCW` | ~1/29 |
| 30 | 45 | 219 | 10 | 55 | `BDFNGHLEAORIUMCSTH` | ~1/29 |
| 31 | 46 | 242 | 11 | 60 | `NGTHAEIOULSCWMRPDF` | ~1/29 |
| 32 | 47 | 228 | 10 | 57 | `LORMEAITHNGCUSPBFW` | ~1/29 |

Section stream: **n ≈ 1423**, raw IOC **~0.0344** (1/29 = 0.03448). Flat. **PASS_ALIGN.**

(Exact per-page n/IOC taken from the desk parser on the cook-box rtkd dump; heads are GP-Latin previews of the page starts, not plaintext.)

## Calibration

### A_WARNING: ok=True

- method: Atbash p = 28-c on the early LP1 warning page
- preview head: `AWARNNGBELIEUENOTHNGFROMTHISBOOCEXCEPTWHATYOUCNOWTOBETRUETES`

### AN_END: ok=True

- method: totient p = (c-(prime-1)) mod 29 on rtkd page -2; F skipped as interrupter
- preview head: `ANENDWITHINTHEDEEPWEBTHEREEXISTSAPAGETHO...`

### PARABLE: ok=True

- method: direct Gematria Primus on last rune page
- preview head: `PARABLELICETHEINSTAR`

**PASS_CALIB.**

### Engine self-test

Leaf-order and branch-order ops are explicit permutations of indices. Forward then inverse restores PARABLE plaintext exactly. After a forward leaf-order pass, long cribs present in raw PARABLE drop to 0, so the op moves text. Odd leftover runes are appended in source order so every trial emits exactly `n` runes (no silent truncation).

## Definition of the family

Targets: whole Wing-and-Tree concat, and each onion page alone.
F modes: `none`, `drop_before` (drop every F, then apply).

Modes (layout-motivated reading orders; wing = even/odd panel, tree = depth-first / breadth-first over line-as-branch):

| mode | rule |
|---|---|
| identity | control |
| odd_lines_then_even | emit odd-indexed lines, then even (1-based wing panels) |
| even_lines_then_odd | even lines, then odd |
| interleave_halves | split page runes into L/R halves, emit L0 R0 L1 R1... |
| interleave_halves_rl | same, R first |
| line_boustrophedon | reverse every other line, then concat |
| line_reverse_all | reverse each line, keep line order |
| cols_then_rows | treat lines as rows; read column-major (ragged rows pad with skip, not a new rune) |
| branch_dfs_pre | lines as children of a virtual root; pre-order walk (line, then next) — equivalent to identity on a flat list; kept as control sibling |
| branch_dfs_post | post-order over lines |
| zigzag_2 | rail-fence height 2 on the page stream (negative control vs burned rail family; height fixed, not cross-measured) |

Total cells: 7 targets (6 pages + concat) x 11 modes x 2 F modes = **154** trials.

Scoring: 3301 crib list, GP spelling, length >= 5, non-overlapping search on the continuous Latin string. Random control: 40 random permutations of the concat stream (seed 3301).

## Results

Identity on the raw Wing-and-Tree stream: **0** cribs >= 5 (expected for flat CT).

Best real cells: a handful of modes (`odd_lines_then_even`, `interleave_halves`, `line_boustrophedon`) each show **at most one** short crib (`THE` / `AND` class, length 3-4 after GP spelling) inside GP noise. IOC stays ~1/29 under every transposition (permutation-invariant). No cell lifts IOC toward the English-on-29 band (~0.06).

Random permutations of the same stream: crib count mean **~0.1**, max **1**. Isolated short function-word fragments are inside the null.

No cell produced a second crib, a 3-word content run, or continuous 3301-style English. Per-page cells agree with the concat null.

Strict improvements over identity crib count (len >= 5): **0 / 140** non-identity cells.

## What kills the family (this grid)

1. **No English.** Short function-word scraps equal the random-perm ceiling.
2. **No structure lift.** IOC is permutation-invariant and already flat; leaf/branch reorder cannot create English-on-29 IOC by itself.
3. **Section cut is not the excuse.** Per-page and whole-stream grids agree.
4. **Calibration is not the excuse.** A WARNING / AN END / PARABLE replay on the same parser.
5. **Art metaphor is not a cipher.** Wing panels and tree branches suggested the reading orders; they did not decode.

## What was not run

- Measuring pixel geometry of the wing/tree art as a numeric key (different family; would need page JPEGs in-repo, which this repo forbids).
- Whole LP2 0-55 under the same leaf-order grid (longer null of the same family).
- Mobius / sexagesimal / Mayfly / cross-height-rail reruns.

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

On onion 27-32, reading with leaf-order / branch-order / panel-interleave / boustrophedon layout transpositions does not yield continuous 3301-style English. Isolated short scraps match random permutation noise. No solve. LP2 0-55 unsolved.

Do not recook this leaf-order grid on 27-32 without a new independent layout measurement that is not one of the modes above.
