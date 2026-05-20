# Examples from my own work

_Four real things I did with AI this year. Map them across to your own._

The earlier pages are the theory. This one is the receipts. Each example below is something I actually built, used, or learned from in my own job over the last six months — not a hypothetical. The shapes will look different in your work, but the patterns underneath should be familiar by now.

## 1. A bot that answers the boring questions

The frustration: my team runs a busy Slack channel where other engineers come asking for help. The same five or six questions get asked every week. Different people. Same answers. The on-call engineer spends real time pattern-matching *"oh you need to fill in form X"* over and over instead of doing the work that actually requires thought.

What I built: a small chatbot, sitting in that Slack channel, with three operating rules baked in.

1. **Is this question for our team?** If not, identify the right team and point the asker at their Slack channel. Don't try to answer.
2. **If yes:** only answer from a curated knowledge collection — our documented patterns. Not from Slack history, not from generic internet knowledge, not from guessing.
3. **If the collection doesn't have a clean answer:** say so. Don't improvise.

It went live in our channel about three weeks ago. It's currently handling around 30% of incoming questions before on-call has to touch them.

A concrete moment from last week. Someone asked for a docker registry setup. The bot replied: *"this is the documented pattern, here's the recipe — but to actually do it for you, we need the registry URL and the auth mechanism."* The asker dropped both into the thread within minutes. Another engineer picked it up, cut the ticket, and had the thing working by end of day. The bot did the boring 80% — state the pattern, ask the right follow-up questions. The human did the 20% that actually needed judgement and action.

Two more details that turned out to matter more than I expected:

- **Every bot reply ends with a one-line disclaimer**: *"our on-call will review this response for accuracy."* A colleague said it best — that line "cognitively shifts people's expectations from word-of-god to good starter advice". Same content, completely different reception.
- **The bot is allowed to say "I don't have a good answer."** That's the rule that built trust. It's easy to build a bot that always says something. The discipline is building one that refuses to guess.

This is pattern 4 from earlier — the 80/20 split. Find the predictable, structure-heavy, write-it-the-same-way-every-time portion of a recurring task. Give that to a bot with strict rules. Keep the human part where it belongs.

The same shape works wherever you've got a recurring stream of questions and a curated source of correct answers. Common policy questions you keep getting asked. Regulatory clarifications where the answer almost always points back to one of three documents. Standard responses to standard queries. You don't necessarily need a *bot* — you can run the same recipe yourself in a chat tool by pasting the rules at the start and the document collection underneath. The pattern is the point.

## 2. A two-week stand-in for when I'm away

The frustration: every time I take more than a couple of days off, the team gets asked things only I would know the answer to. Or worse, things I would just *know who to redirect to* — but my colleagues have to guess.

What I built before going on PTO this week: a smaller version of the same bot, scoped to *me*. Same three rules, but:

- The knowledge collection is a single handoff document plus a handful of context notes.
- The bot's job is mostly to redirect: *"this is something my colleague X handles, here's their channel."*
- The footer says: *"I'll review these responses for accuracy when I'm back from leave."* Same trust-shift line.

Building the bot was the easy part. The valuable part was actually writing the handoff document — forcing myself to make explicit all the *"oh I always just"* things I'd been carrying in my head. AI helped draft that document too, by asking me what I'd want my replacement to know, then turning my scrappy answers into something readable. Then it generated three more artifacts off the same input: a team Slack message, a note for stakeholders, and an out-of-office reply.

For you: every job has the *"if I disappear for two weeks, what would break?"* question. Most of us never write the answer down. The exercise of writing it down is more valuable than any bot you build on top of it. And AI is genuinely good at that exercise — give it your scrappy bullet points, ask it to convert them into a structured handoff, and edit the output. You'll know more about your own job by the end of the hour than you did at the start.

## 3. Meeting notes you don't write

Almost every meeting I'm in at work now has an AI taking notes in the background. The transcript, a summary, a list of decisions, and a list of action items per attendee — all generated within a minute of the meeting ending. I do not write meeting notes anymore. I edit AI's first draft of them.

One small habit that turns out to matter: even when I'm in the meeting room in person, I join the video call from my laptop as well. That way my name shows up in the attendee list, and the AI can attribute *who said what* and *who owns what* in the notes. Without that, you get a perfectly reasonable summary that says *"someone in the room committed to X"* — which is useless when you're trying to follow up.

Honest take on quality: the summaries are good not perfect. Names get garbled occasionally. Subtle dynamics get flattened. Sarcasm reads as sincerity. But the *decisions* and *action items* are nearly always right. And those are the parts that actually matter — what did we agree, who's doing what next.

For you: this works in every meeting you have, regardless of what you do for a living. Board prep, regulatory check-ins, status meetings, one-to-ones, supplier reviews, member-facing conversations. Stop being the person who writes the notes. Start being the person who edits AI's draft and circulates them in the five minutes after the meeting ends. Your colleagues will notice. They won't know why.

If your company has rolled out an integrated tool (Microsoft Copilot inside Teams, Gemini inside Google Meet, the equivalent for Zoom), this is already available to you. Just turn it on.

## 4. The day I learned AI doesn't get tired

I want to end with one I got wrong, because the patterns I've been listing make this look easier than it is.

Earlier this year I got into a habit. I'd be on some piece of work in the evening. AI would help me draft something. The draft would be okay but not great. I'd ask for an improvement. The improvement would land. I'd see another thing to tighten. Ask for that. And again. And again. Two hours would pass. The work would technically be better than the first draft. I would be noticeably worse — tired, fried, irritable, decision-fatigued.

A colleague said something to me at a one-to-one that stuck: *"AI doesn't get tired. You do. That's the whole problem."*

The version I now use I've started taking seriously: the chat tool I work in occasionally suggests *"maybe tackle this in the morning"* when it can tell, somehow, that I'm flagging. For months I ignored it. Now I take it as a real signal. The AI noticing is not the issue. The issue is that I'd built a habit of treating the AI's tirelessness as my tirelessness, and they are not the same thing.

There's a wider pattern here, and it's worth saying out loud. AI lowers the marginal cost of doing one more pass on something. That sounds great, and often is. But the same lowered cost makes it much easier to slide into *"I could just do one more thing"* — late at night, on weekends, after the point where the next pass is actually helping. The new discipline isn't *how to push harder*. It's *knowing when to stop*.

You don't need an AI assistant to put pressure on your week. You already have plenty of pressure. Don't let the *"this is so cheap I might as well"* feeling become the way pressure escalates.

## What these four have in common

Each of them started from a real frustration — repeat questions, leave coverage, meeting-note overhead, iteration creep. Each kept a human in the loop at the point where judgement matters. Each turned out to be more about the *system around* the AI — the curated knowledge collection, the disclaimer, the join-from-laptop habit, the explicit stopping rule — than about the model itself.

If you take one of these and try the equivalent in your own work this month, I'd recommend the meeting-notes one. Lowest setup cost. Highest hit-rate. Most repeatable. You'll know within a week whether it's saving you time.

The last page is a short, opinionated guide to which AI tools actually exist and how to pick one. It's the most boring page on the site, which is appropriate, because the choice of tool genuinely matters less than what you do with it.
