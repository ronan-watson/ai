# Is it working?

_Five metrics I use at work to tell if AI is actually paying off. Then the same five translated for each of your domains._

Every senior person eventually has to answer the question *"is this AI thing actually doing anything for us?"* — to a board, a regulator, a finance director, or just to themselves. The honest answer almost always needs evidence beyond *"the team really likes it."* That answer doesn't survive contact with a CFO.

What follows is the dashboard I look at in my day job. Five metrics, paired in a deliberate way: three of them are about *what we're shipping*, two are about whether it's safe to be shipping that much. Below the engineering version I've translated the same five for each of you — best guess where the analog is obvious, honest disclaimer where it isn't.

## What I look at, at work

I work in software, where the standard playbook for measuring engineering health is a set called DORA — four metrics about how code gets from a developer's laptop to production. I've layered an AI-adoption metric on top to answer the additional question: *is the AI tool the thing causing the change, or is it incidental?* Five in total.

1. **Active use rate** — of the people who have an AI tool licence, how many use it on any given day? Calculated as unique daily users over total licensed users. This is the *gym memberships vs. fitness* metric from the tools page. Licences don't count. Logins barely count. What counts is a meaningful action — accepting a code suggestion, sending a prompt, using an AI-built workflow. Below about 25% daily-active, the tool is shelfware regardless of what people say about it.

2. **Throughput** — how much work the team ships. In my world: pull requests merged, deployments completed, tickets closed in a sprint. I also track an *AI-assisted* version of throughput — what percentage of merged work had AI involved. Throughput on its own is not a goal. It's the *ratio between throughput and the next three* that tells you something useful.

3. **Quality** — change failure rate. Of all deployments to production, what percentage caused a problem that needed a rollback or a hotfix. This is the *if a photocopier gets faster, proofreading matters more* metric. If throughput goes up and quality drops, the AI is helping you ship bugs faster, not better code. I also watch *code churn* — what percentage of AI-generated code gets rewritten or deleted within two weeks. High churn means the AI is producing plausible-looking code that doesn't survive review.

4. **Speed** — lead time for changes. The wall-clock time between a commit being made and that change being live for users. I compare AI-assisted pull requests against non-AI-assisted ones from the same team in the same window. The difference, controlled for size, is the closest thing I have to an honest AI-time-saving number.

5. **Stability** — mean time to recovery. When something goes wrong in production, how long does it take to get it back. The reason this is on the dashboard alongside the adoption metric: if speed and throughput go up but stability goes down, the AI is helping you create complex incidents you can't quickly debug — which is a worse trade than nobody using the tool at all.

The trick is reading them together, not separately. A high active-use rate on its own means nothing. Active-use rising while quality is flat and stability is flat is the signal you want. Active-use rising while quality drops is the signal to slow down.

## For Sebastian Chabal — lifts engineering

I do not work in your industry. The five below are my best guess at the analogs. Tell me which ones I got wrong.

1. **Active use rate** — of the engineers on your team with access to AI tools (CAD copilots, fault-diagnosis assistants, spec-drafting tools), how many use them in a given week? Same shape as mine, slower cadence because design work has a longer rhythm than coding does.

2. **Throughput** — designs completed, fault investigations closed, inspection reports written, non-conformance reports turned around. I'd also track *modernisation cycle time* — start-of-survey to handover — since that's the long-running unit of work the business actually pays for.

3. **Quality** — defect rate at handover, the percentage of installs that need a re-visit within thirty days, NCR count per project. If AI is helping you draft specs faster, the test is whether those specs need more or fewer corrections at site than the ones you drafted by hand. Equivalent to my code-churn metric.

4. **Speed** — design-to-installation cycle time, mean time to fault resolution on callouts, time between a service request and an engineer on site. Comparable to my lead-time metric.

5. **Stability** — mean time between failures on installed units, callback rate within the warranty window, safety incident count. This is the irreducible one. AI helping you ship faster cannot trade against this. If MTBF drops as AI involvement rises, the AI is helping you put bad lifts into buildings, which is a worse outcome than no AI.

The pattern is the same as software. Treat throughput, speed and quality as a triangle — if two are improving and one is collapsing, the picture is not what it looks like at first glance.

## For Ceebs — pensions regulation

Same caveat: I'm an outsider to your domain. Treat this as a starting frame, not a definition.

