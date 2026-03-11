# Design Document: Audio Overview-Inspired OpenPeon Sound Pack

## Purpose

Create an OpenPeon-compatible sound pack that captures the recognizable cadence, banter, and mildly overproduced "podcast" energy of Google's Audio Overview / "deep dive" format without pretending to be an official Google product or reproducing Google-owned voices.

This pack should feel immediately familiar to people who have used NotebookLM or Gemini Audio Overview: upbeat co-host chemistry, constant signposting, faux-spontaneous reactions, and a tendency to oversell the importance of ordinary material.

## Naming Research

### What Google calls the feature

Based on Google's own product and help pages, the relevant official names are:

- `Audio Overview`
- `"Deep Dive" Audio Overview` for the customizable NotebookLM variant
- `AI hosts` or `two AI hosts` for the speakers

### What Google does not appear to call them

I found no official public names for the two host characters. In the public sample transcript, they are labeled only as `Speaker 1` and `Speaker 2`. In product pages and help docs, Google consistently refers to them generically as `AI hosts`.

Implication: the sound pack should not invent lore that implies official Google character identities. Treat them as archetypes, not named canon characters.

## Product Goal

Build a comedic sound pack for coding events that preserves the funniest parts of the Audio Overview vibe:

- over-eager transitions
- "Okay, but here's the really interesting part..."
- fake-host chemistry
- mild astonishment at routine information
- recap language that treats mundane events like a major insight

The result should be amusing in short bursts inside an IDE. It should not become so long or so literal that it slows down the coding loop.

## Non-Goals

- perfect voice cloning of Google's actual generated voices
- use of Google's trademarks in a way that implies endorsement
- reproduction of long transcript excerpts
- making every event a full mini-podcast

## Audience

- OpenPeon users who recognize NotebookLM / Gemini Audio Overview patterns
- developers who enjoy ironic, talky, high-context notification sounds
- users who want novelty more than minimal distraction

## Source Material To Study

Use only publicly available Google material and your own generated imitation scripts.

Recommended reference sources:

1. Google's NotebookLM Audio Overview launch post
2. Google's NotebookLM customization update
3. Gemini Audio Overview help docs
4. NotebookLM Audio Overview help docs
5. The public sample transcript Google linked from its launch post

These sources are enough to identify recurring traits:

- two-host structure
- one host plays the curious/reactive role
- one host plays the explanatory/grounding role
- recurring phrases like "deep dive," "what this actually means," "let's back up," "in a nutshell"
- lots of agreement markers: "right," "exactly," "totally," "okay"
- exaggerated stakes for normal informational tasks

## Sonic Character Model

The pack should emulate the format, not the exact voices.

### Host archetypes

#### Host A: The Enthusiastic Reactor

- more interruptions
- more "wait, seriously?" energy
- asks the obvious audience question
- uses filler and reaction phrases
- sounds delighted, skeptical, or theatrically overwhelmed

#### Host B: The Confident Explainer

- introduces structure
- reframes and summarizes
- lands the "in a nutshell" explanation
- transitions toward conclusions
- sounds slightly calmer and more authoritative

### Core performance traits

- conversational overlap illusion, but keep clips clean enough for notification use
- compressed, bright, podcast-like EQ
- tight pacing with no long pauses
- slight smile in delivery
- frequent contrast pivots: "Right, but...", "Okay, so...", "Here's the thing..."

## Comedy Angle

The humor works best if the clips treat tiny coding events as if they are major editorial developments.

Examples of the target comedic frame:

- session start feels like the opening of an important explainer episode
- task progress feels like hosts narrating an "ongoing story"
- task complete feels like a triumphant conclusion that overstates the accomplishment
- input required feels like the hosts ceremoniously "bringing you in"
- resource limit feels like a solemn discussion of a completely avoidable crisis

## Legal and Brand Constraints

This project is safest if it is clearly "inspired by" the genre and avoids direct impersonation.

Guidelines:

- Do not use `Google`, `Gemini`, or `NotebookLM` in the pack name.
- Do not market the pack as official, compatible with, or endorsed by Google.
- Do not use exact Google voice output samples unless you have clear rights to redistribute them.
- Do not copy substantial transcript text from Google's samples.
- Write fresh lines that capture the format and mannerisms instead of verbatim catchphrases.

Recommended disclaimer language:

`This is an unofficial parody/inspired-by sound pack that evokes AI podcast-host energy. It is not affiliated with or endorsed by Google.`

This is product guidance, not legal advice.

## OpenPeon Packaging Requirements

From the OpenPeon create guide and CESP spec, the pack needs:

