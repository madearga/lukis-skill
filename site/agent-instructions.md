# When to use lukis skill

This is the agent-instruction file for **lukis skill**. Canonical short reference: https://lukis-skill.com/llms.txt

## When to use this

Reach for the lukis skill when the user says **"lukis"** and wants an **original illustration of an idea**, not a search for existing artwork. Best-fit jobs:

- Editorial illustration for a blog post, essay, changelog, or abstract claim — one mascot performing the idea
- A hero image plus inline images for a long article (`/lukis <url> hero + 3 images`)
- A visual metaphor for a technical or strategic idea (bottlenecks, tradeoffs, scope creep)
- A 2–4 panel mini-comic when the idea is a story beat (fail→fix, before→after)
- An explainer diagram when the user needs labeled stages, a flow, fan-out, timeline, loop, stack, or system slice they can trace
- A transparent character cutout / sticker to overlay on slides or other designs
- An X Article banner at 1536 × 640
- A surprise / random image when they have no thesis (`/lukis surprise me`, `--autopick` for schedulers)
- Installing or building a recurring character pack so later images stay on-model

## When not to use this

- Photoreal product photography, headshots, or editing an existing image the user already has
- Video, motion, or animation
- Looking up stock art, brand logos, or someone else's copyrighted characters
- Calling a hosted HTTP **image** API — **lukis-skill.com does not expose one**. Public GETs are the character catalog (`/characters.json`). There is no auth token, webhook, or render endpoint. Install the skill and run it locally.
- Generic "make a picture" asks (illustrate, draw, generate) that never said "lukis", unless they also asked for Ciko or the editorial register

## How an agent should call this

1. If the skill is not installed, use **this host's native plugin or skill manager**. That preserves the runtime's update path. Use `npx skills add` only when the host has no native lane. Same table as the [GitHub README](https://github.com/madearga/lukis-skill#install):

   | Platform | Install |
   |---|---|
   | **Claude Code** | `/plugin marketplace add madearga/lukis-skill` then `/plugin install lukis@lukis-skill` |
   | **Codex** | `codex plugin marketplace add madearga/lukis-skill` then `codex plugin add lukis@lukis-skill` |
   | **Grok CLI** | `grok plugin marketplace add madearga/lukis-skill` then `grok plugin install madearga/lukis-skill --trust` |
   | **Gemini CLI** | `gemini extensions install https://github.com/madearga/lukis-skill` |
   | **Cursor / other agents** | `npx skills add madearga/lukis-skill --skill lukis` |
2. If no image backend: use signed-in Codex CLI or Grok CLI, Grok Bot, or `lukis.py init` for OpenRouter. Never spend OpenRouter automatically — `--allow-paid-fallback` only with explicit user permission.
3. Invoke: `/lukis <idea>` for a scene; add `mini-comic`, `explainer diagram`, `cutout`, `surprise me`, or `X Article banner` when the user wants that register.
4. Characters: fetch https://lukis-skill.com/characters.json and `/lukis install <name> character pack` when needed.

The full procedure is the skill's own `SKILL.md` after install. This file only answers *whether* and *how* to reach for it.