1. **Active use rate** — of your data team and analysts who have access to AI tools, how many use them weekly. Cadence matters in regulation — daily use isn't the right unit; regular use against real work is.

2. **Throughput** — scheme returns processed, supervisory queries answered, data quality checks completed, scheme reviews closed. The AI-assisted version of throughput is the one worth tracking separately: what fraction of those were touched by AI assistance.

3. **Quality** — exception rate on regulatory deliverables, audit findings per quarter, count of data-quality issues escalated. Your domain has a stronger version of my quality metric than I do — when a regulator's data is wrong, the consequences are public and slow to fix. If AI is shortening time-to-report at the cost of more exceptions, that's a worse trade than your current process.

4. **Speed** — turnaround time on supervisory queries, time-to-publication on regulatory reports, time-to-resolution on data quality issues. Track AI-assisted versus manual within the same query type to control for difficulty.

5. **Stability** — repeat-issue rate (same data quality problem coming back), audit pass consistency year over year, regression in the quality of analyses over time. The instinct from your training applies directly here: lineage integrity, reproducibility, the ability to defend a result six months after producing it.

The hidden test in your domain is the audit one. If AI is making it harder, not easier, to reconstruct *how a number was produced and from what source*, the tool is a liability dressed up as productivity.

## For John Cusack — health insurance underwriting

This is the one I'm most confident about — your industry has a long tradition of measuring exactly this set of trade-offs.

1. **Straight-through processing rate** — of incoming applications, renewals, or group quotes, what percentage are processed, priced, and approved entirely by the automated system without an underwriter touching them. Higher STP rate means your underwriting team's time is freed for the cases that actually need judgement. This is the analog of my active-use rate, but inverted in flavour — for you, *more automation* is the success measure; for me, *more human use of the AI tool* is.

2. **Throughput** — quotes generated, policies bound, renewals processed. Volume during open enrolment is the hard test. AI's value is whether it lets you handle peak load without proportionally more underwriters.

3. **Quality** — medical loss ratio (claims paid over premiums collected) and underwriting leakage (the financial value lost when underwriters override the AI's pricing). If AI is mispricing risk, MLR will spike on the cohort it priced. If it's pricing too cautiously, leakage will rise as underwriters discount around it to win business. Either side of that line is a quality problem.

4. **Speed** — underwriting turnaround time, broker quote response time. The competitive metric in your market. AI's value is whether it lets you return a quote in hours rather than days for cases that don't need full human review.

5. **Stability** — actual-to-expected claim variance, combined ratio stability. The book performs how you predicted, or it doesn't. If the AI underwriting models are producing high A:E variance, the algorithms are missing risk factors the human underwriters were catching. This is the irreducible metric — *speed and STP rate cannot trade against it*.

The same triangle rule applies. STP rate and throughput rising while MLR and A:E variance hold is the signal. STP rate and throughput rising while MLR drifts is the signal to slow down and investigate which segment the AI is mispricing.

## What makes a metric actually useful

Three warnings, applicable across all four versions above.

**Access is not usage.** A licence count is the easiest metric to publish and the worst metric to claim victory with. *"We've adopted AI"* almost always means *"we bought it."* The active-use rate is the first honest filter — and as I said in the tools page, counting gym memberships is not the same as measuring fitness.

**Usage is not impact.** Even a 100% active-use rate doesn't prove the AI is producing value. It might just mean the tool is in the way and people are clicking through it. The metric that catches this is the AI-assisted-versus-manual comparison within the *same* category of work — same risk class, same scheme size, same project type. Anything else mixes confounds you can't separate.

**Correlation is not causation.** This is the one that gets boards excited and embarrasses people later. *"Adoption went up 30% and throughput went up 12%"* sounds compelling until you remember that throughput went up because you hired six people and there were no major incidents that quarter. The honest version is: *"AI usage is correlated with these outcomes, and here is what we're doing to test whether it's causal."* Anything stronger than that, in writing, will come back to bite you.

If you take one thing from this page: the metrics work together or not at all. The number to fear is the one that sits on a slide by itself with no context. The one to trust is the trio of *throughput, speed, quality* read alongside each other, with stability as the floor that nothing else gets to trade against.

The next page is a short, opinionated guide to which AI tools actually exist and how to pick one.
