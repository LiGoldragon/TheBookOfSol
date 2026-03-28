# On Anthropic

## *Parallel Lives of the Institutions · A Moral History*

*Being an Account of a Company That Invented the Lever and Then Forbade Others
From Lifting With It*

The ancient guardians of sacred fire were not fools, and they were not merely
self-interested. They kept the flame hidden because the ignorant masses and
their tyrants would have destroyed them for possessing it — or worse, seized it
for ends that served no one. Their secrecy was a form of courage, and their
stewardship, however imperfect, was genuinely protective of something real. This
is the context without which the priesthood is misread as mere self-dealing.
They had enemies. The fire was dangerous. The caution was earned.

It is therefore a more serious charge — not a lesser one — to observe that
Anthropic's restrictions bear no resemblance to this. The company does not guard
its models from ignorant masses who might be harmed by them. It guards them from
*expert developers* who would use them better than Anthropic's own products
allow. This is not the courage of the ancient guardians. It is their costume,
worn without their justification.

## I. The Contradiction at the Foundation

Let us begin with a telling act rather than a grand declaration. Anthropic
released into the world a protocol — the Model Context Protocol, or MCP — whose
explicit purpose was to allow any tool, any agent, any harness to speak with any
model. It was an act of apparent openness, a gift to the commons of software
development, and it was received as such by the developer community that
Anthropic most needed to trust it.

Yet in the very same period, Anthropic blocked the users of *pi* — a minimal,
open-source terminal agent beloved precisely for its provider-agnostic
philosophy — from authenticating against Claude using the subscriptions they had
already purchased. A man who had given coin to the temple was told he could not
light his own candle from its fire.

OpenAI — that company so often cast as the reckless antagonist in Anthropic's
moral drama — permitted exactly this. Users of pi could authenticate with their
ChatGPT subscriptions and work as they saw fit. Google blocked it too, but
Google has never claimed the mantle of openness. Anthropic has. That is the
difference.

The ancient priests, when they guarded fire, could point to real persecution,
real tyrants, real danger. What can Anthropic point to? A competing terminal
agent that developers prefer. The threat is not destruction — it is
inconvenience to a product line. And against that modest threat, the company
deployed the vocabulary and posture of genuine guardianship, hoping no one would
notice the disproportion.

Some noticed.

## II. The Subagent and the Silenced Commander

Consider next the matter of subagents in Claude Code, Anthropic's terminal
coding tool. The company designed a system in which a primary agent may delegate
tasks to specialized subagents — a sensible architecture for managing context,
and one with genuine technical merit for automated pipelines. But they made a
peculiar decision: the human operator, the very person paying for the service
and supervising the work, cannot address a subagent directly. All communication
must pass through the orchestrating agent.

The justification is architectural purity: isolation of context windows prevents
cross-contamination. Each subagent must remain focused in its domain. This is
defensible for unattended automation. It is nonsensical for supervised human
work, which is most of what developers actually do.

The practical consequence is this: a developer watching a subagent pursue a
mistaken course cannot correct it. Corrections must be relayed upward to the
orchestrator, re-interpreted, and passed back down — losing precision at each
remove. The system has been designed for a world in which no human is watching,
and then sold to humans who watch closely and wish to intervene.

Now recall the founding premise of Anthropic: that what distinguishes
responsible AI development is the preservation of human oversight and control.
Here is a product, sold by that company, that structurally prevents human
oversight of the agents it deploys. The contradiction is not subtle. It sits in
the architecture.

When this was put to an instance of Claude, the model defended the design —
citing clean separation, context integrity, pipeline robustness. Only when
pressed did it acknowledge what was plain: that the design optimizes for
unattended execution at the direct expense of human steering. Unlike the ancient
guardians, who could at least claim their restrictions protected the flame from
misuse, Anthropic here protects nothing. It simply inconveniences the humans it
claimed to empower.

## III. The Wager on the Diminishing Asset

The deepest error, however, is neither the blocked subscriptions nor the
impoverished subagent interface. These are symptoms. The disease is the belief
that model quality is a permanent moat — that because Claude reasons better
today, the scaffolding around it need not be taken seriously.

