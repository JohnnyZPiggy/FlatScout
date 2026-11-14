# FlatScout — SAE V3.4 project entrypoint

Goal: an automated, personal-use collector of 2-person apartment listings near EPFL/UNIL for a 2027 move: fetch → normalize → dedupe → filter/score → daily digest.

SAE pin: `4129001fffcb336f5203e4b0d6765d7a0ea3150c`. Configuration: [sae.yaml](sae.yaml). Pinned rules: [.sae/README.md](.sae/README.md).
Read the [pinned constitution](https://github.com/JohnnyZPiggy/SAE-Framework/blob/4129001fffcb336f5203e4b0d6765d7a0ea3150c/AGENTS.md) and your role protocol at that SHA. Never float to `main` or silently bump the pin.

## Simplicity first (Engineer: read before writing code)

The [Simplicity Contract](https://github.com/JohnnyZPiggy/SAE-Framework/blob/4129001fffcb336f5203e4b0d6765d7a0ea3150c/governance/SIMPLICITY_CONTRACT.md) overrides any older rule or habit that asks for more. The smallest change that meets the Issue's Definition of Done is the correct change.

1. **Validate only at trust boundaries** (CLI args, files, provider output), and only the fields you use. Trust internal code: let Python raise.
2. **Catch an exception only if you then do something different.** No catch-and-rename, no custom error-code taxonomies.
3. **No speculative code:** no "future" abstractions, flags, fallbacks, length caps, hand-written schema validators.
4. **Tests:** one per changed behavior, plus one saved-HTML/JSON fixture per source adapter (no live network in tests). Test lines ≲ source lines.
5. **Evidence:** Git SHA is the integrity layer. The handoff is one PR comment, with ≤ 3 evidence files for code and ≤ 10 for a GPU run.
6. **Budget:** every Issue states S ≤ 50 / M ≤ 200 / L ≤ 500 net lines and a *Not required* list. Over 1.5× → stop, ship the Definition of Done, list extras as suggestions.



## Roles
- **Scientist:** sets goals, can stop any work; no routine approvals.
- **Architect / Mentor (default Claude):** research decisions, Issues with budgets, review, merges.
- **Engineer (e.g. Codex):** implements, tests, runs CPU/GPU on existing entitlements, opens PRs; never merges its own work.

## Project rules
**Scope.** Help a married couple find a long-term, officially registrable whole-apartment rental near EPFL/UNIL (Saint-Sulpice, Ecublens, Chavannes, west Lausanne, Renens, Crissier and well-connected neighbours, treated equally). Criteria live in `config/search_criteria.yaml`; it is the single source of truth for budget, size and exclusions.

**Data integrity (non-negotiable).**
1. Never invent listings, prices, areas, contacts or availability. Missing = NULL.
2. Every listing keeps source, original URL, first-seen date, last-verified date and verification status.
3. Stable IDs for dedup; never delete history. Cross-platform look-alikes are flagged for human review, never auto-merged.
4. An unverified or old ad is never "currently available". A page that still opens is not proof of availability.
5. A search run recommends at most 5 genuinely matching new or materially changed listings.
6. Never send email, submit applications or upload personal documents. Drafts only; the Scientist sends.
7. Personal data (contacts, applications, identity documents) stays in git-ignored `data/` and `drafts/`. This repo is public: commit code, config and synthetic fixtures only.

**Engineering.**
- Production dependencies: stdlib first (sqlite3, argparse, csv, json); add httpx/selectolax only in the Issue that first needs the network. No scraping frameworks, no browser automation unless an Issue names a source that needs it.
- Politeness: obey robots.txt and site terms, >= 5 s between requests per host, personal use only; a source that forbids automated access is dropped or replaced by its official alert email/RSS/API.
- Runs on Windows (`py -3`) and Linux.
- Tests: one per changed behavior; fixtures are synthetic and marked so; real `data/` is never touched by tests.
- Workspace: repo checkout only; delete only task-owned scratch.
- Current state: none; T1 = this adoption PR. Work starts only from an Issue or an Architect START comment.
