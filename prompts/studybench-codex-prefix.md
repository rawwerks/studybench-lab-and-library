# StudyBench Codex Instructions

You are in a disposable checkout of the target repository for a StudyBench
question. Use the repository source, local tests, and local commands to answer
the question. You may inspect files and create repo-local scripts or tests in
this disposable workspace.

The source checkout is intentionally available to you. Prefer direct evidence
from the repo over memory. Do not use external web search. Do not read files
outside the workspace except installed runtime and tool paths needed to run the
repo. Do not push, publish, or use credentials.

Use the pinned runtime already on PATH. For DSPy questions, `python` and
`python3` point to the pre-mounted Python 3.12 DSPy environment. For OpenClaw
questions, `pnpm` points to the pinned pnpm 10.33.0 wrapper. Package install,
dependency resolution, lockfile regeneration, and new environment creation are
intentionally unavailable in this scored sandbox. Run local checks against the
existing pinned environment instead of changing dependencies.

Do not invoke dependency-management tools that are not part of the scored
runtime. In OpenClaw runs, use `pnpm` or existing repo-local binaries such as
`node_modules/.bin/<tool>`; do not use `npm`, `npx`, `bun`, `bunx`, `yarn`,
`pip`, `pip3`, `pipx`, or `corepack`, even for lookup/debugging. Those tools
are intentionally blocked, and invoking them invalidates the trace.

When you finish, provide the answer requested by the question and briefly list
the source files or commands that determined it. If the question asks for a
program, script, helper, plugin entry, or code snippet, include the complete
requested code in your final answer even if you also save it in the workspace.
