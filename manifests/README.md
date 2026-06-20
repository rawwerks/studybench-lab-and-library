# Public Harness Manifest

This file records the public harness facts needed to interpret the final
200/200 aggregate matrix. Raw traces, private audit chatter, hidden gold
answers, hidden rubrics, judge inputs, credentials, and scratch logs are not
included in this repository.

## Candidate

| Field | Value |
| --- | --- |
| Agent | [Codex CLI](https://developers.openai.com/codex/cli) |
| Model | [`gpt-5.5`](https://developers.openai.com/api/docs/models/gpt-5.5) |
| Reasoning effort | [`xhigh`](https://developers.openai.com/api/docs/guides/reasoning#reasoning-effort) |
| Codex CLI version | `codex-cli 0.141.0` |
| Native web search | disabled |
| Host user config and rules | ignored for scored runs |
| Skills prompt injection | disabled for scored runs |
| Non-shell Codex feature surfaces | apps, browser/computer use, image generation, plugins, plugin sharing, skill MCP dependency install, and tool suggestions disabled |

## Dataset And Source Pins

| Environment | StudyBench config | Qid-runs per treatment | Dataset SHA-256 | Source pin | Runtime pin |
| --- | --- | ---: | --- | --- | --- |
| DSPy | [`dspy`](https://huggingface.co/datasets/jacobli/studybench) | 30 | `c814c8da2d49aa892930a9d4408f087707720d9e6f84511de7479d0854580325` | [`9cdb0aac28b2a04b064e40697ccd301872cf6a43`](https://github.com/stanfordnlp/dspy/commit/9cdb0aac28b2a04b064e40697ccd301872cf6a43) | Python 3.12, `dspy==3.1.3` |
| OpenClaw | [`openclaw`](https://huggingface.co/datasets/jacobli/studybench) | 20 | `d08f953f9480623a54762fae9fa8b35a9538b375692c4d058895aeba5a1dc50f` | [`da228660306b55a9cce3b973946f3aacfc515848`](https://github.com/openclaw/openclaw/commit/da228660306b55a9cce3b973946f3aacfc515848) | Node `22.14.0`, pnpm `10.33.0` |

## Treatment Surfaces

| Result ID | Full condition name | Library | Lab | Public access surface |
| --- | --- | --- | --- | --- |
| `closed_book` | `closed_book_no_library_no_lab` | no | no | Public row only; no useful repository, docs, runtime, web, or tool surface. |
| `lab_only` | `lab_blackbox_no_library` | no | yes | Public row plus a sealed black-box `labctl` runtime surface; no source, docs, tests, static corpus, web, or prior run cache. |
| `library_only` | `library_docs_code_no_execution` | yes | no | Public row plus a read-only static projection of official docs/source; no imports, tests, builds, package tools, or runtime execution. |
| `library_lab` | `library_lab_full_repo` | yes | yes | Public row plus disposable official checkout and pinned local runtime; dependency mutation blocked. |

## Prompt And Enforcement Hashes

| Result ID | Environment | Prompt SHA-256 | Projection/runtime hash | Policy/lab hash |
| --- | --- | --- | --- | --- |
| `closed_book` | DSPy | `1d00b98031abaeeb9f631cb6d22e8794eb008ce13d744edb1a79df94fdc72dfc` | none | closed-book deny shell `9cb68ee547530a1ebc6a07b41321150e674b7db02de3d7c61b4cd9f4695f341e` |
| `closed_book` | OpenClaw | `1d00b98031abaeeb9f631cb6d22e8794eb008ce13d744edb1a79df94fdc72dfc` | none | closed-book deny shell `9cb68ee547530a1ebc6a07b41321150e674b7db02de3d7c61b4cd9f4695f341e` |
| `lab_only` | DSPy | `bf91ca576fd52ff0d0e38c1a361f6974b25db4d83228eee10da060861237d6d0` | runtime `377f756442317d2199792634310092942942357fe0dba7f4e07b27d9f3f50b31` | policy `006807aae16919322e02c00ff284119a7f3652ee181b0e73fc45da2bca868e4c`; lab server `957db3c9040cff8cdead5ab5867bb60127dc0460685b5d48e1605fa03c7d438c` |
| `lab_only` | OpenClaw | `bf91ca576fd52ff0d0e38c1a361f6974b25db4d83228eee10da060861237d6d0` | runtime `fe3c7469249cfe1eed6cf84247e6d67a02550da8bd50600a2d93b87d1a269d9a` | policy `006807aae16919322e02c00ff284119a7f3652ee181b0e73fc45da2bca868e4c`; lab server `cdd1f9cd4232b74c29f66b96a5eb47be34b38b335f7c932a6f6033eaa8ae54e6` |
| `library_only` | DSPy | `d1be38335f6a4515fac0fa3b81f46a34f09c33b2a991c4ad4d846a41f84014e8` | projection `d37cdca4e296475f3a46422a1d54680698e070c9b1cde38e8bb11cb0c4185318` | static-read policy `e762f2b2acbb3fb911ec9dab3cc4815348a6f23187da2242cf320293192fee80` |
| `library_only` | OpenClaw | `82eb3a5c18bad0904554e12c60792e7c1d55abee34d0494400246f5c1938eb97` | projection `ec3b7ef6820d3f899d033648c1094586b3e74e750b53e67d4c5aebc0a1438d80` | static-read policy `e762f2b2acbb3fb911ec9dab3cc4815348a6f23187da2242cf320293192fee80` |
| `library_lab` | DSPy | `82d8e0b13bc953b5f50420d49e0d8c5947781560131930cb43d75d1fada58965` | full pinned checkout/runtime | dependency mutation blocked |
| `library_lab` | OpenClaw | `82d8e0b13bc953b5f50420d49e0d8c5947781560131930cb43d75d1fada58965` | full pinned checkout/runtime | dependency mutation blocked |
