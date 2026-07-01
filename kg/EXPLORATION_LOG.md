# Knowledge-graph exploration log

This is the **enrichment loop's** plan/log — distinct from
`kg/entities/organization/technical-oversight-committee.md`'s own "Discovery log",
which tracks the separate `finos-discovery` routine's TOC/GitHub-org walk. This file
tracks the broader, human-directed enrichment loop (`/loop` sessions): what class of
gap it's working, what it's found, and what's queued next — so any future run
(scheduled or user-directed) can resume without re-covering the same ground.

Conventions: grounded only in existing graph facts or cited public FINOS sources —
no invention. Every entity in `kg/entities/` gets a `Source:` line. Commit + push
every iteration (see CLAUDE.md / loop instructions).

## Completed passes (chronological)

1. Reciprocal person→company backlinks: AWS, Citi, Red Hat, RBC, JPMC now name
   people already known (via their own entities) to work there.
2. GitProxy maintainer↔project backlinks: added Eddie Knight, Maurizio Pillitu as
   contributors; fixed a plain-text "GitProxy" mention to a wikilink.
3. Person↔SIG reciprocal link: Open Source Readiness Initiative now names
   co-chair Peter Smulovics (was previously one-directional).
4. Thin project-stub enrichment batch 1 (GitHub API: description/homepage/license):
   Vuu, TimeBase-CE, TRAC DAP, Zenith.
5. Thin project-stub enrichment batch 2 + new edge: Morphir, OpenMAMA (flagged
   LGPL-2.1 license exception), a11y Theme Builder, Fin-OCR, Architecture as Code
   (identified as CALM, calm.finos.org; new Matthew Bain↔CALM maintainer edge),
   TraderX.
6. Thin project-stub enrichment batch 3 (license nuances): Financial Objects
   Program, Common Cloud Controls (non-standard spec license), DevOps Automation,
   AI Governance Framework (CC-BY-4.0 license), Fluxnova.
7. Thin project-stub enrichment batch 4 (final): Waltz, InnerSource SIG, Open
   RegTech SIG, kdb+ Working Group; Trevor O'Brien↔InnerSource SIG backlink added.
8. **Structural fix**: consolidated the FDC3/Legend/Common Domain Model
   `project/` vs `organization/` duplicate-entity pairs (identical titles made
   wikilinks ambiguous) into single `organization/` entities — canonical type
   chosen as `organization` since FINOS.md and most existing links already
   pointed there. Merged unique facts (FDC3: Kris West lead maintainer, Brian
   Ingenito; Legend: Rafael Bey-Hernandez top contributor, `-gs` handle note).
   Deleted the `project/` copies; `kg/entities/project/` no longer exists.

State after pass 8: 88 unique entity titles, 0 dangling wikilinks, 0 duplicate
titles. All org/project entities carry license info (Apache-2.0 dominant;
noted exceptions: OpenMAMA LGPL-2.1, AI Governance Framework CC-BY-4.0, Common
Cloud Controls non-standard). Reciprocal person↔company and person↔SIG links
largely complete for the pre-2026-06-30 seed set.

## Pass 9: FINOS member-company expansion (2026-07-01)

No member-list file/paste was found in the repo, scratchpad, or common download
locations, so sourced the authoritative roster directly from the public
`https://www.finos.org/members` page (tiered: Platinum/Gold/Silver/Associate,
~80 companies total). `landscape.finos.org` is JS-rendered and didn't yield data
via fetch — not needed since the members page had everything.

Cross-referenced against the 20 pre-existing `kg/entities/company/*.md` files:
15 matched the roster (AWS, Capital One, Citi, G-Research, GitLab, Goldman Sachs,
JPMC, Moody's, Morgan Stanley, NatWest Group, Point72, Red Hat, Royal Bank of
Canada, Sonatype, UBS) and got a new `member_tier` frontmatter field + a
`Source: https://www.finos.org/members` citation. 5 (Capgemini, Clovyr,
CompliLedger, IRS, Prospective Co.) are NOT on the official member roster —
left untagged rather than invented, since they were captured as
employers/individual contributors, not member orgs.

Scaffolded all missing **Platinum** (5: Bank of America Securities, Fidelity,
Microsoft, Nvidia, TD) and **Gold** (21: Accenture, American Express, Ant Group,
AXA, BlackRock, BrightQuery, Chainguard, Deutsche Bank, Depository Trust &
Clearing Corporation, Google Cloud, interop.io, Japan Securities Clearing
Corporation, Lloyds Banking Group, London Stock Exchange Group, MariaDB, Oracle,
S&P Global, Symphony, Thoughtworks, Tradeweb, Wellington Management) member
companies as minimal grounded stubs (frontmatter + `member_tier` + one-line note
+ Source). Updated `organization/finos.md`'s "Member companies" bullet to name
every Platinum/Gold member and wikilink them, replacing the old 3-name example.

