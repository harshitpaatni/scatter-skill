# Scatter — A Claude Code Skill

Stop letting AI brainstorm collapse to the obvious. Scatter takes any problem and runs it through 6 agents that geometrically prevent convergence — each operates in a different concept-space — then hands you a deliberately unfinished provocation set, not a solution.

Inspired by the convergence of [swarm intelligence](https://en.wikipedia.org/wiki/Swarm_intelligence) and [information-theoretic entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)). Architecturally adjacent to [Karpathy's LLM Council](https://x.com/karpathy/status/1962263486196867115), but built for the opposite phase of thinking — the generative origin, not the convergent end.

---

## Status

This is a working experiment, not a maintained library. The architecture is real; the implementation is not hardened. Expect rough edges. Fork it, break it, improve it.

---

## The Problem

Ask Claude to brainstorm and you get five plausible variations of the most obvious answer. That's not Claude being lazy — it's how language models work. They're trained to produce the response that looks like a high-quality version of what most people have written about similar prompts. The conventional answer is the default.

For brainstorming, that's exactly wrong. The conventional answer is the one you didn't need help finding.

## How Scatter Is Different

The LLM Council pressure-tests decisions you've already formed. Scatter is for the phase before that — when you don't yet know what the right question is.

When you say **"scatter this"**, the skill:

1. **Frames your question** with context from your workspace
2. **Detects your domain type** (technical R&D, business, creative, personal) so agents respect technical reality
3. **Runs 5 Pass 1 agents in parallel**, each applying a different geometric transformation:
   - **Scale Shifter** — instantiates the problem at 1000x and 1/1000th
   - **Domain Transplant** — imports the structural cousin from a field with no cross-pollination history with yours
   - **Constraint Inverter** — inverts every assumed constraint, reasons from the inversion as reality
   - **Substrate Shifter** — reformulates the problem in different mediums
   - **Failure Forensicist** — assumes you failed and reasons backward
4. **Cross-pollinates 3 specific pairings** to surface emergent ideas neither parent could generate alone
5. **Runs an Adjacent Possible agent** that finds under-explored *feasible* moves in the newly-opened space
6. **Synthesizes for entropy preservation, not consensus** — reframings, provocations, under-explored moves, and explicitly-named territory the swarm did not touch
7. **Generates an HTML report + markdown transcript**

The output has no recommendations, no rankings, no "next steps." If you want a decision, run the result through the LLM Council. Scatter widens; Council converges.

---

## Install

### Option 1 — Git clone (recommended)

```bash
git clone https://github.com/[your-username]/scatter-skill ~/.claude/skills/scatter
```

Restart Claude Code.

### Option 2 — Manual

1. Create folder `~/.claude/skills/scatter/`
2. Copy `SKILL.md` into it
3. Restart Claude Code

---

## Use

Trigger phrases:
- `scatter this`
- `scatter`
- `widen this`
- `open this up`
- `go wide on`

**Example:**
> scatter this: I'm working on lipid nanoparticle delivery for mRNA therapeutics. We're trying to improve targeting to non-liver tissues. The standard moves (charge tuning, antibody conjugation, novel ionizable lipids) are all crowded. Where should I look that no one else is looking?

You'll get an HTML report that opens automatically and a full markdown transcript saved alongside it.

---

## When to Use Scatter

**Good scatter questions:**
- "I'm at the start of thinking about X — help me widen the field before I converge."
- "We're brainstorming next year's strategy and I want to make sure we don't lock in obvious moves."
- "This problem feels intractable. Help me see it differently."
- "Beyond the standard approaches in my field, where should I look?"

**Skip scatter for:**
- Decisions with formed options (use [llm-council](https://github.com/tenfoldmarc/llm-council-skill) instead)
- Refinement of existing ideas
- Requests for recommendations
- Anything where you want efficiency over exploration

Scatter produces uncomfortable output by design. If your problem feels smaller and clearer afterward, scatter failed. If it feels bigger and stranger but you can see new dimensions, scatter worked.

---

## Credit

- Conceptual foundations: swarm intelligence (Bonabeau, Kennedy & Eberhart) and information-theoretic entropy (Shannon, Jaynes, Aguirre)
- Architectural inspiration: [Andrej Karpathy's LLM Council](https://x.com/karpathy/status/1962263486196867115) and the [Claude Code skill adaptation](https://github.com/tenfoldmarc/llm-council-skill) by [@tenfoldmarc](https://instagram.com/tenfoldmarc)

---

## License

MIT — do whatever you want with it.
