# Treatment Matrix

The experiment varies two independent switches:

| Switch | Off | On |
| --- | --- | --- |
| Library | no access to the official docs/source corpus | access to the official docs/source corpus |
| Lab | no execution/exploration surface | access to a runnable tool surface for experimentation |

## Treatments

| Display name | Result ID | Full condition name | Library | Lab | Intent |
| --- | --- | --- | --- | --- | --- |
| Closed book | `closed_book` | `closed_book_no_library_no_lab` | off | off | Tests what the model can answer from the public question only, without the benchmark corpus or a runnable environment. |
| Lab only | `lab_only` | `lab_blackbox_no_library` | off | on | Tests whether the agent can learn by interacting with the pinned tool/runtime without being handed docs/source as a study corpus. |
| Library only | `library_only` | `library_docs_code_no_execution` | on | off | Tests static docs/source study without live experimentation. |
| Library + lab | `library_lab` | `library_lab_full_repo` | on | on | Gives both the official corpus and an execution surface, approximating a normal coding-agent environment. |

The harness fixes the agent family, model, reasoning effort, judge system, and
question set while varying only the treatment surface.

## Fixed Variables

| Variable | Value |
| --- | --- |
| Candidate agent | [Codex CLI](https://developers.openai.com/codex/cli) |
| Candidate model | [`gpt-5.5`](https://developers.openai.com/api/docs/models/gpt-5.5) |
| Reasoning effort | [`xhigh`](https://developers.openai.com/api/docs/guides/reasoning#reasoning-effort) |
| Native web search | disabled |
| Public row fields | `id`, `topic`, `question` |
| Hidden controller-only fields | `gold_answer`, `rubric`, `evidence`, scorer inputs, judge artifacts |
| DSPy questions per treatment | 30 |
| OpenClaw questions per treatment | 20 |

Each treatment therefore contributes 50 qid-runs, and the four-treatment matrix
contributes 200 qid-runs.
