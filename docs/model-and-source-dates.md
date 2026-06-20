# Model And Source Dates

This note records the date evidence used when interpreting whether StudyBench
results could be explained by model memorization versus learning from the
provided library and lab surfaces.

## Summary

| Item | Date | Semantics | Source |
| --- | ---: | --- | --- |
| GPT-5.5 | 2025-12-01 | Official disclosed knowledge cutoff, not a separately disclosed training-data cutoff | [OpenAI API model page](https://developers.openai.com/api/docs/models/gpt-5.5) |
| DSPy StudyBench pin | 2026-03-31 | Pinned source commit date | [StudyBench dataset](https://huggingface.co/datasets/jacobli/studybench), [DSPy commit](https://github.com/stanfordnlp/dspy/commit/9cdb0aac28b2a04b064e40697ccd301872cf6a43) |
| DSPy package version | 2026-02-05 | `dspy==3.1.3` release date | [GitHub release](https://github.com/stanfordnlp/dspy/releases/tag/3.1.3), [PyPI](https://pypi.org/project/dspy/3.1.3/) |
| OpenClaw StudyBench pin | 2026-04-18 | Pinned source commit date | [StudyBench dataset](https://huggingface.co/datasets/jacobli/studybench), [OpenClaw commit](https://github.com/openclaw/openclaw/commit/da228660306b55a9cce3b973946f3aacfc515848) |
| OpenClaw package version | 2026-04-18 | `2026.4.18` package version in the pinned source tree; public release-notes date | [OpenClaw release notes](https://openclaw-hub.com/releases/v2026.4.18/) |
| StudyBench dataset snapshot | 2026-06-07 / 2026-06-12 | Hugging Face dataset creation date / last-modified date | [Hugging Face API](https://huggingface.co/api/datasets/jacobli/studybench) |

## Notes

- The OpenAI model page discloses GPT-5.5's knowledge cutoff as December 1,
  2025 (verified live on the page: "Dec 01, 2025 knowledge cutoff"). It does not
  separately disclose a precise training-data cutoff or training mixture
  boundary.
- Conflict (sources, not a transcription error): the Machine Studying post
  states GPT-5.5's knowledge cutoff as August 31, 2025 in its literature-review
  discussion, ~3 months earlier than OpenAI's official December 1, 2025. The
  blog post is internally consistent and correctly cited here; the conflict is
  between Li's stated figure and OpenAI's model page. For this report, treat the
  OpenAI model page as the authoritative current source for the official model
  knowledge cutoff, and treat the blog value as a cited discrepancy rather than
  the controlling date.
  Source: [Machine Studying](https://jacobxli.com/blog/2026/machine-studying/).
- Scope note: in the Machine Studying post, GPT-5.5 appears only in the
  Studying-Literature task (Figures 7-8, GPT-5.1 vs GPT-5.5). The DSPy and
  OpenClaw experiments we replicate here used GPT-5.1 and GPT-5.4-mini, not 5.5,
  so our GPT-5.5 DSPy/OpenClaw runs have no direct counterpart in the original
  post.
- StudyBench pins DSPy to
  `9cdb0aac28b2a04b064e40697ccd301872cf6a43`, which is after the `3.1.3`
  release tag. In local git terms this is `3.1.3-78-g9cdb0aac`; therefore the
  source snapshot date is March 31, 2026, while the package release date is
  February 5, 2026.
- StudyBench pins OpenClaw to
  `da228660306b55a9cce3b973946f3aacfc515848`. The pinned `package.json`
  reports version `2026.4.18`; the public release-notes page for `v2026.4.18`
  is dated April 18, 2026. We did not treat a GitHub tag or npm package as the
  source of truth for that exact version because the pinned commit and dataset
  source are more direct.

## Interpretation

Using the official GPT-5.5 knowledge cutoff as the comparison point, both
StudyBench source snapshots used here postdate the disclosed model cutoff:
DSPy by about four months and OpenClaw by about four and a half months. That
does not prove absence of memorization, because the exact training-data cutoff
is not disclosed, but it makes exact memorization of the pinned source snapshots
a weaker explanation than if the target commits predated the disclosed cutoff.
