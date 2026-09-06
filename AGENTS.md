# lukis-skill

The canonical home of **lukis**, a cross-platform AI agent skill (`SKILL.md`
format) installable through runtime-specific lanes: the generic skills CLI
(`npx skills add madearga/lukis-skill --skill lukis`, works across Claude
Code/Cursor/Codex and other Agent-Skills runtimes), and platform-native
plugin manifests in this repo (`.claude-plugin/`, `.codex-plugin/`,
`.cursor-plugin/`, `.grok-plugin/`, `gemini-extension.json`).

This guide is for anyone (human or agent) editing the repo. Keep it accurate
when conventions change.

Lukis descends from
[tvchow's illo](https://github.com/tmchow/illo-skill) (MIT © Trevin Chow): it
began as an identity fork, and the engine (`skills/lukis/scripts/lukis.py`)
has since been rewritten in this repository. The architecture, methodology,
and reference-doc system still follow illo's design and are credited in
`skills/lukis/NOTICE` — the notice is a license obligation, not branding, and
stays. The name, mascot (Ciko), default look (sablon), and house palette
(pasar) are lukis-original.

## Repo layout

**The skill lives in `skills/lukis/`, deliberately not at the repo root.**
Installers copy the entire skill directory verbatim, so the skill dir must
contain only what every install should ship; repo meta and docs-only images
stay outside it.

- `skills/lukis/SKILL.md` — required. The agent-facing instructions.
- `skills/lukis/README.md` — required. The human-facing landing page.
- `skills/lukis/references/` — deep material loaded on demand, including the
  eighteen look definitions in `references/styles/`.
- `skills/lukis/scripts/` — the engine (`lukis.py`) and the Hermes
  asset-repair preflight.
- `skills/lukis/assets/` — bundled binary assets plus `checksums.txt`, a
  generated manifest (never edit by hand; see Binary assets below).
- `_assets/lukis/` — docs-only images linked by raw URL (logo, calibration
  examples, README embeds). They live outside the skill directory so they
  never ship with installs.
- `tests/` — pytest suite for the engine.
- Root `README.md` — the repo landing page; root `LICENSE` — MIT.

## SKILL.md frontmatter

Required: `name`, `description`, `version`.

- `name` — `lukis`, matching the directory.
- `description` — third person, ≤1024 characters, with **specific** trigger
  phrases and an explicit do-not-trigger clause (lukis must not hijack
  generic illustrate/draw requests). It states only the look *count*
  ("eighteen bundled looks") — bump the number when adding a look, never
  enumerate them.
- `version` — inside the `# x-release-please-start-version` /
  `# x-release-please-end` markers, kept in lockstep with `version.txt` by
  Release Please. Do not edit by hand.

## Binary assets and checksums

`skills/lukis/assets/checksums.txt` pins every bundled binary (SHA256 +
pinned commit). `doctor` verifies them on every preflight, so **any change
to a bundled binary requires regenerating the manifest**:

```bash
python3 tests/regen_asset_checksums.py  # or hand-follow the header format
```

Keep the format in the file header comment intact; the pinned-commit column
exists so already-installed copies can still re-download originals.

## Versioning

Release Please owns versions: `version.txt` is the source of truth, and the
manifests (`.claude-plugin/`, `.codex-plugin/`, `.cursor-plugin/`,
`.grok-plugin/`, `gemini-extension.json`) plus the `SKILL.md` version marker
update through its release PR. Tags are `v<version>`.

## Community character packs

`DEFAULT_PACKS_REPO` in `skills/lukis/scripts/lukis.py` points at the
lukis-native catalog (`madearga/lukis-characters`) — packs carry their own
styles, so they render correctly under lukis. The upstream illo catalog
(`tmchow/illo-characters`) stays installable via `packs install --repo
https://raw.githubusercontent.com/tmchow/illo-characters/main <name>` (or
`--all`); every style its packs use is bundled here. Override per user with
the `packsRepo` config key.
