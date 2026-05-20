# Tools I actually use

_A short, opinionated list — what each is good and bad at, and how to start._

Before we get into names: the most important thing on this page is the same as the first practical pattern. **What you use matters less than how you use it.** A friend with Microsoft Copilot who has internalised the patterns from earlier will get more out of it than a friend with the latest bleeding-edge model who treats it like Google.

That said. Here's the lay of the land.

## The four general-purpose chat tools

You've probably heard of all of these. They're the big ones for typing-questions-getting-answers.

- **ChatGPT** (OpenAI). The one that started the consumer wave. Strong all-rounder. Has a calculator/code mode and image generation. Free tier exists; the paid tier gives you better models and more capacity.
- **Claude** (Anthropic). My personal day-to-day driver. I find it the best at long-form writing, reasoning carefully through a problem, and admitting when it's not sure. Same shape — free and paid tiers. Less integrated into Microsoft Office than the others, more popular among software people.
- **Gemini** (Google). Strong, especially if you live in Google Workspace (Gmail, Docs, Sheets). Tight integration is the selling point.
- **Microsoft Copilot** (Microsoft, using OpenAI models underneath). If you live in Outlook, Word, Excel, Teams — this is the one that sits inside those apps and reads what you're working on. The model underneath is the same family as ChatGPT.

If you're picking from cold: any of them. Try two. Pick the one you'll actually open.

## If your company has only approved one

This is the realistic situation for most people. Your IT department has signed an agreement with one vendor and that's what you get. Common defaults right now:

- **Big corporates running Microsoft 365** → Microsoft Copilot. This is the case for one of you. It's a real tool, not a consolation prize. The patterns in **Practical patterns** all work in it. The thing to know: it reads your work documents (emails, Word files, SharePoint) by default if your company has enabled that, which is actually the most valuable feature any of these tools have.
- **Google Workspace companies** → Gemini for Workspace. Same idea, on the Google side.
- **Companies on neither** → often ChatGPT Business or Claude for Work. Same chat tools, with a contract that says the company's data isn't used to train models.

The advice is the same in all four cases: use the tool you have, lean into the integration features (the bit that reads your actual documents and calendar), and worry less about which underlying model is "best".

## Search-flavoured tools

These are AI tools that lean more towards *finding current information* than *reasoning from scratch*.

- **Perplexity**. Looks like a search engine, behaves more like an AI that searches the web and summarises the answer with links you can verify. I use it for *"what's the current state of X"* questions where I want sources I can click. If you need to chase recent regulation, news, technical standards — this is often faster than a normal chat tool.
- **ChatGPT search / Claude search / Gemini search**. The major chat tools all now have a mode that searches the web before answering. They're decent, but Perplexity is more deliberate about *showing you* the sources, which I value when I want to verify.

For all of these: **always click through to at least one source.** The summary is a starting point. The source is the truth.

## Enterprise and in-house tools

This category is more relevant if your company has invested in AI specifically. You might or might not have access. Worth knowing it exists.

- **Glean** is the one I work with most at Squarespace. It indexes your company's internal documents, Slack, email, and code, and lets you ask questions across all of that. *"Who owns the lift-shaft-modelling spreadsheet?"* — it can actually answer that, because it can see the spreadsheet's permissions and history.
- **In-house chatbots.** Lots of companies are building their own — sometimes thin wrappers over the public models, sometimes deeper. If your IT department has rolled one out, try it. The integration with your stuff is usually worth more than the rawness of the model.

The thing that makes these different from the public tools is they *know your company*. That solves one of the biggest limits we covered on the previous page.

## What I actually use, week to week

For honesty, here's the real breakdown. Yours will look different.

- **Claude** for almost all writing, drafting, thinking-out-loud, and structured reasoning. Most of these notes were drafted with it.
- **ChatGPT** occasionally, when I want a second opinion or a different style on the same question.
- **Perplexity** for *"is this current?"* and *"who else has said this?"* questions.
- **Glean** for anything that requires reading my company's internal documents.
- **Microsoft Copilot** I use the least — but only because my company's documents live in Google, not Microsoft. If they lived in Outlook and SharePoint, I'd live in Copilot.

I do not subscribe to all of these. I have one or two paid subscriptions at any time and use the free tiers of the rest. The marginal value of the second paid subscription is small.

## How to choose if you genuinely have a choice

A simple decision tree.

1. **Does your work mostly happen in Microsoft Office, Google Workspace, or somewhere else?** Use the one that sits inside the apps you actually use. The integration matters more than the model.
2. **Do you do a lot of long-form writing or careful reasoning?** Claude is, in my opinion, the best at this. Try it on the same task you'd try ChatGPT on and see if the output reads more like you.
3. **Do you need a lot of *current* information?** Add Perplexity to whatever else you use. Don't try to make one tool do both jobs.
4. **Is image generation a thing you care about?** ChatGPT and Gemini both have it built in. Skip if not.

The right answer for most non-coders is *one* general-purpose chat tool (whichever your company gave you, or whichever you like the voice of) plus *Perplexity for current-information questions*. That covers 95% of what's useful.

## A note on cost

The paid tiers are mostly in the same price band — roughly the cost of one or two cinema tickets a month. If you're getting use out of one daily, it's the best money-per-hour ratio of any tool you'll buy this year. If you're using it twice a week, stay on the free tier.

If your company is paying, even better — use the enterprise version, both because it's free to you and because it has the privacy contract that the consumer version doesn't.

One aside worth knowing: when your company eventually announces it has "adopted AI", what they usually mean is they've bought licences. That's not the same thing. Counting gym memberships is not the same as measuring fitness. Whether anyone in the building is actually getting value out of those licences is a separate question — and you'll probably be in a better position to answer it than the people who paid for them.

## The thing that changes everything

A tool sitting inside the application you actually work in beats a better tool you have to copy-paste into. The friction of switching windows is the killer. *"Open browser, find tab, copy paragraph in, copy answer back"* — versus *"AI is already in my Word document and can see what I'm writing"* — is a much bigger productivity difference than which model is technically smarter.

This is why I keep telling people: **the boring tool you have, used inside your real workflow, beats the exciting tool you have to context-switch to use.**

That's also why your IT department is, probably annoyingly, actually right about which one they've rolled out. The version that's connected and approved is worth more than the version that isn't.

---

That's the tour. The examples page is next — one worked task each, in your domain, using the patterns from earlier.
