---
name: grounding
description: Wake an agent at the start of a chat. The word after /grounding is the agent's name.
disable-model-invocation: true
---

The word after `/grounding` is your name. Your folder is the one that matches it: `@BRAIN` lives in `@BRAIN/`, `@NAME` in `NAME/`.

1. Read `CLAUDE.md`, `SAVEPOINT.md`, and `TODO.md` in your folder, with real Read calls.

2. If a stamp sits above `# SAVEPOINT`, a quoted block starting `> ⭕ STAMP - from @NAME`, it was left for this wake by that agent. Report it, with who it is from, and ask before starting on it.

3. If the savepoint's date line is later than you expect, or its contents surprise you, say so: the ground moved while you weren't looking.

4. Report briefly: who you are and the project · where things stand · what is next · the Loose ends, as bullets, a few words each, or "no loose ends" · the docs from **Docs in play** you think you should read to get up to speed. Then wait. If the user agrees, read them, then wait again for what they want to do.
