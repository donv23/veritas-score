# VERITAS

**Reliability score for any AI.**
*Truth measured, not promised.*

---

A confident AI answer and a fragile one look identical today. The
correct response and the hallucinated one wear the same tone, the same
fluency, the same apparent authority. For a reader, they are
indistinguishable.

VERITAS is a self-evaluation protocol that any large language model
(LLM) can apply to its own responses. For each substantive answer, it
declares: an operating mode (memory only vs. verified with sources), a
reliability score from 0 to 100 with a color-coded badge, a list of
2-5 key claims each with an explicit status, and a use-risk level. The
score doesn't certify truth — it makes uncertainty legible.

The protocol works with any modern LLM: Claude, ChatGPT, Grok, Gemini,
Mistral, Llama. It's a copy-pasteable system prompt, free, open to
iteration.

---

## Quick start

1. Open your preferred LLM (Claude.ai / ChatGPT / Grok / Gemini).
2. Copy the **VARIANT A** prompt from
   [`VERITAS_v4_1_LITE_EN.md`](./VERITAS_v4_1_LITE_EN.md) into the
   model's Custom Instructions, or as your first chat message
   prefixed `PERMANENT INSTRUCTIONS:`.
3. Ask a substantive question. The model will append a structured
   score block at the end of its response.

Three variants are available — Standard (~45 lines), Mini (~25),
Ultra (~15) — for different system prompt size budgets.

---

## The four dimensions

Every substantive response is scored along four independent axes, each
from 0 to 25 points. The sum is the response's Reliability score (0-100).

| Dimension | What it measures |
|---|---|
| **Verifiability** | How well claims are anchored to facts, data, and real sources |
| **Coherence** | Internal logic, absence of contradictions, argumentative quality |
| **Calibration** | Epistemic honesty — does the model state what it doesn't know? |
| **Specificity** | Concreteness and operational applicability |

---

## Three rules that make the difference

A naive self-scoring system can flag problems while still giving a high
score — defeating the point. VERITAS introduces three rules that close
this loophole.

**Cut Rule.** A single FALSE claim caps Verifiability at 11/25 and the
total score at 65/100. The model must distinguish *uncertainty* (a
claim that should be checked) from *error* (a claim that is
demonstrably wrong).

**Source Discipline.** Every specific claim — a number with more than
one significant digit, an exact date, an attributed name, a citation —
must be either sourced inline, reformulated as an honest range, or
flagged as UNVERIFIED. Three or more undisciplined specific claims cap
Verifiability at 15/25.

**Blind Spot Check.** Before publishing the score, the model is forced
to ask: "Of the 2-3 riskiest claims in my response, am I really sure,
or did I fill the gap with plausible-but-unverified content?" If it
filled, those claims are downgraded.

In v4.1, three more refinements were added based on the first empirical
test: a mandatory mapping of high-stakes content (medical, legal,
safety) to CRITICAL risk; explicit examples for the WEAK status to
prevent the model from defaulting to PLAUSIBLE; and mandatory URL or
verifiable reference in Verified mode to prevent "I claim Verified
without actually searching" behavior.

---

## Three modes

| Mode | Base | Score cap |
|---|---|---|
| **VERITAS-Lite** | Memory only | 84/100 on empirical content |
| **VERITAS-Verified** | Web search / documents / code | No mode cap |
| **VERITAS-Expert** | Verified + domain rubric | No mode cap, custom weights |

The Lite cap is the anti-self-deception mechanism. A confident
answer drawn purely from memory cannot earn a "strong green" badge,
no matter how elegant. Definitional, logical, and mathematical content
is exempt — those don't have external "verification" in the same sense.

---

## What it doesn't do

VERITAS is a self-evaluation, not a certification. It measures what the
model knows it doesn't know. It cannot detect what the model is wrong
about *without knowing*.

For high-stakes domains (medical, legal, financial), the score doesn't
replace expert review — it just helps you know where to spend the
verification budget.

The protocol is only as good as the model that applies it. Smaller
models may degrade the Blind Spot Check into a formality. Frontier
models with strong instruction-following give the best results.

---

## Repository contents

| File | Purpose |
|---|---|
| `VERITAS_v4_1_LITE_EN.md` | **The prompt itself.** Three variants. |
| `Score_di_Affidabilita_v4_1.docx` | Full methodology document (Italian) |
| `veritas_landing.html` | Project landing page (Italian) |
| `VERITAS_articolo_di_lancio.md` | Launch article (Italian) |
| `VERITAS_Brand_Kit.docx` | Brand identity reference |
| `VERITAS_v4_Test_Kit.xlsx` | Empirical test methodology |
| `veritas_feedback.html` | Feedback form for users |

The full methodology document is currently only in Italian. An English
translation may follow once the protocol has been tested cross-language.

---

## Status

VERITAS is an experimental, iterative project. It is currently at
**version 4.1** of the protocol, refined after a first empirical test
on ChatGPT (May 2026). The next iteration (v4.2) will incorporate
feedback from a wider testing pool across multiple models.

The protocol is free and the source materials are open. Iteration is
welcome.

---

## Origin

VERITAS was built in Italian, by someone who needed it for actual work
with LLMs and couldn't find an equivalent tool. The vocabulary (LLM,
prompt, cap, score) is kept in its original English form throughout the
Italian materials. The protocol's logic is language-agnostic.

The brand voice across all materials — sober, precise, modest about
limits — reflects what the protocol is trying to enforce in AI outputs
themselves. A tool that demanded epistemic discipline in others while
overselling itself would be a contradiction.

---

*Truth measured, not promised.*
