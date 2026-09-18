Publication note: live hidden-service / magnet / IPFS / I2P locator encodings were stripped. The published 512-bit AN END hash hex is kept because it is already on the solved page. This is not a retrieve and not a solve.

# AN END 128-hex - Tor2web / CDX pass 1

Date: 2026-08-15 10:42 AM ET
Worker: executor subagent
Mode: falsifiable exact-string lookup only. Honest. No fake solve. No public post.

## Rails kept

- Hex taken from the published solved AN END page (also quoted in notes/uncracked-inventory.md). The locator-encoding list is not in this repo. Not invented.
- Did not brute a hash. Did not grind SHA-512 preimages.
- Did not reconstruct, guess, or visit `.onion` addresses (live or via a live proxy).
- Did not claim a Liber page solve.
- Did not recook burned cipher families.
- Did not use the hex as an outguess password.
- Forum / wiki / pastebin / reddit / GitHub / solver-guide quotes of AN END do **not** count as a hit.

## Hex (desk)

```
36367763ab73783c7af284446c59466b4cd653239a311cb7116d4618dee09a8425893dc7500b464fdaf1672d7bef5e891c6e2274568926a49fb4f45132c2a8b4
```

128 lowercase hex. Published on solved LP2 page 56 (AN END) as the locator the pilgrim is told to seek. This pass asks only whether that string appears as **page body text** in a 2014-2021 Tor2web-class archive capture.

## PASS / FAIL bar

- **PASS** = an HTML or WARC capture whose body contains that hex (a tor2web snapshot of a page that published the locator as content).
- **FAIL** = this public proxy-archive class is closed for that body hit (no body hit; CDX 403/empty; or only forum/wiki quotes).

---

## 1. Queries run

### 1.1 Wayback CDX API (`web.archive.org/cdx/search/cdx`)

Window: `from=2014&to=2021` unless noted. Default CDX page size is 15,000 rows; `showNumPages` is a size probe, not a fetch of every capture.

| Query | HTTP | Result |
|---|---|---|
| `url=onion.to&matchType=host` limit 8 | **200** | 8 apex rows. First 200 HTML: `http://onion.to/` ts `20141218041603`. Earlier 2014 rows are 302 / warc-revisit. |
| `url=onion.link&matchType=host` limit 8 | **200** | 8 apex rows from 2015-09 (`www.onion.link` 200 text/html). |
| `url=onion.city&matchType=host` limit 8 | **200** | 8 apex rows from 2015-02 (`onion.city` / `www.onion.city` 200 text/html). |
| `url=onion.cab&matchType=host` limit 8 | **200** (after 429) | 8 apex rows from 2014-05 (`https://onion.cab/` ts `20140521214256` 200 text/html). Later 2014-15 mostly 301. |
| `url=onion.nu&matchType=host` limit 8 | **200** | 8 apex rows 2014-01-2015-08 (mix 302/200/301). 200 HTML e.g. `20150801185927`. |
| `url=tor2web.org&matchType=host` limit 8 | **429** (retried twice) | Rate-limited. Domain page-count and Common Crawl still show the apex exists. |
| `url=*.onion.to/*` limit 5 | **200** | 5 rows, all **apex** `onion.to` / `www.onion.to` (2014-01-03). Not a subdomain listing. |
| `url=*.tor2web.org/*` limit 5 | **429** | Rate-limited. |
| `url=onion.to&matchType=domain&showNumPages=true` | **200** | **42** pages |
| `url=tor2web.org&matchType=domain&showNumPages=true` | **200** | **3** pages |
| `url=onion.link&matchType=domain&showNumPages=true` | **200** | **177** pages |
| `url=onion.city&matchType=domain&showNumPages=true` | **200** | **30** pages |
| `url=onion.cab&matchType=domain&showNumPages=true` | **200** (after 429) | **3** pages |
| `url=onion.nu&matchType=domain&showNumPages=true` | **200** | **9** pages |
| `url=*36367763ab73783c*&output=json&limit=20` (any host, any year) | **200** (after 429/503) | **`[]` empty** |
| `url=*36367763ab73783c7af284446c59466b4cd653239a311cb7116d4618dee09a8425893dc7500b464fdaf1672d7bef5e891c6e2274568926a49fb4f45132c2a8b4*` | **503** then abandoned | Service unavailable; prefix search already empty. |
| `url=onion.to&matchType=domain&filter=original:.*36367763ab73783c.*` | **200** | **`[]` empty** |
| `url=onion.cab&matchType=domain&filter=original:.*36367763ab73783c.*` | **200** | **`[]` empty** |
| same filter on onion.link / onion.city / onion.nu / tor2web.org | **429** | Rate-limited. Covered by the global `*36367763ab73783c*` URL search (`[]`). |

CDX status for the **proxy class**: **open, not 403, not empty.** Domain page counts imply on the order of 10^5-10^6 captures across the six hosts (177 pages on onion.link alone). That is **not** a small list. Per rails, captures were **not** spidered.

CDX status for **hex-in-URL**: **empty.** No archived URL in the index contains the 16-hex prefix, on these hosts or anywhere the wildcard URL search reached.

Early burst also produced many **429 Too Many Requests** (prior hung wildcard job). Later spaced retries recovered the host rows and the empty hex-URL answers above. No query returned **403**.

### 1.2 Archived HTML fetched (Wayback `id_` raw, apex only)

Small set. Apex proxy homepages, not live onions, not a subdomain spider.

