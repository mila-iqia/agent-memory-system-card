# Memory should be sovereign, and measurable

Your AI agent remembers things about you. Your preferences. The tasks you asked it to do. Facts you mentioned once in a conversation that it now carries into the next one. That memory is what makes agents feel useful. It's also what makes them consequential in a way earlier software wasn't.

We think this memory should be sovereign. It should live with you, and you should be able to choose what any given agent is allowed to release on your behalf.

We also think it should be measurable. You should be able to compare memory systems the same way you compare cars: what does this one prioritize, what does it trade off, and where does it fit your use case.

That's the work we've been doing with Mila, one of the world's leading AI research institutes, over the last several months. Today we want to share where we've landed, invite people building in this space to poke at it, and ask memory-system developers to come find us.

## Why memory needs its own card

Model cards helped people understand what a language model was for and how it failed. Dataset cards did the same thing for training data. Memory systems have grown up without an equivalent, even though memory is the piece of an AI agent that decides, quite literally, what the agent knows about you and what it says on your behalf.

The problem is that memory systems are hard to evaluate. The information that users need to make informed decisions about agent memory is scattered across heterogeneous documentation and marketing material, when it is available at all. Performance claims, privacy practices, user controls, and operational limitations are often documented separately, making it hard to understand how a system works and whether it fits a particular use case.

So we're building a card for that.

## What the card looks like

The Agent Memory System Card (AMS Card) is a long-form, structured documentation template for memory systems. It helps people making decisions about a memory system find answers to the questions that matter: what it remembers and how it works; its intended use and limitations; the evidence for its performance; the controls people have over their data; the privacy and contextual boundaries it enforces; and how it is maintained and governed.

The card is designed for builders, integrators, auditors, and people affected by memory-enabled systems. It documents architecture, lifecycle, supporting evidence, operational governance, and privacy controls. Rather than rating systems or calculating a privacy-versus-performance score, it makes the information and evidence relevant to both topics visible for a reader's own evaluation.

Different readers will focus on different parts of the card. Someone deploying an agent as a research assistant may look closely at performance evidence and capability boundaries. Someone handling health information may focus on privacy controls, retention, and contextual boundaries. The AMS Card gives each of them a common, structured place to find that information.

## What we're publishing today

- A draft AMS Card template and a completed fictional example card, so people can see what a filled-in card could look like.
- A short feedback survey, about five minutes, for anyone who has looked at a memory system in the last twelve months, from any angle.
- A three-week open comment window on the repository. We want to hear where the card is wrong, missing, or too narrow. After three weeks we'll close comments and start iterating on the feedback.

[View the AMS Card repository on GitHub](https://github.com/mila-iqia/agent-memory-system-card)

## What we're asking for

Three things.

1. **Tell us where we're off.** If you build memory systems, evaluate them, or make product decisions about how memory-enabled AI shows up for real users, we want to know where the AMS Card misses the mark. Take the short survey. It asks what you're using memory for, how you weigh privacy against performance and other criteria, what's missing from the card, which memory systems we should know about, and where we've got a verdict wrong. For anything longer or more specific, open a GitHub issue.
2. **Reach out if you're building this.** If you've been quietly working on memory that respects the user, we want to talk. Tick the "direct conversation" box at the end of the survey. The work is more interesting when the people doing it are talking to each other.

We've published a feedback survey so you can tell us what we've missed and where we're wrong.

## What comes next

The Agent Memory System Card is the first concrete piece of a longer research project on sovereign, measurable, portable memory for AI agents. The next steps: an open benchmark that runs against real memory systems, a reference implementation showing what user-owned memory looks like in code, and a broader working group across organizations tackling the same problem from adjacent angles.

Memory is the surface where the next chapter of AI decides what "user agency" actually means. That's worth getting right, and it's worth doing openly. Come look, come argue, come help.

