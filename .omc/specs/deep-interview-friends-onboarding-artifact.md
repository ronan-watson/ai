# Deep Interview Spec: AI Onboarding Artifact for Mark, Claire, and Marc

## Metadata
- Interview ID: di-friends-onboarding-001
- Rounds: 7 (+ Round 0 topology + Round 4.5 mid-topology adjustment)
- Final Ambiguity Score: 15.5%
- Type: greenfield
- Generated: 2026-05-20
- Threshold: 0.20
- Threshold Source: default
- Initial Context Summarized: no
- Status: PASSED — pending approval

## Clarity Breakdown
| Dimension | Score | Weight | Weighted |
|-----------|-------|--------|----------|
| Goal Clarity | 0.95 | 0.40 | 0.38 |
| Constraint Clarity | 0.90 | 0.30 | 0.27 |
| Success Criteria | 0.65 | 0.30 | 0.195 |
| **Total Clarity** | | | **0.845** |
| **Ambiguity** | | | **0.155** |

## Topology

| Component | Status | Description | Coverage / Deferral Note |
|-----------|--------|-------------|--------------------------|
| Friends-Onboarding Artifact (C2) | active | A small hosted website authored from this repo to help three specific friends understand how to use AI tools well | Goal, Constraints, Acceptance Criteria covered below |
| AI Knowledge Repository (C1) | deferred | Long-lived personal knowledge base about AI | User-confirmed deferral 2026-05-20: will emerge organically from C2; revisit once the friends artifact is shipped and follow-up questions arrive |

## Goal

Build a small static website (hosted from this repo) of a landing page plus 4–6 short notes that helps three specific Dublin-based professionals — Mark Watters (mechanical engineer at Schindler), Claire O'Byrne (data manager at the Pensions Authority, ACA + MSc Data Analytics), and Marc Freyne (Head of Underwriting & Portfolio Management at Vhi, Fellow Actuary + MSc Data Analytics) — start using AI tools well in their work.

The artifact is **evocative, not exhaustive**: total read time roughly 30 minutes, designed to elevate the readers' thinking enough that they come back with sharper follow-up questions. The content slice is "practical AI tool use" — drawing on the user's day-to-day experience as a Squarespace engineer deeply embedded in agentic tooling — translated for numerate, non-software-engineering professionals.

Source lives as plain markdown so this repo can grow into a longer-lived AI knowledge base later (deferred C1).

## Constraints

- Audience is three named people, not a general-public artifact. Tone is personal; address them by name where natural.
- Audience is technically literate but **not software-engineering literate**. No assumed familiarity with CLIs, APIs, GitHub workflows, MCP, Claude Code, or agent-building.
- Audience **is** numerate. Marc handles precise statistical language; Claire is data-fluent; Mark is engineering-precise. Don't dumb it down.
- Examples must map to domains the readers actually live in: mechanical / applications engineering (Mark), pensions / regulatory data (Claire), actuarial pricing / underwriting (Marc).
- Total read time ≤ 30 minutes across all pages.
- 4–6 short notes plus a landing page (so 5–7 markdown pages total).
- Hosted as a static website (GitHub Pages or equivalent) so the friends receive a single URL — they will not clone a repo.
- Push-driven curriculum (the user initiates), not pull-driven Q&A.

## Non-Goals

- NOT a comprehensive AI guide. Coverage is intentionally partial.
- NOT a tutorial on building AI products, agents, MCP servers, or Claude Code workflows.
- NOT a theory deep-dive on transformers, neural networks, or ML math.
- NOT a general-public artifact. Voice, examples, and depth are calibrated to three specific readers.
- NOT a one-and-done artifact. It is designed to provoke follow-up conversations, not foreclose them.
- Out of scope for now: the broader long-term knowledge repo structure beyond what this artifact seeds.

## Acceptance Criteria

- [ ] Static website builds and is hostable from this repo (single URL deliverable)
- [ ] Landing page exists with a short intent statement and links to all notes
- [ ] 4–6 short notes covering, at minimum:
  - [ ] **Mental model** — what an LLM actually is, in plain terms (no math; analogy-led)
  - [ ] **Practical patterns** — prompting and usage patterns that pay off for knowledge work
  - [ ] **Limits** — what AI is bad at, where to verify, where calibrated skepticism applies
  - [ ] **Worked examples** mapped to the friends' domains: one engineering-flavored (Mark), one data/summarization-flavored (Claire), one analytical/quantitative-flavored (Marc)
  - [ ] **Tools you actually use and why** — short, opinionated, current
