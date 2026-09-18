# Liber Primus Mayfly GP-direction pass 1 (onion 23-26)

Date: 2026-09-17 (America/New_York).
Source: public Liber Primus rune transcription (`liber-primus-rtkd.txt` on the cook box; scream314 / rtkd delimiters). Full rune dump is not in this repo.
Parser/constants: standard 29-rune Gematria Primus, rebuilt in an ephemeral desk script (not committed; README forbids attack scripts).
Method family: **GP value as reading direction / skip** on the Mayfly section (onion 23-26), taken from the idle leftover "a number rule internal to the unsolved runes (2016: their numbers are the direction)". The section name is only a page bound; the rule is numeric, not entomological metaphor beyond the section cut.

Not Mobius direction-reversal (burned, `notes/mobius-direction-reversal-pass1.md`). Not sexagesimal block as key or transposition (burned, `notes/sexagesimal-block-*-pass1.md`). Not rail on 0-2, not regular columnar, not Vigenere/Beaufort DJUBEI, not running-key/autokey, not totient/An End, not outguess, not Playfair. None of those were rerun.

Honesty rail: no claimed solve unless the parser first replays A WARNING, AN END, PARABLE (and the method would need continuous 3301-style English). Every gloss below is HYPOTHESIS. LP2 0-55 stays unsolved.

## Alignment

rtkd parses to **72 rune pages**. First page starting `SHEOGMIAF` is rtkd index **15** = onion 0. Onion 23-26 are therefore rtkd **38-41**.

| onion | rtkd | n | lines | words | head (GP Latin) | raw IOC |
|---|---|---|---|---|---|---|
| 23 | 38 | 213 | 10 | 52 | `UAWNGGXDGIBIEOTBIY` | 0.03189 |
| 24 | 39 | 270 | 12 | 73 | `DRFEJAENCHWEOIAPEA` | 0.03324 |
| 25 | 40 | 273 | 12 | 66 | `HNGWXCXYSPCOERBYJN` | 0.03326 |
| 26 | 41 | 265 | 12 | 69 | `IAONEAOJYEOXEAAIAN` | 0.03362 |

Section stream: **n = 1021**, raw IOC **0.03427** (1/29 = 0.03448). Flat. **PASS_ALIGN.**

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

`order_by_value` is an explicit stable permutation of indices. Forward then inverse restores PARABLE plaintext exactly. After the forward permutation, the 6 long cribs present in raw PARABLE drop to 0, so the op moves text. Skip/walk modes that break cycles fill remaining indices in order so every trial emits exactly `n` runes (no silent truncation).

## Definition of the family

Targets: whole Mayfly concat, and each onion page alone.
F modes: `none`, `drop_before` (drop every F, then apply).
Modes (GP index 0..28 is the "number"):

| mode | rule |
|---|---|
| identity | control |
| skip_fwd | from i, emit, step = gp[i]+1 forward, mod n; fill unseen in order |
| skip_back | same, step backward |
| cumulative_index | walk i := (i + gp[i] + 1) mod n, emit on first visit; fill rest |
| direction_sign | even gp => +1, odd => -1 after emit; fill rest |
| order_by_value | stable sort positions by (gp, index) |
| order_by_value_desc | stable sort by (-gp, index) |
| step_mod | classical mul-mod with step = gp[0] nudged to coprime with n |
| caesar_by_prev | differential p[i]=(c[i]-c[i-1]) mod 29 (not a transposition; included as the nearest "number from prior rune" substitution) |

Total cells: 5 targets x 9 modes x 2 F modes = **90** trials.

Scoring: 3301 crib list, GP spelling, length >= 5, non-overlapping search on the continuous Latin string. Random control: 40 random permutations of the 1021-rune stream (seed 3301).

## Results

Identity on the raw Mayfly stream: **0** cribs >= 5 (expected for flat CT).

Best real cells: `skip_fwd` and `cumulative_index` with `drop_before` on the whole stream each show **one** hit, `DEATH` at offset 21 (`...NWAECDEATHIAMOS...`). IOC stays 0.03552 (drop-F baseline). Surrounding text is GP noise, not a sentence.

Random permutations of the same stream: crib count mean **0.10**, max **1**. A single short crib is inside the null.

No cell produced a second crib, a 3-word content run, or an IOC lift toward the English-on-29 band (~0.06). Per-page cells were all at 0 cribs except the same chance class.

Strict improvements over identity crib count: **2 / 80** non-identity cells, both at the random max of 1.

## What kills the family (this grid)

1. **No English.** One `DEATH` in noise equals the random-perm ceiling.
2. **No structure lift.** IOC remains ~1/29 under permutations; differential `caesar_by_prev` also stays flat (~0.034-0.036) with 0 cribs on the stream.
3. **Section cut is not the excuse.** Per-page and whole-stream grids agree.
4. **Calibration is not the excuse.** A WARNING / AN END / PARABLE replay on the same parser.

## What was not run

- Whole LP2 0-55 under the same walk (would be a longer null of the same family; not needed to burn the Mayfly cut).
- Using GP **primes** (2,3,5,...) instead of GP **indices** as the step. That is a sibling family; note only.
- Using the 2016 deep-web hash digits as the step stream (different artifact; out of scope for this rune-section pass).
- Mobius / cuneiform / sexagesimal reruns.

## Verdict

**NULL_ATTACK** (PASS_ALIGN, PASS_CALIB, CONTROL_OK, attack inside the null).

On onion 23-26, reading with each rune's Gematria Primus index as a skip, sort key, mul-mod step, sign bit, or differential does not yield continuous 3301-style English. The single `DEATH` crib matches random permutation noise. No solve. LP2 0-55 unsolved.

Idle leftover "numbers are the direction" is **burned for this Mayfly GP-index grid**. Do not recook the same 90 cells.

No public post. Desk script and JSON audit stayed on the cook box and are not committed.
