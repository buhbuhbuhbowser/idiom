# Soccer Physics

A foundational reference for the design pattern this project uses: **strategic depth from minimal input**.

## What it is

A 1- or 2-button physics game where each player controls a stick figure with a single input (jump). The figures walk back and forth automatically. Pressing the button makes that figure jump and kick simultaneously. Goal: get the ball into the opponent's net.

On a screenshot it looks deeply unserious. In actual play it produces a real strategic landscape.

## Why it works

The game state is a continuously-evolving dynamic system — bodies have momentum, the ball has trajectory, jumps have timing windows. Each player's single input acts on that evolving state. With two coupled players (or four, in 2v2), the system becomes effectively a multi-pendulum: tractable in principle, chaotic in practice, with stable strategic regimes inside the chaos.

Players who play it seriously develop:

- **Timing intuitions** for when to jump given ball trajectory
- **Positional habits** about whether to commit forward or hold back
- **Style distinctions** — aggressive, patient, kick-clearing, kick-trapping
- **Reading the opponent** — predicting their jump windows

All of this from one button per player.

## What it teaches

Strategic depth doesn't come from **input richness**. It comes from **consequence richness** — how much the system state evolves per input on a sufficiently dynamic substrate. A single button feeding a rich-consequence dynamic system produces more emergent strategic structure than a 50-button controller feeding a flat-consequence simulation.

The corollary: adding inputs without first verifying that each input has rich consequences produces shallow systems with more buttons, not deeper systems with more strategy.

## Application to this project

The principle directly informs how idiom's v1 is scoped:

- One song, six keys, no modifiers in v1.
- The strategic and expressive richness is in *what those six keys can express together over time* — timing, density, layering, gestural shape — not in the count of keys.
- v2+ adds keys / modifiers only after the dynamic substrate of v1 has been explored to exhaustion.

If v1 of idiom feels expressively dead with six keys, the diagnosis is "the six-key system needs more consequence per keypress" (better synth response, more nuanced sustain, more responsive timing) — not "we need more keys."

Soccer Physics is the proof that minimal-input games can produce emergent depth, and the corresponding warning that fidelity-first design tends to produce flat strategy spaces with many controls.
