# Quality and fidelity rubric

Apply all checks before finalizing.

## 1. Source fidelity

- Every named module, dataset, baseline, metric, equation, and numerical result must be supported by the paper.
- Do not infer a venue, acceptance status, publication date, or SOTA status without evidence.
- If a result comes from an appendix, say so when that context matters.
- If only approximate values can be read from a plot, mark them as approximate.

## 2. Accessibility gate

Assume the reader is not an expert in the paper's narrow subfield.

Before finalizing Q1-Q3, check:
- Did every central niche term receive a first-use explanation?
- Did the explanation cover intuition, technical meaning, and role in the paper when needed?
- Does any sentence rely on an acronym or specialized primitive that was never defined?
- Did Q2 explain prior-work mechanisms instead of merely naming them?
- Could a reader understand why a concept matters before seeing the paper-specific modification?

A useful test: if deleting the term's name would make the paragraph incomprehensible, the mechanism needs more explanation.

## 3. Problem-method alignment

- Q1 must identify a concrete failure mode, not only restate the broad field.
- Q3 must explicitly connect each method component to the failure mode it is designed to mitigate.
- Avoid implementation details that do not help explain the contribution.

## 4. Related-work quality

- Group prior work by methodological idea or limitation.
- Explain each group's core mechanism in accessible language.
- Explain the current paper's delta relative to those groups.
- Do not turn Related Work into a citation dump.

## 5. Experimental precision

For every headline number, verify:
- dataset/task;
- metric;
- retrieval or generation setting;
- model size/version;
- compared baseline;
- absolute versus relative improvement.

Do not mix Recall@k with answer F1/accuracy, or retrieval improvements with end-to-end generation gains.

When the paper reports mixed outcomes, include the important negative or neutral result if it affects interpretation.

## 6. Q5 research value

A strong future direction is anchored to one of these:
- a stated limitation;
- a hidden assumption;
- a missing stress test;
- a scaling or efficiency bottleneck;
- a transfer/generalization gap;
- an unresolved causal mechanism;
- a safety/robustness vulnerability.

Prefer testable proposals. Include a suggested experimental comparison when it adds substance.

## 7. Q7 walkthrough fidelity

Q7 must make the algorithm concrete without fabricating evidence.

Check:
- Is the example source identified as paper-provided or synthetic?
- If synthetic, is it explicitly labeled as a teaching example rather than paper evidence?
- Does the walkthrough follow the paper's real architecture and stage order?
- Are invented numbers labeled as illustrative?
- Are unobservable internals represented symbolically rather than fabricated as exact measurements?
- Does the walkthrough show at least one meaningful intermediate result, not only input and final output?
- Does it explain how the paper's key innovation changes the trajectory of the example?

If the paper contains a good worked example or appendix case study, prefer it over inventing a new one.

## 8. Writing quality

- Default to Simplified Chinese.
- Keep method and metric names in canonical English form when translation could create ambiguity.
- Define acronyms on first use.
- Avoid exaggerated claims such as "fundamentally solves" unless evidence justifies them.
- Avoid repeating the same conclusion in Q1, Q4, and Q6 with nearly identical wording.
- Make Q6 shorter and more synthetic than the combined earlier sections.
- Keep explanations concrete; avoid chains of unexplained jargon.

## 9. Completeness gate

Before answering, confirm that you can answer all seven questions from the source plus clearly marked analysis. If the source is incomplete or unreadable, state the missing evidence and produce the best-supported analysis rather than filling gaps from memory.
