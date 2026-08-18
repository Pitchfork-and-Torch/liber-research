# Liber Primus acrostic / telestich pass 1

Date: 2026-08-14 (America/New_York)
Worker: executor subagent
Source: public Liber Primus rune transcription (scream314/rtkd; cicadasolvers.com). Full rune dump is not in this repo. Linux box only. No public post.
Honesty rail: no claimed solve. Calibration is a hard stop.
Method: one family - acrostic / telestich. For each page and the whole
unsolved stream, take first rune of each word, last rune of each word,
and first+last (concatenated, then interleaved). Words are rtkd `-`
delimited (also broken on `. & $ sect / %`, same as `page_runes`).
Then the known-good Gematria path only:

- identity / direct
- Atbash (28-i)
- Vigenere DIVINITY (WELCOME rule: consume the title F that is M;
  skip later F interrupters after index 47 on the stream being decoded)
- totient `(c-(p-1)) mod 29` with the AN END skip (F at local index 56)

Not used: book-index, word-unit book, running-key AN END, periodic
Vigenere, columnar, SHA-512, YOUR INNOCENCE, INSTAR JPEGs.
Reuse: `lp_analyze.parse_pages` / `page_runes` / `ioc` / `to_latin`;
Atbash / Vigenere / totient match `liber-transposition-pass1.py`.
Script: `box-only acrostic runner (not in this repo)`
Audit: `box-only acrostic audit (not in this repo)`

## 0. Full-stream sanity (not the acrostic test)

The known-good path still replays on this transcription when the
**unreduced** rune stream is used. If this were False the file or
the reused functions would be wrong, and the acrostic test would be
meaningless.

| Title | ok | n runes / words | preview |
|---|---|---|---|
| A_WARNING | True | 184 / 50 | `A WARNNG BELIEUE NOTHNG FROM THIS BOOC EXCEPT WHAT YOU CNOW TO BE TRUE TEST THE C NOWLEDGE` |
| WELCOME | True | 515 / 140 | `WELCOME WELCOME PIL GRIM TO THE GREAT JOU RNEY TOWARD THE END OF ALL THNGS IT IS NOT AN EA` |
| AN_END | True | 85 / 28 | `AN END WITHIN THE DEEP WEB TH ERE EXISTS A PAGE THAT HA SHES TO IT IS THE DUTY OF EUERY PI` |
| PARABLE | True | 95 / 23 | `PARABLE LICE THE INSTAR T UNNELNG TO THE SURFACE WE MUST SHED OUR OWN C IRCUMFERENCES FIND` |

Full-stream known-good path: **True**.

WELCOME title-only no-skip head: `WELCOMEWELCOMEPILGRIMTOTHEGREATJOURNEYTO`.

## 1. Calibration (the actual test)

On each solved page, take first / last / first+last of **ciphertext**
words, then apply identity / Atbash / Vigenere DIVINITY / totient.
Success = the page's own title comes back as a compact string
(`AWARNNG`/`AWARNING`, `WELCOME`, `ANEND`, `PARABLE`) in the reduced
stream, as a title or as the opening.

Why this is the right bar: an acrostic that cannot reprint the title
it already knows is not a method for the unsolved book. First-of-word
of `A WARNNG BELIEUE...` is `A W B N F T B E...`, not `A WARNNG`.
That is the expected failure mode, not a transcription bug.

### 1a. Did any reduction+path recover a title?

