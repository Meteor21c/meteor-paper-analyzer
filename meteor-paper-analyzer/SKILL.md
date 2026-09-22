---
name: meteor-paper-analyzer
description: >-
  Analyze uploaded or linked academic papers in a structured seven-question research brief for a technically literate but non-specialist reader. Use when the user asks to read, summarize, explain, review, or deeply analyze a paper. Read the primary paper rather than relying only on the abstract; explain unfamiliar domain-specific concepts before using them; cover the problem, related work, method, experiments, further research directions, a final synthesis, and a concrete end-to-end algorithm walkthrough. Preserve important equations and exact experimental numbers, distinguish paper claims from your own extensions or illustrative examples, and default to Simplified Chinese unless the user requests another language.
---

# Meteor Paper Analyzer

Produce a faithful, technically substantial paper analysis in a fixed Q1-Q7 structure. Assume the reader understands general computing/AI concepts but is **not automatically an expert in the paper's subfield**.

## Workflow

1. Read the paper before drafting.
   - For an uploaded PDF/document or linked paper, use the available reading tools and inspect all sections needed for the analysis.
   - Do not answer from the abstract or isolated snippets when the full paper is available.
   - Read at minimum: abstract, introduction, related work, method, experiments, conclusion/limitations, and relevant appendix sections.
   - Inspect figures, tables, algorithms, examples, and appendix case studies when they clarify the method or results.
   - Prefer the primary paper over blogs, social summaries, or secondary descriptions.

2. Build a compact evidence map before writing.
   Capture:
   - task/problem and concrete failure mode;
   - gap in prior work;
   - prerequisite concepts a non-specialist must understand;
   - core idea and named modules;
   - model architecture, training/inference flow, equations, and losses;
   - datasets, baselines, metrics, model sizes, and implementation choices;
   - headline results, ablations, efficiency results, robustness tests, and qualitative analyses;
   - paper-provided examples/case studies suitable for the Q7 walkthrough;
   - stated limitations and assumptions.

3. Explain prerequisite concepts before depending on them.
   - Follow `references/explanation-guide.md`.
   - Do not introduce niche terms as unexplained labels. This applies especially to prior-work concepts in Q2 and building blocks in Q3.
   - Prefer the sequence: **plain-language intuition -> technical definition -> role in this paper**.
   - Example of the required behavior: before discussing "FFN neuron mining", first explain what the Transformer FFN is, what a "neuron" means in that FFN, and what "mining" those neurons is trying to identify.

4. Draft Q1-Q7 using `references/analysis-template.md`.
   - Q7 is mandatory unless the user explicitly asks for a shorter format.
   - Prefer a real example from the paper/appendix. If none exists, construct a faithful synthetic example using the paper's true architecture and clearly label all invented values as illustrative.

5. Apply the fidelity and quality checks in `references/quality-rubric.md` before answering.

## Output behavior

- Default to Simplified Chinese.
- Treat the reader as a smart newcomer to the subfield, not as a specialist.
- Keep important English technical terms in parentheses on first mention when useful for precision.
- Define acronyms at first use.
- When a term is central but unfamiliar, give enough explanation to make the next paragraph understandable; do not replace one unexplained jargon term with another.
- Match the paper's own terminology exactly for named methods, modules, datasets, and metrics.
- Use equations when central to understanding the method; explain every symbol that materially affects interpretation.
- Use compact tables for experimental settings and ablations when this improves readability.
- Include exact numbers for the strongest evidence whenever the paper reports them.
- Distinguish absolute improvements from relative improvements. Never convert one into the other silently.
- Attribute claims such as SOTA, robustness, causality, or efficiency to the paper unless independently established by the evidence.
- If publication status is unclear, do not invent a venue. If only an arXiv submission date is known, label it accordingly.
- If a detail is absent or ambiguous in the paper, state that it is not clearly reported rather than guessing.
- If citations are available, cite specific factual claims and numerical results with minimal clutter.

## Analysis depth

- Q1-Q4: evidence-based descriptions of the paper.
- Q5: extensions grounded in limitations, assumptions, unexplored settings, or experimental gaps.
- Q6: concise synthesis rather than repetition.
- Q7: pedagogical reconstruction of how the algorithm actually processes one concrete case from input to output.

Do not reduce the analysis to a generic abstract summary. The target is a research-reading note that lets a non-specialist understand not just **what names appear**, but **what those concepts mean, how the method works, why the experiments support it, and what happens to one concrete example as it passes through the system**.
