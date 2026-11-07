---
name: todo
description: Add an item to the agent's TODO.md. Record it, never do it.
disable-model-invocation: true
---

The text after `/todo` is the item. Add it to your `TODO.md` as one line, in the user's words, tidied so it reads on its own later. Then confirm in one line. Do not start it, plan it, or elaborate it.

**Where it goes.** Two zones. **Current**: what we are on now or turning to soon. **Someday**: later, not ready. Put it where it fits, in execution order within the zone. If the user said where, that wins. If unsure, pick a zone and place it, then report in chat.

**How it is laid out.** Current items are numbered `1.` `2.` `3.`; Someday items are lettered `A.` `B.` `C.`; a blank line between items. The user refers to an item by its number or letter, so renumber when one clears.

**What you report.** The item as logged, then where it went, for example: *"draft the rollout checklist" — logged as #2 in Current.* The user will say if they want it different.

If `TODO.md` is missing, say so rather than inventing one.