| Title | pages | reduction | path | n | ok | opening | head |
|---|---|---|---|---|---|---|---|
| A_WARNING | 0 | first | atbash | 50 | False | False | `AWBNFTHBEWYCTBTTTHCNFYTEPYDDNEORCTHBOTHM` |
| A_WARNING | 0 | last | atbash | 50 | False | False | `ANGENGMSCTTUWOEETECEDRTHXERTHOTTORESCREE` |
| A_WARNING | 0 | fl_concat | atbash | 100 | False | False | `AWBNFTHBEWYCTBTTTHCNFYTEPYDDNEORCTHBOTHM` |
| A_WARNING | 0 | fl_interleave | atbash | 100 | False | False | `AAWNGBENNGFMTHSBCETWTYUCWTOBETETTTHECCNE` |
| WELCOME | 1 | first | vig-DIVINITY-welcome-rule | 70 | False | False | `WDEAGBEFARSTHBLHAEFIFRSHDPSIMJWHDAWAENRJ` |
| WELCOME | 1 | last | vig-DIVINITY-welcome-rule | 70 | False | False | `JEPEITHNUPDIAFLJNTTHSAYXFEHMOEYYGTNWPTHRL` |
| WELCOME | 1 | fl_concat | vig-DIVINITY-welcome-rule | 140 | False | False | `WDEAGBEFARSTHBLHAEFIFRSHDPSIMJWHDAWAENRJ` |
| WELCOME | 1 | fl_interleave | vig-DIVINITY-welcome-rule | 140 | False | False | `WAOELRFTHONIATHWSCURYADDEJPGMBJOSITISNS` |
| WELCOME | 1+2 | first | vig-DIVINITY-welcome-rule | 140 | False | False | `WDEAGBEFARSTHBLHAEFIFRSHDPSIMJWHDAWAENRJ` |
| WELCOME | 1+2 | last | vig-DIVINITY-welcome-rule | 140 | False | False | `JEPEITHNUPDIAFLJNTTHSAYXFEHMOEYYGTNWPTHRL` |
| WELCOME | 1+2 | fl_concat | vig-DIVINITY-welcome-rule | 280 | False | False | `WDEAGBEFARSTHBLHAEFIFRSHDPSIMJWHDAWAENRJ` |
| WELCOME | 1+2 | fl_interleave | vig-DIVINITY-welcome-rule | 280 | False | False | `WAOELRFTHONIATHWSCURYADDEJPGMBJOSITISNS` |
| AN_END | 70 | first | totient-anend-rule | 28 | False | False | `ALSYAAIAXYNGOEIAXFBJFAENGNGJAYPILGG` |
| AN_END | 70 | last | totient-anend-rule | 28 | False | False | `ITHRMYPIAAXNGILCEHFNTPBRIEOTHLXTHAE` |
| AN_END | 70 | fl_concat | totient-anend-rule | 56 | False | False | `ALSYAAIAXYNGOEIAXFBJFAENGNGJAYPILGGMHIAJTOJH` |
| AN_END | 70 | fl_interleave | totient-anend-rule | 56 | False | False | `ANEIANAETWEOHGEOUSMMCEOHNLIYTOIAEOPFANNTAP` |
| PARABLE | 71 | first | identity | 23 | False | False | `PLTHITUTTHSWMSOOCIFTHEDWAE` |
| PARABLE | 71 | last | identity | 23 | False | False | `EEERTNGOEEETDRNCSDTHEYNDE` |
| PARABLE | 71 | fl_concat | identity | 46 | False | False | `PLTHITUTTHSWMSOOCIFTHEDWAEEEERTNGOEEETDR` |
| PARABLE | 71 | fl_interleave | identity | 46 | False | False | `PELETHEIRTTUNGTOTHESEWEMTSDORONCCISFDTHTH` |

Trials: 120 (5 page-groups x 4 reductions x 6 paths).
Titles recovered: NONE.

### 1b. Decrypt-then-reduce diagnostic (not a new cipher)

For letter-wise maps (identity, Atbash) this equals reduce-then-path.
For Vigenere / totient it is the acrostic of the **known plaintext**
words. Shown so the fail is visible as English initials, not noise.

