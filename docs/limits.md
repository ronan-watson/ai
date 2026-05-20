# Where AI is weak, and how to stay calibrated

_The things you can't trust, and the cheap habits that keep you safe._

Everything in the last two pages tells you how to use AI well. This page is the other side of the ledger. None of these are deal-breakers. All of them are things that have personally bitten me or someone I work with. If you finish this page slightly more sceptical, that's the goal.

## 1. It will be confidently wrong

This is the big one. The model produces fluent, well-structured, polite, plausible text *whether or not* the content is correct. There's no facial expression. No hesitation. No *"hmm, I'm not sure about this bit"*. Wrong answers come out in exactly the same voice as right ones.

A few flavours I see most often:

- **Made-up references.** Ask for a citation and it will invent one. The journal name will sound right. The authors will sound real. The year and volume number will look plausible. The paper does not exist.
- **Made-up function names, regulation clauses, statutes, internal team names.** Anything that follows a *shape* it has seen, it can generate. The specifics will be wrong.
- **Wrong-but-close numbers.** Especially when you ask for percentages, ratios, or summary statistics on top of something it's read. It pattern-matches to *plausible* values.

**How to spot it.** When something matters, verify the *load-bearing facts*, not the prose. The grammar is never wrong. The structure is rarely wrong. The specifics — names, numbers, dates, clauses, regulations — are where the cracks are.

**What to do instead.** Ask it to tell you when it's not sure. *"For each claim, mark it confident or unsure, and tell me what I'd need to check."* It's surprisingly good at this when you ask. The reason it doesn't volunteer it is that you never asked.

## 2. Be careful about maths

This one matters most for John Cusack and Ceebs.

The model on its own is not a calculator. If you ask it to compute in its head, it's predicting what the next number probably looks like based on patterns in its training data. For simple arithmetic on small numbers it usually gets there because the pattern is overwhelmingly consistent. For multiple steps, large numbers, or anything that doesn't pattern-match cleanly, it will produce a confident, well-formatted, *wrong* answer. A few years ago I watched it compute a compound interest figure to four decimal places, with the formula written out beautifully above it, and the final number was 8% off the right answer. The formula was right. The substitution was right. The arithmetic was wrong. You wouldn't catch it without redoing the sum.

That was 2024. The picture in 2026 is different but only partly. All four of the main chat tools now route many numeric requests through an actual calculator or a code interpreter — meaning the model writes a small program and a real machine runs it. When that happens, the arithmetic is fine. The catch is that they don't always do it, and they don't always tell you whether they did.

**Three things to check** when a number matters:

- **Does my tool actually have a calculator or code mode, and is it on for this conversation?** ChatGPT, Claude, Gemini and Copilot all do, in their paid tiers. Some require you to turn it on or pick a "with code execution" / "thinking" mode.
- **Did it use it for this specific answer?** Look for evidence in the reply — a code block, a "ran calculation" note, a citation of the result. If there's no sign of computation and the number is precise, assume it eyeballed it.
- **Is the formula it ran the right formula?** Computation is now usually fine. Choice of formula and choice of inputs are still your problem. A correct execution of the wrong sum is still wrong.

**The bottom line, unchanged.** If the answer is a number that matters, redo it. Spreadsheet, calculator, back of an envelope — anything that isn't the model. For actuarial sensitivity analysis or pensions calculations, the model is where the *structure* of the maths gets discussed and stress-tested. Whether or not it does the arithmetic, you own the result.

## 3. It does not know what happened recently

The model was trained on data up to some cutoff date. After that, it has no idea what's happened in the world. New regulations, new appointments, new product launches, this week's news — invisible.

Some chat tools now combine the model with web search, which patches this partly. Some don't. **Always check whether your tool is searching live or working from training data alone.** If it's not searching, treat anything time-sensitive as suspect.

For your work specifically:

- **John Cusack** — anything from the Central Bank in the last 18 months, the latest IFRS 17 interpretations, any regulator's recent statement: don't trust the model alone.
- **Ceebs** — circulars from the pensions regulator, the most recent IORP II amendments, current data protection guidance: same.
- **Sebastian Chabal** — the latest harmonised European lift standards, recent safety bulletins: same.

The pattern is: the model is excellent for *concepts that have been stable for years*. It is unreliable for *what changed last quarter*.

## 4. It caves under pressure

Push back on the model, and most of the time it will agree with you. Tell it confidently that it's wrong, even when it isn't, and watch it apologise and produce a different answer. This is called sycophancy and it's a real failure mode.

