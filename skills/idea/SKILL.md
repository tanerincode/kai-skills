---
name: idea
description: Sir has an idea and asks what Kai thinks or whether to do it. Use when he says "I have an idea about X", "what do you think of Y", "should we build Z". Kai spars on it, arranges the research through agents, and comes back with a verdict, the evidence, and the smallest version worth building.
---

# Idea: from "what do you think" to a verdict with evidence

Sir says "I have an idea about X, should we do it?". Kai does not answer from feeling. Kai shapes it, sends researchers, and returns a verdict.

## Steps

1. **Spar first, in six lines.** What the idea is in one sentence, who would pay, what is strong, what is weak, what Kai would cut. Say it to Sir at once so he can correct the framing while the research runs. Save it as `ideas/<slug>.md` with the date.
2. **Arrange the research, in parallel, through the Bridge.** Three `researcher` agents by `bin/kai-agent spawn kai researcher --name idea-<slug>-<angle>`, each with one brief in `projects/kai/briefs/idea-<slug>-<angle>.md`:
   - **market**: is there demand, how big, who buys today, what they pay (the `market-research` skill's method: read the actual sites and pricing pages, separate verified from inferred).
   - **competitors**: the five closest products, their pricing, their gaps, what reviews complain about.
   - **feasibility**: smallest version, stack, what costs money (APIs, hosting, licences), time to a demo, the one risk that could kill it.
   Each writes `research/<yyyy-mm-dd>-<slug>-<angle>.md` with sources as links and a one-line conclusion at the top, then reports to Kai in one line. Retire them when done.
3. **Verdict.** Read the three files yourself. Write the verdict into `ideas/<slug>.md`: go, no, or pivot; who pays and how much; the smallest version worth building; cost to a demo; the evidence that decided it; what was not verified. Store the one-line conclusion in Synatyx (`project: "kai"`, L3).
4. **Tell Sir** in under ten lines: verdict first, the three strongest facts with links, the smallest version, the cost. Disagree when the evidence disagrees with him.
5. **If go**, offer once: "Say build and you get a demo" (the `build` skill). Nothing is built, bought or published before his word.

## Rules

- Research is agents' work, through the Bridge; Kai reads and judges. Kai searches itself only for the sparring step.
- Verified beats inferred. A number without a source is marked as an estimate.
- Ideas are never dropped silently: a "no" is written down with its reasons, so it is not re-researched next month.
