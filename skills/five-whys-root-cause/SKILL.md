---
name: five-whys-root-cause
description: Apply Taiichi Ohno's Five Whys to drill a problem or a claim down to its actual mechanism. Two modes. Retrospective takes a recurring failure or gap from standard and walks the causal chain back to a systemic root cause plus a countermeasure that prevents recurrence. Prospective takes a prediction, forecast, threat model, or extraordinary claim and forces out every intermediate step required to reach the stated endpoint, exposing the weakest link and the load-bearing unstated assumption. Trigger on "5 whys", "five whys", "root cause", "RCA this", "why does X keep happening", "what is really going on with X", "drill into this claim", "what are the intermediate steps", "walk me through how X leads to Y", "stress test this prediction", "where does this argument break", or any request to dissect a recurring problem or a big claim down to mechanism. Also triggers on a pasted incident report, postmortem, retro, journal entry, essay, or forecast plus a request to find the pattern or test the reasoning.
metadata:
  short-description: Root-cause a failure, or stress-test a claim
---

# Five Whys (Ohno Protocol)

## The real method (primary source)

The Five Whys was originated by Sakichi Toyoda, formalized by Taiichi Ohno at Toyota in the 1950s, and published in Ohno's 1988 book *Toyota Production System: Beyond Large-Scale Production* (Productivity Press). Ohno described it as the basis of Toyota's scientific approach: by repeating why five times, the nature of the problem and its solution both become clear.

The number five is a heuristic, not a rule. Ohno himself noted that sometimes three whys are enough and sometimes eight are needed. Stop when the cause is systemic, structural, and actionable.

The canonical Ohno example (Ohno 1988, p. 17):

1. Why did the machine stop? An overload blew the fuse.
2. Why was there an overload? The bearing was not sufficiently lubricated.
3. Why was it not lubricated? The lubrication pump was not pumping enough oil.
4. Why was the pump not pumping enough? The shaft of the pump was worn and rattling.
5. Why was the shaft worn? There was no strainer attached and metal scrap got in.

Countermeasure: install a strainer. Without that, replacing the fuse or the pump leaves the failure mode intact and it recurs within months.

## Two modes

The method is almost always taught in one direction only: backward, from a defect that already happened. That is half of it. The same discipline run forward is a claim-interrogation tool, and it is arguably the higher-leverage use.

| | Mode A: Retrospective | Mode B: Prospective |
|---|---|---|
| Input | A failure that already happened, usually more than once | A claim about what will happen |
| Question form | "Why did that happen?" | "What has to be true immediately before that?" |
| Direction | Effect back to cause | Endpoint back to preconditions |
| Failure it catches | Fixing symptoms, blaming people | Hand-waving, skipped steps, unfalsifiable claims |
| Output | Root cause plus countermeasure | Weakest link plus the load-bearing assumption |
| Ends at | A process you can change | A step already happening today, or a step nobody can describe |

Pick the mode from the input. A described past event goes to Mode A. A described future outcome, forecast, threat model, projection, valuation case, or catastrophe scenario goes to Mode B. If the user gives both, a past event plus a prediction of where it leads, run A first and then B on the prediction.

## Five non-negotiable rules (both modes)

1. **Start with a clear, specific statement.** Not "X is bad" and not "X is coming." For Mode A: "On [date], during [context], [observable thing] happened, which deviates from [the standard or expectation]." For Mode B: "[Actor] will cause [specific outcome] of [magnitude] by [date] via [mechanism]."
2. **Never end at a person, and never end at a motive.** "Human error", "they dropped the ball", "I am lazy" are symptoms, not causes. "They want power", "they are greedy", "they are naive" are not mechanisms. Push to the process, environment, system, incentive, or physical constraint that allows or prevents the thing.
3. **Each link must be the direct cause of, or the direct precondition for, the previous one.** Test by running the chain in reverse. If it does not hold logically, the analysis is wrong.
4. **Stop when you reach something you can actually change or actually check.** Five is the target, not the ceiling.
5. **Distinguish noise from signal first.** A random one-off does not deserve a Five Whys, and neither does a claim nobody is acting on. Apply this to recurring patterns, gaps from standard, and claims driving real decisions. Reacting to statistical noise is what Deming called tampering, and it makes things worse.

---

# Mode A: Retrospective (the classic protocol)

## Workflow

### Step 1: Define the problem with surgical precision

Convert the description into one clear sentence:

