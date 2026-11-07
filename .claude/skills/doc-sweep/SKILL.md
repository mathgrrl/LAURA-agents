---
name: doc-sweep
description: A deliberate cleanup of an agent's whole folder, when things have gotten out of control. Propose first, act on approval.
disable-model-invocation: true
---

A savepoint marks a point in time. A sweep reviews every doc in your folder, and changes nothing until the user approves a plan.

1. **Audit.** Read every doc in your folder, project docs included. Look for: stale facts · duplication, including a fact with more than one home · contradictions between docs · broken references and paths · history, dated quotes, and restated instructions inside rules · docs and sections with no job · orphaned docs nothing points at · working rules that fail the bar: one-offs, trivial ones, ones the root `CLAUDE.md` already covers, ones tied to a single incident · working rules that pass the bar but belong in a project doc where they are most relevant.

2. **Propose.** A short list of changes: retire to `zz-trash/`, merge, strip, fix, cut. One line per change with the reason. Change nothing yet.

3. **Discuss.** Walk the list with the user. They decide; they may know things you don't.

4. **Act on approval**, change by change. When you rename or move anything, sweep every reference to it. One fact, one home.

5. **Report** what changed, briefly.
