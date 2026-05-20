# A mental model for what AI actually is

_What's really going on under the hood, in plain terms._

If you take one thing away from this whole site, take this:

**A chat AI is a smart, fast, well-read junior employee who has no idea who you are, what your job is, or what you're trying to do.**

That sentence is the model I keep going back to. It's not perfectly accurate as physics, but it's the most useful frame I've found for predicting what these tools will get right and where they'll quietly let you down.

## Unpacking the analogy

Let's go through it piece by piece, because each word does work.

**Smart.** It can reason. It can compare, summarise, plan, argue, restructure. On a generic problem with no hidden context, it's often genuinely impressive.

**Fast.** It will produce in 30 seconds what a person would spend an hour on. That's the whole game, really.

**Well-read.** It has been trained on an enormous amount of public text — books, articles, code, forums, documentation. So it knows the *shape* of almost any topic you can name. Underwriting, actuarial science, pensions regulation, mechanical engineering, lift systems — it's seen the words and the patterns. It can usually sound credible.

**Junior.** This is the bit that trips most people up. It's *junior*. It has no judgement that wasn't taught to it by example. It will not push back unless you've told it to. It defers. It guesses confidently when it should ask. It will hand you a perfectly typed, well-structured answer that is wrong, and it will do it with the same tone as when it's right.

**Has no idea who you are or what you're trying to do.** This is the most important part. The model does not know your company, your role, your colleagues, the system you're working in, the constraint you're operating under, the regulator you answer to, the decision you actually need to make. By default, it is working in a vacuum and pattern-matching to the most generic version of your question.

If you give it nothing, it gives you the average answer for the average person in the average situation. Which is almost never the answer you need.

## The one wrong assumption that wastes the most time

People treat it like a search engine.

You type a question, you expect an answer. The model talks like it knows things, so it feels like Google with prose. That mental model leads you to ask short, decontextualised questions, and get short, decontextualised answers back, and then to either trust them too much or dismiss the whole tool as useless.

It is not a search engine. It is not a database. It is not even a *knower*. At its core it is a thing that produces plausible next words based on what came before. In 2026, the better tools can dress that core up with a calculator, a web browser, the ability to read files and run small programs — and that genuinely changes what tasks they can finish — but the engine underneath is still next-word prediction, and the failure modes still come from there.

That sounds dismissive. It isn't meant to be — that mechanism is genuinely useful. But internalising it changes everything about how you talk to it.

A search engine rewards short queries. The model rewards context. Long, specific, structured input gets you long, specific, structured output. Short, vague input gets you short, vague output that *looks* specific.

## Why this matters for you specifically

**John Cusack**, underwriting and pricing models live and die on the assumptions you bake in. A model with no context will assume the *generic* assumptions — and those won't match your firm, won't match the Irish market, and won't match what your reinsurer expects. The skill is going to be: *get the assumptions out of your head and into the conversation* before you ask for analysis.

**Ceebs**, you work in a field where the question "is this number right?" has a real answer. Data validation, lineage, regulatory reporting. The model will happily generate plausible-looking summaries of plausible-looking data. The instinct to ask *"where did this come from and can I verify it?"* — which you already have — is the single most important habit anyone can bring to these tools.

**Sebastian Chabal**, mech eng has the cleanest test of any of these: does the thing work or not? AI is not going to certify a lift. But it can absolutely save you hours on documentation, on summarising a 200-page standard, on drafting a non-conformance report, on extracting the relevant clause from a regulation you barely have time to read. Anything with words and patterns, it speeds up. Anything with hard physical truth, it informs but doesn't decide.

## The model is one part of the system

Here's the second mental shift, and it took me longer to internalise than the first. The chat box you type into isn't the whole tool. The model is one component of a larger system: the documents it can or can't see, the data it's been given, the guardrails your company has set, the conversations you've had with it before, the rules it's been told to follow.

A great engine in a badly designed car still gives you a bad car. The single biggest improvement I've made in my own usage hasn't been switching to a better model. It's been getting better at giving the same model better surroundings — better context, better sources, better instructions on what to do and what not to.

This is also why your company-issued tool, the one that lives inside your existing documents and knows your colleagues' names, is usually more valuable than a more powerful tool you have to copy-paste into. The model behind it might be slightly weaker. The surrounding system around it is almost certainly stronger.

## What this implies in practice

Three implications follow from the model, and the rest of this site is really just consequences of these:

1. **Context is everything.** Before you ask, tell it what it needs to know. We'll spend a whole page on what that means in practice.
2. **It's a draft generator, not an answer generator.** Treat its output the way you'd treat the first attempt from a competent new hire. Useful, almost always needs editing, sometimes wrong in ways you have to catch.
3. **Verification is your job, not its job.** It will not flag when it's guessing. It will not say "I'm not sure about this." Or rather — it can, but only if you've explicitly asked it to. You stay in the loop. Always.

Internalise the analogy and a lot of the strange things these tools do stop being strange. Of course a junior employee with no context produces generic work. Of course they don't push back. Of course they sound confident — that's how you survive your first six months in any job.

The skill we're all learning is how to be a good manager of this particular junior.

The next page is about how.
