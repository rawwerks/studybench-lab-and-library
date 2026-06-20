# StudyBench Lab and Library

TLDR: we ran StudyBench with Codex `gpt-5.5`, reasoning effort `xhigh`, across a
2x2 treatment matrix: no library/no lab, lab only, library only, and
library+lab. The strict matrix is complete: 200/200 qid-runs counted.

| Treatment | Library | Lab | DSPy | OpenClaw | Mean |
| --- | --- | --- | ---: | ---: | ---: |
| Closed book | no | no | 51.70 | 6.35 | 33.56 |
| Lab only | no | yes | 78.07 | 9.70 | 50.72 |
| Library only | yes | no | 82.97 | 60.30 | 73.90 |
| Library + lab | yes | yes | 85.40 | 62.05 | 76.06 |

The four environments:

- **Closed book**: the agent only sees the question. It gets no docs, no source
  tree, no package metadata, and no runtime to experiment with.
- **Lab only**: the agent gets no docs, no source tree, and no static study
  corpus. It can only learn by running small probes against the pinned
  tool/runtime through the allowed lab surface.
- **Library only**: the agent can read and search the official static material:
  pinned source tree, docs, package metadata, and exposed corpus files. It cannot
  run the package, import it, execute tests, or use a binary/runtime.
- **Library + lab**: the agent gets both surfaces. It can read the official
  static material and also run experiments against the pinned environment.

Interpretation in one sentence: for this Codex harness, library access explains
most of the OpenClaw jump, lab access helps DSPy strongly, and library+lab is the
best aggregate treatment.

## Upstream Links

- [Machine Studying blog post](https://jacobxli.com/blog/2026/machine-studying/)
  by Jacob Xiaochen Li, Rick Battle, and Omar Khattab.
- [StudyBench Hugging Face dataset](https://huggingface.co/datasets/jacobli/studybench).
- Source repositories referenced by the StudyBench dataset:
  [DSPy](https://github.com/stanfordnlp/dspy) at
  [`9cdb0aac`](https://github.com/stanfordnlp/dspy/commit/9cdb0aac28b2a04b064e40697ccd301872cf6a43)
  and [OpenClaw](https://github.com/openclaw/openclaw) at
  [`da228660`](https://github.com/openclaw/openclaw/commit/da228660306b55a9cce3b973946f3aacfc515848).

As of June 20, 2026, I did not find a separate official StudyBench GitHub repo
linked from the blog or Hugging Face dataset; the public benchmark artifact
appears to be the Hugging Face dataset.

## Index

- [`results/scoreboard.csv`](results/scoreboard.csv) - compact table behind the
  TLDR.
- [`results/scoreboard.json`](results/scoreboard.json) - machine-readable
  aggregate scoreboard.
- [`results/blog-comparison.csv`](results/blog-comparison.csv) - compact
  comparison to the blog's published StudyBench scores.
- [`environments/treatment-matrix.md`](environments/treatment-matrix.md) -
  definitions for closed book, lab only, library only, and library+lab.
- `manifests/` - per-treatment environment manifests and hashes.
- `prompts/` - minimal orientation prompts used for Codex.
- `schemas/` - JSON schemas for results, judgments, and manifests.
- `scripts/` - local repository hygiene helpers.
- [`scripts/install-hooks`](scripts/install-hooks) - installs checked-in git
  hooks for local pre-commit checks.
- [`scripts/scan-secrets`](scripts/scan-secrets) - runs the full gitleaks scan.
- [`.gitleaks.toml`](.gitleaks.toml) - default gitleaks rules plus
  publication-specific privacy checks.
- `docs/` - methods notes, caveats, and comparison to the Machine Studying post.
- [`docs/model-and-source-dates.md`](docs/model-and-source-dates.md) - cited
  notes on GPT-5.5 cutoff, StudyBench source pins, and target release dates.
- [`docs/blog-comparison.md`](docs/blog-comparison.md) - comparison between the
  Machine Studying blog's published StudyBench scores and this 2x2 matrix.

The `docs/`, `manifests/`, `prompts/`, and `schemas/` directories are staging
areas in this initial commit; their placeholder READMEs mark the intended public
artifact layout.

## Status

This repository is the clean public-facing staging area. It intentionally omits
raw traces, scratch logs, private audit chatter, failed harness versions, local
credentials, and other internal working artifacts.

Copyright (c) 2026 Raymond Weitekamp. All rights reserved.
