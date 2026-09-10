# Five Whys

An agent skill that runs Taiichi Ohno's Five Whys in **both directions**.

Backward, from a failure that already happened, to a root cause you can actually fix. That is the version everyone knows, and it comes from the Toyota Production System.

Forward, from a claim about the future, to the intermediate steps required to get there. That version is barely taught, and it is the one that turns an unarguable prediction into a falsifiable one.

Works with [Claude Code](https://claude.com/claude-code) and any agent that reads `SKILL.md` files. The method itself needs no tooling at all, so the file is also just a usable document.

---

## Why the second direction matters

Large claims survive because nobody makes the claimant walk the chain out loud.

You cannot get to a spectacular endpoint in one step. There are intermediate steps, and each one has an actor, a mechanism, a resource cost, and a place where it can fail. Asking for those steps, one at a time, does three things at once:

- It separates people who worked out the mechanism from people who absorbed a conclusion.
- It locates the exact step where the argument stops being mechanical and starts being atmosphere.
- It converts an unarguable claim into a falsifiable one, which is the only form a claim can usefully be argued about.

The mode is neutral about whether the claim is right. Plenty of claims survive the drill intact and come out stronger. That is a real result, not a failure of the method.

It applies to any high-stakes forecast. A competitor will take half the market. This regulation will kill the industry. This technology will erase a job category. This valuation is justified. This system will be breached along this exact path. This policy will cause that collapse.

## The two modes

| | Mode A: Retrospective | Mode B: Prospective |
|---|---|---|
| Input | A failure that already happened, usually more than once | A claim about what will happen |
| Question form | "Why did that happen?" | "What has to be true immediately before that?" |
| Direction | Effect back to cause | Endpoint back to preconditions |
| Catches | Fixing symptoms, blaming people | Hand-waving, skipped steps, unfalsifiable claims |
| Output | Root cause plus countermeasure | Weakest link plus load-bearing assumption |
| Ends at | A process you can change | A step already happening today, or a step nobody can describe |

Mode B produces a fixed verdict, one of four:

- **Mechanism sound, magnitude disputed.** Every step is observed or plausible. The fight is about how much and how fast.
- **Chain breaks at step N.** A specific step has no mechanism, no actor, or a resource requirement that does not exist.
- **Unfalsifiable as stated.** No observation would contradict the claim. It needs restatement before it can be evaluated at all.
- **Underdetermined, needs data.** The chain is coherent, but a step turns on a fact nobody in the room has.

## Rules that keep it honest

Both modes share five, and Mode B adds three of its own. The two that do the most work:

**Never end at a person.** "Human error", "they dropped the ball", "I am lazy" are symptoms. Push to the process, environment, incentive, or physical constraint that allowed it.

**Never end at a motive.** The Mode B version of the same rule. "They want it to happen" and "they are incentivized to say it" may both be true, and neither is a step in the chain. Motive is not mechanism.

Plus: steelman before you cut. If a step is missing, supply the strongest version yourself and evaluate that. Rejecting a claim because its holder explained it badly is not analysis.

## Install

**As a Claude Code plugin:**

```
/plugin marketplace add aliihafezii/five-whys
/plugin install five-whys
```

**As a plain skill,** for Claude Code or anything else that reads skill files:

```bash
git clone https://github.com/aliihafezii/five-whys.git
cp -r five-whys/skills/five-whys-root-cause ~/.claude/skills/
```

**As a document:** open [`skills/five-whys-root-cause/SKILL.md`](skills/five-whys-root-cause/SKILL.md) and use it by hand. It contains both protocols, both output templates, three worked examples, and the pitfalls list. No agent required.

## Use

Once installed, it triggers on its own when you describe a recurring problem or a big claim. Or invoke it directly:

```
Run five whys on this: the nightly batch job has failed 3 of the last 10 runs.

Drill into this claim: their new product takes half our market in 18 months.

Where does this argument break? [paste forecast]
```

## Credits

The method is Sakichi Toyoda's, formalized by Taiichi Ohno at Toyota and published in *Toyota Production System: Beyond Large-Scale Production* (1988). The pitfalls section draws on Eric Ries on the "Five Blames" trap and Art Smalley on why five is not a magic number.

The prospective mode exists because of a public suggestion from [Bill Gurley](https://x.com/bgurley) in September 2026, that interviewers should use the Five Whys to make people asserting catastrophic endpoints walk through the intermediate steps required to reach them. That reframing, running the method forward against a claim rather than backward against a defect, is the part that turned into Mode B here.

## License

MIT. See [LICENSE](LICENSE).
