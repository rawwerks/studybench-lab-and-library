# Results

This directory contains the public aggregate results for the final 200/200
StudyBench matrix.

## Files

| File | Role |
| --- | --- |
| [`scoreboard.csv`](scoreboard.csv) | Human-readable aggregate scoreboard: one row per treatment. |
| [`scoreboard.json`](scoreboard.json) | Machine-readable aggregate scoreboard with model, reasoning effort, benchmark counts, and notes. |
| [`blog-comparison.csv`](blog-comparison.csv) | Compact data behind [`docs/blog-comparison.md`](../docs/blog-comparison.md). |

## Counts

Each treatment has 50 qid-runs from the public
[StudyBench](https://huggingface.co/datasets/jacobli/studybench) dataset:

- 30 DSPy questions from the `dspy` config.
- 20 OpenClaw questions from the `openclaw` config.

The matrix has four treatments, so the final public aggregate counts 200
qid-runs.

## Treatment IDs

| Display name | CSV/JSON ID | Full condition name |
| --- | --- | --- |
| Closed book | `closed_book` | `closed_book_no_library_no_lab` |
| Lab only | `lab_only` | `lab_blackbox_no_library` |
| Library only | `library_only` | `library_docs_code_no_execution` |
| Library + lab | `library_lab` | `library_lab_full_repo` |

## Mean

The Mean column uses the StudyBench coding-task mix:

```text
mean = (DSPy * 30 + OpenClaw * 20) / 50
```

It is not an unweighted average of the two benchmark-level scores.
