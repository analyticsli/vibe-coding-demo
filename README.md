# Vibe Coding — companion repo

For **"Vibe Coding: Rapid Research Prototyping with AI"**
(UVA Faculty Upskilling, July 2026 — Jingjing Li, McIntire School of Commerce).

This is a working **Claude Code project**, organized the way real ones are —
clone it and everything the live demos used works on your machine:

```
CLAUDE.md            the project briefing the agent reads every session
.claude/skills/      reusable task recipes ("skills") — see literature-feed
site/                the faculty homepage from Demo 1 — the agent fetched the
                     live site, saved it as plain HTML, then redesigned it
                     (the redesign is on Pages + in the commit history)
tools/               openalex_server.py — the MCP server from Demo 2 (~120
                     lines, written by an agent; public OpenAlex API, no key)
feeds/               generated literature dashboards, one HTML file per topic
data/                empty on purpose — in the demo, one prompt asks the
                     agent to write a script that fetches 1,000 GenAI papers
                     from OpenAlex, cleans them up on the way in, and prints
                     a report of what it did
.gitignore           also a lesson: scratch work and SECRETS stay out of repos
```

## Reproduce the demos

1. Install [Claude Code](https://claude.com/claude-code), open this folder.
2. Demo 1: ask the agent to fetch a website you own, save its content into
   `site/`, and redesign it — describe, run, look, correct. Publish with
   GitHub Pages when you like it.
3. Demo 2: connect the literature socket, then ask for a dashboard:

       claude mcp add openalex python3 tools/openalex_server.py

4. The skill: say *"literature feed on [your topic]"* — the recipe in
   `.claude/skills/literature-feed/` runs with its quality rules enforced
   (every number traces to an API response, and the page states its scope).

## About OpenAlex — and its limits

[OpenAlex](https://openalex.org) is a free, open catalog of the world's
scholarly output — ~250M works across all fields — run by the nonprofit
OurResearch (successor to Microsoft Academic Graph). No account, no API key.

Know its coverage limits before you trust an analysis built on it:

- It indexes **metadata and citations, not full text** — and abstracts are
  missing for a meaningful share of records (publisher restrictions).
- **Citation counts differ from Google Scholar / Scopus / Web of Science**
  (typically lower than Google Scholar). Never mix sources in one analysis.
- Coverage is strongest for **DOI-bearing journal articles**; weaker for books
  and monographs (humanities beware), some conference proceedings, non-English
  and regional venues, and the very newest papers (indexing lag).
- Records inherit occasional errors and duplicates from upstream sources —
  one more reason the skill's rule is *verify counts, flag gaps*.

## Your Monday morning

Pick one recurring task from your own work. Point an agent at a **copy** of
the data. Make it show its work. Three habits:
**commit before you let it loose · never put a real key on screen or in a repo ·
read what changed, not how confident it sounded.**