| Capture | Body contains hex? |
|---|---|
| `https://web.archive.org/web/20141218041603id_/http://onion.to/` | **No.** "Temporarily not available" / hosting-donate notice. |
| `https://web.archive.org/web/20150904204607id_/http://www.onion.link/` | **No.** OnionCity search chrome. |
| `https://web.archive.org/web/20150206202453id_/http://onion.city/` | **No.** OnionCity search chrome. |
| `https://web.archive.org/web/20140521214256id_/https://onion.cab/` | **No.** "To the TOR thou go! Tor2Web-Proxy" feature list. |
| `https://web.archive.org/web/20150801185927id_/http://onion.nu/` | **No.** Gateway page. Lists already-public directory onions as examples. Those live onions were **not** opened. |
| `https://web.archive.org/web/20151125233958id_/https://www.tor2web.org/` | **No.** Project homepage (`.onion.to` / `.onion.city` / `.onion.cab` instructions). Example host is the well-known [well-known public tor2web demo hostname redacted] demo, not a reconstructed locator. |

### 1.3 archive.org item / full-text search

| Query | Result |
|---|---|
| `advancedsearch.php?q=36367763ab73783c` | `numFound`: **0** |
| `advancedsearch.php?q=text:"36367763ab73783c7af284446c59466b4cd653239a311cb7116d4618dee09a8425893dc7500b464fdaf1672d7bef5e891c6e2274568926a49fb4f45132c2a8b4"` (quoted full 128-hex) | `numFound`: **0** |

No IA item, description, or indexed text field holds this hex.

### 1.4 Common Crawl index (`index.commoncrawl.org`)

`collinfo.json` **reachable** (indexes through CC-MAIN-2026-30). In-era probes:

| Query | HTTP | Result |
|---|---|---|
| `CC-MAIN-{2014-52,2015-48,2016-50,2018-51,2020-50,2021-49}-index?url=*36367763ab73783c*` | **504** | Gateway timeout. Leading-wildcard URL search not usable on those indexes from this box. |
| `CC-MAIN-2017-51` and `2019-51` hex wildcard | TLS error | Not a hit, not an empty confirmation. |
| `CC-MAIN-2015-48?url=*.tor2web.org/*` limit 5 | **200** | 3 rows, all apex `tor2web.org` / `www.tor2web.org`. No hex in URL. |
| `CC-MAIN-2016-50?url=*.onion.nu/*` limit 5 | **200** | Apex + robots + two already-crawled subdomains (two already-crawled public-directory hostnames redacted; not reconstructed from the AN END hash). **Hex not in any URL.** Those two archive rows were not opened live. |
| `CC-MAIN-2015-48?url=*.onion.cab/*` | **404** | `No Captures found for: onion.cab/*` |
| `*.onion.to/*`, `*.onion.link/*`, `*.onion.city/*` on sampled 2015/2016 indexes | **504** | Timeout. |

No Common Crawl URL row containing the hex was obtained. Body text is not searchable through this CDX-style index.

### 1.5 Web / exact-string search (quoted hex)

| Query | What came back | Counts as PASS? |
|---|---|---|
| quoted full 128-hex | cicadasolvers.com/deep-web-hash/; GitHub lipeeeee/gematria; Medium 3301 recap; Boxentriq Liber Primus guide; Tor StackExchange 3870 | **No** (guide / forum / wiki-class quotes of AN END) |
| prefix + onion.to / tor2web / onion.link / onion.city / onion.cab / onion.nu | proxy-project pages, not a capture whose body is the hex | **No** |
| `site:web.archive.org` + prefix + named proxies | archived articles *about* onion.city / tor2web (Sophos, seclists, aaronsw). Hex not in those bodies as a published locator page | **No** |
| `site:onion.to OR site:onion.link OR ...` + prefix | live proxy / parking / unrelated apex. No hex page | **No** |
| `site:archive.org` + full hex | unrelated hash-manifest items; not this string | **No** |
| prefix on uncoverycicada / pastebin / reddit | Uncovering Cicada wiki (AN END transcription); pastebin `ntzif5Qz` (same quote) | **No** (explicitly excluded) |

Also seen, still not a hit: krisyotam/cicada3301 (Liber dump notes); monokro.me essay (quotes the hex; claims a v2 reading - **not followed, not visited, not used as a query**).

---

## 2. Body hit

**None.**

No HTML or WARC capture in this proxy-archive class was shown to contain the 128-hex as page body text. No CDX URL contains the hex prefix. Apex captures that were opened do not contain it. Public full-text indexes (web search, archive.org) only surface AN END quotes on clearnet solver pages.

---

## 3. What this does **not** say

- It does not say the deep-web page never existed.
- It does not say Wayback has zero Tor2web captures (it has many).
- It does not retrieve or name a hidden service from the hex.
- It is not a Liber Primus page solve.
- Domain-scale CDX was not exhaustively downloaded and grepped. The class is too large. The claim is: **public exact-string indexes and URL filters did not produce a body hit.**

---

## 4. Verdict

**FAIL**

This public Tor2web proxy-archive class is closed for the published AN END 128-hex as page body text. CDX for the class is open (200 + page counts, not 403/empty). CDX for hex-in-URL is empty. archive.org text search is empty. Common Crawl did not yield a hex URL. Web search only finds excluded forum/wiki/guide quotes. No PASS capture (URL + timestamp).

Do not recook this lookup unless a new archive index appears that can search capture bodies, or a named capture is handed over.