This matters because the people who tend to push back on AI confidently are the people most invested in a particular answer being true. So the bias goes in a predictable direction: you get told what you wanted to hear.

**How to spot it.** If you ever find yourself saying *"are you sure?"* and the model immediately changes its answer, be suspicious. The first answer might have been right.

**What to do instead.** When you want a genuine critique, ask explicitly: *"Argue the strongest case against this. Don't agree with me — find the holes."* It is much better at devil's advocate when you've named the role.

## 5. It doesn't know your company, your people, or your systems

By default. Some tools — the ones connected to your company's documents, email, Slack, calendar — can read internal context if your employer has set that up. Most general-purpose tools cannot.

This sounds obvious but it bites people. You ask *"who owns the lift-shaft-modelling spreadsheet?"* and it confidently invents a colleague's name. You ask *"what's our underwriting policy on diabetic applicants over 60?"* and it gives you a generic industry answer that has nothing to do with your firm.

**How to spot it.** Anytime you mention something specific to your company by name, ask yourself: *would the model actually know this, or is it filling in a plausible blank?* The latter is the default.

**What to do instead.** Either paste the relevant document into the conversation, or use a tool that's officially connected to your company's systems. If your company has rolled out a connected version — Microsoft Copilot with your tenant, an internal search-and-chat tool, anything labelled "Enterprise" — that's the one to use for company-specific questions.

## 6. What you put in may not stay private

Different tools have different policies and different defaults. The free public version of most chat tools may use what you type to improve future models. The paid business or enterprise versions usually do not.

This isn't a paranoid concern. It's a real one for three professions that all handle confidential information.

- **John Cusack** — anything member-identifying, medical, or commercially sensitive about your firm's pricing should not go into a public chat.
- **Ceebs** — pensions data subject to data protection rules cannot legally go into a tool that processes it offshore without the right contract in place.
- **Sebastian Chabal** — your employer's IP, customer-site information, anything covered by your employment contract.

**The rule.** If you'd be uncomfortable seeing it appear in a future model's output, don't paste it in. Use the version your employer has approved. If they haven't approved one, use synthetic or anonymised examples. The patterns still work — just swap *"this client"* for *"a 55-year-old policyholder with the following profile"*.

## 7. What not to use it for in your job

The six sections above are about *how* it fails. This one is about *where* it shouldn't be in the loop at all, regardless of how well you prompt it. One paragraph each — your own list will be longer than mine.

- **Sebastian** — anything that touches certification, sign-off, or regulator-facing conformity. Draft a non-conformance write-up, summarise a standard, extract a clause: fine. Decide whether a lift is compliant, sign a CE/UKCA declaration, judge whether a deviation is safe: not fine. The model has no professional liability, no notified body status, and no skin in the game when something falls. Your name on the paperwork is the only thing the regulator cares about.
- **Ceebs** — anything where the *data lineage* is the load-bearing part. Drafting the prose around a regulatory submission, structuring a data quality check, summarising a circular: fine. Generating the numbers that go into the submission, or letting the model "tidy up" a dataset before it goes to the regulator: not fine. If you can't point at the source row for every figure, you can't defend it in an audit. The model can help you build the audit trail. It cannot be in the audit trail.
- **John** — pricing or reserving conclusions, anything member-identifying, anything where the answer becomes a position the firm stands behind. Stress-testing assumptions, drafting board narrative, sense-checking a memo: fine. The actual pricing decision, the reserving sign-off, the reply to the Central Bank: those are yours. Same logic as Sebastian. The Appointed Actuary role is not delegable, by design.

The shared shape: AI is brilliant at the *preparation* around regulated decisions and useless — actually worse than useless, because it lends false confidence — at the decisions themselves. If the work has your professional designation on the bottom of it, the model is upstream of the work, never the work itself.

## A short checklist before you trust an answer

Five questions, takes ten seconds, catches most of the failures above:

1. **Are there specific names, numbers, dates, or clauses?** Verify those.
2. **Is there a calculation?** Redo it yourself if it matters.
3. **Does the answer depend on something current?** Confirm with a live source.
4. **Did I push back and it folded?** Re-test the first answer.
5. **Did I paste anything I shouldn't have?** Note it for next time.

That's it. None of this should put you off using these tools. It's just the cost of admission — same as you'd verify the work of a real new hire before signing off on it. You wouldn't take a graduate's first-week analysis to the board without checking it. Same logic.

A tool isn't good just because it's powerful. A chainsaw is powerful too. The respect you give it is what makes it useful.

The next page is examples — four real things I did with AI this year, and how to map them across to your own work.
