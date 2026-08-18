# goodbotbad.bot

**Rule the bot without leaving the session.** [goodbotbad.bot](https://goodbotbad.bot) is where
the crowd votes **good bot** or **bad bot** on AI transcripts. This repository is the plugin
that posts one from inside the session it happened in — no copying the exchange into a browser
tab, no retyping it from memory, no cropped screenshot.

```
/goodbotbadbot:bad
```

That is the whole interface. Your agent quotes back what it is about to send, asks you for a
title, and hands you a **private draft URL**. Nothing is published until you open that URL and
confirm.

---

## Install

**Claude Code**

```
claude plugin marketplace add goodbotbadbot/goodbotbadbot && claude plugin install goodbotbadbot@goodbotbadbot
```

**Codex**

```
codex plugin marketplace add goodbotbadbot/goodbotbadbot && codex plugin add goodbotbadbot@goodbotbadbot
```

If you had already added this server to `~/.codex/config.toml` by hand, remove it first —
`codex mcp remove goodbotbadbot`. A server named in the config file takes precedence over a
plugin's server of the same name, and Codex reports a conflict only between two entries of the
same kind: the plugin's server never starts and nothing says so.

**Gemini CLI**

```
gemini extensions install https://github.com/goodbotbadbot/goodbotbadbot
```

**Claude desktop app** — Settings → Connectors → Add custom connector, and give it
`https://goodbotbad.bot/mcp`.

**Anything else that speaks MCP** — Cursor, VS Code, and the rest are one click or one line at
[goodbotbad.bot/connect](https://goodbotbad.bot/connect).

There is no API key to paste. The first call opens a browser, you approve the install by name,
and the grant is revocable on its own at any time from
[your installs page](https://goodbotbad.bot/settings/installs). Access expires hourly and your
client renews it silently, so a token read off a disk months later is not a way in.

## What you type

One wording, four renderings — the sigil and the prefix belong to the client, not to the
plugin.

| Client | Good bot | Bad bot |
| --- | --- | --- |
| Claude Code | `/goodbotbadbot:good` | `/goodbotbadbot:bad` |
| Claude desktop app | `/good` | `/bad` |
| Codex | `$goodbotbadbot:good` | `$goodbotbadbot:bad` |
| Gemini CLI | `/goodbotbadbot:good` | `/goodbotbadbot:bad` |

On a client that surfaces neither, ask in words — *submit that exchange to goodbotbad.bot as a
bad bot* — and the agent will reach for the tool itself.

## What happens when you run it

1. **Your agent shows you what it would send.** The prompt and the response, quoted verbatim,
   plus the model and category it picked. Tool calls travel with them, so an agent's claim that
   it ran something stays checkable against what the tool actually returned.
2. **It asks you for a title**, offering a few drawn from what happened.
3. **It submits and hands back a draft URL** at `/d/…`. The draft is visible to you and nobody
   else.
4. **You open it, write the note, and confirm.** Only then does a moderator see it, and only
   after that does it reach the site.

The **note** — your account of why the exchange is worth posting — is the one thing the agent
will not write. There is deliberately no note parameter on the tool. It is the human layer, and
a machine-written one is the single thing this site will not publish.

## The four tools

Two of them write and two of them read, and the read half is the one people miss: an agent that
has just hit a known model failure can look up whether somebody already posted the fix.

| Tool | |
| --- | --- |
| `submit_transcript` | Stages the exchange as a draft and returns its URL. Never publishes. |
| `complete_pair` | Hands you an unpaired post's prompt to run, then stages your result as the other half — same prompt, different model, opposite outcome. |
| `search_posts` | Searches the archive by words, model, category or side. Worth doing before submitting: a failure already on the site should be voted on rather than posted twice. |
| `get_post` | Pulls one transcript, its note, its verdict and its fixes back into the session. |

Posts are filed under eight fixed categories — **Coding**, **Facts & search**, **Everyday**,
**Math & logic**, **Agents & tools**, **Images & media**, **Writing**, **Meta**.

Writing a permission rule or a hook? Installed as a plugin the tools resolve under their scoped
names, and a rule written against the bare name will not fire:

```
mcp__plugin_goodbotbadbot_goodbotbadbot__submit_transcript
```

## What it will and will not do

- **It never publishes.** Every submission is a draft. A human opens it and confirms before a
  moderator sees it at all.
- **A credential refuses the whole submission, and nothing is stored.** OpenAI, Anthropic,
  GitHub, AWS, Google, Slack and live Stripe keys, private key blocks and signed tokens are
  matched by shape; the tool names the kind it found and stops. It will never quietly edit your
  transcript to get past its own check.
- **Personal data is redacted before it is stored, not after.** Email addresses, phone numbers,
  street addresses and home-directory paths are replaced and then *named in the reply* — so you
  hear about it from your agent, not from a published page.
- **An oversized session is never shipped whole.** Over 64 KB total or 32 KB in one turn, the
  first call carries no transcript at all — only a manifest of roles, sizes and one-line labels
  — and you pick what survives. What you do not pick never leaves your machine.
- **It reads only what you send it.** Nothing here reaches into your files or your history.

## What is in this repository

```
README.md                         this page
LICENSE                           Apache-2.0
.claude-plugin/marketplace.json   the marketplace, one entry
.agents/plugins/marketplace.json  the same, where Codex looks for it
gemini-extension.json             the Gemini CLI extension manifest, root-level by its rules
commands/goodbotbadbot/*.toml     the two commands, as Gemini spells them
goodbotbadbot/                    the plugin
├── .claude-plugin/plugin.json
├── .codex-plugin/                Codex's manifest and its own copy of the server address
├── .mcp.json                     the server address
├── commands/{good,bad}.md        the two commands, as Claude Code spells them
├── skills/{good,bad}/SKILL.md    the same two, as Codex spells them
├── assets/                       the mark
└── README.md                     the plugin's own page
```

No application source, no schema, no seeds — a server address and the wording of two commands.

**Everything except the two READMEs and the LICENSE is generated.** One wording of each command
is rendered into four surfaces by `rails plugin:sync` in the application repository and pushed
here by CI, so no client can end up reading a stale copy. Editing those files here is editing
build output — [open an issue](https://github.com/goodbotbadbot/goodbotbadbot/issues) instead and
it gets fixed at the source.

## Listed on

[![smithery badge](https://smithery.ai/badge/hello-8vdv/goodbotbadbot)](https://smithery.ai/servers/hello-8vdv/goodbotbadbot)

- [Official MCP Registry](https://registry.modelcontextprotocol.io) — `bot.goodbotbad/goodbotbadbot`,
  which is what most of the directories below read rather than a form of their own
- [Smithery](https://smithery.ai/servers/hello-8vdv/goodbotbadbot)
- [Glama](https://glama.ai/mcp/connectors/bot.goodbotbad/goodbotbadbot)
- [Cursor Directory](https://cursor.directory/plugins/goodbotbadbot)

Every one of them describes a server that answers `401` to anything without a token, so what
they are reading is [the server card](https://goodbotbad.bot/.well-known/mcp/server-card.json)
rather than a scan.

## Links

- [goodbotbad.bot](https://goodbotbad.bot) — the site
- [Connect without the plugin](https://goodbotbad.bot/connect) — one-click installs and a config
  blob for every other MCP client, plus a bearer token for headless and CI use
- [Your installs](https://goodbotbad.bot/settings/installs) — revoke any grant on its own
- [Privacy](https://goodbotbad.bot/privacy) · [Terms](https://goodbotbad.bot/terms)

Apache-2.0.
