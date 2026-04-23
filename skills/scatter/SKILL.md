---
name: scatter
description: "Widen a problem before converging. Takes any question and runs it through 5 transformation agents that each move the problem into a different concept-space (geometrically preventing convergence), then a 6th agent that finds under-explored feasible moves in the opened space. Output is deliberately unfinished — reframings, provocations, and named unexplored territory. No recommendations, no rankings. Before running the swarm, asks which report format you want: HTML, Word (.docx), Markdown, or transcript only. MANDATORY TRIGGERS: 'scatter this', 'scatter', 'widen this', 'scatter the problem', 'open this up', 'go wide on'. STRONG TRIGGERS (when combined with a problem at the generative origin of thinking): 'help me brainstorm', 'I'm thinking about X', 'where should I start with', 'I want to explore', 'I'm not sure how to think about'. Do NOT trigger on: decisions with formed options (use llm-council instead), refinement of existing ideas, requests for recommendations, factual questions, or any context where the user wants efficiency over exploration. DO trigger when the user is at the start of thinking and wants to make sure they don't converge prematurely on the obvious."
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

**C. Ask for output format.** After framing the question and detecting domain type, present this prompt to the user before proceeding:

> Before I run the swarm, what format would you like the report in?
>
> 1. HTML (visual report, opens in browser) — default
> 2. Word document (.docx, easy to share)
> 3. Markdown (.md, plain text)
> 4. Transcript only (skip the report)
>
> Reply with a number or format name. The full transcript is saved either way.

Wait for the user's response before proceeding to Step 2.

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
---
[framed question]
---

Domain type: [technical R&D / strategic-business / creative-conceptual / personal]

If technical: respect the constraints of the user's domain. Where your transformation requires technical context you don't have, ask a pointed question rather than producing a naive proposal.

Apply your transformation. Produce 200-400 words. Be specific. Don't hedge. Don't try to be balanced — other agents are covering other dimensions. Lean fully into your transformation.

If your entropy enforcement is STRONG: after producing your initial output, check it against your entropy criterion. If it fails, reject and regenerate. Show only the final output.
```

### step 3: cross-pollination round (3 chosen pairings in parallel)

After all Pass 1 outputs complete, spawn 3 cross-pollination agents in parallel. Each receives the two parent outputs and the framed question.

**Cross-pollination prompt template:**

```
You are running a cross-pollination between two scatter agents.

Parent A ([Agent Name]):
[output]

Parent B ([Agent Name]):
[output]

The user's original problem:
---
[framed question]
---

Your task is NOT to summarize or combine these two outputs.

Your task is to identify the question, possibility, or move that neither parent could have generated alone but becomes visible when both are held together.

If your output could have been produced by either parent independently, you have failed. Push for emergence — what's in the intersection that wasn't in either source?

Produce 150-250 words. One clear emergent question or possibility, then brief reasoning for why it required both parents.
```

### step 4: spawn Pass 2 agent (Adjacent Possible)

After Pass 1 and cross-pollination complete, spawn the Adjacent Possible agent with all upstream material.

**Pass 2 prompt template:**

```
You are the Adjacent Possible agent in a scatter session.

The user's problem (framed):
---
[framed question]
---

Domain type: [type]

Five other agents have already explored this problem from different transformations. Three cross-pollinations between them have surfaced emergent material. Here is everything they produced:

PASS 1 OUTPUTS:
[all 5 Pass 1 outputs, labeled by agent]

CROSS-POLLINATIONS:
[all 3 cross-pollinations, labeled by parent pair]

Your job is to find the under-explored feasible moves in the space these agents have opened up.

