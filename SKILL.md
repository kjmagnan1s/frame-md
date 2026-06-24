---
name: frame-md
description: Build a reusable, video-native frame.md for a brand using HyperFrames' open-source frame.md system. Use when the user wants a frame.md, asks to turn a website / design.md / brand kit into a HyperFrames design system, says "make a frame.md for <brand>", "refresh the frame.md", "video design system for X", or is about to make HyperFrames videos for a brand and has no frame.md yet. A frame.md is a per-brand artifact made once and reused across many videos, so reach for this whenever a brand's video look needs to be defined or updated, even if the user doesn't say "frame.md" by name. Produces the design source; the superframes skill consumes it and hyperframes authors the composition. Not for authoring a composition (hyperframes) or making a whole video (superframes / website-to-video).
---

# frame-md

> **Built on HyperFrames.** The `frame.md` format, the preset library, the
> composition gates, and the treatment recipe are all the work of the
> **HyperFrames / HeyGen** team, open-sourced under Apache 2.0. This skill is a
> thin local wrapper that runs their system without their login-gated web tool.
> See [references/NOTICE.md](references/NOTICE.md) for full attribution and
> [references/HYPERFRAMES-LICENSE.txt](references/HYPERFRAMES-LICENSE.txt).

A `frame.md` is the frame-scale design system for a brand's HyperFrames videos:
the video-first companion to `design.md` (which is written for web pages). Same
file format, reframed with the 1920×1080 frame as the unit. One file per brand,
reused across every video. The canonical format and resolution rules are in
[references/design-spec.md](references/design-spec.md) (HyperFrames' own spec).

This skill does **not** author compositions (`hyperframes`) or build a whole
video (`superframes` / `website-to-video`). It produces the design source.

## The procedure

HyperFrames' generator is a documented four-step overlay. Run it locally:

### 1. Get the brand atoms
Resolve a source, in this order:
- **A `design.md` / `DESIGN.md`** in the project → read it; its tokens are the
  atoms.
- **A live website/URL** → capture tokens with the `website-to-video` skill (it
  emits `tokens.json` + `design-styles.json`). Do not rebuild a token extractor.
- **Raw brand inputs** (a few hexes, font names, a logo) → ask for the minimum:
  primary + accent colors, display + body fonts, light/dark ground.

### 2. Pick the closest preset
Each preset in [references/frame-presets/](references/frame-presets/) is a
complete `FRAME.md` skeleton: the composition grammar, the cqw type ramps, the
six treatments, the self-audit, already written. Pick the one whose register
matches the brand (the full "pick when" table is in `design-spec.md`):

- **`blue-professional`** — consulting-grade restraint; executive, premium,
  measured. (Finance, B2B, premium SaaS.)
- **`claude`** — warm-editorial, developer-facing; cream paper, scarce accent.
  (Developer tools, AI products, editorial brands.)
- **`coral`** — bold editorial magazine; hard-edged, graphic, confident.
- **`capsule`** — playful editorial; soft, friendly, approachable. (Consumer,
  food, lifestyle, community brands.)

Four are vendored here; HyperFrames ships 13 (see `NOTICE.md`). If none fits,
pull another preset from the upstream repo / `hyperframes-creative` skill, or
start from the closest and re-skin.

### 3. Overlay the atoms (atoms are sacred)
Carry the brand's tokens onto the chosen skeleton **verbatim**: exact hex, font
family, weight, radius. Never invent or round an atom. What you keep from the
preset is its *grammar* — the cqw ramps, the gates, the treatment structure, the
motion ceiling. What you swap in is the brand's *atoms* and voice. This is the
whole move: "atoms are sacred, composition is free, numbers come from the
script."

### 4. Adapt the treatments and entities
- Rewrite the six **Frame Treatments** so their focal content reflects the
  brand's real features (e.g. a SaaS product's data plate might become a metrics
  dashboard; a food brand's a menu/flavor plate).
- Build an **Approved Entities** list from the source: the real wordmark,
  tagline, approved labels, contact strings, and the brand's say/don't-say
  lexicon. Keep the hard rule: **the frame may not invent figures** — render
  data slots as placeholders until a script supplies them.

### 5. Emit
Write `frame.md` (always lowercase) to the brand's project. Tell the user it's
reusable across every video for that brand. For recurring brands, keep the
canonical copy in that brand's repo.

## Non-negotiables carried from HyperFrames
These come straight from the presets / `design-spec.md`; keep them:

- **cqw, never vw.** Author every frame-relative size in `cqw` against the frame
  container, so it renders correctly at any size and aspect (16:9 / 9:16 / 1:1).
  `vw` inflates whenever the frame isn't full-screen.
- **Ration one accent.** One saturated voice per frame; everything else is
  ground / ink / hairline.
- **Legibility floor.** Load-bearing lines ≥ 1.4cqw (≈27px @ 1920). Smaller is
  colophon and may not carry meaning.
- **Fit-to-measure.** Headline block ≤ 78cqw; step the size by word count.
- **The gates** (the "Frame Craft Bar"): squint (one element dominates 3–6×),
  silence (sparse frames read mostly empty), restraint (the scarce gesture fires
  once), reference (aim at an editorial target, not a SaaS feature grid).
- **One idea per frame**, and run the **Pre-Render Self-Audit** before export.

## References
- [references/design-spec.md](references/design-spec.md) — HyperFrames' canonical
  frame.md format + resolution rules + the full preset "pick when" table.
- [references/frame-presets/](references/frame-presets/) — four full preset
  skeletons (blue-professional, claude, coral, capsule).
- [references/NOTICE.md](references/NOTICE.md) — attribution; how to pull the
  other 9 presets.
