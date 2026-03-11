# Google's Audio Overview Deep Dive Banter

`Deep Dive Banter` is an OpenPeon-compatible sound pack built from mined and tightened clips from Google's `Audio Overview` outputs, mostly from NotebookLM.

The point of the pack is the AI hosts' exaggerated podcast mannerisms: over-serious framing, constant transitions, dramatic recaps, and polished banter applied to tiny software events.

The repo serves two purposes:

1. it contains the packaged OpenPeon sound pack in a clean, shippable format
2. it preserves the working materials and workflow for mining additional clips from generated audio sources

## Repo Layout

- `openpeon.json`: OpenPeon / CESP v1.0 manifest
- `sounds/`: packaged `.mp3` files tracked in Git and ready for OpenPeon
- `clips-curated/`: approved working clips in `.m4a`, used for review and repackaging
- `clip-preview.html`: local browser UI for reviewing curated clips
- `out/curated-clip-candidates.md`: working inventory of candidate and approved clips
- `out/whisper-transcripts/`: markdown transcripts for mined source audio
- `out/whisper-json/`: raw timestamped Whisper outputs used for trimming
- `source_clips/`: ignored raw source audio dropped in for transcription and mining

## Current OpenPeon Pack

Included categories:

- `session.start`
- `task.acknowledge`
- `task.progress`
- `task.complete`
- `task.error`
- `input.required`
- `resource.limit`
- `session.end`

Pack constraints already satisfied:

- manifest format: `CESP v1.0`
- audio format: `.mp3`
- individual file size: well under `1 MB`
- total pack size: well under `50 MB`

## How To Use The Pack

If you just want the pack:

1. Use [openpeon.json](/Users/nelson/code/openpeon-deepdive/openpeon.json) and the files in [sounds](/Users/nelson/code/openpeon-deepdive/sounds).
2. Import or copy the pack into whatever OpenPeon pack location you use.
3. Keep `source_clips/` out of the installed pack. It is only for raw mining inputs.

If you want to audition the current curated clips first:

1. Open [clip-preview.html](/Users/nelson/code/openpeon-deepdive/clip-preview.html) in a browser.
2. Listen to the `verified` clips.
3. Promote or replace pack assets based on what you want to ship.

## How To Add More Clips With Codex

The intended workflow is simple: dump more generated audio into `source_clips/`, then tell me to mine it.

### Step 1: Add Source Audio

Put new raw source files in [source_clips](/Users/nelson/code/openpeon-deepdive/source_clips).

Good inputs:

- Google Audio Overview / NotebookLM `.m4a`
- other Google Audio Overview examples or similarly structured generated `.m4a`, `.mp3`, or `.wav`
- multiple files at once

`source_clips/` is gitignored on purpose, so you can dump raw material there without polluting the repo history.

### Step 2: Tell Me What To Do

Useful prompts you can give me in this repo:

- `Mine the new files in source_clips for good Google Audio Overview host phrases.`
- `Transcribe everything in source_clips and update the preview.`
- `Find short standalone phrases for task.complete and input.required.`
- `Tighten these clips to exact word boundaries and repackage the sounds.`
- `Use the new sources, keep only the strongest lines, and update openpeon.json.`

If you already know what you want, be specific:

- target categories
- phrases you like
- phrases you want removed
- whether to favor very short clips or more theatrical ones

### Step 3: What I’ll Usually Do

When asked to mine new material, I will usually:

1. transcribe the source audio
2. identify candidate phrases with timestamps
3. cut candidate clips
4. add them to [clip-preview.html](/Users/nelson/code/openpeon-deepdive/clip-preview.html)
5. mark the strongest ones in [out/curated-clip-candidates.md](/Users/nelson/code/openpeon-deepdive/out/curated-clip-candidates.md)
6. tighten any selected keepers
7. convert approved clips into pack-ready `.mp3` files in [sounds](/Users/nelson/code/openpeon-deepdive/sounds)
8. update [openpeon.json](/Users/nelson/code/openpeon-deepdive/openpeon.json) if the pack contents change

### Step 4: Review Loop

The fastest review loop is:

1. drop files into `source_clips/`
2. ask me to transcribe and mine them
3. open [clip-preview.html](/Users/nelson/code/openpeon-deepdive/clip-preview.html)
4. tell me which clips are good, too long, truncated, noisy, or wrong
5. ask me to retighten and repackage the approved ones

Examples:

- `That clip has too much lead-in. Tighten it.`
- `Use the earlier take instead.`
- `This line is good, but only keep the first sentence.`
- `Tag these five as verified and update the pack.`

## How Transcription Works Here

This repo already contains derived transcription outputs under `out/`.

The main mining path used here was:

- local Whisper transcription for source audio and timestamps
- timestamp-guided trimming for clip extraction
- curated review in the HTML preview
- conversion of approved clips to OpenPeon-safe `.mp3`

In practice, you do not need to manually run that pipeline. You can just ask me to do it from the repo state.

## Recommended Maintenance Pattern

If you want to keep extending this pack over time:

1. keep adding new generated audio to `source_clips/`
2. use the preview to narrow down the strongest lines
3. only promote verified clips into `sounds/`
4. commit only the curated pack assets and metadata
5. leave raw source media untracked

## Notes

- Raw generated source files are intentionally excluded from Git and kept local in [source_clips](/Users/nelson/code/openpeon-deepdive/source_clips).
- The tracked deliverable is the OpenPeon pack, not the raw source library.
- The curation standard for this repo is short, clean, reusable, stand-alone phrases with minimal lead-in and minimal tail noise.