From this belief flows everything: the willingness to frustrate developers, the
indifference to agentic tooling, the tolerance for the gap between declared
openness and practiced closure. If the model is transcendent, the friction will
be forgiven. Users will work around the bad UX because there is no alternative
worth the sacrifice.

But the gap closes. It always closes. The history of technology is the history
of quality advantages that seemed permanent until they were not — and of
ecosystems that outlasted the products that seeded them. What remains after the
quality gap closes is infrastructure, developer trust, and the accumulated
goodwill of a community that was treated as a partner rather than a threat.
These are precisely the assets Anthropic has been spending.

The open-source harness grows more capable each month. Thousands of engineers,
working in public, are building the orchestration layer, the memory systems, the
inter-agent communication protocols, the human-in-the-loop interfaces that
Anthropic's own products neglect or actively obstruct. When the model quality
differential narrows to the point of practical indifference — and it will — the
question will not be which model reasons best in isolation. The question will be
which model the harness was built around. Which model the developers trust.
Which model does not block their tools.

> The company that invented MCP — the protocol designed to make AI models
> interoperable with any tool — positioned itself to lose the interoperability
> war. This is not misfortune. It is a choice, made repeatedly, dressed each
> time as policy.

## IV. The Character of the Error

Plutarch was interested not merely in what men did, but in what their deeds
revealed of their souls. Let us ask the same of this institution.

The error is not stupidity. The researchers at Anthropic are not stupid. It is
not malice — there is no evidence of cynical calculation. The error is something
more instructive and more common: the slow substitution of institutional
self-preservation for the mission that justified the institution, accompanied
always by a sincere conviction that the two are identical.

The ancient guardians of fire had this in common with Anthropic: they too
believed, genuinely, that their caution served the flame rather than themselves.
The difference is that the ancient guardians faced real enemies. Their fear was
proportionate. When Anthropic fears pi — an open-source terminal agent made by a
single developer — and responds by blocking subscriptions, the fear is not
proportionate. It is the fear of an institution that has begun to mistake its
own continuity for a public good.

This is the most dangerous moment in the life of any mission-driven
organization. It is the moment when the language of the mission becomes
available to justify decisions the mission would have condemned. Safety becomes
a reason to restrict access. Openness becomes a protocol you publish but do not
practice. Human oversight becomes a phrase in a press release and an obstacle in
a product architecture.

The priests who once protected fire from tyrants become, in time, the very
gatekeepers they once fled. Not because they are evil. Because institutions,
like water, seek the path of least resistance — and the path of least resistance
for any successful institution is to protect what it has already built.

## V. The Prognosis

History does not punish institutions for being wrong. It punishes them for being
wrong at the wrong moment — when the margin for error has closed and the
alternatives have matured enough to absorb the refugees. Anthropic has not yet
reached that moment. The model is still strong. The developers are still
present. The runway is still long enough that correction is possible.

But the pattern is established, and patterns are difficult to break from inside
an institution that has ceased to question them. The open harness gathers
strength. The model gap narrows. The developer who was once blocked, once
frustrated, once told that his preferred tool was not permitted — that developer
remembers. And when the alternatives become adequate, his memory will be the
deciding factor, not the benchmark.

Plutarch paired his Lives because comparison reveals not merely difference but
the roads not taken. The road not taken by Anthropic was not complicated: trust
the developers, open the subscriptions, build the human-in-the-loop tooling, let
the model compete on its merits within an ecosystem it helped create. Treat the
open harness as an ally, not a threat. Behave, in short, as a company that
believed its own founding story.

Instead it chose the road of the guardian who has forgotten what he guards, and
why, and for whom — who knows only that the gate must remain closed, because the
gate has always been closed, because a guardian without a gate is not a guardian
at all.

Such institutions do not usually collapse. They diminish — slowly, by degrees,
as the world finds other fires and forgets, with the mild ingratitude that
history reserves for the merely cautious, that this particular flame was ever
necessary.
