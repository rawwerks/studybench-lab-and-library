# StudyBench Lab and Library

This repository publishes the clean aggregate results for a Codex CLI
StudyBench access-surface experiment: four treatments on DSPy and the same four
treatments on OpenClaw.

## TLDR

[StudyBench](https://huggingface.co/datasets/jacobli/studybench) is a coding
benchmark over real open-source codebases. The public dataset includes 30
[DSPy](https://github.com/stanfordnlp/dspy) questions and 20
[OpenClaw](https://github.com/openclaw/openclaw) questions, each with a
source-grounded rubric.

We ran [Codex CLI](https://developers.openai.com/codex/cli) with
[`gpt-5.5`](https://developers.openai.com/api/docs/models/gpt-5.5) and
OpenAI reasoning effort
[`xhigh`](https://developers.openai.com/api/docs/guides/reasoning#reasoning-effort)
across a 2x2 matrix: no library/no lab, lab only, library only, and
library+lab. The final matrix is complete: 200/200 qid-runs counted.

A qid-run is one scored question under one treatment. Each treatment has 50
qid-runs: 30 DSPy and 20 OpenClaw. The Mean column is the StudyBench coding-task
mix: `(DSPy * 30 + OpenClaw * 20) / 50`.

| Treatment | Result ID | Library | Lab | DSPy | OpenClaw | Mean |
| --- | --- | --- | --- | ---: | ---: | ---: |
| Closed book | `closed_book` | no | no | 51.70 | 6.35 | 33.56 |
| Lab only | `lab_only` | no | yes | 78.07 | 9.70 | 50.72 |
| Library only | `library_only` | yes | no | 82.97 | 60.30 | 73.90 |
| Library + lab | `library_lab` | yes | yes | 85.40 | 62.05 | 76.06 |

The four treatments are:

- **Closed book**: the agent only sees the public question. It gets no docs, no
  source tree, no package metadata, and no runtime to experiment with.
- **Lab only**: the agent gets a sealed black-box runtime surface for small
  probes. It gets no docs, no source tree, no tests, and no static study corpus.
- **Library only**: the agent can read and search the official static material:
  pinned source tree, docs, package metadata, and exposed corpus files. It cannot
  run the package, import it, execute tests, or use a binary/runtime.
- **Library + lab**: the agent gets both surfaces. It can read the official
  static material and also run experiments against the pinned environment.

The shape of the result is simple:

- OpenClaw is mostly library-driven: 9.70 with lab only, 60.30 with library
  only, and 62.05 with library+lab.
- DSPy improves strongly from lab access alone: 51.70 closed book, 78.07 lab
  only, 82.97 library only, and 85.40 library+lab.
- The best aggregate treatment is library+lab at 76.06.

## Public Artifacts

Results:

- [`results/scoreboard.csv`](results/scoreboard.csv) - compact table behind the
  TLDR.
- [`results/scoreboard.json`](results/scoreboard.json) - machine-readable
  aggregate scoreboard.
- [`results/blog-comparison.csv`](results/blog-comparison.csv) - compact
  comparison to the Machine Studying blog's published StudyBench scores.
- [`results/README.md`](results/README.md) - file relationships, treatment ID
  mapping, qid-run counts, and the Mean formula.

Methods and environment controls:

- [`environments/treatment-matrix.md`](environments/treatment-matrix.md) -
  treatment definitions and fixed harness variables.
- [`manifests/README.md`](manifests/README.md) - public harness manifest:
  candidate, dataset, source, runtime, prompt, and enforcement hashes.
- [`prompts/`](prompts/) - exact public prompt prefixes used for the four
  treatment surfaces.
- [`schemas/scoreboard.schema.json`](schemas/scoreboard.schema.json) - JSON
  Schema for `results/scoreboard.json`.

Context docs:

- [`docs/model-and-source-dates.md`](docs/model-and-source-dates.md) - cited
  notes on GPT-5.5 cutoff, StudyBench source pins, and target release dates.
- [`docs/blog-comparison.md`](docs/blog-comparison.md) - comparison between the
  [Machine Studying blog](https://jacobxli.com/blog/2026/machine-studying/) and
  this 2x2 matrix.
- [`docs/README.md`](docs/README.md) - docs index.

Repository hygiene:

- [`scripts/install-hooks`](scripts/install-hooks) - installs checked-in git
  hooks for local pre-commit checks.
- [`scripts/scan-secrets`](scripts/scan-secrets) - runs the full gitleaks scan.
- [`.gitleaks.toml`](.gitleaks.toml) - default gitleaks rules plus
  publication-specific privacy checks.

This public repository contains aggregate results, public prompts, schemas, and
method notes only. It omits raw traces, scratch logs, credentials, private audit
chatter, hidden gold answers, hidden rubrics, judge inputs, and other internal
working artifacts.

## Model And Source Dating

The official GPT-5.5 model page lists a December 1, 2025 knowledge cutoff.
`xhigh` is an OpenAI reasoning-effort parameter, not a separate model snapshot.
OpenAI does not disclose an exact training-data mixture boundary.

The StudyBench DSPy source pin is March 31, 2026, and the OpenClaw source pin is
April 18, 2026. See
[`docs/model-and-source-dates.md`](docs/model-and-source-dates.md) for the
source links and interpretation caveat.

## Upstream Links

- [Machine Studying blog post](https://jacobxli.com/blog/2026/machine-studying/)
  by Jacob Xiaochen Li, Rick Battle, and Omar Khattab.
- [StudyBench Hugging Face dataset](https://huggingface.co/datasets/jacobli/studybench).
- Source repositories referenced by the StudyBench dataset:
  [DSPy](https://github.com/stanfordnlp/dspy) at
  [`9cdb0aac`](https://github.com/stanfordnlp/dspy/commit/9cdb0aac28b2a04b064e40697ccd301872cf6a43)
  and [OpenClaw](https://github.com/openclaw/openclaw) at
  [`da228660`](https://github.com/openclaw/openclaw/commit/da228660306b55a9cce3b973946f3aacfc515848).

On June 20, 2026, no separate official StudyBench GitHub repository was linked
from the blog or Hugging Face dataset; the public benchmark artifact appears to
be the Hugging Face dataset.

Copyright (c) 2026 Raymond Weitekamp. All rights reserved.
