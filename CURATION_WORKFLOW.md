# Curation Workflow

This repo is not just the shipped pack. It also preserves the working materials and workflow for mining additional clips from generated audio sources.

## Repo Layout

- `openpeon.json`: OpenPeon / CESP v1.0 manifest
- `sounds/`: packaged `.mp3` files tracked in Git and ready for OpenPeon
- `clips-curated/`: approved working clips in `.m4a`, used for review and repackaging
- `clip-preview.html`: local browser UI for reviewing curated clips
- `out/curated-clip-candidates.md`: working inventory of candidate and approved clips
- `out/whisper-transcripts/`: markdown transcripts for mined source audio
- `out/whisper-json/`: raw timestamped Whisper outputs used for trimming
- `source_clips/`: ignored raw source audio dropped in for transcription and mining

## Add More Clips With Codex

The intended workflow is simple: dump more generated audio into `source_clips/`, then ask Codex to mine it.

### Step 1: Add Source Audio

Put new raw source files in `source_clips/`.

Good inputs:

- Google Audio Overview / NotebookLM `.m4a`
- other Google Audio Overview examples or similarly structured generated `.m4a`, `.mp3`, or `.wav`
- multiple files at once

`source_clips/` is gitignored on purpose, so you can dump raw material there without polluting the repo history.

### Step 2: Tell Codex What To Do

Useful prompts in this repo:

- `Mine the new files in source_clips for good Google Audio Overview host phrases.`
- `Transcribe everything in source_clips and update the preview.`
- `Find short standalone phrases for task.complete and input.required.`
- `Tighten these clips to exact word boundaries and repackage the sounds.`
- `Use the new sources, keep only the strongest lines, and update openpeon.json.`

If you already know what you want, be specific about:

- target categories
- phrases you like
- phrases you want removed
- whether to favor very short clips or more theatrical ones

### Step 3: What Codex Will Usually Do

When asked to mine new material, the usual flow is:

1. transcribe the source audio
2. identify candidate phrases with timestamps
3. cut candidate clips
4. add them to `clip-preview.html`
5. mark the strongest ones in `out/curated-clip-candidates.md`
6. tighten any selected keepers
7. convert approved clips into pack-ready `.mp3` files in `sounds/`
8. update `openpeon.json` if the pack contents change

### Step 4: Review Loop

The fastest review loop is:

1. drop files into `source_clips/`
2. ask Codex to transcribe and mine them
3. open `clip-preview.html`
4. note which clips are good, too long, truncated, noisy, or wrong
5. ask Codex to retighten and repackage the approved ones

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

In practice, you do not need to manually run that pipeline. You can just ask Codex to do it from the repo state.

## Recommended Maintenance Pattern

If you want to keep extending this pack over time:

1. keep adding new generated audio to `source_clips/`
2. use the preview to narrow down the strongest lines
3. only promote verified clips into `sounds/`
4. commit only the curated pack assets and metadata
5. leave raw source media untracked

## Curation Standard

The bar for clips in this repo is:

- short
- clean
- reusable
- stand-alone
- minimal lead-in
- minimal tail noise
