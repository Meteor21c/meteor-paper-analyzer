# Concept explanation guide

Use this guide whenever the paper contains domain-specific terminology, prior-work mechanisms, or architecture components that a technically literate non-specialist may not know.

## Reader model

Assume the reader may know broad concepts such as Transformer, LLM, embeddings, RAG, training, and inference, but may not know the paper's niche vocabulary, specialized variants, or prior methods.

Do not assume familiarity merely because a term is common inside one research community.

## First-use rule

Before relying on an unfamiliar concept, explain it on first use with this three-step pattern:

1. **Intuition:** what it is in plain language.
2. **Technical meaning:** how it is represented or operated on.
3. **Why it matters here:** what role it plays in the cited prior work or current paper.

Keep the explanation proportional to importance:
- central prerequisite: 2-5 sentences;
- secondary term: 1-2 sentences;
- standard acronym: short parenthetical definition may be enough.

## Dependency rule

Never explain concept B using concept A if A has not yet been explained and is equally specialized. Resolve the dependency chain first.

Bad:
> The method performs Neuron Mining over FFN neurons and selects high-activation experts.

Better:
> Transformer layers contain a feed-forward network (FFN), which applies learned nonlinear transformations independently to each token after attention. Individual hidden dimensions in this FFN are sometimes informally called "neurons" because each dimension can become strongly activated by certain input patterns. **Neuron Mining** refers to searching these dimensions for neurons whose activation is consistently associated with a target behavior or concept. The prior method uses those identified neurons as a way to locate where certain knowledge or behaviors may be represented.

Only after this bridge should the analysis discuss how the paper modifies or reuses Neuron Mining.

## Related-work rule

Q2 must not become a list of paper names plus unexplained keywords. For every major research stream:
- explain the common mechanism first;
- introduce representative methods second;
- then explain the limitation and the current paper's delta.

If a cited predecessor is essential to the new method, explain enough of that predecessor for the reader to understand what is inherited and what is changed.

## Equation rule

Before or immediately after an equation:
- say in words what the equation is doing;
- define non-obvious symbols;
- identify the quantity that changes and the effect of increasing/decreasing it when relevant.

Do not present formulas as decorative evidence.

## Analogy rule

Use analogies only when they shorten understanding. Mark the analogy as intuition, not as the formal mechanism. Prefer one good analogy over several loose metaphors.

## Jargon density check

After drafting each subsection, inspect its first paragraph. If it contains 3 or more specialized terms that were not already explained, rewrite the paragraph to add conceptual bridges or stagger the terminology.