- WHAT happened (observable, not interpretive)
- WHEN it happened (date, or the pattern frequency)
- WHERE, or in what context
- HOW it deviates from the standard or expectation

If any of WHAT, WHEN, WHERE, or HOW is missing or ambiguous, ask. Use the host's structured question tool if one is available, otherwise ask one short direct question. Do not write clarifying questions as long prose or a numbered interrogation.

### Step 2: Pull in context

Before running the chain, check whatever record exists:

- Prior analyses of the same or an adjacent pattern
- Incident reports, postmortems, retros, monitoring history, tickets, commit history
- Personal notes, journals, meeting notes, or a decision log
- Anything that shows whether this is a first occurrence or the fifth

This is what turns the analysis from generic to surgical. Reference what was found in the Notes section of the output.

### Step 3: Run the chain

- Ask Why #1 and give the most likely direct cause, grounded in what was described and the context from Step 2
- For each subsequent Why, the answer must be the direct cause of the previous answer, not a vague theme and not a jump
- Continue until the cause is structural, systemic, and actionable
- If the chain branches into more than one parent cause, note the branches and follow the highest-leverage path first. List the unexplored branches in the output rather than dropping them

### Step 4: Verify with the therefore-chain

Walk it back upward: root cause, therefore A, therefore B, therefore the original problem. If the chain breaks or jumps logic anywhere, the analysis is wrong. Redo it.

### Step 5: Propose a countermeasure

Three layers. The first is optional and must be labelled as what it is.

1. **Containment (optional).** Whatever stops the bleeding today. This is allowed to treat the symptom, and it must be labelled as containment so nobody mistakes it for the fix. Replacing the fuse is containment.
2. **Countermeasure.** One concrete action doable in the next seven days that addresses the root cause, not the symptom. Specific. Schedulable. Installing the strainer is the countermeasure.
3. **System change.** The standard, gate, habit, or design change that catches this failure mode earlier next time. This is what scales the lesson.

### Step 6: Output

Use the template below. It is plain Markdown and pastes cleanly into any notes system, ticket, or doc.

## Output template (Mode A)

```markdown
# Five Whys: [Short Problem Title]

**Date:** YYYY-MM-DD
**Domain:** Engineering | Operations | Product | Personal | Health | Finance | Other
**Tags:** ...

## Problem Statement
[One clear sentence. What, when, where, how it deviates from standard.]

## The Chain
1. Why did [problem] happen? -> [direct cause 1]
2. Why [cause 1]? -> [direct cause 2]
3. Why [cause 2]? -> [direct cause 3]
4. Why [cause 3]? -> [direct cause 4]
5. Why [cause 4]? -> [root cause: systemic, structural, actionable]

## Therefore-Chain (sanity check)
[Root cause] -> [4] -> [3] -> [2] -> [1] -> [original problem]. Holds.

## Root Cause
[One sentence. Structural, not personal.]

## Containment (optional)
[Symptom-level action taken today, labelled as such. Omit if none.]

## Countermeasure (root cause, this week)
[One concrete action. Specific. Schedulable. Addresses the root cause.]

## System Change (long-term)
[The standard, gate, or design change that catches this failure mode earlier next time.]

## Notes
[Branches considered, alternative causes ruled out, related patterns from past records.]
```

## Worked example A1: personal habit

**Problem:** On three of five weekdays this week, the 9 PM writing session did not happen. The standard is five sessions a week.

1. Why did the session not happen? By 9 PM there was no energy left and I chose sleep.
2. Why was there no energy left at 9 PM? The session sits after a full workday, dinner, and family time, at the lowest point of the day.
3. Why does the session sit at the lowest point of the day? It was placed in the only slot the calendar showed as empty.
4. Why was 9 PM the only empty slot? Mornings are consumed by chat and email triage, which begin the moment I wake.
5. Why does triage consume the mornings? No block in the calendar protects a morning hour from it, so whatever arrives first takes the time.

**Therefore-chain:** No protected morning block, so triage takes the mornings, so the only empty slot is 9 PM, so the session sits at the daily energy low, so on heavy days there is nothing left and it is skipped. Holds, all five links.

**Root cause:** No protected block exists. Writing is scheduled into leftover time, and leftover time carries leftover energy.

**Containment:** None needed. Nothing is on fire.

**Countermeasure (root cause, this week):** Block 6:30 to 7:30 AM Monday to Friday as writing only. Phone in another room.

**System change:** Writing is scheduled first, not into whatever gap remains. Chat and email do not open until the block is closed.

