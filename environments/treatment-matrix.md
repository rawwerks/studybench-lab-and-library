# Treatment Matrix

The experiment varies two independent switches:

| Switch | Off | On |
| --- | --- | --- |
| Library | no access to the official docs/source corpus | access to the official docs/source corpus |
| Lab | no execution/exploration surface | access to a runnable tool surface for experimentation |

## Treatments

| Treatment | Library | Lab | Intent |
| --- | --- | --- | --- |
| Closed book | off | off | Tests what the model can answer without the benchmark corpus or a runnable environment. |
| Lab only | off | on | Tests whether the agent can learn by interacting with the tool/runtime without being handed docs/source as a study corpus. |
| Library only | on | off | Closest thematic match to the Machine Studying setup: study the corpus, then answer without live experimentation. |
| Library + lab | on | on | Gives both the official corpus and an execution surface, approximating a real coding-agent environment. |

The harness fixes the agent family, model, reasoning effort, judge system, and
question set while varying only the treatment surface.