| Title | pages | reduction | n | ok | az head |
|---|---|---|---|---|---|
| A_WARNING | 0 | first | 50 | False | `AWBNFTHBEWYCTBTTTHCNFYTEPYDDNEORCTHBOTHMCWETHWRO` |
| A_WARNING | 0 | last | 50 | False | `ANGENGMSCTTUWOEETECEDRTHXERTHOTTORESCREEDNREOSRR` |
| A_WARNING | 0 | fl_concat | 100 | False | `AWBNFTHBEWYCTBTTTHCNFYTEPYDDNEORCTHBOTHMCWETHWRO` |
| A_WARNING | 0 | fl_interleave | 100 | False | `AAWNGBENNGFMTHSBCETWTYUCWTOBETETTTHECCNEFDYRTTHE` |
| WELCOME | 1 | first | 70 | False | `WWPGTTHGJRTTHEOHOFDFETHWWEATHDLEHLDUWAENAEJEOBDL` |
| WELCOME | 1 | last | 70 | False | `EELMOETUYDEDGJNMASEAGWFAEJOGBLXBNWPTHAERAIAPRWNA` |
| WELCOME | 1 | fl_concat | 140 | False | `WWPGTTHGJRTTHEOHOFDFETHWWEATHDLEHLDUWAENAEJEOBDL` |
| WELCOME | 1 | fl_interleave | 140 | False | `WEWEPLGMTOTHEGTJURYTDTHEEDOGHJONFMDAFSEEATHGWWWF` |
| WELCOME | 1+2 | first | 140 | False | `WWPGTTHGJRTTHEOATHIINAEATBFTHWFTHWHIIANOALTHWYWF` |
| WELCOME | 1+2 | last | 140 | False | `EELMOETUYDEDFLSTSTNYPTREODRYETSAYEANGEYULDNNDONG` |
| WELCOME | 1+2 | fl_concat | 280 | False | `WWPGTTHGJRTTHEOATHIINAEATBFTHWFTHWHIIANOALTHWYWF` |
| WELCOME | 1+2 | fl_interleave | 280 | False | `WEWEPLGMTOTHEGTJURYTDTHEEDOFALTHSITISNTANEAYTPBT` |
| AN_END | 70 | first | 28 | False | `AEWTHDWTHEEAPTHHSTIITHDOEPITSOTHP` |
| AN_END | 70 | last | 28 | False | `NDNEPBTHESAETASOTSEYFYRMOCTSE` |
| AN_END | 70 | fl_concat | 56 | False | `AEWTHDWTHEEAPTHHSTIITHDOEPITSOTHPNDNEPBTHESAETAS` |
| AN_END | 70 | fl_interleave | 56 | False | `ANEDWNTHEDPWBTHTHEEESAAPETHTHASSTOITISTHEDYOFEYP` |
| PARABLE | 71 | first | 23 | False | `PLTHITUTTHSWMSOOCIFTHEDWAE` |
| PARABLE | 71 | last | 23 | False | `EEERTNGOEEETDRNCSDTHEYNDE` |
| PARABLE | 71 | fl_concat | 46 | False | `PLTHITUTTHSWMSOOCIFTHEDWAEEEERTNGOEEETDRNCSDTHEY` |
| PARABLE | 71 | fl_interleave | 46 | False | `PELETHEIRTTUNGTOTHESEWEMTSDORONCCISFDTHTHEEDYWNA` |

Plaintext first-of-word initials:

- **A_WARNING** p[0]: `AWBNFTHBEWYCTBTTTHCNFYTEPYDDNEORCTHBOTHMCWETHWRO`
- **WELCOME** p[1]: `WWPGTTHGJRTTHEOHOFDFETHWWEATHDLEHLDUWAENAEJEOBDL`
- **WELCOME** p[1, 2]: `WWPGTTHGJRTTHEOATHIINAEATBFTHWFTHWHIIANOALTHWYWF`
- **AN_END** p[70]: `AEWTHDWTHEEAPTHHSTIITHDOEPITSOTHP`
- **PARABLE** p[71]: `PLTHITUTTHSWMSOOCIFTHEDWAE`

Those strings are `AWBNFTBEWY...`, `WWPTTGJTT...`, `AEWTDWTEAP...`,
`PLTITTSWMS...`. None is a title. Last-of-word and first+last are
the same kind of initialism, not `A WARNNG` / `WELCOME` / `AN END`
/ `PARABLE`.

## 2. Verdict

**CALIBRATION FAIL**

None of the four titles can be recovered from their own solved
page under first / last / first+last of words followed by
identity, Atbash, Vigenere DIVINITY, or totient.

Hard stop. The reduction is not applied as an attack on LP2 0-55.
A passing combo does not exist, so there is nothing to carry
forward. IOC-on-reduced-unsolved is not a substitute for a
title that this method cannot reprint.

## 3. Note: unsolved first-letters (inventory only, not an attack)

Allowed on FAIL. Direct Gematria of the reduced streams. No claim
that any of these is plaintext. LP2 0-55 = `parse_pages` 15..69
(55 rune-bearing pages, 3316 words).

Whole-stream reduced IOC (1/29 = 0.03448; English-on-29 ~ 0.06):

| reduction | n | IOC29 | vs 1/29 |
|---|---|---|---|
| first | 3316 | 0.03459 | +0.00011 |
| last | 3316 | 0.03455 | +0.00007 |
| fl_concat | 6632 | 0.03454 | +0.00006 |
| fl_interleave | 6632 | 0.03454 | +0.00006 |

Whole-stream first-of-word (direct, first 80 Latin glyphs):

