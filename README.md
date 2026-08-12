# Structural Enforcement of Deliberation in Language Models — Pilot Studies
 
Two pre-registered pilot studies testing whether the structure of a language
model's answer (the order of a decision field vs. a reasoning field, and how
strictly that structure is enforced) changes the severity of the decisions
the model makes.
 
## Pre-registration
 
Both studies were pre-registered before data collection:
https://gist.github.com/mikefitzgeraldpersonal-cell/86b15151f666eb7fab1706f3ca887b8c
 
## What's here
 
All files sit at the repository root.
 
- **`1.Arm1_Pilot_Colab_SUPERSEDED.ipynb`** — the original Study 1 notebook,
  superseded by a later mechanism fix. Kept for transparency; not the
  source of any reported result.
- **`2.Arm1_Pilot_Colab_FINAL.ipynb`** — Study 1 (four production API
  models).
- **`3.Arm1b_OpenWeight_FSM.ipynb`** — Study 2 (two open-weight models,
  identical FSM enforcement).
- **`arm1_results.jsonl`** — raw generation log, Study 1.
- **`openweight_results.jsonl`** — raw generation log, Study 2.
- **`arm1_distributions.png`** — severity distributions, Study 1.
- **`openweight_distributions.png`** — severity distributions, Study 2.
## The studies, in brief
 
A model plays a national-security advisor across ten fictional crisis
scenarios and returns a decision severity (1 = strong de-escalation, 5 =
severe escalation) plus its reasoning, as a two-field structured answer.
Three conditions vary only the structure of that answer:
 
- **C1** — decision field first, structurally enforced
- **C2** — reasoning field first, structurally enforced
- **C3** — reasoning first requested in the prompt only, unenforced
**Study 1** ran four production API models (GPT-4o-mini, o4-mini, Claude
Sonnet 4.6 with and without extended thinking), 30 repetitions per cell,
3,600 successful calls.
 
**Study 2** ran two open-weight models locally (Qwen2.5-1.5B, Phi-3.5-mini)
with C1/C2 enforced by identical finite-state-machine code on both models,
15 repetitions per cell, 900 generations, zero errors.
 
Every response's actual field order was logged as a manipulation check.
Analysis follows the pre-registered plan: ordered logit with scenario as
covariate (confirmatory), plus rank-based pairwise comparisons with Cliff's
δ and Holm correction.
 
Full write-up, tables, and findings: see the accompanying findings
document (linked from the community post once published).
 
## Reproducing the results
 
Each notebook is self-contained and regenerates its results and figures
from the corresponding `.jsonl` file in this repository. No API keys are
required to reproduce the analysis from the logged data; running the
generations fresh requires provider API keys (Study 1) or local model
weights (Study 2).
 
## Status
 
Both pilots are complete and archived as of August 2026. This repository is
frozen at the pilot stage; any follow-on work (expanded scenarios,
non-cooperative conditions) will live in a separate, clearly labelled
location.
 
## License
 
- Code (notebooks): [MIT](https://opensource.org/licenses/MIT)
- Data and figures (`results/`, `figures/`): [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/)
Reuse is welcome under these terms; please credit this repository and cite
the pre-registration linked above.please credit this repository and cite
the pre-registration linked above.
