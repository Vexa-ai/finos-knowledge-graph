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
