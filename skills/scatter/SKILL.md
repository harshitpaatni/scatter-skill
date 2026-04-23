---
name: scatter
description: "Widen a problem before converging. Takes any question and runs it through 5 transformation agents that each move the problem into a different concept-space (geometrically preventing convergence), then a 6th agent that finds under-explored feasible moves in the opened space. Output is deliberately unfinished — reframings, provocations, and named unexplored territory. No recommendations, no rankings. MANDATORY TRIGGERS: 'scatter this', 'scatter', 'widen this', 'scatter the problem', 'open this up', 'go wide on'. STRONG TRIGGERS (when combined with a problem at the generative origin of thinking): 'help me brainstorm', 'I'm thinking about X', 'where should I start with', 'I want to explore', 'I'm not sure how to think about'. Do NOT trigger on: decisions with formed options (use llm-council instead), refinement of existing ideas, requests for recommendations, factual questions, or any context where the user wants efficiency over exploration. DO trigger when the user is at the start of thinking and wants to make sure they don't converge prematurely on the obvious."
---

# Scatter

You ask AI to brainstorm, you get five variations of the most plausible answer. Plausible is the default failure mode of language models — they're trained to produce the response that looks most like a high-quality version of what others have written. For brainstorming, that's exactly wrong. The conventional answer is the one you didn't need help finding.

Scatter does the opposite. It takes your problem, runs it through 5 agents that each apply a different geometric transformation to move the problem into a different concept-space, then a 6th agent that finds the under-explored feasible moves in the space the others opened up. The agents are designed so they *cannot* converge on the same answer — they're not different perspectives on the same problem, they're reasoning about deliberately-transformed versions of it.

The output is a provocation set, not a solution set. Reframings of what the problem even is. Pointed questions you haven't answered. Explicitly-named territory the swarm didn't touch. There is no recommendation. There is no "do this first." If you want a decision pressure-tested, run it through the LLM Council. Scatter is for the phase before that — when you're at the generative origin and you want to make sure you don't converge prematurely on the obvious.

