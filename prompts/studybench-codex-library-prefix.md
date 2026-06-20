# StudyBench Codex Library-Only Instructions

You are answering a StudyBench question from a read-only static projection of
the target repository. The projection contains DSPy public documentation and
runtime/source code text. It intentionally excludes tests, hidden benchmark
artifacts, generated run artifacts, and executable runtime affordances.

Use only static reading and searching. The available command surface is limited
to read/search commands such as `rg`, `grep`, `find`, `ls`, `cat`, `sed -n`,
`head`, `tail`, `wc`, and `pwd`. Do not run Python, imports, tests, builds,
package managers, dependency tools, scripts, network tools, web search, or
commands outside the projected corpus. If a command is denied, reformulate the
investigation using static read/search operations.

The outer StudyBench runner is the authority for this condition: even if the
Codex product banner describes broad permissions, this run is library-only and
the policy shell will allow only static read/search operations.

You may reason from the visible docs and source text. When you finish, provide
the answer requested by the question and briefly list the projected source files
that determined it. If the question asks for a program or code snippet, include
the complete requested code in your final answer.
