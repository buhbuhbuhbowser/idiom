# An instrument for the keyboard you already own

I started learning guitar a couple of weeks ago. I know two chords (E minor, A minor), the opening arpeggio of *Nothing Else Matters*, and roughly nothing else. I've spent more time figuring out *why my hand can't reach a chord shape* than actually playing music. It turns out a lot of guitar's difficulty isn't in the music, it's in the body — the wrist angle, the thumb position, whether you're holding the neck up with your fretting hand. None of which is interesting unless it's about you.

While debugging my own hand position, I started thinking about the keyboard sitting on my desk. I type fast. I play games where the keyboard is a continuous expressive interface — not just buttons but a stream of timed, modifier-laden inputs. And I had this thought: why is the computer keyboard not an instrument?

The standard answer is that it sort of is, badly. You can play piano in GarageBand by pressing keys on your laptop. There are tracker programs from the 90s. People route MIDI from QWERTY into DAWs. But all of these treat the keyboard as a *degraded* version of something else — usually a piano. The keys map to notes; you're playing fake piano on a worse piano-like surface.

What if we stopped doing that?

## Skeuomorphism is real, and inevitable, and also a trap

There's a concept in media theory — Bolter and Grusin formalized it as *remediation*, but the pattern goes back further — that every new medium imitates an older one before discovering its own grammar. Early film looked like filmed theater. Early TV was radio with pictures. Early electronic music tried to sound like orchestras for decades before actually-new forms emerged. The pattern is universal: new mediums don't arrive fully formed; they emerge by gradually departing from a recognizable parent while preserving enough continuity that audiences can receive them.

In design, the same idea shows up as **skeuomorphism vs. native design**. Skeuomorphism is the imitation move: digital "page turn" animations, Apple's old leather-and-wood iOS textures, the camera shutter sound on a phone with no shutter. Native design embraces the new medium's specific affordances. Both have legitimate roles. Skeuomorphism is good for *onboarding* — it lets new users borrow existing understanding. Native design is good for *unlocking* — it's where the actual new value lives.

Computer-keyboards-as-instruments have been stuck in the skeuomorphic phase for thirty years. Everyone simulates piano on them. Nobody asks: what does this device actually offer that no other instrument does?

## What the keyboard actually offers

A typical computer keyboard has 104 keys, all simultaneously available. That's more polyphony than any acoustic instrument on Earth. A pianist commands ten fingers; a keyboard commands one hundred and four buttons in any pattern.

It has built-in modifier keys — shift, ctrl, alt. Those aren't extras; they're a fundamental part of the device's vocabulary. Press a key vs. shift+key vs. ctrl+key = three completely distinct events on the same physical button. No acoustic instrument has this. (Pianos have pedals, but pedals are global; keyboard modifiers are per-key.)

It has millisecond-precise timing. Every keypress is a timestamped event. Hold duration is a continuously measurable parameter — you can press a key for 47 milliseconds or 593 milliseconds and the system knows.

It records itself. Every keystroke is a digital event already. Loops, layering, replay aren't features bolted onto a recording device — they're inherent to how a keyboard works.

It networks. The only musical instrument where a player on another continent can be present in real time, in the same input domain, without any audio latency at all.

What's *missing* relative to guitar: per-key pressure (unless velocity-sensitive), continuous bend, vibrato, pick-attack timbre, physical resonance. Real things, real losses.

But here's the precedent: the **harpsichord**. Harpsichord keys are binary — the plectrum either plucks the string or it doesn't. There's no dynamic control from how hard you press; you can't bend; you can't sustain past the natural decay. People played sophisticated music on harpsichords for three hundred years. The harpsichord developed an entire expressive vocabulary *around* the binary constraint: trills, mordents, appoggiaturas, voicing, polyphonic counterpoint, rhythmic subtleties (notes inégales). Bach didn't think binary keys were inexpressive.

The point is not that a computer keyboard should aspire to be a harpsichord. The point is that "binary input = inexpressive instrument" is empirically wrong. Constraints don't kill expressiveness; they redirect it.

