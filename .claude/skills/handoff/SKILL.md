---
name: handoff
description: A savepoint plus precise starting instructions for the next chat, either to continue from exactly this point or to do specific tasks.
disable-model-invocation: true
---

1. Anything in your context but not in the docs is lost when this chat ends. Deal with it now: answer an open question from what you have read, ask the user a question only you know is open, or distill an exploration into a doc.

2. If something mid-flight could be finished in a few minutes, name it and ask the user whether to do it now. Tiny dangling things are worth closing before leaving. In the same message, ask what the user has in mind for next time: continue exactly from here, or start a specific new task. Name any loose end tiny enough to close now. Their answers shape the restart block, and the handoff is the last thing in the session; nothing waits after it.

3. Run `/savepoint` in full.

4. Then add a stamp between `# @NAME` and `# SAVEPOINT`: a quoted block, every line starting `>`, whose first line is `> ⭕ STAMP - from @NAME` with your own name, then a line holding only `>`, then a note that tells a future you who remembers nothing exactly how to start. Either it continues from this point: what we were doing, what is half-done, what was decided, what to do first. Decisions go in their docs before the block is written, never only in the block. Or it precisely describes the task or tasks for the next session. As long as it needs to be. Redundancy with the rest of the savepoint is fine. The next `/savepoint` deletes it.