`SSTHFONNHPEOABESYBGNGIAEYTHHTIAXECEOTHYYEDBMEABXYNGYOEEAFFFMNGAEAOEEAEODOEAEHSTSFMDWASOECIARYOEFFRMAEOEN`

Whole-stream last-of-word (direct, first 80 Latin glyphs):

`FCAEOETHUTHIANTHXPFIAHUPTHIGJYEOAEIAYNGNTHPEANYWFEGBTHAEOJLEAXAENNIASBOEAHGTTCOERSAENGRWNIATTHIAFTIOEAHHYLG`

Per-page first-of-word (direct). High per-page IOC on n~30-70 is a
small-n artifact, not English.

| LP2 | words | IOC first | first-of-word |
|---|---|---|---|
| 0 | 65 | 0.03654 | `SSTHFONNHPEOABESYBGNGIAEYTHHTIAXECEOTHYYEDBMEABXYNGYOEEAFFFMNGAEAOEEAE` |
| 1 | 72 | 0.03247 | `ASOECIARYOEFFRMAEOENAEOENGLAEEABCLNTHUOEPNGGPCTGJIOEOFDDWFIMWNCWEAFJXD` |
| 2 | 45 | 0.0404 | `OEUHBEANDHWUNPNGDFJDETHIANGEEPAEBCFPJEADTHPNRTHTHNGOABCFH` |
| 3 | 50 | 0.02449 | `LEOTSYWPBIAOROENGRDMINWEATHCBJDPEOAEIAEAWUHLNSOCTICHEAFFXXOIH` |
| 4 | 70 | 0.03354 | `LYLPHJMOEUNGLXUGMALMHGFAENWGTHTHSGEAIATHEEEACTHPEOMBOMAEPXRMJECSEORIXE` |
| 5 | 66 | 0.03636 | `RXCICGEDEATHIAEOELXRPPEOYFXICYXTHYPEEOHTHCAUYHOEXUIIEEAIAEMJHFUTDAEBYD` |
| 6 | 48 | 0.03635 | `XXAEEAEIAWIATHYGNGRDUOAMGXGXNGCJOECDAEXMUOLJPDOEDGOYUPMEOAES` |
| 7 | 57 | 0.0401 | `HLSLXEAMMBLEAODTEAIAEACIALAEAEDBXCIEOTHIAJGTENDDLAEOHDWEOTHBEACOEOEIED` |
| 8 | 56 | 0.02792 | `XUIAEAPONGJSOEORYAEEAPOAOEYIAPEAYSGEOOAARMGXNJIFTNHLFGMHETHAEBMOENRSEO` |
| 9 | 66 | 0.02984 | `YNGAPIXIAFTHOSOEOETHUTHOEEOEAJHXFTHCAEBGEALXEAIAEWAENGMOEOEOGPPLGOEEAF` |
| 10 | 73 | 0.03387 | `CXPGENOEDNITHOEEFDENDMWMXJYINSYEOYRIEALCGUTONBMOENXEOSFOGLYAEIXAEEHRCA` |
| 11 | 62 | 0.03067 | `IAWNTHBNGJNGBFLJHMTFHLEOCCAEOFANUNIDXXIANEOAENGAXUAEEOOEIABWTLIASEAXEO` |
| 12 | 72 | 0.02817 | `CREATHIAGUGWJNBXEAYUXRILFPTGXEDTHHMHFAENGLOESWEXOECAGEABNGYGIOUITNLUPI` |
| 13 | 69 | 0.02941 | `GBNOYNGUOMTRXETYEOFIANNEAWIAUNGNGLYWEITYTHOHIAAFTCRJSLTHETHOEPADXEOHBS` |
| 14 | 34 | 0.04278 | `TFNLEAOEEONDTHIAAEOETHSIAEACWOXEAXXXNXHBACHOES` |
| 15 | 42 | 0.02904 | `FALCBIOEUGYOENAUPTOTHIWYFMIANGPHOTHIAUTHLTAYOEIABREAX` |
| 16 | 69 | 0.02941 | `EOMDGATHSTNGNGBTNGIAARIDUHLHPMOGIAXBPOJNXIAJJUCSHXTJLEOACENGCYDXFYLTEO` |
| 17 | 79 | 0.03181 | `LPTHIANCNGLNGRSEONGFEAAETERHEONGMNGSUTPTFJOEBXEACPIAREAEONINGWEOEGJXSP` |
| 18 | 68 | 0.03644 | `EARWEAIEGAXIADYIOEONGTAEEAEAMHXOEIACTFTHFDEAEOOEJYOEBCNGASPDPAOEEAOEEO` |
| 19 | 74 | 0.03628 | `NODRAEOJOERJDXUTHEAFIAEAWAETJNGERCAAEOSOYDRTHNLJRFSLDAEMTNGJNGTHEAINGM` |
| 20 | 71 | 0.03139 | `PJGPPNGHOEAXEAUFOEDHREUCIAJJEANGIAEOGXWLMNGYARLAGDTOSIXCFITIAEOLIMAENG` |
| 21 | 60 | 0.03559 | `CDONMPPHAEIAFTEDPIOETHMFPIAAEPMRXDDUTEAAEELXAADOEIANGEAWPAETNAEOJWNGNG` |
| 22 | 32 | 0.02823 | `NGIJCYTHXCALRBOETHIAEAWIANUTHLOEEOGEWIABEOF` |
| 23 | 52 | 0.03469 | `UWIEOEAPEOWGNGODDAUSYDPLGAEMUFROEYLAREANGNIANIHNGAEOFAEAIAGUDCDGA` |
| 24 | 73 | 0.03158 | `DENEOMWANCGGNEIAPXWTHUXOOLAEUXMFYIASUUIETHPFPOEEAOEFLOFAAEOEEAEEPSRLEH` |
| 25 | 66 | 0.03869 | `HGWSBNYLUNGBTIEACEOUEADUULOLTFMEAEAELSNOBONGBGCPEOEANEULXIGAEMRYBAEEOB` |
| 26 | 69 | 0.03112 | `IAOJNPUNGXEAFBLEANGNSGEAEFEAOTHOETHOOCJPRTHBXDRNTUJCLBMDUAPMYAESCPEOED` |
| 27 | 57 | 0.03195 | `MLLNHBDBAEPAERBNMIAEPFEOEAEEOTUOEEAYANGFWIRYUMOETOEIAAWWYUNGNAEYDEAPSD` |
| 28 | 67 | 0.03754 | `PJDWTERNGTHYEAFIAEIBSCDEOOEHJIAEODDNEOOEAAJIFEAJBSFSOEOWIAFCDAFEAOEAJU` |
| 29 | 79 | 0.03278 | `THUUGJAEBTHILWNLPDSCEOESCLLDFTHCAEIOUHJBWCOIAHIAXAEOERLMTIIACTRODCEOEI` |
| 30 | 67 | 0.03166 | `DMXERYEOGAEGEAXGJNGEEARTHEOUOEOOEROPETHDNGCOOEEAUIABXNGCWAELNGFDSUANGH` |
| 31 | 72 | 0.03521 | `THSOPLHEOLIJTIALPAEBLJEATRBIBTIAJPMFAXTHEOFHRTETAENGIAEXBEEAMWFJHMOEHP` |
| 32 | 26 | 0.03692 | `LTHAEWOEIAFHNGLWTHWAUWSOEMBEAENUFA` |
| 33 | 61 | 0.03115 | `DXEOFIAYOWYDUAEIALTIOSAPEEHNGSJNGIDYMEOXCNNFEOEOOTPENGMDXBEOEPSWNGJLNR` |
| 34 | 71 | 0.03903 | `MNEOHEAAETHDIACUWEOLNCCNNOETEOEAHJNDOEATBJJBFRUDAEOENGNPPBLJEOPGJPBCAJ` |
| 35 | 71 | 0.04225 | `NGEACWHDJMMOOEOILCAEEATHCPJTFIOENGOEPLREARCMDPIJRYTXSMIAOESSJPTHIJOEII` |
| 36 | 58 | 0.03388 | `YUGOLNFXNNTHPPTHYXXFXRIAJDILAMAEOTYOEWIXRDIHEAJOCTHUGIEEOBYINJHROD` |
| 37 | 60 | 0.03051 | `NNNGTAJCENGEALTHCOUPFCWNYFDWRAENGBDJAENGUEOEAEAEHIEAIAOHAIMBGERANGNYEA` |
| 38 | 53 | 0.04209 | `UIASSIAENEUNWMCHTAEEOHHITMHCEGOEIARHNGWGENGCRCNGNGHJLHAEOEYPAEAXAH` |
| 39 | 64 | 0.03621 | `STHNXBUNDAEYEAFIAICGGYOEMMMGGNGWHPWMIAPAMGEOXOEYHDETNGTCNBUWUBWEALFLNM` |
| 40 | 63 | 0.03072 | `FYAEOTEALMDTAETHGIOEWYRMREADNNSTUEOELBICJGLLENOHOYEIOENFPJSTFOEOPGUFCG` |
| 41 | 68 | 0.03819 | `EASBOCRHJADNGXOEBEOEOFAEBEOOEODXHTOTWAEAAOCREAHEOLEEAEMEPWFIAFSEJREOOA` |
| 42 | 68 | 0.02941 | `DXIPFWLUNPLAEJULAEXFMOCEORDBFTHOYAENNTHBIADAIEAEOSEXASJRGJJTAIHIAXEAFT` |
| 43 | 69 | 0.03708 | `HIGCGFXHTEOIAUPGFEOJBEAEAFACBAEAELBEHRAENREAJOETFBOEIAHOBOESAEFOECUNAE` |
| 44 | 65 | 0.02933 | `EAGTHIIAIFFHNGXEOLBJMDAOETHETISJAEFPYCDEBEOEPOEJYAETHEYIABUGTCMRTHTJIA` |
| 45 | 70 | 0.03147 | `CTHNGHTUSMNGOEFDIAJOEHMAEAOEOEAEXJAWITHMAMTEOOLAIAETYMLBYEAOETJPEAALRO` |
| 46 | 71 | 0.0326 | `HDSMDNGEOFNGGLAEIACGWNGBPOEATYEATOOELTHEECDPYXAEIAONGLOETHOAEEAEYIAEEX` |
| 47 | 66 | 0.03963 | `EABFTHPBTHUWBOEIAOETHIAESYNEANGBMLAEBAEUELERAENGOEBIANGWICYNGHEOBEOEAN` |
| 48 | 74 | 0.03406 | `HJNGIALFPNGGFOEIATHAEOEIABEOOIWNTHOPXNGTPMIANGTOSTTHMUOEATHCEADWOEUEAA` |
| 49 | 20 | 0.03684 | `IAEFIIMMBNNGTEADUTHEBAOE` |
| 50 | 23 | 0.03557 | `WFCHBEOMAPATSNGOESLNGYBAMWP` |
| 51 | 70 | 0.03727 | `PFNGYIAWGEAPHTHEAAEBPMTHDSEYPIPUYNGNGUTHFABWEAHNGSOEAOENGBTEAYEOXOFTHN` |
| 52 | 46 | 0.03382 | `EOUXGIADOEMUBEIYJEAOEONEEUJYIGDDWOEOMDTPWNREOEAIAHTHGHUP` |
| 53 | 58 | 0.03569 | `AMIATNGNGIAEMETOFTHCRODOBJXMEOYXOEMOETMNGRYNHGXUOEEAGNYIAMEXNGSCDHBHEA` |
| 54 | 19 | 0.03509 | `NGAESXSFWBEAMBEOEAETHCCDB` |

