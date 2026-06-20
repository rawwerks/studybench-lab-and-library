# Comparison To The Machine Studying Blog

This note compares the published StudyBench scores in the Machine Studying blog
with our Codex `gpt-5.5` / `xhigh` 2x2 environment matrix.

## Caveat

This is not an apples-to-apples reproduction. The blog evaluates models inside a
ReAct harness with `grep`, `glob`, and `read_file` across direct, 5-iteration,
20-iteration, and forced-20 budgets. Our matrix evaluates Codex CLI under four
environment treatments. The cleanest conceptual comparison is our **library
only** condition, because it is static corpus access without runtime execution,
but the command surface and agent harness still differ.

## Blog Numbers Used

From Figure 3 in the blog:

| Blog run | DSPy | OpenClaw |
| --- | ---: | ---: |
| GPT-5.1 best shown point | 29.8 | 10.0 |
| GPT-5.4-mini best shown point | 39.7 | 9.7 |
| Best shown point across either model | 39.7 | 10.0 |

The blog also reports Qwen3.5-9B studying variants. Those are useful context,
but less directly comparable because they are Qwen weight/context-management
experiments rather than frontier Codex CLI environment treatments. The best
shown Qwen lenient single points are 29.4 on DSPy and 18.1 on OpenClaw.

Sources:

- [Machine Studying blog post](https://jacobxli.com/blog/2026/machine-studying/)
- [StudyBench Hugging Face dataset](https://huggingface.co/datasets/jacobli/studybench)

## Our Matrix Versus Blog Figure 3

Weighted means use the StudyBench coding-task mix: 30 DSPy questions and 20
OpenClaw questions.

| Run | DSPy | OpenClaw | Weighted mean |
| --- | ---: | ---: | ---: |
| Blog GPT-5.4-mini best shown point | 39.70 | 9.70 | 27.70 |
| Blog best shown point across GPT-5.1/GPT-5.4-mini | 39.70 | 10.00 | 27.82 |
| Our closed book | 51.70 | 6.35 | 33.56 |
| Our lab only | 78.07 | 9.70 | 50.72 |
| Our library only | 82.97 | 60.30 | 73.90 |
| Our library + lab | 85.40 | 62.05 | 76.06 |

Against the blog's GPT-5.4-mini best shown points:

| Our run | DSPy delta | OpenClaw delta | Weighted-mean delta |
| --- | ---: | ---: | ---: |
| Closed book | +12.00 | -3.35 | +5.86 |
| Lab only | +38.37 | +0.00 | +23.02 |
| Library only | +43.27 | +50.60 | +46.20 |
| Library + lab | +45.70 | +52.35 | +48.36 |

## Reading

The main result is not just that Codex `gpt-5.5` is stronger. The shape of the
2x2 matrix says where the extra performance comes from:

- **OpenClaw** changes dramatically when the static source/docs corpus is
  available: 9.70 in lab-only versus 60.30 in library-only and 62.05 in
  library+lab.
- **DSPy** benefits from both surfaces, but even lab-only is already very strong:
  78.07 without docs/source, 82.97 with library-only, and 85.40 with both.
- The blog's published ReAct results are much closer to our closed-book/lab-only
  OpenClaw performance than to our library-only or library+lab OpenClaw
  performance.

The conservative claim is that a modern coding agent with a richer native
environment and static access to the pinned corpus can substantially outperform
the blog's published ReAct baselines on the same open StudyBench questions. The
less conservative claim, which needs more controlled replication, is that the
blog harness materially underestimates what current coding agents can do when
they are allowed to operate in an environment closer to normal software work.