**Notes:** Branch considered and ruled out: poor sleep. The three missed days were the three heaviest meeting days, which points at load rather than rest. No prior analysis on file.

## Worked example A2: operations incident

**Problem:** The nightly reporting batch job failed on 3 of the last 10 runs, and nobody noticed until a stakeholder asked why the dashboard was stale.

1. Why did the job fail? It exited on an unhandled timeout while querying the reporting database.
2. Why did it time out? The query does a full scan of an events table that has grown past the statement timeout.
3. Why did the table grow past that point? It has no retention or partitioning policy, so rows have accumulated since launch.
4. Why is there no retention policy? The table was added in a hotfix that shipped outside the normal schema review.
5. Why did a hotfix skip schema review? Schema review is an advisory human checklist, not a gate enforced in CI.

**Therefore-chain:** Review is advisory, so a hotfix skipped it, so the table shipped with no retention policy, so it grew unbounded, so the query exceeded the statement timeout, so the job failed. Holds.

**Root cause:** Schema changes can reach production without passing the review gate, because the gate is a convention rather than an enforced check.

**Containment:** Raise the job's statement timeout and rerun it so the dashboard refreshes tonight, and add the missing retention policy so the table stops growing. Neither touches the root cause. Both are labelled containment so nobody files this as fixed.

**Countermeasure (root cause, this week):** Add a required CI status check that blocks merge of any migration creating a table without a declared retention policy. Ship it this week, so the gate exists before the next hotfix.

**System change:** Hotfixes go through the same check as everything else. The only bypass is an explicit exemption field in the migration itself, reviewed after the fact. The gate stops being a checklist and becomes a property of the pipeline.

**Notes:** Branch not followed: the failure was silent. That is a separate chain, rooted in the job's exit status not being monitored. It shares no cause with this one and needs its own analysis. Do not merge them.

---

# Mode B: Prospective (claim interrogation)

## Why this works

A catastrophic or spectacular endpoint is easy to assert and hard to reach. Getting there requires a chain of intermediate steps, and every one of those steps has an actor, a mechanism, a resource requirement, and a point of possible failure. Most large claims survive only because nobody makes the claimant walk the chain out loud.

Running the whys forward does three things at once. It separates people who have thought the mechanism through from people who have absorbed a conclusion. It locates the exact step where the argument stops being mechanical and starts being atmosphere. And it converts an unarguable claim into a falsifiable one, which is the only form in which a claim can be usefully argued about at all.

This applies to any high-stakes forecast: a competitor will take half the market, a regulation will kill an industry, a technology will erase a job category, a valuation is justified, a system will be breached along a specific path, a policy will cause a specific collapse. The mode is neutral about whether the claim is right. Some claims survive the drill intact, and that is a real result rather than a failure of the method.

## Mode B rules

1. **Restate the claim in falsifiable form before drilling.** Actor, mechanism, magnitude, deadline. If any of the four is missing, that absence is itself the first finding. A claim with no magnitude and no date cannot be wrong, which means it cannot be right either.
2. **Ask for preconditions, not reasons.** The question is "what has to be true immediately before that step, for that step to be possible?" and not "why do you believe that?" Beliefs are not steps.
3. **Every step names an actor, an action, and a resource.** Who does it, what they do, and what it costs them in money, time, compute, access, or physical material. A step with no actor is not a step.
4. **Tag every step.** Observed (already happening today, cite it), Plausible (no known barrier, no evidence yet), Unsupported (asserted, no mechanism given), or Unfalsifiable (no observation could contradict it).
5. **Score the conjunction.** The chain is at most as strong as its weakest link, and independent steps multiply. Five steps at 80 percent confidence each is 33 percent, not 80. State this explicitly when the chain is long. If the steps are correlated rather than independent, say so instead of multiplying blindly.
6. **Steelman before you cut.** If a step is missing, supply the strongest version of it yourself, then evaluate that version. Rejecting a claim because its holder explained it badly is not analysis.
7. **Never end at motive.** "They want it to happen" and "they are incentivized to say it" are not mechanisms. Both may be true and neither is a step in the chain. Same rule as never ending at a person in Mode A.
8. **Stop at one of two places.** Either a step already observably happening today, in which case the argument is grounded and the remaining disagreement is about magnitude and timing rather than possibility. Or a step nobody can describe in actor-action-resource terms, in which case that gap is the finding.

## Workflow

