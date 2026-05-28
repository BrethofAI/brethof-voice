# Brethof Voice Pro

> **Local-first speech-to-text for Linux & Windows.** Transcribes 36 languages, runs entirely on your machine, no cloud, no telemetry, no account required. Clone your own voice with LoRA training. Hotkey transcription anywhere. Free tier + paid Pro.

**Download:** [brethof.ai/voice/](https://brethof.ai/voice/)
**Docs:** [brethof.ai/voice/docs/](https://brethof.ai/voice/docs/)
**Report a bug:** [open an issue here](https://github.com/BrethofAI/brethof-voice/issues/new/choose)

---

## What is this repo

This is the **public issue tracker and documentation hub** for Brethof Voice Pro.

It does **not** contain source code — Brethof Voice Pro is a commercial closed-source application. This repo is here so you can:

- 🐛 **Report bugs** with a structured template
- 💡 **Request features** the team can publicly vote on
- 🎙️ **Get help with voice cloning** (LoRA training is a power-user feature; we triage these closely)
- 📖 **Find docs** that haven't yet made it to the website
- 📋 **Read the changelog** for every release

The docs in this repo are MIT-licensed (see [LICENSE](LICENSE)). The application binaries themselves are governed by the [Brethof Voice Pro EULA](https://brethof.ai/voice/license/).

## Quick start

1. **Download** the installer for your OS from [brethof.ai/voice/](https://brethof.ai/voice/).
2. **Install** — Linux: AppImage or `.deb` / `.rpm`. Windows: signed `.exe` installer.
3. **First run** — pick a language (default English), assign a global hotkey (default `Ctrl+Shift+Space`).
4. **Press the hotkey** anywhere on your system → speak → release → the transcription appears at your cursor.

That's it. No login, no account, no cloud. Models download once (~1.5 GB for the default tier; larger tiers available) and live on your disk.

## What makes this different

- **100% offline.** Audio never leaves your machine. No server roundtrip — your speech-to-text runs on your CPU or GPU.
- **36 languages,** including languages most cloud STT services skip (Polish, Czech, Hungarian, Vietnamese, full Nordic set, full Slavic set).
- **Your voice, your LoRA.** Train a personal LoRA adapter on ~5 minutes of your own speech for accuracy that matches your accent / vocabulary / industry terminology.
- **Built on open models.** Qwen3-ASR + GGUF + llama.cpp under the hood. We packaged the cloud-grade stack into a desktop app.
- **One-time payment, perpetual licence.** No subscriptions. Free tier covers most personal use; Pro unlocks the larger model tiers, LoRA training, and priority support.

## Reporting a bug

Please use the [bug report template](https://github.com/BrethofAI/brethof-voice/issues/new?template=bug-report.yml). It asks for:

- Your OS + Brethof Voice Pro version (Help → About copies this).
- What you expected.
- What actually happened.
- Steps to reproduce.
- The contents of `~/.config/brethof-voice/log/latest.log` (Linux) or `%APPDATA%/brethof-voice/log/latest.log` (Windows) for the failing session, if any.

**Do not** include audio recordings with private content in public issues. If a bug only reproduces with sensitive audio, mark the issue as such and we'll handle it via email (`support@brethof.ai`).

## Reporting a security issue

**Do not open a public issue for security vulnerabilities.** See [SECURITY.md](SECURITY.md) for the responsible-disclosure process.

## Feature requests

Use the [feature request template](https://github.com/BrethofAI/brethof-voice/issues/new?template=feature-request.yml). The team reviews these weekly and labels them with current intent (`planned`, `considering`, `out-of-scope`). 👍 reactions on existing issues count more than duplicates.

## Roadmap

Public roadmap is in [ROADMAP.md](ROADMAP.md). High-level: we update it monthly; near-term items are firm, long-term items can shift based on what hits the issue tracker.

## Related Brethof projects

- **[awesome-local-ai](https://github.com/BrethofAI/awesome-local-ai)** — Curated list of AI tools that run 100% on your machine (Voice Pro is one of them).
- **[awesome-private-ai](https://github.com/BrethofAI/awesome-private-ai)** — Privacy-first AI more broadly.
- **[awesome-ai-minefield](https://github.com/BrethofAI/awesome-ai-minefield)** — AI model/tool licence receipts so you can ship without lawyering up.
- **[brethof-mind](https://github.com/BrethofAI/brethof-mind)** — SurrealDB-backed long-term memory system for Claude Code (open source, MIT).

## License

The contents of this repo (issues, docs, templates, changelogs, screenshots) are **MIT** licensed — see [LICENSE](LICENSE).

The Brethof Voice Pro application binaries are **proprietary** and licensed under the [Brethof Voice Pro EULA](https://brethof.ai/voice/license/) — see the EULA bundled with the installer or read it on the website.

---

Maintained by **[Brethof AI](https://brethof.ai)** — local-first AI tools built for people who take their data seriously.
