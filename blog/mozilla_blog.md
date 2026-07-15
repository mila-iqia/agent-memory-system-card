Memory should be sovereign, and measurable
Your AI agent remembers things about you. Your preferences. The tasks you asked it to do. Facts you mentioned once in a conversation that it now carries into the next one. That memory is what makes agents feel useful. It's also what makes them consequential in a way earlier software wasn't.
We think this memory should be sovereign. It should live with you, and you should be able to choose what any given agent is allowed to release on your behalf.
We also think it should be measurable. You should be able to compare memory systems the same way you compare cars: what does this one prioritize, what does it trade off, and where does it fit your use case.
That's the work we've been doing with Mila, one of the world's leading AI research institutes, over the last several months. Today we want to share where we've landed, invite people building in this space to poke at it, and ask memory-system developers to come find us.
Why memory needs its own card
Model cards helped people understand what a language model was for and how it failed. Dataset cards did the same thing for training data. Memory systems have grown up without an equivalent, even though memory is the piece of an AI agent that decides, quite literally, what the agent knows about you and what it says on your behalf.
The problem is that memory systems are hard to compare. The information that users need to make informed decisions about agent memory is scattered across heterogenous documentation and marketing material (when it's available at all). Every project publishes performance numbers on the axes it does well on. Almost nobody publishes what happens to their system's performance when you turn privacy protections up. That trade-off is where the interesting question lives. The cost of giving users real control. And nobody has been reporting on it.
So we're building a card for that.
What the card looks like
At the top level, the Agent Memory System Card (AMS Card) is a single sheet. An at-a-glance read of how a memory system treats the dimensions that matter to whoever is choosing it. The dimensions we think matter:
Privacy. How the system treats your data and what leaves the machine you're on.
Performance. How well it actually remembers.
User control. Can you inspect what it holds, edit it, delete it?
Compartmentalization. Does the system honor category boundaries (health separate from work, personal separate from professional)?
Portability. Can you take your memory with you when you leave?
How each dimension is expressed on the card, a plain-English rating or a shade or a phrase, is deliberately still in flight. The point of the card isn't the grading system. The point is that these dimensions become legible to someone deciding.
Beneath the single sheet sits the long-form card: how a system actually works, what evidence supports its claims, what the operational trade-offs are, and where the honest edges live. The single sheet is for someone deciding whether a memory system is right for a given use case. The long-form card is for someone doing a thorough evaluation.
For someone deploying an agent as a research assistant, performance may matter more than compartmentalization. For someone handling health information, the balance flips. The AMS Card is a way to make those trade-offs visible in the same format across systems, so choosing intentionally is possible.
What we're publishing today
A draft of the AMS Card template on GitHub, with the technical design document, the criteria we're using, and worked examples.
A short feedback survey. Ten questions, about five minutes, for anyone who has looked at a memory system in the last twelve months, from any angle.
A three-week open comment window on the repository. We want to hear where the card is wrong, missing, or too narrow. After three weeks we'll close comments and start iterating on the feedback.
Link to the github repo
What we're asking for
Three things.
One. Tell us where we're off. If you build memory systems, evaluate them, or make product decisions about how memory-enabled AI shows up for real users, we want to know where the AMS Card misses the mark. Take the ten-question survey. It asks what you're using memory for, how you weigh privacy against performance and other criteria, what's missing from the card, which memory systems we should know about, and where we've got a verdict wrong. For anything longer or more specific, open a GitHub issue.
Two. Reach out if you're building this. If you've been quietly working on memory that respects the user, we want to talk. Tick the "direct conversation" box at the end of the survey. The work is more interesting when the people doing it are talking to each other.
We've published a feedback survey so you can tell us what we've missed and where we're wrong.
What comes next
The Agent Memory System Card is the first concrete piece of a longer research project on sovereign, measurable, portable memory for AI agents. The next steps: an open benchmark that runs against real memory systems, a reference implementation showing what user-owned memory looks like in code, and a broader working group across organizations tackling the same problem from adjacent angles.
Memory is the surface where the next chapter of AI decides what "user agency" actually means. That's worth getting right, and it's worth doing openly. Come look, come argue, come help.