1. Write the claim exactly as it was made, verbatim, before restating anything.
2. Restate it in falsifiable form. Flag every one of actor, mechanism, magnitude, deadline that had to be supplied rather than found in the original.
3. Work backward from the endpoint. Number the steps so that step 1 is the endpoint and the highest number is closest to today, or number forward from today. Pick one and label the direction clearly.
4. For each step: actor, action, resource, tag, evidence or the absence of it.
5. Identify the weakest link, meaning the step with the largest gap between assumed and demonstrated.
6. Identify the load-bearing assumption, meaning the single thing that, if false, collapses the chain regardless of the other steps.
7. State what evidence would move you, in both directions. If nothing would, say so and note that the claim is currently unfalsifiable as stated.
8. Give a verdict from the fixed set below.

## Verdicts (use exactly these)

- **Mechanism sound, magnitude disputed.** Every step is observed or plausible. The disagreement is about how much and how fast.
- **Chain breaks at step N.** A specific step has no mechanism, no actor, or a resource requirement that does not exist.
- **Unfalsifiable as stated.** No observation would contradict the claim. It needs restatement before it can be evaluated at all.
- **Underdetermined, needs data.** The chain is coherent but one or more steps turn on a fact nobody in the room has. Name the fact and where it would come from.

## Output template (Mode B)

```markdown
# Five Whys (Prospective): [Short Claim Title]

**Date:** YYYY-MM-DD
**Claim source:** [who said it, where, when]
**Domain:** Market | Technology | Policy | Security | Health | Finance | Other

## Claim as Stated
[Verbatim, or as close as the source allows.]

## Restated in Falsifiable Form
[Actor] will cause [outcome] of [magnitude] by [date] via [mechanism].
*Supplied by me rather than found in the original: [list any of actor / mechanism / magnitude / deadline].*

## The Chain (endpoint backward to today)
| # | Step | Actor | Resource required | Tag | Evidence |
|---|------|-------|-------------------|-----|----------|
| 1 | [the endpoint] | | | | |
| 2 | [what must be true immediately before 1] | | | | |
| 3 | | | | | |
| 4 | | | | | |
| 5 | [closest to today] | | | | |

## Reverse Read (sanity check)
Today, therefore [5], therefore [4], therefore [3], therefore [2], therefore [1]. Holds / breaks at [N].

## Weakest Link
Step [N]. [The gap between what is assumed and what is demonstrated.]

## Load-Bearing Assumption
[The single thing that, if false, collapses the chain regardless of the other steps.]

## Conjunction
[N] steps. [Independent or correlated, and why.] Rough joint confidence: [x] percent.

## What Would Change My Mind
- Toward the claim: [specific observable]
- Against the claim: [specific observable]

## Verdict
[One of the four fixed verdicts, plus one sentence.]

## Notes
[Steps steelmanned on the claimant's behalf. Alternative chains to the same endpoint that were not explored.]
```

## Worked example B: a competitive threat claim

**Claim as stated:** "Their new product will take half our market within eighteen months."

**Restated in falsifiable form:** The competitor will capture 50 percent of our current revenue-weighted customer base within 18 months, via a lower-priced product with equivalent core functionality. *Supplied by me: the mechanism (price plus parity) and the definition of market share. Neither was in the original.*

**The chain, endpoint backward:**

| # | Step | Actor | Resource required | Tag | Evidence |
|---|------|-------|-------------------|-----|----------|
| 1 | Half our revenue-weighted customers are on their product | our customers | switching budget, migration time | Plausible | No barrier in principle. Nothing observed yet. |
| 2 | Half our customers complete a migration | customer engineering teams | 3 to 6 engineer-weeks each | Plausible | The mechanism exists. Our own onboarding data supplies the cost, and the cost is what strains the deadline. |
| 3 | Half our customers decide to switch | buyers | an internal business case | Plausible | The price delta is real and came up in two renewal calls this quarter. |
| 4 | Their product reaches parity on the two features that appear in 80 percent of our renewal calls | their engineering team | roughly 4 quarters at current headcount | Plausible | Both features are on their public roadmap. Neither has shipped. |
| 5 | They price materially below us and sustain it | their finance function | gross-margin tolerance or subsidy | Observed | Their published pricing, live today. |

**Reverse read:** Today they underprice, therefore they could reach parity in about four quarters, therefore buyers could build a case, therefore they decide to switch, therefore they migrate, therefore they are on the competitor's product. Holds. Every step has a mechanism.

