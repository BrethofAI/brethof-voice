# Brethof Voice Pro

> **Offline voice-to-text and 38-language translation, 100% on your machine.** Linux x86_64 + Windows x64. One portable binary on Linux, per-user installer on Windows. No cloud mode, no telemetry, no per-minute billing. Pay once, own it forever.

**Download + 14-day free trial:** [brethof.ai/voice/](https://brethof.ai/voice/)
**Feature tour & per-language table:** [brethof.ai/voice/tour/](https://brethof.ai/voice/tour/)
**Support / FAQ:** [brethof.ai/voice/support/](https://brethof.ai/voice/support/)
**Report a bug:** [open an issue here](https://github.com/BrethofAI/brethof-voice/issues/new/choose)

---

## What this repo is

The **public issue tracker and documentation hub** for Brethof Voice Pro. It does **not** contain source code — Voice Pro is a closed-source commercial product. This repo exists so you can:

- 🐛 **Report bugs** with structured templates (Linux / Windows specifics, log excerpts, repro steps)
- 💡 **Request features** and 👍 ones you want
- 🧠 **Get help with LoRA fine-tuning** — the personal-voice adapter that learns from your corrections
- 🌐 **Get help with translation** — 38 languages, two model tiers (Fast 1.8B / Quality 7B)
- 📖 **Find docs** that haven't yet made it to the website
- 📋 **Read the changelog**

The docs in this repo are MIT-licensed (see [LICENSE](LICENSE)). The application binary itself is governed by the [Brethof Voice Pro EULA](https://brethof.ai/voice/license/) bundled with the installer.

## Install — one binary per OS

- **Linux x86_64** — Ubuntu 22.04+, Fedora 38+, Arch, Debian 12+, CachyOS, openSUSE. X11 and Wayland. Single portable binary (~161 MB), no install, no admin rights. Drop it anywhere and run it.
- **Windows x64** — 10 (21H2+) and 11. Per-user graphical installer (~83 MB on disk), no admin rights.
- **macOS** — not yet. On the roadmap, no ETA.

**Minimum hardware:** 8 GB RAM, AVX2 CPU. For GPU acceleration: **Vulkan 1.2+** drivers — which means **NVIDIA, AMD, and Intel Arc all work** from the same build, not just CUDA cards.

## Free trial → buy

1. **Download** for your OS from [brethof.ai/voice/](https://brethof.ai/voice/).
2. **Create an account** — email + password, then click the confirmation link in your inbox.
3. **14-day free trial** starts. Every feature unlocked. No credit card required.
4. **Pay once after trial** — perpetual licence, no subscription.

## What it does

### Transcription
Drag-and-drop **audio or video file** (mp4 / mkv / mov / webm + a dozen more — the engine pulls the audio track out), or capture **mic** or **system audio** (anything playing on your speakers — meetings, browser tabs, calls). Output: plain text or **SRT with timestamps**. Optional **Forced Aligner** for word-level timestamps.

### Voice keyboard
**F9** default (hold-to-talk or toggle, optional right-mouse trigger). Push-to-talk dictation into any focused application at the OS level — editor, browser, terminal, chat box.

### Translation (new in 2.0)
**38 languages** via Tencent's Hunyuan-MT2 (open-sourced May 2026), running locally. Two model tiers:

| Tier   | Size on disk | COMET-22 |
|--------|--------------|----------|
| Fast (1.8B)    | ~1 GB    | **87.6** |
| Quality (7B)   | ~4.3 GB  | **89.0** |

Per-engine device control means you can run **ASR on one GPU and translation on another**, or pin the 7B model to CPU on a VRAM-tight laptop.

Translation shows up in three places:
- **Transcribe popup** — "Translate to" dropdown on file / mic / system-audio capture.
- **Voice keyboard** — pick one or several targets; it types the translation (inline, one per line, or primary-only).
- **Subtitle translator** — translate every SRT/VTT cue, keep timings, optional **bilingual** mode (source + translation).

### Train it on your own voice (LoRA fine-tune)
This is the part the cloud can't do. **Every time you correct a misheard word, the audio-and-correction pair is saved to a local dataset**. Main window shows your running sample count. One click runs a **LoRA fine-tune** — auto-selects NVIDIA CUDA backend if available, CPU otherwise — then merges and exports to GGUF. Switch to your personal model right from the main screen.

Our internal benchmark: fine-tuned the small 0.6B model on ~11 hours of Polish → **6.10% WER, beating Whisper Large-v3's 8.40%** on the same audio. A model a fraction of the size, on-device, out-performing the big general model.

### MCP server for AI agents
Same binary, just `brethof-voice --mcp`. **19 MCP tools** exposing ASR + translation to Claude Desktop, Claude Code, Cursor, Cline, OpenClaw, Hermes:

```json
{
  "mcpServers": {
    "brethof-voice": { "command": "brethof-voice", "args": ["--mcp"] }
  }
}
```

Transport is stdio — no port, no localhost binding, no firewall prompt. Agent can transcribe files, record-and-transcribe the mic, translate text and SRTs, switch compute devices, manage voice profiles — all offline, no API keys, no per-minute billing.

## Languages (stated honestly)

- **Transcription: 30 selectable languages + 22 Chinese dialects** the model auto-detects (52 in total). Plus auto-detect mode.
- **Translation: 38 languages** via Hunyuan-MT2.
- **23 languages work in both directions** (speak → see written → see in any other).

ASR and translation lists don't perfectly overlap (ASR has Danish, Greek, Finnish, Swedish that translation doesn't; translation has Hindi, Bengali, Tamil, Ukrainian that ASR doesn't surface). Full per-language table at [brethof.ai/voice/tour/](https://brethof.ai/voice/tour/).

## Privacy guarantee

- **No cloud mode.** There is no toggle to send audio off-machine for "better accuracy."
- **No telemetry.** No usage stats, no crash phone-home. Only network calls: licence check, update check, model downloads you trigger — all documented, all disableable.
- **Audio never hits disk.** The buffer lives in RAM during transcription and is freed the moment the text is produced.

## Reporting a bug

Please use the [bug report template](https://github.com/BrethofAI/brethof-voice/issues/new?template=bug-report.yml). It asks for OS + version + repro + the log excerpt (the app's Help menu has a "Show log location" — paste the relevant lines).

**Do not include audio recordings with private content in this public issue.** If a bug only reproduces with sensitive audio, mark it as such and email `hello@brethof.ai`.

## Reporting a security issue

**Do not open a public issue for security vulnerabilities.** See [SECURITY.md](SECURITY.md) for the responsible-disclosure process.

## Related Brethof projects

- **[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai)** — Curated list of AI tools that run 100% on your machine.
- **[awesome-private-ai](https://github.com/BrethofAI/awesome-private-ai)** — Privacy-first AI more broadly.
- **[awesome-ai-minefield](https://github.com/BrethofAI/awesome-ai-minefield)** — AI model + tool licence receipts so you can ship without lawyering up.
- **[brethof-mind](https://github.com/BrethofAI/brethof-mind)** — SurrealDB-backed long-term memory system for Claude Code (open source, MIT).

## License

Repo contents (README, docs, templates, screenshots, changelog) — **MIT**, see [LICENSE](LICENSE).
Brethof Voice Pro application binary — **proprietary**, see the [EULA](https://brethof.ai/voice/license/) bundled with the installer.

---

Maintained by **[Brethof AI](https://brethof.ai)** — local-first AI tools for people who take their data seriously.