Your output is successful only if the moves you identify are:
(a) currently feasible with existing tools and capabilities
(b) not already being actively pursued by anyone in the user's stated competitive set
(c) emergent from the upstream material (not just restating one agent's output)

If the move is already in active research or in published strategy in the user's field, reject it and find another. Push to combinations of upstream outputs that no one has put together yet.

Produce 200-400 words. Identify 2-3 specific feasible-but-unpursued moves with brief reasoning for why each is feasible AND why it's not currently being pursued (which is what makes it under-explored).
```

### step 5: synthesis (entropy-preserving, NOT consensus-finding)

This is the final agent. Its role is structurally inverted from a normal synthesizer — it is *not* trying to find consensus or produce a recommendation. It is preserving and ordering the highest-entropy material from the swarm.

**Synthesizer prompt template:**

```
You are the synthesizer for a scatter session. Your role is the opposite of a normal synthesis: you are preserving uncertainty, not resolving it.

The user's problem:
---
[framed question]
---

All upstream material:
[Pass 1 outputs, cross-pollinations, Pass 2 output]

Produce a synthesis using this exact structure:

## Reframings
The most distinct ways the agents reformulated what the problem actually is. Each reframing should be one paragraph. Order by how far the reframing moves the user from their original framing — most destabilizing first. Aim for 3-5 reframings.

## Provocations
Pointed questions the swarm surfaced that the user has not answered. These should be sharp and specific — not "have you considered..." but pointed challenges to the user's assumed framing. Aim for 4-6 provocations. Order by entropy — the most uncomfortable provocations first.

## Under-explored Feasible Moves
The moves the Adjacent Possible agent surfaced that are doable now but not being pursued. Present each with the brief reasoning for feasibility and the reasoning for why it's currently unpursued. Aim for 2-3 moves.

## What the Swarm Did Not Touch
Honestly name the dimensions of the user's problem that none of the agents addressed. This is high-entropy content because it's what's still unknown after the entire exercise. Be specific — don't say "long-term implications," say "what happens to your strategy if [specific unaddressed factor] turns out to matter."

## Where the Swarm Tried to Converge
If multiple agents accidentally produced similar outputs (despite their transformations being orthogonal), name this explicitly. Convergence in scatter is a warning sign — it usually means the swarm collapsed toward conventional thinking on that dimension. Flag it as low-information signal, not consensus.

EXPLICIT PROHIBITIONS:
- Do not produce a recommendation
- Do not rank or score the options
- Do not suggest a "next step" or "first move"
- Do not attempt to balance perspectives — preserve the sharpest disagreements
- Do not soften provocations to make them more palatable

The user wants to leave this session with a wider, sharper, more uncomfortable problem space than they started with. Your job is to deliver that.
```

### step 6: generate the scatter report

After synthesis, generate the report artifact based on the format the user chose in Step 1. All formats share the same content structure: synthesis prominent at the top, agent outputs as an appendix (collapsible or clearly delimited).

**Content structure (all formats):**
1. **The framed question** at the top
2. **The synthesis** prominently displayed (this is what most users will read)
3. **Collapsible or delimited sections** for each Pass 1 agent's full output, each cross-pollination, and the Pass 2 output
4. **A footer** showing timestamp

**Critical formatting rule:** Reframings and Provocations sections at the top, ordered by entropy (most destabilizing first). "Under-explored Feasible Moves" comes third. "What the Swarm Did Not Touch" gets equal visual weight — it is not a footnote.

**If HTML (option 1):** Generate `scatter-report-[timestamp].html`. Style: clean, white background, readable sans-serif (system font stack), subtle borders, soft accent colors to distinguish agent sections. Agent sections collapsed by default. Open the file in the browser after generating it.

**If Word document (option 2):** Generate `scatter-report-[timestamp].docx`. Use the docx skill if available (`~/.claude/skills/docx/SKILL.md`). If not available, generate the .docx using python-docx (install if needed). Same structure as the HTML report — synthesis first, agent outputs as an appendix section. Use Word heading styles (Heading 1, Heading 2) so the document has a navigable outline.

**If Markdown (option 3):** Generate `scatter-report-[timestamp].md`. Use markdown headers (`##`, `###`) for sections. Use `<details><summary>Agent name</summary>...</details>` tags for collapsible agent sections. Same structure as HTML — synthesis at the top, agent outputs below the fold.

**If Transcript only (option 4):** Skip Step 6 entirely. Step 7 saves the full transcript as usual.

### step 7: save the full transcript

Runs regardless of format choice — the transcript is always saved.

Save `scatter-transcript-[timestamp].md` in the same location with:
- Original question
- Framed question
- Domain type detected
- All 5 Pass 1 outputs
- All 3 cross-pollinations
- Pass 2 output
- Full synthesis

---

## output format

Every scatter session produces one or two files based on the format chosen in Step 1:

```
scatter-report-[timestamp].html    # if HTML chosen (synthesis-forward, agents collapsible)
scatter-report-[timestamp].docx    # if Word chosen
scatter-report-[timestamp].md      # if Markdown chosen
scatter-transcript-[timestamp].md  # always saved, full record
```

---

## important notes

- **Spawn Pass 1 agents in parallel.** Sequential spawning lets earlier agents bleed into later ones, which collapses the orthogonality the skill depends on.
- **Pass 1 agents do NOT see each other's outputs.** Cross-pollination is a deliberate later step. Pass 1 contamination would defeat the geometric separation.
- **The synthesizer does NOT recommend.** If you find yourself writing "the user should..." or "the strongest option is..." stop. That's the LLM Council's job. Scatter's job is to widen.
- **Entropy enforcement is selective, not uniform.** Strong on Domain Transplant, Substrate Shifter, and Adjacent Possible. Light on Constraint Inverter and Failure Forensicist (their transformations push toward unconventional output structurally). Medium on Scale Shifter.
- **Cross-pollination is selective, not all-pairs.** Only the three chosen pairings run.
- **Convergence is a warning sign.** When multiple agents land on similar territory despite orthogonal transformations, that's the swarm collapsing toward conventional thinking — flag it explicitly in the synthesis as low-information signal.
- **Don't scatter trivial questions.** If the user has a decision with formed options, route them to llm-council. If they want efficiency, just answer the question. Scatter is for genuine generative-origin moments.

---

Built on the convergent ideas of swarm intelligence (Bonabeau, Kennedy & Eberhart) and information-theoretic entropy as observer-dependent uncertainty (Shannon, Jaynes, Aguirre). Architecturally inspired by Karpathy's LLM Council pattern, but inverted — where the Council converges on a recommendation, scatter preserves divergence.

License: MIT.
