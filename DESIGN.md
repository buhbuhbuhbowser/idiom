# idiom — design doc

A new musical instrument designed around the affordances of a regular computer keyboard, treated as its own thing rather than a degraded piano or fake guitar.

---

## Design principle: skeuomorphic-to-native curve

Per Bolter & Grusin's *remediation* concept: every new medium imitates an older one before discovering its own grammar. Don't fight this. Start guitar-skeuomorphic (so a recognizable thing can be played on day 1) and walk toward native as the vocabulary builds.

What's native to a computer keyboard:

- **Massive polyphony** — 104 keys simultaneously available, beyond any acoustic instrument.
- **2D spatial layout** — rows and columns, gesture-able like a grid.
- **Modifier semantics built in** — shift/ctrl/alt aren't extras, they're part of the vocabulary. Key vs. shift+key vs. ctrl+key = three musical events on the same physical key.
- **Hold-duration as a dimension** — millisecond-precise capture, so press duration becomes a real expressive parameter.
- **Native record/playback** — every keypress is a timestamped event. Loops, layering, replay are default, not bolt-ons.
- **Networking** — the only instrument where another player a continent away can be co-present in real time.

What's missing relative to guitar:

- Per-key pressure / velocity (unless velocity-sensitive keys)
- Continuous bend / vibrato in the analog sense
- Pick-attack timbral variation
- Physical resonance / sympathetic vibration

The framing flip: stop treating these as deficiencies. Treat them as constraints around which the instrument's expressive language develops. The harpsichord precedent — a binary-keyed instrument with centuries of sophisticated repertoire — proves binary inputs can be expressive. The vocabulary just lives elsewhere (timing, ornamentation, polyphony, voicing) than it does on guitar.

---

## Hardware: QWERTY half-keyboard

A standard half-size QWERTY keyboard, not a gaming keypad like the Razer Tartarus. Reasoning:

- The instrument *is* the QWERTY layout itself — universal motor memory of where keys are.
- Modifier keys (shift/ctrl/alt) are native to QWERTY and structurally part of the design.
- Programmability matters less when the keys' physical positions are themselves the meaningful units.

---

## Approach: A.5 — recorded sequences + transformation operators

Between exact-playback (A) and full ML-learned mapping (C), the tractable middle:

- **Each piece you play becomes a stored named sequence** — a "macro" in motor vocabulary.
- **A small set of operators transforms stored sequences in real time** — transpose, time-stretch, layer, mode-shift.
- **No ML required.** The system is "stored sequences + a small set of transformations that act on them."

This matches a "designing in song-space" intuition: 687 Days establishes a region of input-space; Nothing Else Matters extends a different region; modifier keys connect them. The instrument is a *space of stored gestures with transformations between them*, not a fixed key-to-pitch mapping.

---

## Mode-shift as a native affordance

Modifier keys don't just transpose — they switch *which piece-space you're in*. Tab might mean "we're now in Nothing Else Matters space," and pressing the same physical keys produces different musical events depending on which song-space is active. This "modulating between songs" mid-performance is a native affordance impossible on guitar (no mid-song retuning). It's a primitive specific to this instrument.

---

## v1: the 687 Days machine

The starting commitment is hyper-narrow. Don't build a general-purpose instrument — build "the 687 Days machine." Six specific keys, ergonomically chosen, mapping to the six notes/events that show up in the simplified intro loop. Everything else on the keyboard is dead in v1, and that's a feature, not a bug. The instrument has one job; the rest of the keyboard is the unused workshop.

### The six keys

```
Left hand (home row):     A  S  D       ← pinky, ring, middle
Right hand (mostly home): M  K  L       ← index (down 1 row), middle, ring
```

Both hands engaged, hands stay anchored, minimum reaching. The specific key→pitch mapping gets fixed by recording what feels right while listening to / imagining the song, then committing to whatever six pitches show up.

### Modifier ideas (deferred until v2+)

Sketched for the future architecture but NOT part of v1. v1 has zero modifiers — six keys, six notes, that's it. Modifiers come in once a second song needs to be added.

- **shift + key** → bend up
- **ctrl + key** → palm mute / short note
- **alt + key** → octave up
- **hold key** → sustain (release = note end)
- **space** → separate pick trigger
- **tab** → mode-shift between piece-spaces
- **enter** → start/stop loop record

### The future envelope (not v1)

If full expansion ever happens, the maximum mapping looks like:

```
1 2 3 4 5 6 7 8 9 0       ← modifiers / mode switches
q w e r t y u i o p       ← string 1, frets 0-9
a s d f g h j k l ;       ← string 2, frets 0-9
z x c v b n m , . /       ← string 3, frets 0-9
```

But v1 uses only six of those keys. Grow into the rest as actual repertoire demands, not preemptively.

---

## Open design questions

- **How does a new song get added to the vocabulary?** Played once and recorded, with the system storing its keystroke pattern? Or composed directly in the instrument's notation?
- **What transformations beyond the initial set are useful?** Reverse, mirror, layer-with-self, harmonize-up-a-fifth?
- **What's the smallest piece of repertoire that proves the instrument exists?** A 30-second composition designed *for* it, demonstrating 2-3 affordances impossible on guitar.
- **How are simultaneous-multi-piece states handled?** Chords across song-spaces — does that mean anything musically?
- **Does the system listen to itself?** Live-looping is in the design — the instrument hears its own past output.

---

## Phase plan

1. **v1: the 687 Days machine (an evening)**: VirtualMIDIPiano or AutoHotkey + LoopMIDI → soft synth (Spitfire LABS, free electric guitar patches). Map A/S/D/M/K/L to six pitches that play the simplified 687 Days intro. Other keys do nothing. Press the six keys, hear the song. Existence proof, narrow.
2. **v2: a second song (later)**: Add Nothing Else Matters or another piece. Decide whether it claims new physical keys or reuses the same six with a mode-shift modifier (Tab). The first decision point where the modifier semantics start doing real work.
3. **v3: A.5 architecture (a project)**: Generalize the pattern. Stored sequences + transformation operators. Record songs as sequences, build operators (transpose, time-stretch, layer, mode-shift), modulate between piece-spaces.
4. **v4+: repertoire (ongoing)**: Compose pieces *for* this instrument, not transposed in from elsewhere. Each new piece tells you what the instrument actually wants to be.

The goal of v1 isn't a working instrument — it's a single moment: pressing one of those six keys and hearing 687 Days. That moment is the existence proof and the motivational hook. Everything in v2+ gets evaluated against whether it preserves and extends that moment.
