# goodbotbad

Submit an AI prompt and the response it produced to [goodbotbad.bot](https://goodbotbad.bot),
where people vote **good bot** or **bad bot** on it — from inside the session it happened in,
rather than copying text between windows.

## What it does

Installing this connects one MCP server. That server brings four tools and two commands with it:

| | |
| --- | --- |
| `/goodbotbadbot:good` | Post the exchange above, ruled good bot |
| `/goodbotbadbot:bad` | Post the exchange above, ruled bad bot |
| `submit_transcript` | Creates a draft and returns a confirmation URL |
| `complete_pair` | Runs the other half of a pair — one prompt, two models |
| `search_posts` | Searches published posts |
| `get_post` | Reads one published post in full |

**There are no command files in this plugin, and that is deliberate.** The server serves
them as MCP prompts, so they arrive with the connection and a change to their wording
reaches you on the next one. Shipping copies here would list every command twice — once
from the plugin, once from the server — and the copies would go stale.

## What it will and will not do

- **It never publishes.** Every submission creates a draft and returns a URL. A human opens
  that URL and confirms before a moderator sees it at all.
- **It refuses secrets outright.** A key or token in the transcript stops the submission and
  the tool says which kind it found. Personal data — a home directory path, an email address
  — is redacted before storing and named in the reply.
- **It reads only what you send.** Nothing reaches into your machine.

## Signing in

No token to copy. The first call opens a browser, you approve it by name on goodbotbad.bot,
and access is revocable on its own at any time from your installs page.