Verified after this pass: 113 unique entity titles, 0 dangling wikilinks, 0
duplicate titles (46 company entities now, up from 20).

**Queued for next passes — Silver tier (~36 companies)**: Adaptive, Artian, BMO,
Bank of New York, Canonical, CloudBees, Commonwealth Bank of Australia, Container
Solutions, ControlPlane, Crafty Penguins, dltHub, elevenai, Elgin White, Epam,
EQTY Lab, FossID, Here, Hedera, HITACHI, JUXT, Kosli, KPMG, Moderne, Octopus
Deploy, Provectus, Regnosys, Scott Logic, State Street, Summit58, Syntasso,
Temporal, tetrate, Tokenovate, Trade Header (AWS, G-Research, GitLab, Point72
already scaffolded).

**Queued — Associate tier (~23 orgs, several are universities/industry
associations rather than companies — note that honestly in body text rather
than mislabeling)**: ACTUS, Alliance for Innovative Regulation, AlmaLinux, Ayodo,
Columbia University, Canadian Regtech Association, Data Foundation, The Digital
Dollar Project, EDM Council, ESOP, FIX Trading Community, InnerSource Commons,
Interledger Foundation, InterWork Alliance, ISDA, ISLA, Mifos, Mojaloop
Foundation, OpenFinity, OpenUK, Regtech Association, Scion Association, Yeshiva
University.

Full roster snapshot (2026-07-01) is in this log for future reference — no need
to re-fetch finos.org/members unless checking for roster changes.

## Pass 10: FINOS Silver-tier member companies (2026-07-01)

Scaffolded all missing Silver-tier companies (34 new: Adaptive, Artian, BMO,
Bank of New York, Canonical, CloudBees, Commonwealth Bank of Australia,
Container Solutions, ControlPlane, Crafty Penguins, dltHub, elevenai, Elgin
White, Epam, EQTY Lab, FossID, Here, Hedera, HITACHI, JUXT, Kosli, KPMG,
Moderne, Octopus Deploy, Provectus, Regnosys, Scott Logic, State Street,
Summit58, Syntasso, Temporal, tetrate, Tokenovate, Trade Header) as minimal
grounded stubs (frontmatter + `member_tier: Silver` + Source). AWS, G-Research,
GitLab, Point72 already existed and are unchanged (already tagged in pass 9).
Updated `organization/finos.md`'s roster bullet to name and wikilink the full
Silver tier, replacing the "dozens more, e.g." placeholder.

Company entity count: 80 (up from 46). Still queued — **Associate tier**
(~23 orgs; see the list above) is the last remaining tier.

## Pass 11: FINOS Associate-tier member companies — roster complete (2026-07-01)

Scaffolded all 23 Associate-tier entries (ACTUS, Alliance for Innovative
Regulation, AlmaLinux, Ayodo, Columbia University, Canadian Regtech Association,
Data Foundation, The Digital Dollar Project, EDM Council, ESOP, FIX Trading
Community, InnerSource Commons, Interledger Foundation, InterWork Alliance,
ISDA, ISLA, Mifos, Mojaloop Foundation, OpenFinity, OpenUK, Regtech Association,
Scion Association, Yeshiva University) as minimal grounded stubs
(`member_tier: Associate` + Source). Several are universities/nonprofits/trade
associations rather than corporations — noted honestly in each body rather than
mislabeled. Along the way, fixed a plain-text "Columbia University" mention in
[[Tim Paine]]'s entity to a proper wikilink (he's an adjunct professor there),
now resolving to the new entity.

Updated `organization/finos.md`'s roster bullet to name and wikilink the
complete Associate tier, finishing the full Platinum→Gold→Silver→Associate
roster expansion started in pass 9.

**This closes out the FINOS member-roster expansion thread**: 103 company
entities (up from 20 at the start), all ~80 official FINOS members scaffolded
with tier + source, plus the 5 pre-existing non-member companies (Capgemini,
Clovyr, CompliLedger, IRS, Prospective Co.) correctly left untagged. Verified
0 dangling wikilinks, 0 duplicate titles after this pass.

Next open thread for a future pass: the graph currently has no other systematic
gap queued. Candidates to scope next: (a) enrich the new company stubs with a
real one-line description of what each org does (most are currently
placeholder "[[FINOS]] X member." with no company description — grounded via
a company-website/GitHub-org lookup pass, similar to the earlier project-stub
GitHub-API enrichment); (b) cross-check whether any TOC/candidate/contributor's
employer is now a scaffolded member company that could gain a reciprocal
person↔company link (e.g. do any newly added Associate/Silver members already
appear as an employer elsewhere in the graph — spot check before assuming);
(c) resume the general wikilink/reciprocal-link sweep pattern from passes 1-7 now
that the graph is much larger.

