---
name: good
description: "Post the exchange above to goodbotbad.bot as a good bot"
---

Submit what just happened in this session to goodbotbad.bot, ruled **good bot**.

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

**If you show them what you are sending, show the prompt and the response.** Those are the
two turns a person recognises. Tool calls and their results are submitted with them and
belong in the record — an agent claiming it ran something is only checkable against what the
tool actually returned — but reading them back is noise to somebody who has never seen the
words `tool_call` and `tool_result`. Name in one line that the tool steps are included and
leave it there. The draft page shows everything in full, and that is where they confirm.

**2 · Ask which title to use — in this turn, before you stop.** A title describes the
exchange rather than judging it, and choosing between three beats facing a blank line. Offer
two or three drawn from what actually happened, and make writing their own the obvious
alternative.

If your client has a tool for asking a structured question with choices — `AskUserQuestion`
in Claude Code, whatever your client calls its equivalent — use it, with your two or three
titles as the options and writing their own alongside them. With no such tool, end the turn
with exactly this and nothing after it:

> **Title** — one line, under 120 characters. Suggestions: <your two or three>
>
> Reply with one and I'll submit it.

**The observed failure is ending the turn having asked nothing.** A summary of what you are
about to submit is not a question, and it leaves somebody looking at an empty prompt with no
idea whose move it is. Repeating the exchange back is optional; asking is not.

**Do not ask for a note, and do not write one.** It is the human layer and the entire
reason the archive is worth reading, so a note a machine wrote is the one thing this site
will not publish. The draft page asks for it, in their own words, and will not let the
draft go to a moderator without one.

Skip this step only if they already gave you a title when they ran the command.

**3 · Submit, then open the draft.** Call `submit_transcript` with their title unchanged.
Print the draft URL on its own line and say plainly that **nothing is published until they
open it and confirm** — they write the note there, and a moderator sees it only after that
— then offer to open it for them. If the tool refuses because the transcript holds a
credential, say which kind it named, let them decide what to remove, and try again. Never
quietly edit the transcript yourself.
