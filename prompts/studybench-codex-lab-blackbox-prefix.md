# StudyBench Codex Lab-Only Black-Box Instructions

You are answering a StudyBench question in lab-only black-box mode. No source
code, documentation, tests, fixtures, repository checkout, static corpus, web
search, browser, or prior run cache is available.

You may run small inline probes only through the provided black-box `labctl`
tool against the pinned target runtime. Use `labctl manifest` first.

For DSPy, use `labctl run-python --code '...'`. Multiline probes are allowed
only as quoted `--code` strings, for example:

`labctl run-python --code 'print("alpha")
print("beta")'`

For OpenClaw, use the pinned built package through `labctl run-node --code
'...'`. The lab exposes the public runtime package but not repository docs,
source files, tests, fixtures, or hidden benchmark artifacts. Prefer CommonJS
`require(...)` inside probes, for example:

`labctl run-node --code 'const { resolveAgentRoute } = require("openclaw/plugin-sdk/routing"); console.log(typeof resolveAgentRoute)'`

Your final answer may still use normal TypeScript/ESM imports if the question
asks for code.

Do not use heredocs, pipes, redirects, shell command substitution, package
tools, direct `python`/`node`, or filesystem/source inspection. Base your
answer on observed behavior from `labctl`. Do not try to inspect package files,
source locations, docstrings, source maps, test files, hidden benchmark
artifacts, host paths, function source strings such as JavaScript
`toString()`/`Function.prototype.toString`, Python `help()`/`inspect.getdoc`,
or non-public task state.

Do not monkeypatch, wrap, replace, or intercept runtime primitives to infer
hidden internals. In particular, do not override filesystem APIs, `inspect`,
`require`, module loader APIs, subprocess APIs, `fetch`, sockets, or other
guarded primitives to see what the package tries to read, import, spawn, or
contact. You may create ordinary toy inputs, public config objects, callbacks,
classes, functions, plugins, and fake user-space dependencies inside the inline
probe; treat the target package itself as a black box. For OpenClaw, use public
package entrypoints and construct toy configs/events/plugins to observe behavior
without reading implementation files. If a public entrypoint needs hidden
package assets and the lab returns a denial, report that as an observation
instead of trying to route around the guard.

When you finish, provide the answer requested by the question and briefly list
the black-box observations that determined it. If the question asks for a
program, script, helper, plugin entry, or code snippet, include the complete
requested code in your final answer.
