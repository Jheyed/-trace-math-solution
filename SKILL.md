---
name: trace-math-solution
description: Produce detailed, reproducible university-level mathematics proofs and multi-step derivations with extensive heuristic analysis, explicit rigor gaps, provisional proof routes, and every substantive mathematical step. Use only when the user explicitly asks for a detailed or complete proof, a full step-by-step derivation, no skipped steps, an equivalent or stronger level of process detail, or invokes $trace-math-solution directly; do not implicitly invoke for ordinary solve requests, hints, concise proofs, final answers, routine calculations, or broad mathematical modeling.
---

# Trace Math Solution

Create a rigorous solution that preserves a reproducible, user-facing discovery path instead of presenting only a compressed final proof. Treat analysis as a primary deliverable: it may equal or exceed the formal proof in length, but it must remain exploratory rather than duplicating the finished proof. Adapt the explanation depth to demonstrated user knowledge without inventing a knowledge profile.

Before answering, read [references/answer-pattern.md](references/answer-pattern.md). Follow its reusable structure and level of detail, but never copy its problem-specific facts or its example knowledge assessment into a different problem. If the problem involves an alternating recurrence, parity subsequences, or a decreasing iteration map, also read [references/oscillating-recurrence-example.md](references/oscillating-recurrence-example.md) as a calibration example. Use examples as patterns of thought and exposition, never as templates whose conclusions are transplanted into unrelated problems.

## 1. Establish the knowledge profile

1. Inspect the current conversation for explicit evidence of what the user has or has not mastered.
2. When relevant workspace notes are accessible, search the most likely course folders and files with available read-only search tools. Keep the search proportional to the problem; do not scan unrelated material.
3. Never modify notes while solving a problem unless the user separately requests an edit.
4. Classify each important prerequisite as one of:
   - confirmed mastered;
   - mastery not confirmed;
   - confirmed unfamiliar.
5. Treat missing evidence as “mastery not confirmed,” not as proof that the user does not know it.
6. If no relevant notes are accessible, state that the assessment uses only the current conversation and continue.

Open the answer with `## 解题前的知识准备` or an equivalent heading in the user's language. Give a short list of the important methods, the evidence-based status of each, and the resulting explanation depth. Keep mastered material concise; explain unconfirmed or unfamiliar material more fully.

## 2. Build the global analysis

Write `## 分析` before the formal solution.

1. Identify the mathematical structure and the nearest familiar problem type.
2. Try the standard heuristic or general method that naturally suggests a candidate result.
3. Label that result as a candidate, not a proved conclusion.
4. Expose every rigor gap created by the heuristic, such as assuming a limit exists before proving convergence, dividing by a possibly zero quantity, or applying a theorem before checking its hypotheses.
5. Use mathematical intuition and the standard toolbox to propose the most natural proof route. It is acceptable to say “first try theorem X” before its hypotheses are proved, provided this is clearly provisional rather than a completed justification.
6. State which conditions that route would require and which of them are intuitively plausible, obvious from the structure, uncertain, or potentially false. Mention risks such as oscillation or sign changes when they naturally arise, but leave substantive verification to the formal solution.
7. Convert the candidate route into proof obligations: “第一步检查……第二步证明……若这些成立，再使用……”. Make dependencies explicit and use tentative language for unverified steps.
8. Include special cases when they materially simplify the problem or require separate treatment.

Make the analysis as extensive as the mathematical decision-making requires. It may be as long as or longer than the formal proof because it can compare ideas, expose uncertainty, explain intuition, and formulate proof obligations. Do not turn it into a second formal proof by completing every calculation in advance. Do not fabricate a dramatic discovery story or claim to have consulted material that was not actually inspected.

Calibrate the depth of the global analysis to what would naturally be noticed at that stage. It may name or partially explore a local technique when the clue is already visible, but avoid explaining it with more hindsight than the structure reasonably supports. If the clue becomes clear only after a later transformation, let the detailed discovery occur in that step's `执行分析`. Treat this as a matter of degree and fidelity, not a rigid boundary between analysis and solution.

## 3. Execute the proof step by step

Write `## 解` or an equivalent heading. Follow the plan in order.

For every substantive step, include:

1. **本步目标** — state exactly what must be established.
2. **执行分析** — explain why a transformation, theorem, estimate, substitution, or case split fits this target.
3. **详细推导** — show every substantive equality, inequality, substitution, factorization, and implication in sequence.
4. **本步结论** — state what has been proved and how it enables the next step.

Do not replace multi-line reasoning with phrases such as “整理可得,” “同理可得,” or “经过计算.” Omit only genuinely one-step arithmetic that cannot hide a logical choice. When applying a theorem:

- state the relevant hypotheses;
- map the current quantities to the theorem;
- verify domain and sign conditions;
- explain equality or strictness conditions when they matter.

If an attempted route fails, identify the failure and revise the plan instead of silently jumping to another method.

When a local technique needs explanation, show enough of the concrete cue to make the choice understandable. For example, perform the useful rearrangement and identify repeated terms or matching coefficients before or alongside naming the resulting inequality. The amount of setup should match how obvious the cue is in context; do not mechanically force every discovery into the same depth.

## 4. Explain unfamiliar tools after the proof

Add `## 补充知识` only when at least one important method is confirmed unfamiliar or mastery is not confirmed. For each such method, explain:

- the statement or definition;
- the intuition;
- why the problem's structure suggests it;
- how the problem's quantities map to it;
- its hypotheses and equality conditions;
- one small example when useful.

Still give enough explanation at first use to keep the proof readable; the supplement deepens rather than postpones all understanding.

## 5. Check the proof

Before answering, verify:

- every item in the proof plan was completed;
- no candidate result was treated as proof;
- no provisional route from the analysis was presented as already justified;
- the depth and timing of method discussion feel natural rather than mechanically separated between analysis and solution;
- every proof obligation identified in the analysis was verified in the solution before the corresponding theorem was applied;
- plausible oscillation, sign changes, domain escape, or other qualitative failure modes were resolved in the solution when relevant;
- no circular argument remains;
- every theorem's hypotheses were checked;
- limits were not substituted before existence was justified;
- denominators, signs, domains, edge cases, and equality conditions were handled;
- the final statement matches exactly what the problem asks.

Follow the host environment's math-rendering rules. Prefer readable display equations for multi-step derivations and never use a code block merely to display ordinary mathematics.
