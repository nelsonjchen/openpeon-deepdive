# Google's Audio Overview Deep Dive Banter

`Deep Dive Banter` is an OpenPeon-compatible sound pack built from mined and tightened clips from Google's `Audio Overview` outputs, mostly from NotebookLM.

The gimmick is simple: exaggerated AI podcast-host energy applied to tiny coding events. Over-serious framing, dramatic recaps, polished banter, and a level of synthetic importance that no routine task deserves.

## What Is In The Pack

This repo ships a complete CESP v1.0 sound pack with:

- `openpeon.json` manifest
- pack-ready `.mp3` files in `sounds/`
- coverage for `session.start`, `task.acknowledge`, `task.progress`, `task.complete`, `task.error`, `input.required`, `resource.limit`, and `session.end`

Pack constraints already satisfied:

- manifest format: `CESP v1.0`
- audio format: `.mp3`
- individual file size: under `1 MB`
- total pack size: under `50 MB`

## Install

If this pack is available in your registry, install it with:

```bash
peon packs install deep-dive-banter
peon packs use deep-dive-banter
```

If you want to use this repo directly, install it locally:

```bash
peon packs install-local /path/to/openpeon-deepdive
peon packs use deep-dive-banter
```

You can also manually copy `openpeon.json` and `sounds/` into your OpenPeon pack directory if you prefer.

## Preview And Layout

- [`openpeon.json`](openpeon.json): pack manifest
- [`sounds/`](sounds): packaged audio files
- [`clip-preview.html`](clip-preview.html): local browser UI for reviewing curated clips
- [`CURATION_WORKFLOW.md`](CURATION_WORKFLOW.md): mining, transcription, and repackaging workflow

If you want to audition the curated source clips before shipping anything, open [`clip-preview.html`](clip-preview.html) in a browser and listen to the `verified` entries.

## Notes

- Raw source media belongs in `source_clips/` and is intentionally not tracked in Git.
- The tracked deliverable is the OpenPeon pack, not the raw source library.
- This is an unofficial fan-style pack built from generated Google Audio Overview material. See [`openpeon.json`](openpeon.json) for license metadata.