- `openpeon.json` at the repo root
- audio files in `sounds/`
- supported formats: `.wav`, `.mp3`, `.ogg`
- max `1 MB` per file
- max `50 MB` total pack size
- short clips, ideally `1-5 seconds`
- category mapping under CESP v1.0

Core categories worth covering first:

- `session.start`
- `task.acknowledge`
- `task.complete`
- `task.error`
- `input.required`
- `resource.limit`

Extended categories worth adding if the joke has range:

- `task.progress`
- `session.end`
- `user.spam`

## Content Strategy By CESP Category

The strongest version of this pack uses 3 to 5 clips per category so repetition stays funny longer.

### `session.start`

Desired feeling: cold open to a suspiciously enthusiastic explainer show.

Line style:

- "Okay, so today we're diving into..."
- "Welcome back, because this session is already getting interesting."
- "Right, so the workspace is live and there's actually a lot to unpack here."

### `task.acknowledge`

Desired feeling: the hosts have received the premise and are about to analyze it.

Line style:

- "Okay, let's break down what we're looking at."
- "Right, so the request is in, and honestly there's a lot going on."
- "First, let's zoom out and understand the task."

### `task.complete`

Desired feeling: overblown conclusion, mild amazement, tidy wrap-up.

Line style:

- "And that's the key takeaway: it worked."
- "So, in the end, the task actually came together pretty nicely."
- "Right, and that really brings the whole thing full circle."

### `task.error`

Desired feeling: a polite but dramatic postmortem.

Line style:

- "Okay, so that's obviously not what we wanted."
- "Right, and this is where things get a little more complicated."
- "Let's pause there, because the failure is actually pretty revealing."

### `input.required`

Desired feeling: the hosts invite the listener to weigh in.

Line style:

- "This is the moment where we actually need your take."
- "Okay, quick pause, because this next part depends on you."
- "Before we go further, we need one key piece of input."

### `resource.limit`

Desired feeling: big-picture analysis of a boring limit.

Line style:

- "Here's the thing: we've hit a constraint."
- "Right, so the real story here is the limit."
- "This is one of those moments where the system is telling us to slow down."

### `task.progress`

Desired feeling: filler banter while waiting.

Line style:

- "While that's working, it's worth stepping back for a second."
- "This is still unfolding, and honestly that context matters."
- "Okay, so we're in the middle of it now."

### `session.end`

Desired feeling: outro.

Line style:

- "And on that note, we'll leave it there."
- "That's probably a good place to wrap."
- "So that's the session, and honestly I think we covered a lot."

### `user.spam`

Desired feeling: the hosts gently scold the listener for over-participation.

Line style:

- "Okay, that's a lot of prompts in a very short time."
- "Let's take one thing at a time here."
- "Right, so we're moving faster than the conversation can keep up with."

## Scriptwriting Rules

To keep the pack coherent:

- Keep clips under about 6 seconds, preferably 2 to 4.
- Write for instant recognition, not full narrative arcs.
- Use partial conversational structure even in single clips.
- Favor one punchline or one recognizable podcast-ism per clip.
- Avoid topical references that will age quickly.

Useful recurring phrases:

- "Okay, so..."
- "Right, exactly."
- "Here's the thing..."
- "Let's back up."
- "In a nutshell..."
- "What this actually means..."
- "That's the key point."

Phrases to use sparingly so the joke does not flatten:

- "game changer"
- "mind blown"
- "deep dive"
- "let's unpack that"

## Voice Production Options

### Option A: Human performance

Best for parody clarity and legal safety.

- Cast two performers with distinct energies.
- Direct them toward the archetypes above.
- Record dry, close-mic speech.
- Add light mastering to get a polished podcast tone.

### Option B: TTS generation

Fastest for volume, but riskier if voices become too close to known Google outputs.

- Use generic commercial or open TTS voices.
- Avoid trying to match Google's exact timbre.
- Differentiate hosts by tempo, pitch, and confidence level.

### Option C: Hybrid

- Use TTS for ideation and timing
- re-record the best lines with humans for release

Recommended path: Hybrid or human-only.

## Audio Direction

- mono or narrow stereo is fine
- normalize loudness consistently across clips
- trim silence aggressively
- avoid background music; it will get annoying fast in an IDE
- optional tiny room tone or subtle studio air if it survives compression

Target feel:

- crisp spoken-word podcast
- energetic but not shouty
- immediately intelligible on laptop speakers

## File and Manifest Plan

Suggested repo structure:

