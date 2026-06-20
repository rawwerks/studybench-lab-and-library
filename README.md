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

Interpretation in one sentence: for this Codex harness, library access explains
most of the OpenClaw jump, lab access helps DSPy strongly, and library+lab is the
best aggregate treatment.

## Index

- [`results/scoreboard.csv`](results/scoreboard.csv) - compact table behind the
  TLDR.
- [`results/scoreboard.json`](results/scoreboard.json) - machine-readable
  aggregate scoreboard.
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

The `docs/`, `manifests/`, `prompts/`, and `schemas/` directories are staging
areas in this initial commit; their placeholder READMEs mark the intended public
artifact layout.

## Status

This repository is the clean public-facing staging area. It intentionally omits
raw traces, scratch logs, private audit chatter, failed harness versions, local
credentials, and other internal working artifacts.

Copyright (c) 2026 Raymond Weitekamp. All rights reserved.
