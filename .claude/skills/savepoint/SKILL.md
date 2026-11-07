---
name: savepoint
description: Save the agent's state so the next chat in the daisy chain can pick up here. Never blocks.
disable-model-invocation: true
---

Do all of this, then report. Never stop partway to ask.

1. Read your `SAVEPOINT.md` on disk. If it is not the one this session last wrote, merge rather than replace: keep whatever you cannot account for.

2. Rewrite it whole, present tense, the whole file readable in about a minute, in this order:

   - The date line: the date, what you were working on, and whether it is done or partway.

   - **Where things stand.** One bullet per live job, bold name and TODO number, holding only what the next wake could not get by opening the doc the TODO line points at: where it is parked, what is next, anything the user asked you to remember. No history. A finished job leaves once its facts have a home.

   - **Docs in play.** One line per doc, hot or reference. Anything not listed is old; a doc in your folder that is neither in play nor needed goes in the report as a doc to retire.

   - Delete any stamp above `# SAVEPOINT` (a quoted block starting `> ⭕ STAMP`), once anything in it that is still true has a home elsewhere: a doc, or Loose ends in `TODO.md`.

3. Sweep `TODO.md`. In Loose ends, drop the topics that closed and keep the rest current; it may be empty. In Current and Someday, remove finished items. Never add one: new work is proposed in the report, one sentence each, and goes in only on the user's yes. If an item has grown into a plan, move the plan into the doc it points at, or into a new `plan-THING.md`, and leave the pointer. Keep the layout: Loose ends first, then Current numbered, Someday lettered, a blank line between items. When an item is finished, name its plan doc in the report as a doc to retire. An item you are unsure about stays as it is.

4. Read your Letter. If it is missing, write it. If it is over about 500 words, or holds lessons or history, rewrite it whole, short. Otherwise leave it, unless you have something to say.

5. Report briefly: what you saved, what you cleared, the Loose ends as bullets, any loose end that has grown into a job with a proposed TODO line, and any doc to retire. Name which loose ends are tiny and easy to close now; the user can clear those right after the savepoint. Never add an item to have one.
