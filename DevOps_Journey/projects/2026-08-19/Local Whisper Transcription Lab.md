# Local Whisper Transcription Lab

**Category:** AI / ML  
**Date:** 2026-08-19  
**Difficulty:** Intermediate  

## Overview
A local-first toolkit for transcribing audio (meetings, lectures, voice memos) using OpenAI's Whisper running **entirely on your machine** — no cloud, no API cost, no privacy leak. Includes batch transcription, speaker-aware chunks, and searchable output. Perfect for a CSE student who wants to turn recorded lectures into searchable notes.

## Architecture / Structure
```
whisper-lab/
├── transcribe.py         # CLI entry
├── model_manager.py      # download/quantize model selection
├── batch.py              # folder of audio -> transcripts
├── export.py             # to markdown / srt / json
├── search.py             # grep-like search over transcripts
├── models/               # cached GGUF/ctranslate2 models
└── README.md
```

## Workflow
1. Drop audio files into an `inbox/` folder.
2. `transcribe.py` picks a model size (tiny→large) based on a quality/speed flag.
3. Whisper transcribes locally (faster-whisper / ctranslate2 for speed).
4. Outputs saved as `.md`, `.srt`, and `.json`; `search.py` indexes them.
5. Optional: summarize a transcript with a local LLM (llama.cpp).

## Tools
- Python, `faster-whisper` or `whisper.cpp` / `ctranslate2`
- `ffmpeg` for audio preprocessing
- Optional: `llama.cpp` for local summarization
- SQLite or plain files for the search index

## Learning Goals
- Run inference locally and manage model weights/quantization.
- Audio preprocessing pipelines.
- Build a reusable CLI tool around an ML model.
- Combine ASR + LLM for note synthesis.

## Build Milestones
1. Transcribe a single file with faster-whisper end-to-end.
2. Add model-size selection + batch folder processing.
3. Export to SRT + Markdown with timestamps.
4. Add a local search index over transcripts.
5. (Bonus) Wire a local LLM to produce meeting summaries.
