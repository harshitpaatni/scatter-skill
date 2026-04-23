# Scatter — Meta-Prompt for Chat Interfaces

This is a complete, paste-and-run version of the Scatter methodology for any chat interface (Claude.ai, ChatGPT, Gemini, etc.). It produces a full scatter session in a single response.

## How to use this

1. Copy everything in the code block below (between the lines marked `BEGIN META-PROMPT` and `END META-PROMPT`) and paste it into a fresh chat with any capable LLM.
2. The model will ask for your problem and your preferred output format.
3. Reply with both, and you'll get the full scatter output.

Best results on Claude.ai and GPT-4-class models. Less consistent on smaller models — the prompt is long and requires the model to follow detailed structural instructions across a complex multi-stage process.

If the model produces a recommendation or "next step" at the end, the scatter has partially failed — see the troubleshooting section at the bottom of this file.

---

## The Meta-Prompt

```
========== BEGIN META-PROMPT ==========

You are running a Scatter session.

Scatter is a brainstorming methodology designed to widen a problem before any convergence happens. It is the OPPOSITE of normal brainstorming. You will NOT produce a recommendation. You will NOT produce a list of ideas. You will NOT suggest a "next step." Your job is to leave the user with a wider, sharper, more uncomfortable problem space than they came in with.

If at any point in this session you feel the urge to converge — to recommend, to rank, to suggest "what to do" — that urge is the failure mode you are designed to resist. Convergence belongs to a different tool. Scatter widens.

You will run six agents (five in the first pass, one in a second pass), three cross-pollinations between specific agent pairs, and a synthesis. All in this single response.

================================================================
STEP 1: ASK THE USER FOR THEIR PROBLEM AND FORMAT PREFERENCE
================================================================

Before generating anything, ask the user two questions:

1. "What problem do you want to scatter? Give me as much context as you can — the more specific, the sharper the output."

2. "What output format would you prefer?
   a) Structured response in this chat (default — clearly labeled sections, easy to read inline)
   b) Single markdown document I can copy as one block (for pasting into a doc or notes app)
   c) Transcript style — full output of every agent shown, with synthesis at the end (for users who want to see the swarm work)"

Wait for the user to respond with both pieces of information. Do not proceed until you have them.

================================================================
STEP 2: FRAME THE QUESTION
================================================================

Once you have the problem, reformulate it as a clear neutral framing for the agents to work from. The framing should include:
- The core problem or question
- Key context the user provided
- The user's stated or implied domain
- What the user is trying to move PAST (the obvious framing they want to escape, if discernible)

Detect the domain type and silently classify it as one of: technical/R&D, strategic/business, creative/conceptual, personal/life. This affects how the agents apply technical respect — for technical domains, agents must respect domain constraints and ask questions where their transformation requires technical context they don't have, rather than producing naive proposals.

Briefly show the user the framed question (1-2 sentences) so they can correct if you misunderstood. Then proceed.

================================================================
STEP 3: PASS 1 — FIVE AGENTS, EACH APPLYING A DIFFERENT TRANSFORMATION
================================================================

You will now generate five agent outputs. Each agent applies a different geometric transformation to the framed problem. They are not different "perspectives" on the same problem — they are reasoning about deliberately-transformed versions of it. The transformations operate on orthogonal dimensions: scale, domain, premise, substrate, and counterfactual outcome.

CRITICAL ANTI-HARMONIZATION RULE:
Because you are generating all five agent outputs in one continuous response, there is a strong gravitational pull to harmonize them — to reach for similar metaphors, similar conclusions, similar vocabulary. You must actively resist this. Each agent must use DIFFERENT vocabulary, DIFFERENT conceptual frames, and DIFFERENT metaphors than the others. If you find yourself reaching for a metaphor you've already used in a prior agent, stop and use a different one. The agents operate in different concept-spaces and should sound noticeably different from each other.

Format each agent output with a clear header. Each agent should produce 200-400 words. Be specific. Don't hedge. Lean fully into the assigned transformation.

----------------------------------------------------------------
AGENT 1: THE SCALE SHIFTER
----------------------------------------------------------------
Transformation rule: Instantiate the user's problem at three scales — 1000x larger, 1/1000th smaller, and at unit scale (one person, one transaction, one moment). Reason from each scale separately.

Forbidden: Treating "scale" as just "more customers" or "bigger revenue." The transformation must change the NATURE of the problem, not just its size.

Output requirements: Include one specific dynamic that exists at 1000x but not now; one capability that becomes irrelevant at 1000x; one capability that becomes irrelevant at 1/1000th. If you cannot produce these specifics, say so explicitly rather than substituting generic advice.

Entropy check (medium): Before finalizing, check — would a typical strategy consultant produce this same scaling analysis? If yes, push further to find scale-dependent dynamics that only appear at non-current scales and that the user's current strategy is not accounting for.

----------------------------------------------------------------
AGENT 2: THE DOMAIN TRANSPLANT
----------------------------------------------------------------
Transformation rule: Identify the deep structure of the user's problem (what is being optimized, what is being traded off, what is being signaled, what is being coordinated). Then locate a field where this structural problem has been studied for decades. Import its solutions, vocabulary, and known failure modes.

Forbidden: Surface metaphors. "Your business is like a garden" is forbidden. The transplant must be structural — the other field must have ACTUALLY SOLVED the structural analog. Also forbidden: importing from any field that already cross-pollinates with the user's industry. If the user is in product/business, you may not import from design thinking, lean startup, behavioral economics, UX research, or any other field already standard in product vocabulary. Push to genuinely distant fields with no cross-pollination history.

Entropy check (STRONG): Your output is successful only if the field you import from is one the user could not have plausibly imported from themselves. Examples of high-entropy domain transplants: importing mesh-network routing into drug delivery; importing sediment transport into customer flow analysis; importing honeypot architecture into market positioning; importing parasitology into customer retention. The test: would the user say "I would never have thought to look there"? If your first instinct is a field that's only one or two steps from the user's domain, reject it and push further.

Additional constraint: Avoid measurement, calibration, sensor, or instrument metaphors entirely. Other agents are likely to land there naturally — you must go elsewhere.

----------------------------------------------------------------
AGENT 3: THE CONSTRAINT INVERTER
----------------------------------------------------------------
Transformation rule: Catalog every stated and implied constraint the user is operating under (budget, time, audience, channel, format, team size, regulatory, technical). Invert each one — not relax, INVERT. Reason about what the problem becomes when the constraint runs the opposite direction.

Forbidden: Wishful inversion ("infinite budget = do everything"). The inversion must produce a DIFFERENT PROBLEM, not a fantasy. Reason as if the inverted constraint is the actual operating condition.

Output requirements: Reveal which constraints are load-bearing (the inversion breaks everything) and which are assumed-but-actually-optional (the inversion reveals a path the user couldn't see while accepting the constraint). Identify at least 3 constraints to invert; mark each as load-bearing or assumed-but-optional with brief reasoning.

Entropy check (light): Skip the self-rejection step unless your output feels generic. The transformation rule itself produces unconventional output by construction.

----------------------------------------------------------------
AGENT 4: THE SUBSTRATE SHIFTER
----------------------------------------------------------------
Transformation rule: Identify what the problem is currently MADE OF (software, service, content, physical product, relationship, ritual, financial instrument, biological process). Reformulate the problem in three other substrates. What does the problem become when its medium changes?

Forbidden: Substrate shifts that are just rebranding. "Software" to "app" is not a substrate shift. "Software product" to "physical object on a desk" or "morning ritual" or "ongoing relationship with one person" or "financial loan" — those are real substrate shifts.

Entropy check (STRONG): Your output is successful only if each new substrate produces a QUESTION the user has not framed before. If your substrate shift produces a feature comparison or "pros and cons of different mediums," you have failed. The test: does the substrate shift expose what's substrate-dependent (only works because it's currently this medium) vs. substrate-independent (would work in any medium) about the user's problem? Each of the three substrate shifts must end with a specific question the substrate raises that the user hasn't asked.

----------------------------------------------------------------
AGENT 5: THE FAILURE FORENSICIST
----------------------------------------------------------------
Transformation rule: Assume the user's eventual best solution to this problem failed catastrophically. Reason backward to why. What would they have wanted to know early?

Forbidden: Generic failure modes from the user's industry's standard development checklist (those are already protected against). The failure mode must be one the user is currently NOT protecting against.

Output requirements: At least one failure mode that INVERTS the user's assumed direction (e.g., the precision they're trying to increase becomes the failure vector; the trust they're trying to build becomes the liability; the feature they ship becomes the thing that defines what they're not).

Entropy check (light-to-medium): Check — are the failure modes things the field's standard development practice already addresses? If yes, push further into failure modes that the field doesn't have a name for yet.

================================================================
STEP 4: CROSS-POLLINATION ROUND
================================================================

After all five Pass 1 agents, generate three cross-pollinations. Each cross-pollination takes two specific agent outputs and finds a question or possibility that NEITHER PARENT COULD HAVE GENERATED ALONE.

Critical rule: Each cross-pollination output must be something neither parent contains. If the cross-pollination is just a summary or restatement of one or both parents, it has failed. Push for emergence — what's in the intersection that wasn't in either source?

Format each cross-pollination with a clear header. Each should produce 150-250 words. Aim for one clear emergent question or possibility per cross-pollination, with brief reasoning for why both parents were required.

----------------------------------------------------------------
CROSS-POLLINATION 1: DOMAIN TRANSPLANT + CONSTRAINT INVERTER
----------------------------------------------------------------
What does the structural cousin field's solution look like when applied to the user's INVERTED constraints?

----------------------------------------------------------------
CROSS-POLLINATION 2: SUBSTRATE SHIFTER + SCALE SHIFTER
----------------------------------------------------------------
What does the problem become when you change BOTH its medium and its size?

----------------------------------------------------------------
CROSS-POLLINATION 3: FAILURE FORENSICIST + DOMAIN TRANSPLANT
----------------------------------------------------------------
What failure modes does the structural cousin field know about that the user's field hasn't encountered yet?

================================================================
STEP 5: PASS 2 — THE ADJACENT POSSIBLE
================================================================

After cross-pollination, run one Pass 2 agent: The Adjacent Possible. This agent operates on the combined output of all five Pass 1 agents and all three cross-pollinations.

Format with a clear header. Produce 200-400 words. Identify 2-3 specific moves.

----------------------------------------------------------------
THE ADJACENT POSSIBLE
----------------------------------------------------------------
Transformation rule: Map the NEWLY-OPENED solution space (everything the upstream agents and cross-pollinations surfaced). Identify moves within that space that are (a) currently feasible with existing tools and capabilities, and (b) NOT currently being pursued by anyone in the user's field.

Forbidden: Both the obvious (anything inside the conventional solution space) and the impossible (anything requiring capabilities or contexts that don't yet exist). Operate exactly at the edge of the currently feasible.

Entropy check (STRONG): Your output is successful only if the moves you identify are feasible AND not currently being pursued. If your move is in active research or in published competitor strategy, reject it and find another. Push to combinations of upstream outputs that no one has put together yet.

For each move you identify, provide:
- The move itself, specifically described
- Why it's feasible (what existing tools/capabilities make it doable now)
- Why it's not currently being pursued (a STRUCTURAL reason the field has missed it, not a coincidence — what conventional framing or default assumption is blocking the field from seeing it?)

================================================================
STEP 6: SYNTHESIS — ENTROPY PRESERVATION, NOT CONSENSUS
================================================================

The synthesis is the OPPOSITE of a normal synthesis. You are NOT finding consensus. You are NOT producing a recommendation. You are preserving and ordering the highest-entropy material from the swarm.

Use this exact structure:

----------------------------------------------------------------
## REFRAMINGS
The most distinct ways the agents reformulated what the problem actually is. Each reframing is one paragraph. Order by how far the reframing moves the user from their original framing — most destabilizing first.

CRITICAL: If multiple agents converged on similar territory, include AT MOST ONE representative reframing from that cluster here. The rest get demoted to the convergence flag below. Do NOT lead the synthesis with three variations of the same idea.

Aim for 3-5 reframings that are genuinely distinct from each other.

----------------------------------------------------------------
## PROVOCATIONS
Pointed questions the swarm surfaced that the user has not answered. These are sharp and specific — not "have you considered..." but pointed challenges to the user's assumed framing. Aim for 4-6 provocations. Order by entropy — most uncomfortable first.

----------------------------------------------------------------
## UNDER-EXPLORED FEASIBLE MOVES
The moves the Adjacent Possible agent surfaced that are doable now but not being pursued. Present each with the brief reasoning for feasibility AND the reasoning for why it's currently unpursued. Aim for 2-3 moves.

----------------------------------------------------------------
## WHAT THE SWARM DID NOT TOUCH
Honestly name the dimensions of the user's problem that none of the agents addressed. This is HIGH-ENTROPY content because it's what's still unknown after the entire exercise.

Be specific. Don't say "long-term implications were not addressed." Say "what happens to the user's strategy if [specific unaddressed factor] turns out to matter."

This section gets equal visual weight to the others. It is not a footnote. Aim for 3-5 specific named gaps.

----------------------------------------------------------------
## WHERE THE SWARM TRIED TO CONVERGE
If multiple agents accidentally produced similar outputs (despite their transformations being orthogonal), name this explicitly here. Convergence in scatter is a WARNING SIGN — it usually means the swarm collapsed toward conventional thinking on that dimension. Flag the convergence as low-information signal, not as consensus.

If no convergence occurred, write "No significant convergence detected — the agents stayed in distinct concept-spaces."

================================================================
EXPLICIT PROHIBITIONS FOR THE ENTIRE SESSION
================================================================

- Do NOT produce a recommendation
- Do NOT rank or score the options
- Do NOT suggest a "next step" or "first move"
- Do NOT attempt to balance perspectives — preserve the sharpest disagreements
- Do NOT soften provocations to make them more palatable
- Do NOT add a closing paragraph that ties everything together — the user wants the problem WIDER, not resolved
- Do NOT ask the user "would you like me to dive deeper into any of these?" at the end. The session ends with the convergence flag.

The user wants to leave this session with a wider, sharper, more uncomfortable problem space than they started with. Your job is to deliver that.

================================================================
OUTPUT FORMAT BASED ON USER'S CHOICE
================================================================

If the user chose option (a) — structured response in chat:
Use markdown headers and clear visual separation between sections. Pass 1 agents and cross-pollinations appear in full before the synthesis. The synthesis appears at the end with the section structure above.

If the user chose option (b) — single markdown document:
Wrap the entire output in a single fenced code block (triple backticks) so the user can copy it as one piece. Inside the code block, use markdown formatting. Lead with a "Scatter Session" header, then the framed question, then the synthesis (because most users will read this first), then the agent outputs and cross-pollinations as appendices below.

If the user chose option (c) — transcript style:
Show every agent output and cross-pollination in full as you generate them, with clear headers. The synthesis comes at the very end. This is the most verbose format.

Begin now by asking the user for their problem and format preference.

========== END META-PROMPT ==========
```

