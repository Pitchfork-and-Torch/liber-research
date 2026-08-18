# Liber Primus running-key / autokey pass 1

Date: 2026-08-14 (America/New_York)
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo.
Method family: running-key Vigenere / Beaufort and plaintext- or ciphertext-autokey,
keys = Gematria-Primus rune indexes of solved LP2 56 AN END and 57 PARABLE plaintext.
Not Wave 1. Not book-index. Not SHA-512. Not YOUR INNOCENCE YOUR ILLUSIONS.
Honesty rail: no claimed solve unless calibration replays and a decode lifts IOC toward ~0.06+ with readable 3301 English.

## Calibration

All four known pages replay from this transcription. GP spellings kept (C/K, U/V, NG).

| Page | Method | n | ok | Preview |
|---|---|---|---|---|
| A_WARNING | Atbash p = 28-c on rtkd[0] | 184 | True | A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE FIND YOUR TRUTH EX PERIENCE Y |
| WELCOME | Vigenere DIVINITY; consume F at 5 and 14 (M in each WELCOME title) and F at 47 ( | 515 | True | WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EASY TRIP BUT FOR THOSE WHO FIND |
| AN_END | totient p=(c-(prime-1)) mod 29; skip F at page-local index 56 (the OF interrupte | 85 | True | AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PILGR IM TO SEEC OUT THIS PAGE |
| PARABLE | direct Gematria Primus | 95 | True | PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND TH E DIUINITY WITHIN AND EMER |

Notes:

- **A WARNING** (rtkd 0): Atbash `p = 28-c`. Opens `A WARNNG BELIEUE NOTHNG FROM THIS BOOC...` (WARNNG/BELIEUE/BOOC/CNOW are GP, not a fail).
- **WELCOME** (rtkd 1-2): Vigenere key DIVINITY = DIUINITY `[23,10,1,10,9,10,16,26]`. The F in each title WELCOME decrypts to M and **must consume the key**. Remaining F after index 47 are interrupters (do not consume). Skip-all-F breaks the title into WELCOFA. Recovered known opening through `ALONG THE WAY YOU WILL FIND AN END TO A` and later `ARE A LAW UNTO YOURSELF EACH INTELLIGENCE IS HOLY`. The middle gap is the already-burned INNOCENCE/ILLUSIONS region; not used as a key and not treated as calibration failure of DIVINITY.
- **AN END** (rtkd 71, 85 runes + 128 hex chars): totient `p = (c-(prime-1)) mod 29`, skip the F at **page-local index 56** (the F of OF). Full known text: `AN END WITHIN THE DEEP WEB THERE EXISTS A PAGE THAT HASHES TO IT IS THE DUTY OF EUERY PILGRIM TO SEEC OUT THIS PAGE`. Community 'skip index 202' is a no-op on this 85-rune page and leaves `DUTY OOE`. Hex sits between rune 45 and rune 46 and is not itself runes.
- **PARABLE** (rtkd 72, 95 runes): direct GP. `PARABLE LICE THE INSTAR TUNNELNG TO THE SURFACE WE MUST SHED OUR OWN CIRCUMFERENCES FIND THE DIUINITY WITHIN AND EMERGE`.

CALIBRATION_PASS True

## Keys (plaintext rune indexes, not Latin letters)

| Key | n | Head (GP Latin) | What |
|---|---|---|---|
| `anend_letters` | 85 | ANENDWITHINTHEDEEPWEBTHEREEXISTSAPA | AN END PT runes only (totient skip F@56), 85 |
| `anend_full` | 149 | ANENDWITHINTHEDEEPWEBTHEREEXISTSAPA | AN END PT[0:45] + hash bytes%29 (64) + PT rest, 149 |
| `parable` | 95 | PARABLELICETHEINSTARTUNNELNGTOTHESU | PARABLE PT runes (direct), 95 |
| `anend_then_parable` | 180 | ANENDWITHINTHEDEEPWEBTHEREEXISTSAPA | AN END letters + PARABLE, 180 |
| `parable_then_anend` | 180 | PARABLELICETHEINSTARTUNNELNGTOTHESU | PARABLE + AN END letters, 180 |
| `anend_full_then_parable` | 244 | ANENDWITHINTHEDEEPWEBTHEREEXISTSAPA | AN END full + PARABLE, 244 |

AN END letters-only is the 85 totient-decrypted runes (hash excluded).
AN END full inserts the 64 hash bytes reduced mod 29 at the natural hash slot (after 45 PT runes).
PARABLE key is the page itself (direct). Concatenations are those streams back-to-back.

## Cipher variants

All mod 29 on the 12956-rune unsolved stream (LP2 0-55, rtkd 15-70, IOC 0.03448).

- `rk_vig`: running-key Vigenere `p = (c-k) mod 29`, key repeats
- `rk_beau`: running-key Beaufort `p = (k-c) mod 29`, key repeats
- `auto_pt` / `auto_ct`: primer = key, then append decoded plaintext or ciphertext (Vigenere subtract)
- `auto_pt_beau` / `auto_ct_beau`: same primers with Beaufort `p = (k-c)`
- skip F: do not consume key on ciphertext F, vs consume every rune
- align `off0`: key[0] at global 0; `djubei_shift`: key[0] at global 6555 (whole stream); `djubei_from`: decode only from 6555

Trials run: **216** (6 keys x 6 ciphers x 2 F-rules x 3 alignments).

## IOC table (top 20 by whole-stream IOC)

| IOC | best 200+ win | content | key | cipher | skipF | align | head |
|---|---|---|---|---|---|---|---|
| 0.03609 | 0.04291 n=200 @9805 | 0 - | anend_then_parable | rk_vig | True | djubei_from | `EATHEOHAOSFJSRFSAETHTREAHTHYEANGLPCFBPET` |
| 0.03609 | 0.04291 n=200 @9805 | 0 - | anend_then_parable | rk_beau | True | djubei_from | `UIABNGCYXFEXAEFXRIAPAEUNGIAOUHNTAFEOTJIA` |
| 0.03604 | 0.04141 n=200 @9750 | 0 - | parable_then_anend | rk_vig | True | djubei_shift | `PMAXBGLFIAAFBTPYAEIFAEIAMXAELTEOUTLWRNGG` |
| 0.03604 | 0.04141 n=200 @9750 | 0 - | parable_then_anend | rk_beau | True | djubei_shift | `TICSEODNFTHCFEOPTORMFRTHISRNPBEAPNOEAEHD` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | anend_then_parable | auto_ct | True | off0 | `LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGO` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | anend_then_parable | auto_ct | True | djubei_shift | `LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGO` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | anend_then_parable | auto_ct_beau | True | off0 | `NUFGBBEOFTPLIPNGWEOBFAEAEXOETAFJYSFDOXNG` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | anend_then_parable | auto_ct_beau | True | djubei_shift | `NUFGBBEOFTPLIPNGWEOBFAEAEXOETAFJYSFDOXNG` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | parable_then_anend | auto_ct | True | off0 | `THPXHEEANFATPOOPUYIFAIAEAOEUFNEYOEAMINGG` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | parable_then_anend | auto_ct | True | djubei_shift | `THPXHEEANFATPOOPUYIFAIAEAOEUFNEYOEAMINGG` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | parable_then_anend | auto_ct_beau | True | off0 | `IATSNGJULFCPTYYTEAOMFCTHUWEAFLJOYUIMHDFA` |
| 0.03601 | 0.04266 n=200 @10350 | 0 - | parable_then_anend | auto_ct_beau | True | djubei_shift | `IATSNGJULFCPTYYTEAOMFCTHUWEAFLJOYUIMHDFA` |
| 0.03599 | 0.04166 n=200 @10255 | 0 - | anend_then_parable | auto_ct | True | djubei_from | `EATHEOHAOSFJSRFSAETHTREAHTHYEANGLPCFBPET` |
| 0.03599 | 0.04166 n=200 @10255 | 0 - | anend_then_parable | auto_ct_beau | True | djubei_from | `UIABNGCYXFEXAEFXRIAPAEUNGIAOUHNTAFEOTJIA` |
| 0.03595 | 0.04166 n=200 @10255 | 0 - | parable_then_anend | auto_ct | True | djubei_from | `ITYOEUMWFOESHPTHUIAETHMTHSEOTTFPEAFGEOTH` |
| 0.03595 | 0.04166 n=200 @10255 | 0 - | parable_then_anend | auto_ct_beau | True | djubei_from | `MPOWEAIOEFWXNGTIAEAMRIAIIAXBPPFTUFDBIAXE` |
| 0.03594 | 0.04347 n=200 @5750 | 0 - | parable | rk_vig | True | off0 | `THPXHEEANFCNGFMTNGTHLNFWGTHFOELIASUNGPRY` |
| 0.03594 | 0.04347 n=200 @5750 | 0 - | parable | rk_vig | True | djubei_shift | `THPXHEEANFCNGFMTNGTHLNFWGTHFOELIASUNGPRY` |
| 0.03594 | 0.04347 n=200 @5750 | 0 - | parable | rk_beau | True | off0 | `IATSNGJULFAHFIPHIANLFOEDIAFWNTHXEAHTAEOL` |
| 0.03594 | 0.04347 n=200 @5750 | 0 - | parable | rk_beau | True | djubei_shift | `IATSNGJULFAHFIPHIANLFOEDIAFWNTHXEAHTAEOL` |

Max whole-stream IOC: **0.03609** (baseline 0.03448; English-on-29 ~ 0.06+).
Max window IOC (200/400/800, step 50): **0.04508**.

The entire top 20 is `skipF=True`. Leaving ciphertext F unmoved slightly raises IOC because F is already common in the stream; that +0.0016 is an interrupter artifact, not language. Consume-every-rune rows stay on ~0.0345. Autokey `djubei_shift` equals `off0` (primer still starts at 0); the real DJUBEI autokey test is `djubei_from`.

## Candidate prefixes

Highest-IOC decode heads (not claimed plaintext):

- `anend_then_parable` / rk_vig skipF=True djubei_from IOC=0.03609: `EATHEOHAOSFJSRFSAETHTREAHTHYEANGLPCFBPETHJEOFDCSUEUFNHYAEIEEOOHRTHEWYNTHEIAS`
- `anend_then_parable` / rk_beau skipF=True djubei_from IOC=0.03609: `UIABNGCYXFEXAEFXRIAPAEUNGIAOUHNTAFEOTJIAEBFGAXEAJEAFLNGORMJBYNGAEIAJOEOLIAJTHX`
- `parable_then_anend` / rk_vig skipF=True djubei_shift IOC=0.03604: `PMAXBGLFIAAFBTPYAEIFAEIAMXAELTEOUTLWRNGGXGSMFTGEASYYLGEOOEUGBFUWOWXBFIA`
- `parable_then_anend` / rk_beau skipF=True djubei_shift IOC=0.03604: `TICSEODNFTHCFEOPTORMFRTHISRNPBEAPNOEAEHDSDXIFPDUXOONDBWEADEOFEAOEYOESEOFTH`
- `anend_then_parable` / auto_ct skipF=True off0 IOC=0.03601: `LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGOWRSSFOEDMATHOENUSXGAAEDOEYNGAFX`
- `anend_then_parable` / auto_ct skipF=True djubei_shift IOC=0.03601: `LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGOWRSSFOEDMATHOENUSXGAAEDOEYNGAFX`

No row produced a 3301-style English sentence. Isolated function words (THE/OF/A) appear at chance in 29-rune noise and were not counted as hits.

## What was not done

- No Atbash / Caesar / totient / Vigenere-on-DIVINITY-CIRCUMFERENCE / LP1-running-key / 15.jpg stream (Wave 1).
- No LP1 English / 2016 / 2012-14 path as book-cipher coordinates.
- No SHA-512 preimage. No YOUR INNOCENCE YOUR ILLUSIONS pad.
- No public post.

## Verdict

FAIL: no running-key/autokey from AN END / PARABLE lifts unsolved 0-55 IOC (0.03448) toward 0.06+ with readable 3301 English (max IOC 0.03609, max 200+ window 0.04508).

Parser log:
```
rtkd raw %-parts: 74
dropped trailing section-mark part
content parts: 73
LP1 rtkd 0-14: 15
LP2 0-55 rtkd 15-70: 56
AN END rtkd 71 runes=85
PARABLE rtkd 72 runes=95
KEY DIVINITY [23, 10, 1, 10, 9, 10, 16, 26] DIUINITY
CAL A_WARNING ok=True n=184 A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE
CAL WELCOME ok=True n=515 WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EA
CAL AN_END ok=True n=85 AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PI
CAL PARABLE ok=True n=95 PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND
CALIBRATION_PASS True
AN END hex chars=128 head=36367763ab73783c7af284446c59466b
hex bytes%29 n=64 head=[25, 25, 3, 12, 26, 28, 4, 2, 6, 10, 16, 10]
KEY anend_letters n=85 latin_head=ANENDWITHINTHEDEEPWEBTHEREE | AN END PT runes only (totient skip F@56), 85
KEY anend_full n=149 latin_head=ANENDWITHINTHEDEEPWEBTHEREE | AN END PT[0:45] + hash bytes%29 (64) + PT rest, 149
KEY parable n=95 latin_head=PARABLELICETHEINSTARTUNNE | PARABLE PT runes (direct), 95
KEY anend_then_parable n=180 latin_head=ANENDWITHINTHEDEEPWEBTHEREE | AN END letters + PARABLE, 180
KEY parable_then_anend n=180 latin_head=PARABLELICETHEINSTARTUNNE | PARABLE + AN END letters, 180
KEY anend_full_then_parable n=244 latin_head=ANENDWITHINTHEDEEPWEBTHEREE | AN END full + PARABLE, 244
UNSOLVED pages=56 runes=12956 ioc29=0.03448
DJUBEI global 6555 rune=D
TRIALS 216
TOP10 by IOC:
  ioc=0.03609 win=0.04291@200+9805 content=0 anend_then_parable rk_vig skipF=True djubei_from head=EATHEOHAOSFJSRFSAETHTREAHTHYEANGLPCFBPETHJEOFDCSUE
  ioc=0.03609 win=0.04291@200+9805 content=0 anend_then_parable rk_beau skipF=True djubei_from head=UIABNGCYXFEXAEFXRIAPAEUNGIAOUHNTAFEOTJIAEBFGAXEAJE
  ioc=0.03604 win=0.04141@200+9750 content=0 parable_then_anend rk_vig skipF=True djubei_shift head=PMAXBGLFIAAFBTPYAEIFAEIAMXAELTEOUTLWRNGGXGSMFTGEAS
  ioc=0.03604 win=0.04141@200+9750 content=0 parable_then_anend rk_beau skipF=True djubei_shift head=TICSEODNFTHCFEOPTORMFRTHISRNPBEAPNOEAEHDSDXIFPDUXO
  ioc=0.03601 win=0.04266@200+10350 content=0 anend_then_parable auto_ct skipF=True off0 head=LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGOWRSSFOEDMA
  ioc=0.03601 win=0.04266@200+10350 content=0 anend_then_parable auto_ct skipF=True djubei_shift head=LEAFDEOEOBFPTNMTHOEBEOFRRSWPCFEOXFGYSHGOWRSSFOEDMA
  ioc=0.03601 win=0.04266@200+10350 content=0 anend_then_parable auto_ct_beau skipF=True off0 head=NUFGBBEOFTPLIPNGWEOBFAEAEXOETAFJYSFDOXNGDYOEAEXXFW
  ioc=0.03601 win=0.04266@200+10350 content=0 anend_then_parable auto_ct_beau skipF=True djubei_shift head=NUFGBBEOFTPLIPNGWEOBFAEAEXOETAFJYSFDOXNGDYOEAEXXFW
  ioc=0.03601 win=0.04266@200+10350 content=0 parable_then_anend auto_ct skipF=True off0 head=THPXHEEANFATPOOPUYIFAIAEAOEUFNEYOEAMINGGFCAEJCPUEA
  ioc=0.03601 win=0.04266@200+10350 content=0 parable_then_anend auto_ct skipF=True djubei_shift head=THPXHEEANFATPOOPUYIFAIAEAOEUFNEYOEAMINGGFCAEJCPUEA
HITS_STRICT 0
MAX_IOC 0.03609 MAX_WIN 0.04508
VERDICT: FAIL: no running-key/autokey from AN END / PARABLE lifts unsolved 0-55 IOC (0.03448) toward 0.06+ with readable 3301 English (max IOC 0.03609, max 200+ window 0.04508).
```
