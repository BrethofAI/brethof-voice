# Changelog

All notable changes to Brethof Voice Pro will be listed here. Format
loosely follows [Keep a Changelog](https://keepachangelog.com/). Dates
are ISO 8601.

The application source itself is closed-source — this changelog is the
public-facing record of releases. For deeper context on a release (the
why, not the what), see the [release post on Dev.to](https://dev.to/brethofai)
or [brethof.ai/voice/updates/](https://brethof.ai/voice/updates/).

## [Unreleased]

_Items in flight for the next release. Subject to change._

## [2.0.0] — 2026-05-15

Major release. Engine rebuilt around **Qwen3-ASR + GGUF + llama.cpp**;
offline **translation** added as the headline feature; same binary now
ships as an **MCP server** for AI agents.

Full launch article: [The local voice stack that beats the cloud at its own benchmarks](https://dev.to/brethofai/the-local-voice-stack-that-beats-the-cloud-at-its-own-benchmarks-449d).

### Added

- **Offline translation across 38 languages** powered by Tencent's
  Hunyuan-MT2 (open-sourced May 2026). Two model tiers — Fast (1.8B,
  ~1 GB, COMET-22 87.6) and Quality (7B, ~4.3 GB, COMET-22 89.0).
- **Translation everywhere transcription is:** "Translate to" dropdown
  in the Transcribe popup; voice-keyboard target-language selection
  (inline / one-per-line / primary-only); SRT/VTT subtitle translator
  with optional **bilingual** mode (source + translation per cue).
- **MCP server mode** — `brethof-voice --mcp` exposes 19 tools (ASR,
  translation, device management, voice-profile management) over
  stdio to Claude Desktop, Claude Code, Cursor, Cline, OpenClaw,
  Hermes. No port, no firewall prompt.
- **Per-engine device control** — ASR on one GPU, translation on
  another, or pin the 7B model to CPU on VRAM-tight laptops.
- **Word-level timestamps** via the optional Forced Aligner (on top
  of the standard SRT cue-level timestamps).
- **Hotwords** field now does double duty: biases ASR toward your
  brand names and jargon, and pins terminology for the translator.
- **22 Chinese-dialect auto-detection** on top of the 30 selectable
  transcription languages.
- **System-audio capture** alongside mic and file — transcribe a
  meeting, a browser tab, or any audio playing on your speakers.

### Changed

- **Engine: Whisper-based → Qwen3-ASR on llama.cpp with GGUF
  quantisation.** Result: 5–7× faster transcription than Whisper,
  ~400 ms cold start, 83 MB install on Windows / 161 MB on Linux.
- **GPU acceleration: CUDA-only → Vulkan 1.2+.** NVIDIA, AMD, and
  Intel Arc all work from the same binary now.
- **LoRA fine-tune pipeline** for personal-voice adapters — one-click
  training, auto-selects NVIDIA CUDA backend if available else CPU,
  merges + exports to GGUF, switch personal model from the main screen.
- **DeepFilter noise reduction** included but **off by default** —
  hurts quality on short clean clips, available for noisy rooms.

### Performance receipts

Accuracy numbers below come from **after-fine-tune evaluations** —
the upstream Qwen3-ASR project's own evaluation set, and our internal
Polish LoRA benchmark. They're useful as upper bounds, not as the
held-out accuracy you'll see on stranger audio. The 14-day free trial
is there so you can measure on your own speakers / language / domain
before committing.

- **Qwen3-ASR (after fine-tune):** 1.84% average WER across the
  10-language test set; 4.5% WER on English (Whisper Large-v3: 7.4%).
- **Language identification (after fine-tune):** 97.9% accurate across
  30 languages (Whisper Large-v3: 94.1%).
- **Voice-LoRA, small 0.6B base, ~11h Polish (after on-device fine-tune):**
  6.10% WER, vs Whisper Large-v3's 8.40% on the same audio.

Engineering measurables (objective on your hardware):

- **Install size:** 83 MB on Windows / 161 MB on Linux — one binary,
  no separate runtime to install.
- **Cold start:** ~400 ms — weights are memory-mapped, so the first
  hotkey press after a reboot is already listening.
- **Transcription throughput:** 5–7× faster than Whisper Large-v3 on
  the same hardware (Whisper used as baseline because every guide on
  the internet measures against it).
- **Translation latency:** Fast tier (1.8B) sub-second on CPU; Quality
  tier (7B) sub-second on GPU.

### Removed

- Cloud-mode toggles. There never was one; 2.0 reaffirms — no audio
  off the machine, no telemetry, no usage stats.

---

_Earlier versions are listed in their release posts under
[brethof.ai/voice/updates/](https://brethof.ai/voice/updates/).
The 2.0.0 release is the first under this unified public-changelog
process._