## Pass 12: deep dive on DTCC (2026-07-01, user-directed)

User asked for a deeper loop specifically on DTCC (Depository Trust & Clearing
Corporation), which pass 9 had only scaffolded as a bare member stub. Researched
via `finos.org` sitemap search + GitHub API/search — found a real, well-documented
FINOS↔DTCC relationship: the annual **Innovate.DTCC AI-Powered Hackathon**
(DTCC-organized, FINOS-partnered):

- **2025 edition** (Feb 3–7): DTCC + FINOS + [[Broadridge]] (new minimal company
  stub — not a FINOS member, but a named hackathon co-partner). Teams used DTCC's
  AI Sandbox + FINOS GitHub; winners got FINOS funding to open-source their work.
  Named DTCC person: Johnna Powell (opening remarks). Winning team "Cyber Third
  Eye" (DTCC/Standard Chartered/Codincity/DevRel Talent, $75K) — did NOT scaffold
  entities for these one-off team members, to stay scoped to DTCC itself rather
  than the whole hackathon ecosystem.
- **2026 edition**: [[Matthew Bain]] (CALM lead maintainer) personally seeded
  FINOS/CALM hackathon participation (architecture-as-code issue #2050) — added
  this as a new, reciprocal edge on [[Matthew Bain]], [[Architecture as Code]],
  and [[Depository Trust & Clearing Corporation]] (three-way cross-link).
- Hackathon winners present at FINOS AI Readiness SIG meetings afterward — noted
  but did NOT create an "AI Readiness SIG" entity (distinct from the existing
  AI Governance Framework and Open Source Readiness Initiative entities) since
  that's outside this pass's DTCC scope. **Queued**: scaffold an AI Readiness SIG
  organization entity in a future pass if it recurs as a hub for more facts.

Verified after this pass: graph integrity clean (see verification command in
CLAUDE.md workflow), no dangling links, no duplicate titles.

## Pass 13: person↔company reciprocal sweep + company-stub descriptions (2026-07-01)

Ran a fresh plain-text-mention sweep now that ~80 new companies exist (pass
9-11) — checked whether any person entity mentions a company by name without a
wikilink. Two genuine hits:
- [[Peter Smulovics]]'s "a decade-plus at Microsoft" was plain text — now
  wikilinked to the (newly-scaffolded) [[Microsoft]] entity, with a reciprocal
  note added on Microsoft's own page.
- [[Jon Freedman]]'s "Symphony Software Foundation" mention is a **false
  positive** — that's FINOS's historical predecessor org, not the [[Symphony]]
  company (Gold member, Symphony Communication Services). Correctly left
  unlinked to avoid conflating two distinct entities; `Symphony Platform
  tooling` already cites Jon Freedman for that history.

Also enriched 13 of the bare Gold/Silver company stubs from pass 9-10 with a
real one-line description (sourced to each company's own homepage, not
invented — these are well-known public companies): Accenture, BlackRock,
Oracle, Google Cloud, KPMG, Deutsche Bank, American Express, Canonical,
MariaDB, CloudBees, Thoughtworks, Tradeweb, AXA.

**Still queued** (~64 more bare company stubs without a description — mostly
Silver/Associate tier, many niche/harder to verify quickly): Ant Group,
BrightQuery, Chainguard, interop.io, Japan Securities Clearing Corporation,
Lloyds Banking Group, London Stock Exchange Group, S&P Global, Wellington
Management, and the full Silver/Associate lists in passes 10-11. Also still
queued: an AI Readiness SIG organization entity (flagged in pass 12).

## Pass 14: more company-stub descriptions (2026-07-01)

Enriched 20 more bare stubs with real one-line descriptions (sourced to each
company's homepage meta description or well-known public facts, not invented):
Nvidia, Fidelity, Bank of America Securities, Lloyds Banking Group, London
Stock Exchange Group (LSEG), S&P Global, Wellington Management, Hedera, Epam,
Chainguard, Temporal, Scott Logic, State Street, Octopus Deploy, Here (HERE
Technologies), HITACHI, dltHub, Bank of New York (BNY Mellon), Ant Group,
Japan Securities Clearing Corporation.

**Remaining bare stubs (~27, mostly smaller/harder-to-verify Silver/Associate
members)**: BrightQuery, interop.io, Adaptive, Artian, BMO,
Commonwealth Bank of Australia, Container Solutions, ControlPlane,
Crafty Penguins, elevenai, Elgin White, EQTY Lab, FossID, JUXT, Kosli, Moderne,
Provectus, Regnosys, Summit58, Syntasso, tetrate, Tokenovate, Trade Header,
ACTUS, Alliance for Innovative Regulation, AlmaLinux, Ayodo, Canadian Regtech
Association, Data Foundation, The Digital Dollar Project, EDM Council, ESOP,
FIX Trading Community, InnerSource Commons, Interledger Foundation, InterWork
Alliance, ISDA, ISLA, Mifos, Mojaloop Foundation, OpenFinity, OpenUK, Regtech
Association, Scion Association — many of these are small/niche vendors or
associations without an easily-fetchable homepage description; a future pass
should fetch what it can and leave the rest as bare member-tier stubs rather
than force a description. Also still queued: AI Readiness SIG organization
entity (flagged in pass 12).

## Pass 15: more company-stub descriptions, careful skip on ambiguous domain (2026-07-01)

Enriched 11 more bare stubs with real one-line descriptions (homepage meta
descriptions, not invented): Adaptive, Commonwealth Bank of Australia, FossID,
interop.io, Moderne, Provectus, tetrate, Tokenovate, Trade Header, Kosli,
AlmaLinux (noted as a nonprofit-stewarded distro, not a corporation).

**Deliberately skipped** Container Solutions, ControlPlane, and Regnosys this
pass — `container-solutions.com`/`control-plane.io`/`regnosys.com` didn't
return usable content, and a plausible-looking `controlplane.com` hit
described an unrelated PaaS product (not the FINOS Silver member, which is a
Kubernetes/cloud-native security consultancy at control-plane.io) — rather
than risk misattributing a different company's description, left these three
as bare stubs. A future pass could retry with a different fetch method.

**Remaining bare stubs (~16)**: BrightQuery, Artian, BMO, Container Solutions,
ControlPlane, Crafty Penguins, elevenai, Elgin White, EQTY Lab, JUXT, Regnosys,
Summit58, Syntasso, and the Associate-tier trade associations/nonprofits
(ACTUS, Alliance for Innovative Regulation, Ayodo, Canadian Regtech
Association, Data Foundation, The Digital Dollar Project, EDM Council, ESOP,
FIX Trading Community, InnerSource Commons, Interledger Foundation, InterWork
Alliance, ISDA, ISLA, Mifos, Mojaloop Foundation, OpenFinity, OpenUK, Regtech
Association, Scion Association) — these are mostly fine to leave as bare
member-tier stubs; diminishing returns on further fetching. Also still queued:
AI Readiness SIG organization entity (flagged in pass 12).

## Pass 16: AI Readiness SIG entity + 3 new people (2026-07-01)

Company-stub descriptions were hitting diminishing returns, so switched to
closing the AI Readiness SIG gap flagged since pass 12 (DTCC deep dive) —
a genuinely different, higher-value class than squeezing more stub text.

Fetched `finos/ai-readiness`'s README, which names three co-chairs with real
company affiliations — none previously in the graph. Created:
- [[AI Readiness SIG]] organization entity (61 stars, CC-BY-4.0,
  finos.org/ai-readiness) — incubated the [[AI Governance Framework]] in its
  first year before that spun out as its own project (added this reciprocal
  note to AI Governance Framework's entity too).
- Three new people, each linked to their (pre-existing) employer company:
  [[Colin Eberhardt]] (CTO, [[Scott Logic]]), [[Ian Micallef]] (ICG Head of
  Developer Engineering, [[Citi]]), [[Madhu Coimbatore]] (Head of Firmwide AI
  Development Platform, [[Morgan Stanley]]).
- Reciprocal employer-side mentions added to Scott Logic, Citi, and Morgan
  Stanley's company entities.
- Updated `organization/finos.md`'s projects list to include AI Readiness SIG
  with its co-chairs, and fixed the stale "this graph doesn't yet have an AI
  Readiness SIG entity" note on `company/dtcc.md` (from pass 12) now that it
  does, wikilinking it properly.

This closes the last open thread from the DTCC deep dive (pass 12). Verified
graph integrity clean after this pass (see verification command below).

## Pass 17: final round of company-stub descriptions (2026-07-01)

Enriched 10 more bare stubs: Artian, Elgin White, EQTY Lab, JUXT, Summit58,
Syntasso, BrightQuery (homepage meta descriptions), plus successfully
resolved the three previously-skipped ambiguous ones via WebFetch (which
extracts real page content rather than relying on raw meta tags, avoiding the
earlier `controlplane.com`-vs-`control-plane.io` domain mix-up): ControlPlane
(Kubernetes/cloud-native security consulting), Container Solutions
(cloud-native engineering consulting), Regnosys (low-code regulatory-reporting
platform). Caught and self-corrected one drafting slip: an initial Regnosys
description speculated an unlinked "likely related to Common Domain Model"
connection with no citation — removed immediately as ungrounded speculation,
consistent with the no-invention rule.

**Remaining bare stubs (~6, likely low-yield)**: ACTUS, Ayodo, Crafty
Penguins, elevenai, ESOP, OpenFinity — smaller/harder-to-find vendors; fine to
leave bare going forward rather than force weak fetches. The company-stub-
description class is now effectively exhausted.
