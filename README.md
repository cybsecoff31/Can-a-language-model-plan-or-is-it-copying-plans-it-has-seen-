<div align="center">

# Can a Language Model Plan, or Is It Copying Plans It Has Seen?
### An Enhanced Review Organised Around the Output-Only Test

**Hubert Yakpé Trolindo and CAP 6671 group members**

University of Central Florida · CAP 6671 · November 2026

[![Paper](https://img.shields.io/badge/Paper-PDF-b31b1b.svg)](project_submission_enhanced.pdf)
[![Project page](https://img.shields.io/badge/Project-Page-1f6feb.svg)](https://cybsecoff31.github.io/Can-a-language-model-plan-or-is-it-copying-plans-it-has-seen-/)

</div>

Can today's language and reasoning models be called planners in the classical sense, judging only from what they output? And what output-only test would separate a valid plan from plan-shaped text?

This repository holds a literature review of three core readings and eight further papers, along with its project page. There is no code: the evidence is plan validity scored by an external validator, on ordinary and obfuscated domains, as reported in the cited papers.

## Conclusion

Current models are not planners in the classical sense, but "copying" no longer describes the best of them. Classical planners are invariant to renaming, while every language model studied loses validity under obfuscated names. Standard LLMs collapse to near zero on Mystery Blocksworld, and reasoning models keep between about a third and nine-tenths of their ordinary performance. Validity guarantees come from sound components, at inference or at construction time.

## Key evidence

Valid plans or tasks solved (%) for the same setup under ordinary and obfuscated names. Rows with different benchmarks must not be compared with each other.

| Setup | Model / system | Ordinary | Obfuscated |
|---|---|---:|---:|
| PlanBench, zero-shot, 600 instances | GPT-4 | 34.6 | 0.16 |
| | Claude-3 Opus | 59.3 | 0 |
| | o1-mini | 56.6 | 19.1 |
| | DeepSeek R1 | 97 | 42.6 |
| | o1-preview | 97.8 | 52.8 |
| Fresh IPC-2023 tasks, 360 instances, random-string names | LAMA (classical planner) | 56.7 | 56.7 |
| | GPT-5 | 56.9 | 42.2 |
| | Gemini 2.5 Pro | 43.1 | 40.6 |
| | DeepSeek R1 | 43.6 | 25.8 |
| Generalized programs, 7 domains, held-out tasks | GPT-4 writes Python | 61.6 | 4.4 |

The paper's Table 1 gives the full evidence base, including hybrid systems and the conditions behind every number.

## Four claims about the question

| Claim | Summary | If the claim were wrong we would see |
|---|---|---|
| **A: retrieval** | LLMs retrieve plan-shaped text rather than plan | Obfuscated validity close to ordinary validity for the same model and prompt |
| **B: partial capability** | Reasoning models show a partial, improving, renaming-sensitive competence | A collapse to near zero on fresh random renamings, or performance that follows familiarity rather than difficulty |
| **C: system property** | Planning belongs to a system in which a sound component guarantees validity | No gain over a random or empty proposer when the same sound component is used |
| **D: write the planner** | The LLM's useful role is to write the planner, not the plan | Programs that fit the training tasks but fail on larger held-out ones; no drop without names |

## Proposed output-only test

A system earns the label "planner" on a domain if, on freshly generated instances scored by VAL:

1. its validity under *k* ≥ 3 independent random bijective renamings is statistically indistinguishable from ordinary names, with per-instance agreement across renamings;
2. its validity degrades with optimal plan length no faster than a classical planner under the same budget;
3. it reports unsolvable instances as unsolvable.

For a generated program, these apply to held-out tasks larger than any training task. When a sound component takes part, the label belongs to the system, and the LLM's share is measured against a null proposer.

## Repository contents

| File | Purpose |
|---|---|
| [`project_submission_enhanced.pdf`](project_submission_enhanced.pdf) | The full paper, with references |
| [`index.html`](index.html) | The project page, served by GitHub Pages |

## Citation

```bibtex
@techreport{yakpetrolindo2026language,
  author      = {Yakp{\'e} Trolindo, Hubert and {CAP 6671 group members}},
  title       = {Can a Language Model Plan, or Is It Copying Plans It Has Seen?
                 An Enhanced Review Organised Around the Output-Only Test},
  institution = {University of Central Florida},
  type        = {CAP 6671 Course Report},
  year        = {2026},
  month       = nov,
  url         = {https://github.com/cybsecoff31/Can-a-language-model-plan-or-is-it-copying-plans-it-has-seen-}
}
```

## AI use disclosure

Claude (Anthropic) was used to extract figures from the cited papers.