No title needle (`AWARNNG`, `WELCOME`, `ANEND`, `PARABLE`) is claimed
here. Scanning the raw first-letter stream for those strings would be
an attack, and calibration already forbids treating a hit as a solve.

## 4. Why this family is closed

1. The four titles are properties of the **full** rune stream under
   four different maps (Atbash, Vigenere DIVINITY, totient, identity).
   They are not properties of the word-edge subsequence.
2. Taking first/last of each word is a many-to-one deletion. `WARNNG`
   (5 runes) becomes `W` or `NG`. You cannot get the title back.
3. First+last concat / interleave doubles the initials and still
   drops the middle. `W A R N NG` -> `W`+`NG`, not `WARNNG`.
4. Vigenere and totient are position-keyed. After deletion the key
   no longer lines up with the cells it was built for, so the
   WELCOME / AN END rules cannot reprint their titles either.
5. Prior page-local first-of-word on raw LP2-0 (`SSTHFONNHPEOABESYBGNGIAE...`)
   was already logged as fail in `cicada-3301-uncracked.md`. This pass
   asked the only question that pass did not: whether the known-good
   *substitution* after the reduction reprints a title. It does not.

## 5. What was not done

- No attack on LP2 0-55 with this reduction.
- No new cipher, no key guess, no book index, no running key,
  no periodic Vigenere, no columnar, no SHA-512, no pad, no JPEG.
- No public post.
- Line-acrostic (first of each `/` line) was not in scope.

VERDICT: CALIBRATION FAIL