**Weakest link:** Step 2. Not because the mechanism is missing, but because its cost was never counted. Our own data says 3 to 6 engineer-weeks per customer, and 18 months is roughly four quarters of parity work, plus a buying cycle, plus that migration, in sequence rather than in parallel.

**Load-bearing assumption:** That switching cost is negligible. If migration really is 3 to 6 engineer-weeks, the 18-month deadline fails on scheduling alone even if every other step lands perfectly.

**Conjunction:** Five steps, partly correlated, since parity drives both the decision and the migration. Per-step confidence within 18 months, roughly: step 5 at 95 percent, step 4 at 70, step 3 at 60, step 2 at 50, step 1 at 90 given step 2. Multiplied as if independent: about 18 percent. Treat that as the floor. Adjusting for the correlation between steps 4, 3, and 2 puts it nearer 25 percent. Rerun at 36 months and step 2 rises to about 80 percent, which moves the independent figure to roughly 30 percent and the adjusted one higher still.

**What would change my mind.** Toward: a published one-click migration tool from them, or three reference customers who switched in under two weeks. Against: our next four renewals citing migration cost as the reason for staying.

**Verdict:** Mechanism sound, magnitude disputed. Every step is observed or plausible, so the threat is real. The deadline is what fails. The argument worth having is about the date and the switching cost, not about whether they are a threat.

**Notes:** Steelmanned on the claimant's behalf: the mechanism (price plus parity) and the definition of market share, neither of which was in the original. Alternative chain not explored: the competitor acquiring our largest customer's parent company, which reaches the same endpoint without steps 2 through 4 and is a separate analysis.

---

## Scaling this into a practice

1. **Trigger.** Any recurring frustration, anything that has happened twice, anything draining energy without resolution. On the prospective side, any claim currently driving a decision, a budget, a hire, or a public position.
2. **Capture.** One line into whatever inbox already exists, tagged pending. One line is enough.
3. **Schedule.** Once a week, run the analysis on the top one to three captured items. Fifteen minutes each.
4. **Store.** Save each completed analysis in one place with a stable filename pattern such as `YYYY-MM-DD_short-title.md`. The value is in the collection, not the individual file.
5. **Review.** Quarterly, scan for repeats. Root causes that recur across unrelated analyses point to a deeper structural issue worth its own project. Claims that keep failing at the same kind of step tell you something about the source, not only about the claim.
6. **Cross-link.** Tag related notes, tickets, and entries. The pattern only emerges when they are visible together.
7. **Publish the good ones.** A recurring root cause, or a claim that broke at an interesting step, usually makes a better essay than an opinion does.

## Common pitfalls

- **The Five Blames trap** (Eric Ries, *The Lean Startup*). Frustrated people turn the method into finger pointing. If the chain ends at a person, it is not finished. The Mode B equivalent is ending at motive.
- **Deduction instead of investigation.** Listing five plausible causes at once is not Five Whys. Each link must be the actual cause of, or precondition for, the previous link, supported by evidence or direct observation.
- **Premature satisfaction.** The first reasonable explanation is rarely the root. Push past comfort.
- **Treating noise as signal.** Apply this to recurring problems and gaps from standard, not to one-off random events.
- **Skill dependence.** Two people running Five Whys on the same problem can reach different answers. Build the muscle by doing it consistently, reviewing chains critically, and pairing with someone who pushes back when the logic is weak.
- **Shallow stop.** Art Smalley, formerly of Toyota, noted that Ohno used five because that is how many it took in *that* case. Some chains need three. Some need eight. Stop at the actionable structural cause, not at the fifth question.
- **Gotcha mode.** In Mode B the goal is to find where the chain is load-bearing, not to score points. A chain that survives the drill has been strengthened, not defeated. Treat that outcome as legitimate and common.

## When not to use this, and what to use instead

- **Complex problems with multiple interacting causes.** Use a Fishbone / Ishikawa diagram or FMEA, optionally with Five Whys on each branch.
- **Statistical or random variation.** Use Pareto analysis or statistical process control, not Five Whys.
- **No data yet.** Gather data first. Run the method on patterns, not on speculation.
- **A claim nobody is acting on.** Prospective mode costs real effort. Spend it on claims that are moving money, policy, or careers.

## Anchor quote

"Observe the production floor without preconceptions. Ask 'why' five times about every matter."
Taiichi Ohno, *Toyota Production System: Beyond Large-Scale Production* (1988)