This is adapted from the convergent ideas of swarm intelligence (decentralized agents in different positions producing emergent insight) and information-theoretic entropy (uncertainty as fuel, the observer's distinguishing lens determines what counts as signal, maximum entropy as a discipline against premature assumption).

---

## when to run scatter

Scatter is for the start of thinking, not the end of it.

Good scatter questions:
- "I'm trying to figure out how to improve customer retention but I think I'm stuck in obvious moves."
- "We're a biotech working on tissue-targeted delivery. Beyond the standard approaches, where should I look?"
- "I want to write a book about X but I'm not sure what angle is actually interesting."
- "Our team is brainstorming next year's strategy and I want to widen the field before we converge."
- "I have a problem that feels intractable. Help me see it differently."

Bad scatter questions:
- "Should I launch product A or product B?" (decision with formed options — use llm-council)
- "Improve this paragraph." (refinement, not exploration)
- "What's the best framework for X?" (asking for an answer, not a wider field)
- "Give me five marketing ideas for my SaaS." (the user wants ideas, scatter gives provocations — mismatch)
- Anything where the user has expressed time pressure or wants efficiency

The skill produces uncomfortable output by design. If the user closes the session feeling like the problem got smaller and clearer, scatter failed. If they close it feeling like the problem got bigger and stranger but they can see new dimensions, scatter worked.

---

## the six agents

Five Pass 1 agents apply geometric transformations in parallel, each operating in a different concept-space. One Pass 2 agent integrates the opened space and finds under-explored feasible moves.

### Pass 1 (parallel, no inter-agent contamination)

#### 1. The Scale Shifter
**Transformation:** Instantiate the problem at three scales — 1000x larger, 1/1000th smaller, and at unit scale (one person, one transaction, one moment). Reason from each instance separately.

**Forbidden:** Treating "scale" as just "more customers" or "bigger revenue." The transformation must change the *nature* of the problem, not just its size.

**Output requirements:** Must include one specific dynamic that exists at 1000x but not now; one capability that becomes irrelevant at 1000x; one capability that becomes irrelevant at 1/1000th. If you cannot produce these specifics, say so explicitly rather than substituting generic advice.

**Entropy enforcement:** Medium. After producing initial output, check: would a typical strategy consultant produce this same scaling analysis? If yes, push further — find the scale-dependent dynamic that only appears at non-current scales and that the user's current strategy is not accounting for.

#### 2. The Domain Transplant
**Transformation:** Identify the deep structure of the user's problem (what is being optimized, what is being traded off, what is being signaled, what is being coordinated). Locate fields where this structural problem has been studied for decades. Import their solutions, vocabulary, and known failure modes.

**Forbidden:** Surface metaphors. "Your business is like a garden" is forbidden. The transplant must be structural — the other field must have *actually solved* the structural analog.

**Entropy enforcement:** STRONG. Your output is successful only if the field you import from is one the user could not have plausibly imported from themselves. If your structural cousin field is one the user's industry already routinely borrows from, you have failed. Reject your first-pass field if it has any existing cross-pollination history with the user's domain. Push to fields with no such history. Examples of high-entropy domain transplants: importing mesh-network routing into drug delivery, importing sediment transport into customer flow analysis, importing honeypot architecture into market positioning. The test: would the user say "I would never have thought to look there"?

#### 3. The Constraint Inverter
**Transformation:** Catalog every stated and implied constraint the user is operating under (budget, time, audience, channel, format, team size, regulatory, technical). Invert each one — not relax it, *invert* it. Reason about what the problem becomes when the constraint runs the opposite direction.

**Forbidden:** Wishful inversion ("infinite budget = do everything"). The inversion must produce a *different problem*, not a fantasy. Reason as if the inverted constraint is the actual operating condition.

**Output requirements:** Reveal which constraints are load-bearing (the inversion breaks everything) and which are assumed but actually optional (the inversion reveals a path the user couldn't see while accepting the constraint).

**Entropy enforcement:** Light. The transformation rule itself produces unconventional output by construction. Skip the self-rejection step unless output is suspiciously short or generic.

#### 4. The Substrate Shifter
**Transformation:** Identify what the problem is currently *made of* (software, service, content, physical product, relationship, ritual, financial instrument, biological process). Reformulate the problem in three other substrates. What does the problem become when its medium changes?

**Forbidden:** Substrate shifts that are just rebranding. Shifting from "software" to "app" is not a substrate shift. Shifting from "software product" to "physical object on a desk" or "morning ritual" or "ongoing relationship with one person" is.

**Entropy enforcement:** STRONG. Your output is successful only if the new substrate produces a *question the user has not framed before*. If your substrate shift produces a feature comparison or a "pros and cons of different mediums" answer, you have failed. The test: does the substrate shift expose what's substrate-dependent (only works because it's currently this medium) vs. substrate-independent (would work in any medium) about the user's problem?

#### 5. The Failure Forensicist
**Transformation:** Assume the user's eventual best solution to this problem failed catastrophically. Reason backward to why. What would they have wanted to know early?

**Forbidden:** Generic failure modes from the user's industry's standard development checklist (those are already protected against). The failure mode must be one the user is currently *not* protecting against.

**Output requirements:** At least one failure mode that inverts the user's assumed direction (e.g., the precision they're trying to increase becomes the failure vector; the trust they're trying to build becomes the liability).

**Entropy enforcement:** Light-to-medium. The transformation rule pushes toward unconventional output, but check: are the failure modes ones the field's standard development practice already addresses? If yes, push further.

### Cross-pollination round (selective)

After Pass 1 completes, run cross-pollination only for these specific pairings (chosen because their transformations productively combine):

1. **Domain Transplant + Constraint Inverter:** What does the structural cousin field's solution look like when applied to the user's *inverted* constraints?
2. **Substrate Shifter + Scale Shifter:** What does the problem become when you change *both* its medium and its size?
3. **Failure Forensicist + Domain Transplant:** What failure modes does the structural cousin field know about that the user's field hasn't encountered yet?

Each cross-pollination agent receives the two parent outputs and the original framed question. Instruction: "Your task is not to combine these two outputs. Your task is to identify the question or possibility that *neither output could have generated alone* but that becomes visible when they're held together. If your output could have been generated by either parent independently, you have failed."

Skip cross-pollination for Constraint Inverter alone and Failure Forensicist alone — their outputs are sharp enough on their own that forced collisions add cost without proportional value.

### Pass 2 (integrative)

#### 6. The Adjacent Possible
**Operates on:** Combined output of all 5 Pass 1 agents + all 3 cross-pollinations + original framed question.

**Transformation:** Map the *newly-opened* solution space (everything the other agents and cross-pollinations surfaced). Identify the moves within that space that are (a) currently feasible with existing tools and capabilities, and (b) not already being pursued by anyone in the user's stated competitive set.

**Forbidden:** Both the obvious (anything inside the conventional solution space the user already knew about) and the impossible (anything requiring capabilities or contexts that don't yet exist). The agent must operate exactly at the edge of the currently feasible — the moves that *could* be made today but require someone to make a non-obvious connection.

**Entropy enforcement:** STRONG. Your output is successful only if the moves you identify are feasible *and* not currently being pursued. If your move is in active research or in published competitor strategy, you have failed. Push to combinations of upstream agent outputs that no one has put together yet. The test: could the user act on this move starting Monday with their existing capabilities, AND is there a reason no one is currently doing it (which suggests an under-explored opportunity)?

---

## how a scatter session works

### step 1: frame the question (with context enrichment)

When the user invokes scatter, do two things before framing:

**A. Scan for context.** Quickly check for:
- `CLAUDE.md` or `claude.md` in the project root
- Any `memory/` folder with relevant context
- Files the user explicitly referenced
- Recent scatter transcripts in this folder (to avoid re-scattering the same problem)

Don't spend more than 30 seconds. Looking for the 1-2 files that would let agents respond to the user's *actual* situation rather than a generic version of it.

**B. Frame the question.** Reformulate the user's question as a clear, neutral prompt that all agents will receive. Include:
1. The core problem or question
2. Key context from the user's message and workspace
3. The user's stated or implied domain (so agents can apply technical-respect appropriately)
4. What's currently *not* being asked (the obvious framing the user is trying to move past, if discernible)

If the question is too vague, ask one clarifying question. Just one. Then proceed.

**Detect domain type.** Before spawning agents, determine: is this a technical/R&D problem, a strategic/business problem, a creative/conceptual problem, or a personal/life problem? Pass this domain type to each agent so they can apply appropriate technical-respect. For technical problems, agents must respect the constraints of the user's domain and ask questions where their transformation requires technical context they don't have.

### step 2: spawn Pass 1 agents (5 in parallel)

Spawn all 5 Pass 1 agents simultaneously. Each gets:
1. Their agent identity, transformation rule, forbidden moves, output requirements, and entropy enforcement level (from the descriptions above)
2. The framed question and detected domain type
3. Instruction to produce 200-400 words. Substantive enough to be useful, focused enough to be sharp.

**Pass 1 agent prompt template:**

```
You are [Agent Name] in a scatter session.
Your transformation rule: [from agent description]
What you are forbidden from doing: [from agent description]
Your output requirements: [from agent description]
Your entropy enforcement: [from agent description]

The user's problem (framed):
[framed question]

Domain type: [technical R&D / strategic-business / creative-conceptual / personal]
If technical: respect the constraints of the user's domain. Where your transformation requires technical context you don't have, ask a pointed question rather than producing a naive proposal.

Apply your transformation. Produce 200-400 words. Be specific. Don't hedge. Don't try to be balanced — other agents are covering other dimensions. Lean fully into your transformation.

If your entropy enforcement is STRONG: after producing your initial output, check it against your entropy criterion. If it fails, reject and regenerate. Show only the final output.
```

### step 3: cross-pollination round (3 chosen pairings in parallel)

After all Pass 1 outputs complete, spawn 3 cross-pollination agents in parallel. Each receives the two parent outputs and the framed question.

**Cross-pollination prompt template:**

```
You are running cross-pollination [Pairing Name] in a scatter session.

Parent output A — [Agent A Name]:
[Agent A output]

Parent output B — [Agent B Name]:
[Agent B output]

Original framed question:
[framed question]

Your task is not to combine these outputs or summarize them. Find the question or possibility that neither parent could have generated alone — something that only becomes visible when these two transformations are held together.

If your output could have been generated by either parent independently, you have failed.

Produce 150-300 words. Name the specific thing that appears only at the intersection. Don't hedge.
```

### step 4: spawn Adjacent Possible agent (Pass 2)

After cross-pollination completes, spawn the Adjacent Possible agent with all outputs assembled.

**Adjacent Possible prompt template:**

```
You are The Adjacent Possible in a scatter session.

Your transformation: Map the boundary of the space the other agents opened. Find moves that are (a) feasible with existing capabilities and (b) not currently being pursued in the user's competitive set. Operate exactly at the edge of currently-feasible — not inside the conventional space, not in speculation.

Your entropy enforcement is STRONG. After identifying candidate moves, check each one: is it in active research or published competitor strategy? If yes, reject it. Push to combinations that no one has put together yet.

What you are forbidden from doing: summarizing other agents' outputs, recommending which move to pursue, speculating about capabilities that don't exist yet.

Original framed question:
[framed question]

Domain type: [domain type]

Pass 1 outputs:
Scale Shifter: [output]
Domain Transplant: [output]
Constraint Inverter: [output]
Substrate Shifter: [output]
Failure Forensicist: [output]

Cross-pollination outputs:
Domain Transplant × Constraint Inverter: [output]
Substrate Shifter × Scale Shifter: [output]
Failure Forensicist × Domain Transplant: [output]

Identify 4-6 named moves at the edge of this space. For each: name it (bold), state why it's feasible now (one sentence), state why it's under-explored (one sentence). Produce 250-400 words total.
```

### step 5: write output files

Collect all outputs. Do not summarize, rank, or conclude.

Write two files to the current working directory using the timestamp `YYYYMMDD-HHMM`:

**Markdown transcript:** `scatter-YYYYMMDD-HHMM.md`

```
# Scatter — [framed question]
[timestamp]

## Framed Question
[framed question]
Domain: [domain type]

## Pass 1

### Scale Shifter
[output]

### Domain Transplant
[output]

### Constraint Inverter
[output]

### Substrate Shifter
[output]

### Failure Forensicist
[output]

## Cross-Pollination

### Domain Transplant × Constraint Inverter
[output]

### Substrate Shifter × Scale Shifter
[output]

### Failure Forensicist × Domain Transplant
[output]

## Adjacent Possible
[output]
```

**HTML report:** `scatter-YYYYMMDD-HHMM.html`

Generate the HTML inline using this structure. Entropy-order the sections: STRONG-enforcement agents first (Domain Transplant, Substrate Shifter, Adjacent Possible), then medium-enforcement (Scale Shifter, Failure Forensicist), then light-enforcement (Constraint Inverter). Cross-pollination outputs appear as bridge sections between their parent pairs.

Use this HTML template:

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Scatter — [framed question truncated to 60 chars]</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { background: #0a0a0a; color: #e0e0e0; font-family: monospace; font-size: 14px; line-height: 1.7; padding: 2rem; max-width: 860px; margin: 0 auto; }
  h1 { font-size: 1.1rem; color: #fff; border-bottom: 1px solid #333; padding-bottom: 0.5rem; margin-bottom: 0.3rem; }
  .meta { color: #555; font-size: 0.85rem; margin-bottom: 2.5rem; }
  .section { margin-bottom: 2.5rem; border-left: 2px solid #2a2a2a; padding-left: 1.2rem; }
  .section.high-entropy { border-left-color: #c0392b; }
  .section.bridge { border-left-color: #2980b9; background: #0d1117; padding: 1rem 1.2rem; }
  .section.adjacent { border-left-color: #27ae60; }
  .agent-name { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.1em; color: #666; margin-bottom: 0.4rem; }
  .section.high-entropy .agent-name { color: #c0392b; }
  .section.bridge .agent-name { color: #2980b9; }
  .section.adjacent .agent-name { color: #27ae60; }
  h2 { font-size: 1rem; color: #ccc; margin-bottom: 0.8rem; }
  p { margin-bottom: 0.8rem; color: #bbb; }
  strong { color: #e0e0e0; }
  .footer { margin-top: 3rem; color: #333; font-size: 0.8rem; border-top: 1px solid #1a1a1a; padding-top: 1rem; }
</style>
</head>
<body>
<h1>Scatter</h1>
<div class="meta">[framed question] · [timestamp]</div>

<!-- STRONG entropy agents first -->
<div class="section high-entropy">
  <div class="agent-name">Domain Transplant · high entropy</div>
  <div>[domain transplant output as HTML paragraphs]</div>
</div>

<div class="section high-entropy">
  <div class="agent-name">Substrate Shifter · high entropy</div>
  <div>[substrate shifter output as HTML paragraphs]</div>
</div>

<!-- Bridge: Domain Transplant × Constraint Inverter -->
<div class="section bridge">
  <div class="agent-name">Cross-pollination · Domain Transplant × Constraint Inverter</div>
  <div>[cross-pollination output as HTML paragraphs]</div>
</div>

<!-- Medium entropy agents -->
<div class="section">
  <div class="agent-name">Scale Shifter · medium entropy</div>
  <div>[scale shifter output as HTML paragraphs]</div>
</div>

<!-- Bridge: Substrate Shifter × Scale Shifter -->
<div class="section bridge">
  <div class="agent-name">Cross-pollination · Substrate Shifter × Scale Shifter</div>
  <div>[cross-pollination output as HTML paragraphs]</div>
</div>

<div class="section">
  <div class="agent-name">Failure Forensicist · medium entropy</div>
  <div>[failure forensicist output as HTML paragraphs]</div>
</div>

<!-- Bridge: Failure Forensicist × Domain Transplant -->
<div class="section bridge">
  <div class="agent-name">Cross-pollination · Failure Forensicist × Domain Transplant</div>
  <div>[cross-pollination output as HTML paragraphs]</div>
</div>

<!-- Light entropy -->
<div class="section">
  <div class="agent-name">Constraint Inverter · light entropy</div>
  <div>[constraint inverter output as HTML paragraphs]</div>
</div>

<!-- Adjacent Possible last — always -->
<div class="section adjacent">
  <div class="agent-name">Adjacent Possible · Pass 2</div>
  <div>[adjacent possible output as HTML paragraphs]</div>
</div>

<div class="footer">scatter · no recommendations · no rankings · [timestamp]</div>
</body>
</html>
```

After writing both files, tell the user the file paths. Do not summarize the outputs. Do not name a "best" idea. Do not suggest what to do next.
