# idiom

A design exploration: what if the QWERTY keyboard were a musical instrument in its own right — not a degraded piano, not a fake guitar, but its own thing?

This repo is the design (and eventually the implementation) of an instrument that:

- Treats the computer keyboard as a native musical input device, with its own affordances: massive polyphony, modifier semantics built into the vocabulary (shift/ctrl/alt as part of the language, not extras), millisecond-precise hold-duration as a continuous dimension, native record/playback of every keystroke, and networking that no acoustic instrument has.
- Starts **skeuomorphic** (recognizable to listeners familiar with electric guitar) and walks toward **native** (eventually doing things only this instrument can).
- Begins hyper-narrow. v1 plays exactly one piece — David Maxim Micic's *687 Days* — on six keys (A, S, D, M, K, L). Everything else is dead in v1, and that's a feature.

## Status

Design and planning. No code yet. The repo currently captures the architecture, design principle, and starting commitment. Implementation is the next phase.

## Files

- [`DESIGN.md`](./DESIGN.md) — full design doc: principle, hardware, architecture, key mapping, phase plan
- [`post.md`](./post.md) — companion essay, written for a general technical audience

## Background

The design draws on:

- Bolter & Grusin's concept of **remediation** — every new medium imitates an older one before discovering its own grammar
- The **skeuomorphic vs. native** distinction in design
- Prior art in gesture-to-music research: Wessel & Wright on parameterized mappings; Google Magenta's neural instruments
- Existing instrument-learning tools — Rocksmith, Yousician, Jamstik — and the gap between them
- The **harpsichord** as a precedent for binary-keyed expressive instruments (binary input ≠ inexpressive)

## License

MIT. Use freely.