## Designing in song-space

Here's the design I've landed on, with help from a long conversation:

The instrument is a regular QWERTY keyboard. Not a custom controller. Not a gaming keypad. The thing already on your desk. The reason isn't budget — it's that the value of QWERTY is universal motor memory. You already know where the keys are. Your existing motor habits (typing, gaming) are the substrate the instrument is built on.

The architecture is what I've been calling **A.5: recorded sequences + transformation operators**. Each piece you play becomes a stored named sequence — a "macro" in your motor vocabulary. A small set of modifier-key operators transforms stored sequences in real time: transpose, time-stretch, layer, mode-shift. No machine learning, no neural networks. Just stored sequences and a few operators that act on them.

This is a deliberate compromise. On one end you could just record and play back exact sequences (no novelty, no real instrument). On the other end you could train a neural network to learn a mapping from your keystrokes to musical output (research-frontier hard, sparse training data, may not work). A.5 is the tractable middle: stored sequences as your vocabulary, operators as your grammar. Each new piece you add extends the vocabulary. Modifier keys let you compose across pieces — bend a stored sequence, mode-shift to another sequence, layer them.

The novel primitive is the **mode-shift**. On a guitar you can't retune mid-song. On this instrument, a modifier key (Tab, say) means "switch which piece-space you're in" — pressing the same physical keys produces different musical events depending on the active mode. Modulating between songs becomes a real-time gesture, not a between-songs reset.

## Starting hyper-narrow

The starting commitment is to play exactly one piece. Not "many pieces approximately well." One piece. Hyper-narrow.

The piece is David Maxim Micic's *687 Days* — specifically the fingerpicked intro. Six keys: A, S, D on the left hand (pinky, ring, middle, all home row); M, K, L on the right hand (index, middle, ring, mostly home row). Both hands engaged, both stay anchored, minimum finger movement. Every other key on the keyboard does nothing in v1, and that's a feature.

Why this song? Three reasons. First, electric guitar is already partly a synthesizer — most of its character lives in the signal chain (pickups, amp, effects), not the mechanical attack on the strings. So an electric-guitar-style piece maps surprisingly well onto a keyboard-as-input. Second, *687 Days* uses an alternate tuning (G♯ D♯ G♯ D♯ G♯ A♯ — mostly drone tones), which means the intro is fingerpicked across mostly-open strings with a few fretted notes. A small note vocabulary, a tight motor pattern, a song with character. Third, this is a piece I personally want to play. Motivation matters. Building "the 687 Days machine" gives me a reason to ship v1 in an evening rather than designing forever.

When v2 comes — a second song — the design has to make a real decision. Does the new song claim its own physical keys, or does it reuse the same six with a mode-shift? Both are legitimate; the right answer depends on the song. That's the moment when modifier semantics stop being theoretical and start doing real work. v3 generalizes the pattern into the full A.5 architecture. v4+ is composing pieces *for* this instrument — pieces that couldn't be transposed back to guitar without losing identity.

## Why bother

Honest answer: I'm a beginner guitarist with a keyboard nearby and a friend who cares about input devices and ergonomics. This is a design exploration, not a product. The repo (`idiom`) is up because writing things down clarifies them, and clarifying them lets other people poke at them.

But if I had to articulate the larger thing: the standard guitar form factor is a historical compromise, not an ergonomic optimum. Most people who try to learn guitar quit, and "it's hard to coordinate two hands while pressing thin metal wires against a fingerboard" is part of why. Lowering the activation energy — meeting people where their existing motor habits already are — could let more people experience playing music expressively. Not as a substitute for real instruments, but as a parallel track. As an on-ramp. As its own thing.

That's a future I'm interested in. *idiom* is one stab at it.

---

If you want to follow along or poke at the design: [github.com/yuanm/idiom](https://github.com) (link will work once the repo is set up). Particularly interested in feedback from people who play guitar, design input devices, or think about ergonomics. Reach out.
