# Sablon — style pack

Hand-pulled screen print (sablon): flat spot-color inks pressed through a
hand-cut stencil onto heavy cotton paper. A look for **character packs**
(the pack's `Style:` line) suited to opinion pieces, launch posts, and
street-poster energy — the loud, physical voice of the library, and the
house default.

## Prompt blocks (replace the template's LINE LANGUAGE and STYLE lines)

```text
LINE LANGUAGE: draw EVERYTHING — mascot, objects, arrows — with ONE thick, even-width outline with squared terminals (a solid marker pulled through a stencil), flat spot-color fills inside; where two ink layers meet, separate them with a thin sliver of bare paper.

STYLE: HAND-PULLED SCREEN PRINT — flat opaque spot-color inks on heavy cotton paper, one flat tone per shape, NO halftone dots and NO gradients; edges carry a faint hand-cut stencil wobble; only very large fills show faint directional squeegee streaks; a thin bare-paper seam separates neighboring color layers; heavy paper tooth under everything; no photorealism, no digital smoothness.
```

## Palette mapping

- **Paper** ← the palette paper — heavy warm cotton stock, visible in the
  negative space and in the seams between inks.
- **Ink** ← the structure ink: all linework, the darkest shapes, and label
  lettering.
- **Accent** ← the palette accent, pressed as one flat spot color.
- **Secondary** ← the palette's secondary accent as one flat spot color,
  sparing.

Classic default (no palette given): paper `#f6ecd9`, ink `#1d1a15`, accent
chili red `#d4492e`, secondary leaf teal `#1a6e5f`.

PALETTE line: `heavy cotton paper {paper hex} showing through in the negative
space and the seams between inks. Ink {structure hex} for all linework,
forms, and label lettering. Accent {accent hex} as one flat spot color — the
character's accent part + 1–2 elements. Secondary {secondary hex} for one
secondary note only. One flat tone per shape, no halftone.`

## Character treatment

The mascot is printed like everything else — flat spot-color shapes inside
the thick outline. Dark-capable characters → ink-filled body with paper dot
eyes; light-bodied characters → paper-tinted body with ink outline and ink
eyes. The accent part is one flat accent shape; a thin bare-paper seam may
separate the accent shape from the body outline (a print trap) — never an
offset ghost of the outline.

## Labels

Bold hand-lettered block capitals in the ink color on bare paper —
marker-through-stencil energy, slightly irregular, confident, never typeset.

## QA deltas (replace the riso grain checks)

- Flat spot color everywhere — **no halftone dots, no gradients, no gloss.**
- Edges wobble like a hand-cut stencil, but the outline itself stays thick
  and even — no thin scratchy linework.
- Neighboring color layers meet across a thin bare-paper seam — not a
  colored offset halo, not a hard butt joint.
- Squeegee streaks only inside very large fills — never on the mascot or
  small props.
- Accent appears only on the character's accent part + 1–2 elements.

Calibration example (not bundled — fetch the URL): https://raw.githubusercontent.com/madearga/lukis-skill/main/_assets/lukis/sablon-poster-drop.png — study it for flat spot-color discipline, the single thick even outline, and accent restraint; never copy its composition.

Variant note: when deriving a sablon pack from a character whose sheet was
born in another look, the original sheet works directly as the `--ref` — the
style prompt overrides its rendering.