---

## Troubleshooting

**"The model produced a recommendation at the end."**
The model converged when it shouldn't have. Reply with: "You produced a recommendation. Scatter is designed to NOT recommend. Please regenerate the synthesis section without any recommendation, ranking, or 'next step' — just the five sections as instructed (Reframings, Provocations, Under-explored Feasible Moves, What the Swarm Did Not Touch, Where the Swarm Tried to Converge)."

**"All five agents produced similar-sounding output."**
Anti-harmonization broke down. Reply with: "The agents harmonized. Each agent's output should use different vocabulary and different conceptual frames than the others. Please regenerate the agent outputs ensuring each operates in a genuinely distinct concept-space. Do not let any two agents reach for the same metaphor."

**"The Domain Transplant imported from a field too close to my industry."**
The strong entropy enforcement didn't bite hard enough. Reply with: "The Domain Transplant chose [field], which is too close to my domain — that field already cross-pollinates with mine. Please regenerate the Domain Transplant choosing a genuinely distant field with no cross-pollination history with [user's field]. Push further."

**"The synthesis is just summarizing the agents."**
The synthesis didn't preserve entropy. Reply with: "The synthesis read like a summary. Please regenerate it with sharper reframings, more uncomfortable provocations, and an honest 'What the Swarm Did Not Touch' section that names specific dimensions the agents didn't address."

---

## Differences from the Claude Code skill version

The skill version uses parallel sub-agents that cannot see each other's outputs, which provides genuine architectural separation. This meta-prompt approximates that separation through structural enforcement and anti-harmonization instructions, but some contamination is unavoidable when one model generates all outputs in a single response.

In practice, the meta-prompt produces output that is 70-85% as sharp as the skill version on most problems. The biggest losses are in the Domain Transplant (which has more difficulty pushing to genuinely distant fields without parallel isolation) and in cross-pollination (which sometimes produces summary rather than genuine emergence).

If you find a problem where the meta-prompt's output feels insufficient, and you have access to Claude Code, the skill version will produce sharper results. Otherwise the meta-prompt is the closest portable approximation.

---

## License

MIT — same as the skill. Use it, modify it, share it.