- [ ] Total read time ≤ 30 minutes (verified by word-count / reading-time estimate per page)
- [ ] No CLI / code / MCP / Claude-Code / agent-building jargon required for comprehension
- [ ] Voice is personal — written as the user sharing his experience, not neutral documentation
- [ ] Each note includes at least one concrete example from the user's own AI use
- [ ] At least three examples are domain-mapped (one each for Mark / Claire / Marc's worlds)
- [ ] Site is deployable to GitHub Pages (or equivalent) and the source markdown is portable for future migration into a broader knowledge repo

## Assumptions Exposed & Resolved

| Assumption | Challenge | Resolution |
|------------|-----------|------------|
| "Contain my knowledge about AI" was the goal | Rounds 1–3 separated audience, trigger, and content slice as distinct concerns | Goal narrowed to: practical AI tool use, taught to specific friends |
| Audience was generic | "Who specifically?" | Three named professionals; profiles read |
| The friends had similar backgrounds | LinkedIn profiles surfaced | Different domains → examples must span engineering / data / actuarial |
| A GitHub repo of markdown was the right delivery | Round 4.5 challenged "they will never click into a repo" | Hosted static site (repo as source, web as consumption surface) |
| The artifact should be comprehensive | Simplifier mode (round 6) challenged this | Small, evocative, conversation-starter: 4–6 short notes |
| C1 (knowledge repo structure) had to be designed up-front | Topology adjustment round 4.5 | Deferred — emerges from C2 |
| Success = adoption | Round 5 reframed | Success = engagement elevation (sharper follow-up questions) |

## Technical Context (greenfield)

- Empty repo: only `.git` and `.omc/` present at interview time.
- User language preferences (from `~/dev/CLAUDE.md`): Go, Python, Java/Kotlin; minimal comments; self-documenting code. Not directly load-bearing for a static content site, but informs any tooling/build scripts.
- Static-site stack is **deferred to the planning phase**. Candidates: plain markdown + GitHub Pages, Astro, mkdocs-material, Hugo, Jekyll. Constraint: source must remain readable as plain markdown for future migration into the broader knowledge repo.

## Ontology (Key Entities)

| Entity | Type | Fields | Relationships |
|--------|------|--------|---------------|
| Friend | core domain | name, role, employer, domain, AI exposure | reads → Note; sends → Follow-Up Question |
| Mark Watters | instance of Friend | mech-eng, Schindler, AutoCAD/Revit, 20+ yrs project/applications eng. | needs engineering-flavored examples |
| Claire O'Byrne | instance of Friend | data manager, Pensions Authority, ACA + MSc Data Analytics | needs data / summarization examples |
| Marc Freyne | instance of Friend | Head of Underwriting, Vhi, Fellow Actuary + MSc Data Analytics | needs analytical / quantitative examples |
| Site | core domain | hosted URL, source repo path, build pipeline | comprises → Landing Page + Notes |
| Landing Page | core domain | intent statement, links | part of → Site |
| Note | core domain | title, topic, body, est-reading-time, examples[] | belongs to → Site; contains → Example |
| Example | supporting | domain (eng/data/actuarial), source-of-experience | belongs to → Note |
| AI Tool | supporting | name, what the author uses it for | referenced by → Note |
| Follow-Up Question | success signal | content, who-asked, when-asked | sent by → Friend (post-read) |

## Ontology Convergence

| Round | Entity Count | New | Changed | Stable | Stability Ratio |
|-------|-------------|-----|---------|--------|----------------|
| 1 | 3 | 3 | – | – | N/A |
| 2 | 4 | 1 | 0 | 3 | 75% |
| 3 | 5 | 1 | 0 | 4 | 80% |
| 4 | 7 | 2 | 0 | 5 | 71% (Mark/Claire/Marc resolved as concrete instances) |
| 5 | 8 | 1 | 0 | 7 | 88% |
| 6 | 9 | 1 | 0 | 8 | 89% |
| 7 | 10 | 1 | 0 | 9 | 90% |

## Interview Transcript

<details>
<summary>Full Q&A (Round 0 + 7 rounds + 1 mid-topology adjustment)</summary>

### Round 0 — Topology
**Q:** 2-component topology (Knowledge Repo + Friends Artifact) — confirm?
**A:** Looks right — 2 components

### Round 1 — Audience
**Q:** Who are these friends and where are they starting from with AI?
**A:** A specific named friend or two
**Ambiguity:** 87.5%

### Round 2 — Trigger
**Q:** Did they ask you, or are you initiating?
**A:** I'm initiating — they're curious but vague
**Ambiguity:** 79.5%

### Round 3 — Core slice
**Q:** If they walked away understanding one thing, what would it be?
**A:** How to actually use AI tools well
**Ambiguity:** 65%

### Round 4 — Friend characterization
**Q:** Quick characterization of Mark, Claire, and Marc?
**A:** LinkedIn profile PDFs provided. Read: Mark (mech-eng, Schindler), Claire (data manager, Pensions Authority, ACA + MSc DA), Marc (Head of Underwriting, Vhi, Fellow Actuary).
**Ambiguity:** 48.5% C2-only / 85.5% cross-component

### Round 4.5 — Topology adjustment + delivery surface
**Q1:** Defer C1 (knowledge repo) and focus entirely on C2?
**A1:** Defer — let it emerge from C2
**Q2:** How will they consume this?
**A2:** Hosted web page they can just open
**Ambiguity:** 45%

### Round 5 — Success criteria
**Q:** What single observable thing would make you say "this worked"?
**A:** They come back to you with sharper questions
**Ambiguity:** 30%

### Round 6 — Simplifier Mode
**Q:** What's the smallest version that would still trigger sharper-question follow-ups?
**A:** Small site, 4–6 short notes, ~30-min read
**Ambiguity:** 20.5%

### Round 7 — Topic seed
**Q:** What should the 4–6 notes most likely cover?
**A:** Mental models + practical patterns + limits + examples
**Ambiguity:** 15.5% ✅

</details>

## Status

`pending approval`