```text
audio-overview-inspired-pack/
  openpeon.json
  README.md
  LICENSE
  sounds/
    session-start-01.mp3
    session-start-02.mp3
    task-ack-01.mp3
    task-complete-01.mp3
    task-error-01.mp3
    input-required-01.mp3
    resource-limit-01.mp3
    task-progress-01.mp3
    session-end-01.mp3
    user-spam-01.mp3
```

Suggested pack metadata:

- `name`: `deep-dive-banter`
- `display_name`: `Deep Dive Banter`
- `license`: `CC-BY-NC-4.0` if you want sharing but not commercial reuse
- `language`: `en`

## Example Manifest Skeleton

```json
{
  "cesp_version": "1.0",
  "name": "deep-dive-banter",
  "display_name": "Deep Dive Banter",
  "version": "0.1.0",
  "description": "An unofficial sound pack inspired by two-host AI deep-dive podcast energy.",
  "author": {
    "name": "Nelson"
  },
  "license": "CC-BY-NC-4.0",
  "language": "en",
  "categories": {
    "session.start": {
      "sounds": [
        { "file": "sounds/session-start-01.mp3", "label": "Cold open" },
        { "file": "sounds/session-start-02.mp3", "label": "Welcome back" }
      ]
    },
    "task.acknowledge": {
      "sounds": [
        { "file": "sounds/task-ack-01.mp3", "label": "Let's break it down" }
      ]
    },
    "task.complete": {
      "sounds": [
        { "file": "sounds/task-complete-01.mp3", "label": "Key takeaway" }
      ]
    },
    "task.error": {
      "sounds": [
        { "file": "sounds/task-error-01.mp3", "label": "That escalated" }
      ]
    },
    "input.required": {
      "sounds": [
        { "file": "sounds/input-required-01.mp3", "label": "Need your take" }
      ]
    },
    "resource.limit": {
      "sounds": [
        { "file": "sounds/resource-limit-01.mp3", "label": "We hit a limit" }
      ]
    }
  }
}
```

## Production Plan

### Phase 1: Research and taxonomy

- collect 20 to 40 recurring Audio Overview mannerisms
- group them into reaction types, transitions, summaries, and outros
- write 3 to 5 short lines per CESP category

### Phase 2: Voice tests

- record or generate 2 host voices
- test for recognizability, intelligibility, and annoyance
- reject any voice that feels too close to a known Google output

### Phase 3: First playable pack

- produce the 6 core CESP categories
- create `openpeon.json`
- validate file sizes and naming

### Phase 4: Usability pass

- install locally
- test in actual IDE event flow
- remove clips that are too long, too quiet, or too repetitive

### Phase 5: Release

- add README with attribution/disclaimer
- tag `v0.1.0`
- publish to GitHub
- submit to OpenPeon registry if desired

## Success Criteria

The pack is successful if:

- users instantly recognize the Audio Overview parody
- no clip feels like a stolen transcript reading
- the joke lands within 1 to 3 seconds
- repeated use stays tolerable for at least one coding session
- the pack passes OpenPeon packaging constraints

## Key Risks

### Risk: too derivative

Mitigation:

- use fresh scripts
- do not use official audio
- keep inspiration at the level of format and archetype

### Risk: too annoying for daily use

Mitigation:

- keep clips short
- avoid music beds
- include only the strongest lines

### Risk: not recognizable enough

Mitigation:

- preserve two-host contrast
- keep the signposting language
- lean into faux-insight and reaction phrasing

## Recommendation

Proceed with a parody pack built around generic "AI podcast hosts" rather than explicit Google branding. The best version is a two-voice, short-form, podcast-EQ pack named something like `Deep Dive Banter` or `Two Hosts, One Task`, with 3 to 5 clips across the six core CESP categories first.

## References

- OpenPeon create guide: <https://openpeon.com/create>
- OpenPeon CESP v1.0 spec: <https://openpeon.com/spec>
- Google launch post for NotebookLM Audio Overview: <https://blog.google/innovation-and-ai/products/notebooklm-audio-overviews/>
- Google NotebookLM customization update: <https://blog.google/innovation-and-ai/products/notebooklm-update-october-2024/>
- Google Gemini Audio Overview announcement: <https://blog.google/products-and-platforms/products/gemini/gemini-collaboration-features/>
- NotebookLM help: Generate Audio Overview: <https://support.google.com/notebooklm/answer/16212820?hl=en>
- Gemini help: Generate Audio Overviews in Gemini Apps: <https://support.google.com/gemini/answer/16047373?hl=en>
- Public sample transcript PDF linked by Google: <https://storage.googleapis.com/gweb-uniblog-publish-prod/documents/NotebookLM_Audio_Overview_Sample_Transcript.pdf>
