# frame-md

Build a reusable, video-native `frame.md` — a brand's frame-scale design system —
for [HyperFrames](https://github.com/heygen-com/hyperframes) videos. This is a
thin local wrapper around HyperFrames' open-source `frame.md` system, so you can
generate a `frame.md` from a `design.md` or a brand without HyperFrames'
login-gated web tool.

## Built on HyperFrames

The `frame.md` format, the preset library, the composition gates, and the
treatment recipe are all the work of the **HyperFrames / HeyGen** team,
open-sourced under Apache 2.0. This skill vendors a subset of their material
**verbatim** and runs their documented overlay procedure locally. **Full credit
to the HyperFrames / HeyGen team.**

- Source: https://github.com/heygen-com/hyperframes (`skills/hyperframes-creative/`)
- What's vendored, and how to pull the rest: [`references/NOTICE.md`](references/NOTICE.md)

## What it does

Runs HyperFrames' four-step overlay: get the brand atoms (a `design.md`, a
`website-to-video` capture, or raw brand inputs) → pick the closest preset →
overlay the atoms verbatim onto that skeleton → adapt the treatments and build
the entity allowlist → emit a lowercase `frame.md`. See [`SKILL.md`](SKILL.md).

## Install

Copy this folder into `~/.claude/skills/frame-md/` (or install it as a plugin
skill).

## License

The vendored HyperFrames material (`references/design-spec.md` +
`references/frame-presets/`) is **Apache 2.0**, © HeyGen — see
[`references/NOTICE.md`](references/NOTICE.md) and
[`references/HYPERFRAMES-LICENSE.txt`](references/HYPERFRAMES-LICENSE.txt). This
repository is distributed under the same Apache 2.0 license.
