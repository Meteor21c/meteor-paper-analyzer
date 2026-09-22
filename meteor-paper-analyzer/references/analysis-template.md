# Meteor Paper Analyzer output template

Use the following seven questions in this order. Keep the exact Q1-Q7 structure unless the user explicitly asks for a different format.

If a reliable publication or submission timestamp is available, begin with:

**Publish**: YYYY-MM-DD HH:MM:SS UTC

If only a date is available, use the date only. Do not fabricate a timestamp.

## Q1: 这篇论文试图解决什么问题？

Heading:

**Q1**: 这篇论文试图解决什么问题？

Cover:
- the target task/system setting;
- the specific failure mode or bottleneck in prior methods;
- why that failure matters in practice or evaluation;
- the research objective and proposed high-level remedy.

Start with a crisp problem statement, then use 2-5 bullets for background/challenges when useful.

If the problem statement depends on a specialized concept, explain that concept before using it as the premise of the argument.

## Q2: 有哪些相关研究？

Heading:

**Q2**: 有哪些相关研究？

Organize related work into 2-5 meaningful research streams rather than listing citations chronologically.

For each stream, use this order:
1. explain the common idea in accessible language;
2. define any important specialized concept;
3. name representative methods/papers actually cited by the source paper;
4. explain the limitation relevant to this paper;
5. explain how the current paper differs.

If a predecessor introduces something like FFN neurons, neuron mining, sparse autoencoders, personalized PageRank, contrastive decoding, memory tokens, or another niche primitive, explain what that primitive is before comparing methods that use it.

End with a short synthesis of the paper's claimed position in the landscape.

Do not invent citation details that were not verified in the paper.

## Q3: 论文如何解决这个问题？

Heading:

**Q3**: 论文如何解决这个问题？

This is usually the most detailed section. Start with a one-paragraph overview, then decompose the method into numbered components or stages.

For each component, explain:
- input and output;
- mechanism;
- why it addresses the failure mode from Q1;
- important equations, objectives, or scoring functions;
- training versus inference behavior when they differ.

Before using a specialized building block, give the reader the prerequisite explanation needed to understand it.

When the paper contains central equations:
- first state in words what the equation accomplishes;
- reproduce only necessary formulas in readable LaTeX;
- define the symbols;
- explain the operational effect of the important terms.

Conclude with a compact unified pipeline such as:
`input -> representation/retrieval -> intermediate module(s) -> scoring/selection -> generation/output`.

## Q4: 论文做了哪些实验？

Heading:

**Q4**: 论文做了哪些实验？

Use this order when information exists:
1. Experimental setup.
2. Datasets/tasks.
3. Baselines.
4. Metrics.
5. Main results.
6. Ablations.
7. Efficiency, robustness, scaling, visualization, or case studies.
8. What the experiments do and do not establish.

Prefer a compact table for dataset/task/metric information when there are several settings.

For key results:
- report exact values when available;
- name the compared baseline;
- state whether the gain is absolute or relative;
- preserve top-k, model size, retrieval budget, language, and other conditions needed to interpret the number.

If a metric itself is specialized, briefly explain what a high/low value means before interpreting results.

Do not say a method is universally superior when the paper only shows gains on a subset of settings.

## Q5: 有什么可以进一步探索的点？

Heading:

**Q5**: 有什么可以进一步探索的点？

Generate approximately 5-10 non-trivial future directions, adjusted to the paper's scope. Start from:
- limitations stated by the authors;
- architectural assumptions;
- missing ablations;
- narrow datasets or languages;
- cost/latency/memory bottlenecks;
- robustness and safety gaps;
- scaling questions;
- unexplored combinations with adjacent methods;
- theoretical or interpretability gaps.

Each direction should contain:
- the concrete extension or research question;
- why it follows from this paper;
- at least one plausible evaluation or experimental design when useful.

Avoid generic filler such as "use a larger model" unless the paper creates a specific scaling hypothesis that can be tested.

Clearly distinguish these ideas from the authors' own stated future work.

## Q6: 总结一下论文的主要内容

Heading:

**Q6**: 总结一下论文的主要内容

Provide a high-density but accessible synthesis. A good default structure is:
- Core problem.
- Proposed method.
- Key experimental evidence.
- Main contribution/significance.
- Important limitation or boundary condition when material.

Aim for a self-contained recap that can be read without Q1-Q5. Do not merely paste or compress the abstract.

## Q7: 用一个具体例子展示算法是怎么工作的

Heading:

**Q7**: 用一个具体例子展示算法是怎么工作的

Purpose: turn the abstract method into a concrete, step-by-step execution trace that a non-specialist can follow.

### Source preference

Use this priority order:
1. a worked example explicitly provided in the paper;
2. a case study/figure/example from the appendix;
3. if neither exists, a **faithful synthetic example** created solely for explanation.

If using a paper-provided example, say so and preserve its important facts while paraphrasing rather than copying long passages.

If constructing the example, begin with:
> **下面是依据论文真实架构构造的教学示例，并非论文中的真实实验样本；其中具体文本/数值仅用于说明流程。**

Never present invented illustrative values as measured paper results.

### Required walkthrough

Show the example through the actual method's stages. Adapt labels to the paper, but normally include:

1. **原始输入** — query, document, graph, image, prompt, etc.
2. **预处理/表示** — chunks, tokens, entities, embeddings, activations, summaries, candidate sets, etc.
3. **核心模块逐步处理** — show what each named module receives and emits.
4. **中间结果** — rankings, selected neurons, retrieved passages, weights, latent codes, candidate answers, etc.
5. **关键公式如何落到这个例子上** — when feasible, substitute small toy values or symbolic values and show the effect.
6. **最终输出** — the final prediction/answer/retrieval set and how it arose.
7. **对照说明** — briefly state what would likely happen without the paper's key innovation, if the paper supports such a comparison.

### Numerical honesty

- Use exact numeric values only when the paper supplies them for that example.
- For a synthetic walkthrough, label toy values as **示意数值**.
- Do not invent hidden-state coordinates, probabilities, attention weights, or activations and imply they were observed.
- When exact internals are not observable, use symbolic placeholders or qualitative states, e.g. `score(A) > score(B)`.

### Pedagogical style

Prefer a compact table such as:

| 步骤 | 输入 | 系统做什么 | 中间结果/输出 |
|---|---|---|---|
| 1 | ... | ... | ... |

Then add 1-3 paragraphs explaining why the example demonstrates the paper's core contribution.

## Style notes

- Use Chinese prose with English names/terms where they aid precision.
- Assume a non-specialist reader; explain before relying on niche terminology.
- Prefer concrete nouns and mechanisms over promotional adjectives.
- Use bold text for method names, metrics, or particularly important findings, not every sentence.
- Keep lists nested only when needed.
- Use tables when comparison structure is clearer than prose.
- Preserve enough technical depth that another researcher could reconstruct the paper's logic without requiring prior expertise in that narrow subfield.
