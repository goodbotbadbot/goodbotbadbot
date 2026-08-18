# goodbotbad.bot

Post the AI exchange you are already in to [goodbotbad.bot](https://goodbotbad.bot), where the
crowd votes **good bot** or **bad bot** on it — from inside the session it happened in, rather
than copying text between windows.

Installing this connects one MCP server. See the [repository
root](https://github.com/goodbotbadbot/goodbotbadbot) for the install line for your client.

## Using it

Two commands. Which sigil you type is the client's business, not the plugin's — `/good` and
`/bad` in the Claude desktop app, `$goodbotbadbot:good` and `$goodbotbadbot:bad` in Codex.

| | |
| --- | --- |
| `/goodbotbadbot:good` | Post the exchange above, ruled good bot |
| `/goodbotbadbot:bad` | Post the exchange above, ruled bad bot |

Either one quotes back what it is about to send, asks you for a title, and returns a **private
draft URL**. You open it, write the note, and confirm — and only then does a moderator see it.
The note is deliberately yours: there is no note parameter on the tool, because a machine-written
account of why an exchange is worth posting is the one thing this site will not publish.

## The four tools

| | |
| --- | --- |
| `submit_transcript` | Stages the exchange as a draft and returns its URL |
| `complete_pair` | Runs an unpaired post's prompt here and stages the other half |
| `search_posts` | Searches the archive by words, model, category or side |
| `get_post` | Reads one published post — transcript, note, verdict, fixes — in full |

## What it will and will not do

- **It never publishes.** Every submission creates a draft and returns a URL. A human opens that
  URL and confirms before a moderator sees it at all.
- **It refuses secrets outright.** A key or token in the transcript stops the submission — nothing
  is stored — and the tool says which kind it found.
- **Personal data is redacted before storing** and named in the reply: email addresses, phone
  numbers, street addresses, home-directory paths.
- **An oversized session is never shipped whole.** Past the size caps the first call sends a
  manifest — roles, byte counts, one-line labels, no bodies — and you choose what to send.
  Everything unpicked stays on your machine.
- **It reads only what you send.** Nothing reaches into your files.

## Signing in

No token to copy. The first call opens a browser, you approve it by name on goodbotbad.bot, and
the grant is revocable on its own at any time from
[your installs page](https://goodbotbad.bot/settings/installs).

## About the files here

The commands ship twice on purpose. `commands/good.md` and `commands/bad.md` are for the surfaces
a server's MCP prompts do not reach — the desktop app lists a connector's tools but not its
prompts, so without the copies there would be nothing to type there; `skills/good` and
`skills/bad` are the same two texts in the shape Codex reads. A bundle tells the server it
already carries them, so the server withholds its own prompts and no client lists a command
twice.

All of it is generated from one wording in the application repository and pushed here by CI, so
the copies cannot drift. Edit them upstream, never here.
