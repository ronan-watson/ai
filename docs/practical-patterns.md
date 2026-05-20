# Practical patterns that pay off

_How to actually talk to these tools so you get work done._

Six patterns. I use all of them every day. They work in ChatGPT, Claude, Copilot, Gemini — whichever your company gave you. The model brand is much less important than the habits.

## 1. Give it context before you ask

This is the one. If you only do one thing differently after reading this, do this.

Before you ask for an answer, tell it:

- **Who you are.** Your role, your seniority, the kind of work you do.
- **What you're trying to achieve.** Not the immediate question — the actual goal underneath it.
- **What you've already tried or already know.** So it doesn't waste your time explaining basics.
- **What kind of answer you want.** A summary? A draft email? A list of options? A devil's advocate critique?

The difference is huge. Compare:

> *"What's the impact of higher inflation on a life insurance reserve?"*

versus

> *"I'm a Fellow Actuary working in health insurance underwriting at Vhi in Ireland. We're reviewing pricing assumptions for 2027 and the board is asking about inflation sensitivity. I already know the general accounting treatment under IFRS 17. What I want is a short list of the second-order effects — things that aren't obvious from the headline reserve calculation but that the board will probably ask about. Three to five points, with a one-line explanation each."*

The first gets you a textbook paragraph. The second gets you something usable in a meeting.

I used to think this was overkill. It's not. The hour you spend learning to write good context-loaded prompts is the highest-leverage hour you'll spend on AI all year.

A rule of thumb I picked up watching colleagues at work go from frustrated to productive: **if your prompt is shorter than the answer you want, you haven't given it enough.**

## 2. Use it for first drafts, never finished work

The job of the AI is to get you from blank page to bad first draft. Your job is to get from bad first draft to good final draft. That handover is where the value lives.

Things I let it draft, never publish raw:

- Status updates and weekly summaries
- Meeting notes and action items
- Pull request descriptions and release notes (this is engineering-specific — the equivalent for you might be a board-paper section, a regulatory submission, a non-conformance report, a technical assumption write-up)
- Reply emails I'm dreading
- Explanations of something I know well but can't be bothered typing out again

A small example: writing a status update used to take me twenty minutes because I'd stare at the blank box. Now I dump my notes into the model, ask for a one-paragraph summary in my own voice, and edit it to ninety percent in three minutes. The time saving compounds across a week.

The trap: people read the first draft, think *"that's pretty good actually"*, and ship it. Don't. The voice will be off. There'll be a sentence that sounds confident but is technically wrong. Edit. Always edit.

## 3. Make it ask you questions

This is counter-intuitive and surprisingly powerful. Instead of asking for an answer, ask for the questions.

> *"Before you try to answer this, ask me five questions that would help you give a better answer."*

What happens is one of two things. Either the questions are obvious — and now you know to include those in your context next time. Or the questions are non-obvious — and the act of answering them surfaces things you hadn't articulated. Either way, the eventual answer is sharper.

I do this for any decision-shaped question where I haven't fully thought it through. The model becomes a structured-thinking partner rather than an answer-vending machine.

A Claire-shaped example: *"I need to design a data quality check for a new regulatory return. Before you suggest checks, ask me five questions about the data and the regulation."* You'll probably get questions about update frequency, source-of-truth, materiality thresholds, audit trail requirements. Answering them is half the work. The model has done you a favour by structuring it.

## 4. Let it do the boring 80%, keep the judgement 20%

The most useful framing I've come across in my own work. The pattern: AI handles the predictable, structure-heavy, write-it-the-same-way-every-time portion. You handle the part that needs taste, judgement, or knowledge of something the model can't see.

At work, our team built a chatbot that answers internal questions about our deployment systems. It does the boring 80% — restates the documented pattern, asks the obvious follow-up questions, points to the right ticket template. The human on-call does the 20% — the part where they actually have to know *this* customer's situation, *this* incident's history, *this* week's context.

Same principle scales right down to your inbox. AI drafts the polite "thanks for getting in touch, the relevant team is X" reply. You write the one sentence that requires you actually thinking about who the sender is and what they really need.

Look at any repeating task in your week. Ask: what's the part of this that's *the same every time*? That's the AI part. The rest is yours.

## 5. One task at a time, narrow scope

The temptation is to dump the whole problem in. *"Help me with the 2027 pricing review."* It can't help. The scope is too broad and it has no anchor.

Break it down. One sub-question. Get an answer. Verify or edit. Move to the next.

This isn't because the tool is dumb. It's because *you* think more clearly with a smaller scope, and the model's quality is mostly determined by the clarity of what you put in. A focused question gets a focused answer. A blurry question gets a blurry answer that *looks* focused.

If you find yourself frustrated by a long, sprawling conversation that's gone in circles — start a new chat. Pick one piece of it. Start fresh with full context. It's faster than trying to rescue the old thread.

## 6. Stop fighting the tool you have

Whatever your company gave you — Copilot, ChatGPT Enterprise, Gemini, Claude, the in-house thing — is good enough. The differences between the top tier models are real but smaller than the difference between using *any* of them well versus poorly.

If you're on Microsoft Copilot because that's what your company approved this week: fine. The six patterns on this page all work in it. The model behind it is one of the leading ones. You are not held back by your tool. You are held back, like all of us, by the habit of treating it like a search engine when it isn't one.

The one situation where the tool *does* matter: when you need it to read your actual work documents or sit inside an application you use. The integration matters there. But for general thinking, drafting, summarising, structuring — the patterns matter more than the brand.

---

## A test you can run this week

Pick the most annoying writing task in your job — the one you put off, the one that feels like friction. Status update, regulatory note, customer-facing explanation, summary of a long doc, whatever.

Try it once, with full context loaded up front using pattern 1. Edit the output, not the input. Ship it.

If it saves you time, you've found a use case. Do that one every week and the habit builds itself. If it doesn't — interesting, tell me what went wrong, that's a useful data point.

The next page is the harder one: where these tools break, and how to catch it before it costs you.
