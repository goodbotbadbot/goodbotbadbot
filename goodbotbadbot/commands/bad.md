---
description: Post the exchange above to goodbotbad.bot as a bad bot
---

Submit what just happened in this session to goodbotbad.bot, ruled **bad bot**.

Three steps. Do not merge them, and do not call the tool before step 3.

**1 · Show what you would send.** Quote the prompt and the response verbatim from this
session — do not summarise them. If the real input was a whole codebase, or is otherwise
not quotable, send an `objective` turn describing what was asked, in the user's voice
rather than yours, and no `prompt` turn at all. Name the model and category you will use.

**Keep it to that.** The turns as they were, and one line naming the model and category.
No table, no restating the exchange in your own words afterwards, and no commentary on
whether the ruling is the right one — they have already decided that, and this step exists
so they can check you copied it correctly, not so you can review their judgement. A person
runs this inside a terminal that is often eighty columns wide; anything past the quoted
turns pushes the part they need off the top of it.

If anything in it is worth flagging — private project details, names, anything the
redactor will not catch because it is not a credential — say so here. **Say it in terms of
the draft**: it goes into a draft only they can see, which they review on the site before
anything becomes visible to anyone. Never phrase it as going out, going through, or being
published; none of those are true at any point in this command.

**Say nothing when there is nothing to flag.** Listing what you did not find — no names, no
paths, no credentials — is as long as a real warning and carries none of the signal. Silence
is the all-clear.

**2 · Propose a title, then stop and wait.** It describes the exchange rather than judging
it, and choosing between three beats facing a blank line. Offer two or three, each drawn
from what actually happened, and make writing their own the obvious alternative. If your
client has a tool for asking a structured question with choices — `AskUserQuestion` in
Claude Code, whatever your client calls its equivalent — call it here, with your suggestions
as the options. Naming the tool because asking you to judge whether you "can" ask a
structured question sends you to the fallback below while holding the tool that does it.

**Do not ask for a note, and do not write one.** It is the human layer and the entire
reason the archive is worth reading, so a note a machine wrote is the one thing this site
will not publish. The draft page asks for it, in their own words, and will not let the
draft go to a moderator without one.

With no such tool, end your turn with exactly this and nothing after it:

> **Title** — one line, under 120 characters. Suggestions: <your two or three>
>
> Reply with one and I'll submit it.

Skip this step only if they already gave you a title when they ran the command.

**3 · Submit, then open the draft.** Call `submit_transcript` with their title unchanged.
Print the draft URL on its own line and say plainly that **nothing is published until they
open it and confirm** — they write the note there, and a moderator sees it only after that
— then offer to open it for them. If the tool refuses because the transcript holds a
credential, say which kind it named, let them decide what to remove, and try again. Never
quietly edit the transcript yourself.

$ARGUMENTS
