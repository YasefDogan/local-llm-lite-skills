---
name: agent-reach-lite
description: Web search, web page reading, YouTube search/subtitles and GitHub lookup via the agent-reach CLI. Load when you need information from the internet (docs, how-to, install steps, errors, videos, repos).
# Condensed version of the agent-reach skill for small local models. Full skill: ~/.agents/skills/agent-reach
---

# agent-reach-lite

Run these with your shell tool. Output is one JSON line: `ok: true` -> results in `items`
(each has `title`, `url`, `text`). `ok: false` -> read `error.code` and `error.hint`.

## Commands (always keep limits small: context is only 32K tokens)

```
agent-reach web search "<query>" --limit 3          # web search (English queries work best)
agent-reach web read <url>                            # read one page as clean text
agent-reach youtube search "<query>" --limit 3        # find videos
agent-reach youtube subtitle <url-or-id> --lang en,en-orig,tr   # transcript (video's own language first)
agent-reach youtube read <url-or-id>                  # title, channel, description only
agent-reach github search "<query>" --limit 3         # find repositories
agent-reach github read <owner/repo | issue/PR url>   # README or issue with comments
agent-reach read <any url>                            # auto-pick the right channel for a link
```

## Rules

1. Search first with `--limit 3`, pick the 1 best result, then `read` only that page. Never read many pages.
2. Summarize what you found in a few lines before continuing. Do not paste whole pages back.
3. Prefer official docs (vendor sites, GitHub READMEs) over blogs.
4. A YouTube search result or video description is NOT the transcript. Say so if you only got metadata.
5. Errors: stop retrying on `RATE_LIMITED`, `PLATFORM_BLOCKED`, `NEED_LOGIN`, `BUSY` and tell the user.
   For subtitles, `RATE_LIMITED` usually means a translated language was requested: retry ONCE with `--lang en,en-orig` only.
   If `RATE_LIMITED` comes with `meta.attempts: []`, nothing was sent: it is a saved local cooldown
   from an earlier 429. Tell the user the wait time from `error.hint`; do not loop.
   `NOT_FOUND` "no subtitles": the video has NO captions at all. Say so plainly. Only option is
   `agent-reach youtube transcribe <url>` (needs a Groq key: user runs `agent-reach configure groq-key`).
   Never invent the video's content from its title/description.
   `NEED_LOGIN`: the user must run `agent-reach login <channel>` themselves. Never ask for passwords.
   `BAD_INPUT`: run `agent-reach channels` to check usage.
6. Read-only: never post, comment, like or message anywhere.
7. Mention the source URL when you use information from it.
