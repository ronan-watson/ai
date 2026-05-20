# RALPLAN: AI Onboarding Site for Mark, Claire, and Marc

**Status:** `pending approval`
**Source spec:** `.omc/specs/deep-interview-friends-onboarding-artifact.md`
**Mode:** consensus (short) — final after Planner → Architect → Critic loop (1 iteration, both reviewers APPROVE_WITH_IMPROVEMENTS, all accepted improvements applied)

## Requirements Summary

Build a small static website hosted from this repo containing a landing page + 5 short notes for three specific friends (Mark Watters, Claire O'Byrne, Marc Freyne) on practical AI tool use for non-software-engineering knowledge workers. Total read time ≤ 30 minutes. Source must stay as portable plain markdown so the repo can grow into a longer-lived AI knowledge base.

The artifact is intentionally evocative, not exhaustive. Success criterion is engagement elevation (sharper follow-up questions from the readers post-ship), not adoption metrics.

---

## RALPLAN-DR Summary

### Principles

1. **Markdown is the contract.** All content lives as readable plain markdown — vanilla CommonMark + GFM tables/code-fences only in v1. No generator-specific dialect (no `!!! note` admonitions, no `???` details blocks, no MDX). Future migration is a copy operation, not a rewrite.
2. **Tool fit beats novelty.** The static-site stack must be ergonomic for the author (a Go/Python/Kotlin engineer) and produce a clean reading surface for the audience. No invented tools.
3. **One URL is the deliverable.** Mark/Claire/Marc receive a link. They do not clone, build, or install anything.
4. **Audience calibration is not optional.** Each note must pass an explicit jargon-allowlist check and contain at least one example mapped to one of the three friends' domains.
5. **Ship small, learn from real signal.** Engagement elevation is only measurable post-ship; keep the build small enough that real follow-up questions, not internal polish, drive the next iteration.

### Decision Drivers

1. **Authoring ergonomics.** The user must be able to write a note in a single markdown file and see it on the site with minimum friction.
2. **Reading-surface quality.** Site must look polished enough that three senior professionals don't dismiss it on first impression.
3. **Future portability of source.** The repo is a seed for a long-lived knowledge base; the choice cannot lock content into a generator-specific format.

### Viable Options (Static-Site Stack)

| Option | Approach | Pros | Cons |
|--------|----------|------|------|
| **A. mkdocs-material** (chosen) | Python-based SSG with Material theme. Source = plain markdown. CI = GitHub Actions → GitHub Pages via `actions/deploy-pages`. | Material typography is publication-grade. Matches user's Python comfort. ~15-line `mkdocs.yml`. Built-in search, dark mode, mobile responsive. | Python toolchain dependency for local preview. Theme is opinionated. |
| **B. Astro + Starlight** | JS/TS SSG with the Starlight docs theme. | Modern, very fast, excellent typography. | JS/Node toolchain (outside user's stated language preferences). More moving parts than a 5–7-page artifact needs. |
| **C. Plain GH-Pages Jekyll** | Default GH-Pages Jekyll, minimal theme. | Zero local toolchain (GitHub builds it). | Default themes look dated; Material's typography advantage is real for a "small reading site". Customization adds Ruby/Liquid friction. |
| **D. Hugo** | Go-templated SSG. | Fast; matches user's Go comfort. | Less batteries-included for a small reading-focused site; theme selection is less curated than mkdocs-material. |

**Invalidation rationale for explicitly considered-and-rejected alternatives:**

- **Notion / Substack / Google Docs as host:** rejected — fails Principle 1 (markdown-as-contract) and the spec's hard constraint that this repo seeds a long-lived knowledge base.
- **Custom Next.js site:** rejected — over-engineering for 5–7 markdown pages; conflicts with Principle 2.

**Favored option: A (mkdocs-material).** Best fit on all three Decision Drivers. The Jekyll antithesis (zero local toolchain) is real but a small reading site lives or dies on typography, where Material is meaningfully better than default Jekyll themes.

---

## Architecture / Repo Layout

```
ai/
├── .github/
│   └── workflows/
│       └── deploy.yml          # actions/deploy-pages flow on push to main
├── docs/
│   ├── index.md                # Landing page (intent + nav + reading order)
│   ├── mental-model.md         # Note 1
│   ├── practical-patterns.md   # Note 2
│   ├── limits.md               # Note 3
│   ├── examples.md             # Note 4 (Mark/Claire/Marc domain-mapped)
│   ├── tools.md                # Note 5
│   ├── 404.md                  # Personal "wrong path" page
│   └── assets/                 # Optional images / screenshots (if needed)
├── mkdocs.yml                  # Site config + nav + theme
├── requirements.txt            # mkdocs==1.6.*, mkdocs-material==9.5.*
├── .gitignore                  # site/, .venv/, __pycache__/, *.pyc
└── README.md                   # Repo-level intent + preview + deploy steps
```

**`mkdocs.yml` configuration (vanilla):**
- `site_name`, `site_url` (set to the eventual `https://<user>.github.io/ai/`)
- `theme: name: material` with a `palette` for light + dark and a `features:` list (`navigation.instant`, `content.code.copy`)
- `nav:` listing the 6 content pages in reading order
- `not_found: 404.md`
- `markdown_extensions:` **only** `toc` with `permalink: true` — **no admonition, no pymdownx**, to honor Principle 1
- `plugins: - search`
- `extra:` `noindex: true` if/when robots-control is desired (see Privacy below); also a `generator: false` to hide the "Made with Material for MkDocs" footer in favor of a personal note

**Privacy:** the site is for three named friends. Add `<meta name="robots" content="noindex">` via a Material theme override (1-line `overrides/main.html`) so the page isn't indexed by Google. Append a short footer: "Personal correspondence — please don't republish."

---

## Acceptance Criteria (testable)

**Build correctness**
- [ ] `pip install -r requirements.txt` exits 0
- [ ] `mkdocs serve` starts a local server and returns HTTP 200 on `/`, all 6 content pages, and `/404.html`
- [ ] `mkdocs build --strict` exits 0 (fails on broken links, missing nav, unknown extensions)
- [ ] `ls docs/*.md | wc -l` equals 7 (`index`, 5 notes, `404`)

**Content shape**
- [ ] Combined word count across the 6 content pages (excluding `404.md`) is between 4,500 and 7,500 (≈18–30 min at 250 wpm). Verify: `wc -w docs/index.md docs/mental-model.md docs/practical-patterns.md docs/limits.md docs/examples.md docs/tools.md | tail -1`
- [ ] `docs/examples.md` contains three labeled named-domain blocks: one for mechanical/applications engineering, one for data analysis / regulatory data, one for actuarial / pricing. Verify by reviewer reading the file with the three friends in mind.

**Principle 1 (markdown-as-contract) — automated**
- [ ] `grep -rE '^!!!|^\?\?\?|^===\s' docs/` returns no matches
- [ ] `grep -rE '\{%|\{\{' docs/` returns no matches
- [ ] No MDX, no shortcodes, no `pymdownx.*` extensions enabled in `mkdocs.yml`

**Principle 4 (audience calibration) — explicit verification**
- [ ] `docs/_jargon-allowlist.md` exists, listing every AI-domain term that may appear in the notes (e.g. `LLM`, `prompt`, `context window`, `hallucination`, `chat model`, `agent`, `RAG`, `embedding`, `fine-tune`, `token`). Any term not on the allowlist that appears in the notes must be glossed inline on first use.
- [ ] Reviewer (the user) performs a single-pass read on the final draft, listing any out-of-allowlist term they encounter; that list must be empty before merge.
- [ ] Belt-and-braces grep: `grep -i -E '\b(mcp|claude code|sdk|cli|stdin|stdout|repo|commit)\b' docs/` returns either nothing or only matches that are explicitly glossed in the same paragraph.

**Deploy correctness**
- [ ] `.github/workflows/deploy.yml` uses `actions/checkout`, `actions/setup-python`, `actions/configure-pages`, `actions/upload-pages-artifact`, `actions/deploy-pages` (not `mkdocs gh-deploy --force`); has `permissions: pages: write, id-token: write`; deploys from the artifact, not a `gh-pages` branch
- [ ] One-time Pages setup is documented in `README.md`: Settings → Pages → Source = "GitHub Actions"
- [ ] First deploy is validated on a feature branch before merging to `main`: PR workflow builds and uploads artifact, manual preview via `actions/deploy-pages` with `preview: true` if available, OR `mkdocs serve` against the PR branch locally
- [ ] Published URL returns 200 (`curl -I`)
- [ ] Site is mobile-readable (Material default; manual phone check)
- [ ] Footer contains the personal-correspondence note; `<meta name="robots" content="noindex">` is present in served HTML

---

## Implementation Steps

### Phase 1 — Content first

> Rationale: spec success criterion is engagement, not infra. Write real content before scaffolding so the build proves itself against real text on its first invocation.

1. **Draft `docs/index.md`** as plain markdown (no SSG yet): personal intro — who this is for, why, how to read it (5 notes, ~30 min, suggested order, an invitation to come back with questions).
2. **Draft `docs/mental-model.md`** end-to-end as plain markdown: what an LLM actually is, analogy-led, no transformer math, one concrete "what this means in practice" hook.
3. **Read both files in plain GitHub markdown preview** to confirm they read well as raw markdown (Principle 1 sanity check — if it doesn't read well as raw markdown, the extensions weren't the problem).

### Phase 2 — Scaffold the site

4. Create `requirements.txt` with two lines: `mkdocs==1.6.*`, `mkdocs-material==9.5.*`.
5. Create `mkdocs.yml` per the configuration sketch above — vanilla extensions only.
6. Create `.gitignore` with `site/`, `.venv/`, `__pycache__/`, `*.pyc`.
7. Create the remaining placeholder files (`practical-patterns.md`, `limits.md`, `examples.md`, `tools.md`, `404.md`) with H1 titles + a one-line placeholder so `mkdocs build --strict` passes.
8. Add `overrides/main.html` extending the Material base to inject `<meta name="robots" content="noindex">` and a footer note. Wire `theme.custom_dir: overrides` in `mkdocs.yml`.
9. Create `docs/_jargon-allowlist.md` listing approved AI terms.
10. **Local verification:** `pip install -r requirements.txt && mkdocs serve` → all 6 content pages + 404 render; nav works; `<meta robots noindex>` and footer present.

### Phase 3 — CI + Pages

11. Create `.github/workflows/deploy.yml` using the modern `actions/deploy-pages` flow (not `gh-deploy --force`). Trigger on push to `main`; concurrency group `pages` with `cancel-in-progress: false`; `permissions: pages: write, id-token: write, contents: read`.
12. Push the feature branch and let the workflow build + upload the artifact. Confirm the build job is green before merging.
13. Document the one-time GitHub Pages enablement in `README.md`: Settings → Pages → Source = "GitHub Actions" (must be done once by the repo owner; otherwise the deploy step succeeds-but-shows-nothing).

### Phase 4 — Author the remaining notes

14. Write `docs/practical-patterns.md` (prompting patterns that pay off for knowledge work; one paragraph + one short example per pattern).
15. Write `docs/limits.md` (hallucinations, stale knowledge, false confidence, the verification rule of thumb; one concrete example each).
16. Write `docs/examples.md` with three labeled, domain-mapped blocks:
    - **Engineering (Mark):** AI helping draft an applications-engineering spec / summarising a supplier datasheet / explaining back a tricky CAD-adjacent calc.
    - **Data / regulatory (Claire):** AI helping summarise a long regulatory document / draft data-quality rules / translate an ambiguous spec into a SQL query she can validate.
    - **Actuarial (Marc):** AI helping read and translate a dense actuarial paper / sense-check a pricing argument / rewrite a Pricing Committee paper for clarity.
17. Write `docs/tools.md` — three to five tools the author actually uses, what each is good and bad at, simplest first step per friend.
18. **Word-count gate:** `wc -w docs/*.md` → confirm 4,500–7,500 across the six content pages. If over, split or trim.
19. **Jargon pass:** read each note; for every AI term not on `_jargon-allowlist.md`, either gloss it inline on first use or remove it.
20. **Empathy pass:** read `examples.md` once as Mark, once as Claire, once as Marc. Each block must elicit "yes, that's a problem from my world." Rewrite any that don't.

### Phase 5 — Ship

21. Open PR, self-review against acceptance criteria.
22. Merge to `main`; CI builds and `actions/deploy-pages` publishes.
23. `curl -I` the live URL → 200; open on phone; visually verify footer + noindex.
24. Send the URL personally (WhatsApp / email) to Mark, Claire, Marc with a one-sentence "I wrote this for you" framing.

---

## Risks and Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Author over-writes, site balloons past 30-min read | Med | Med | Hard word-count gate (4,500–7,500) in acceptance criteria. If exceeded, split or trim — don't relax the gate. |
| Author under-writes, notes too thin to provoke real follow-ups | Low–Med | High | Every note must include at least one concrete example. `examples.md` must include all three named-domain blocks. Enforced via PR checklist. |
| Examples are generic and don't land for the specific friends | Med | High | Empathy pass (step 20). Reviewer reads `examples.md` as if they were each named friend. |
| GitHub Pages deploy fails on first run (Pages not enabled, permissions wrong) | Med | Low | One-time setup documented in `README.md`. Build is validated on a feature branch before merge (step 12). |
| `pymdownx`/admonition syntax sneaks into a note mid-iteration and locks the markdown | Low | Med | Automated `grep` in acceptance criteria catches it. Extensions are not enabled in `mkdocs.yml`, so syntax would render as literal text — visible at preview. |
| Site is indexed by Google despite the friends-only intent | Low | Med | `<meta name="robots" content="noindex">` via `overrides/main.html`; footer makes the personal-correspondence framing explicit. |
| Author wants to edit a note after the URL has been sent — friends see a moving target | Low | Low | Append a small "last updated YYYY-MM-DD" footer per page (rendered from `git log` via mkdocs-material's `git-revision-date-localized` plugin — optional; if added, allowed under Principle 1 since dates are HTML render, not markdown source). Out of scope for v1 unless the author wants it. |
| Friends never click the link | Med | Med (out of build scope; tracked here as user post-ship handoff) | **Post-ship TODO for the user (not the build):** send the URL personally with a one-sentence framing. See "Post-ship handoff". |
| Repo later grows into the broader knowledge base and `docs/`-flat layout doesn't scale | Low | Low | Plain markdown files; future restructure is `mv` operations, not rewrites. |

---

## Verification Steps

### Build correctness (mechanical)
```
pip install -r requirements.txt
mkdocs build --strict                          # exit 0
mkdocs serve                                   # all pages render locally
ls docs/*.md | wc -l                           # = 7 (index + 5 notes + 404)
wc -w docs/index.md docs/mental-model.md \
      docs/practical-patterns.md docs/limits.md \
      docs/examples.md docs/tools.md | tail -1 # 4500–7500
```

### Principle 1 (markdown portability)
```
grep -rE '^!!!|^\?\?\?|^===\s' docs/                  # empty
grep -rE '\{%|\{\{' docs/                              # empty
grep -E 'pymdownx' mkdocs.yml                          # empty
```

### Principle 4 (audience calibration — manual + automated)
```
grep -i -E '\b(mcp|claude code|sdk|cli|stdin|stdout|repo|commit)\b' docs/ | \
  grep -v _jargon-allowlist                            # empty OR only glossed matches
```
Plus manual single-pass read: list every out-of-allowlist term encountered; that list must be empty before merge.

### Deploy correctness
```
grep -E 'actions/(configure|upload-pages-artifact|deploy-pages)' .github/workflows/deploy.yml  # all three present
grep 'gh-deploy' .github/workflows/deploy.yml                                                  # empty
curl -I "$LIVE_URL"                                                                           # HTTP/2 200
curl -s "$LIVE_URL" | grep -E 'robots.*noindex'                                                # present
```

### Empathy pass (post-content, pre-ship)
- Read `examples.md` end-to-end as if you were Mark. Note any block that wouldn't make him say "yes, that's a problem from my world." Rewrite.
- Repeat as Claire.
- Repeat as Marc.

---

## Post-ship Handoff (user, not build)

Not part of the deliverable, but the spec's success criterion can only fire post-ship:
- Send the URL personally to each of Mark, Claire, Marc. One-sentence framing: "I wrote this for you — would love to hear what questions it raises."
- Track follow-ups for 4 weeks. The signal is qualitative shift: from "what is AI?" to "how would I get Claude to handle X case from my work?"
- Use the actual follow-up questions to seed the next iteration (and to begin the deferred C1 — the broader AI knowledge repo).

---

## ADR — Static-Site Stack

**Decision:** Use **mkdocs-material** (Option A), deployed to GitHub Pages via the modern `actions/deploy-pages` flow (not `gh-deploy`).

**Drivers:**
1. Authoring ergonomics (Python toolchain matches user's language comfort; markdown source stays plain).
2. Reading-surface quality (Material's typography is publication-grade; first-impression risk is real for three senior professional readers).
3. Future portability of source (vanilla CommonMark + GFM only; no generator-specific extensions enabled).

**Alternatives considered:**
- **Astro + Starlight (B):** higher ceiling, but adds Node toolchain and more moving parts than 5–7 pages need. Outside user's stated language preferences.
- **Plain GH-Pages Jekyll (C):** zero local toolchain (real upside), but default theme typography is meaningfully weaker than Material for a small reading-focused artifact.
- **Hugo (D):** matches user's Go comfort, but theme curation for "small reading site" is less batteries-included.
- **Notion / Substack / Google Docs:** not source-portable; fails Principle 1.
- **Custom Next.js:** over-engineered for the page count; fails Principle 2.

**Why chosen:** best fit across all three Decision Drivers with the lowest moving-parts cost. The repo grows into the broader knowledge base without ever leaving plain markdown.

**Consequences:**
- Python toolchain dependency for local preview (`pip install`, `mkdocs serve`). Acceptable.
- Theme is opinionated; deep visual customization deferred.
- Markdown extensions deliberately restricted to vanilla CommonMark + GFM to honor Principle 1, even at the cost of nicer-looking admonitions in v1.

**Follow-ups (deliberately deferred):**
- Custom domain on GH Pages.
- Analytics (may conflict with the personal-not-public tone — defer until post-ship signal exists).
- "Last updated" timestamps per page (`git-revision-date-localized`) — optional addition.
- A second tier of "deeper notes" once real follow-up questions arrive (this is the C1 → broader-knowledge-base evolution the spec deferred).

---

## Changelog (consensus iteration applied)

Both Architect and Critic returned APPROVE_WITH_IMPROVEMENTS. The following improvements were merged into this plan:

**Accepted from Architect:**
- Drop `pymdownx.details` and `pymdownx.superfences` extensions; restrict to vanilla CommonMark + GFM (Principle 1 hardening).
- Add automated `grep` acceptance criterion enforcing Principle 1.
- Replace `mkdocs gh-deploy --force` with the modern `actions/deploy-pages` + `upload-pages-artifact` flow; remove the `gh-pages` branch dependency.
- Add `site_url:` to `mkdocs.yml`.
- Add `.gitignore` covering `site/`, `.venv/`, `__pycache__/`, `*.pyc`.
- Replace `pyproject.toml` with `requirements.txt`.
- Add `docs/404.md` and `not_found:` config.
- Reorder Phase 1 to content-first (write `index.md` + `mental-model.md` as plain markdown before scaffolding).
- Document the one-time GitHub Pages enablement step explicitly in `README.md`.

**Accepted from Critic (additional):**
- Drop `admonition` extension too (go fully vanilla in v1).
- Tighten word-count gate from 4,500–8,500 to **4,500–7,500** (≤30 min at 250 wpm; matches spec ceiling).
- Replace soft "no jargon" verification with an explicit `_jargon-allowlist.md` artifact + reviewer single-pass + belt-and-braces grep.
- Add image/asset policy (`docs/assets/`).
- Add Privacy section: `<meta robots noindex>` + personal-correspondence footer for the three named friends.
- Move "friends never click" risk from build-scope risk table into a dedicated **Post-ship Handoff** section (not part of the deliverable).
- Make feature-branch CI verification an explicit step (Phase 3 step 12), not a risk-table aside.
- Add Hugo as an explicit fourth row in Viable Options to remove ADR inconsistency.

**Rejected (with rationale):**
- Per-page reading-time check (Architect #3d). Aggregate `wc -w` is sufficient for 5 notes; per-page is over-engineering. Critic agreed.

**Deferred (out of v1 scope, but listed under Follow-ups):**
- `git-revision-date-localized` plugin for per-page "last updated" timestamps.
- Analytics; custom domain; second-tier "deeper notes" layer.

---

## Status

`pending approval`
