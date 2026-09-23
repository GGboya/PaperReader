<h1 align="center">PaperReader</h1>

<p align="center">
  <strong>A one-click AI reading companion for research papers: select-to-ask, page citations, in-place translation, and a coach-style reading agent.</strong>
</p>

<p align="center"><sub><a href="README.md">中文</a> · English</sub></p>

<p align="center">
  <img src="assets/paperreader/demo.gif" alt="PaperReader: select to ask → page citation → jump back with highlight" width="100%">
</p>

<p align="center">
  <a href="https://github.com/GGboya/PaperReader/releases/latest"><img src="https://img.shields.io/github/v/release/GGboya/PaperReader?style=flat&label=release&color=4D6BFE" alt="Latest release"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-2EA44F?style=flat" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/macOS-Universal-4493F8?style=flat-square" alt="macOS Universal">
</p>

## What is this

PaperReader is a ready-to-use desktop app for reading research papers: a paper library on the left, a PDF reader in the middle, and an AI conversation on the right. Select any sentence to ask about it; answers come with page numbers that jump back to the highlighted source; one click generates a full Chinese translation.

It is not written from scratch — **PaperReader = [DSH Desktop](https://github.com/anywhere-labs/deepseek-harness-desktop) (the desktop shell) + [dsh-paper-reader](https://github.com/GGboya/dsh-paper-reader) (the reading-companion plugin, preinstalled)**. This repository is a fork of DSH Desktop that does exactly three things: rebranding, preinstalling the plugin, and disabling the upstream update channel. Everything else — including the full commit history and the MIT LICENSE — is kept as-is.

## Download & install

| Platform | Download | How to install |
| --- | --- | --- |
| macOS Universal (Intel + Apple Silicon) | [Download DMG](https://github.com/GGboya/PaperReader/releases/latest/download/PaperReader-0.1.0-universal.dmg) | Open the DMG, drag PaperReader into Applications |
| Windows | Coming soon | — |

Two things to know:

- **Unsigned release**: we haven't purchased an Apple Developer certificate, so on first launch use right-click → Open (or System Settings → Privacy & Security → Open Anyway). It only asks once.
- **Slow first launch**: the first run performs a one-time initialization (plugin environment assembly, a few minutes; your fan may spin up). Subsequent launches are fast.

## Features

- 📚 **Library sidebar**: two-level organization (topics → papers); drop in a PDF and it's a paper
- 💬 **Select to ask**: select text in the reader → a question box pops up → the conversation answers in real time
- 📍 **Page citations**: "page N" in answers is clickable, smoothly jumping back to the PDF page with a highlight
- 🤖 **Coach-style reading**: a dedicated agent preset that reads with you like a teacher — builds a step-by-step reading plan (with page numbers and reflection questions) → walks through sections with feedback → quizzes you and grades your answers → records scores and weak spots into a study profile that accumulates across sessions
- 🀄 **Chinese translation toggle**: one click switches between the original and a full Chinese translation; on first use it automatically downloads and installs the [BabelDOC](https://github.com/funstory-ai/BabelDOC) translation environment (uv + managed Python, entirely inside your user directory — **no need to install Python yourself**)
- 🔍 **Full-text transcription & retrieval**: local PDF text extraction (header/footer removal, hyphenation healing, paragraph reflow), so answers are grounded in real page numbers

## Standing on the shoulders of these open-source projects

Most of what PaperReader can do comes from the work of the projects below. Sincere thanks:

| Project | What it provides |
| --- | --- |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | The AI agent runtime: conversations, streaming, tool calls, and the plugin system. All of PaperReader's AI capability is driven by it |
| [anywhere-labs/deepseek-harness-desktop](https://github.com/anywhere-labs/deepseek-harness-desktop) (DSH Desktop) | The desktop shell: windows, tray, terminal, zero-environment install. PaperReader is forked directly from its v2.0.13 |
| [GGboya/dsh-paper-reader](https://github.com/GGboya/dsh-paper-reader) | The reading-companion plugin (the core feature set preinstalled here), also published independently on npm |
| [funstory-ai/BabelDOC](https://github.com/funstory-ai/BabelDOC) | The PDF full-text translation engine (invoked behind the translation toggle; auto-installed on first use) |
| [mozilla/pdf.js](https://github.com/mozilla/pdf.js) | PDF rendering and text extraction |
| [Electron](https://github.com/electron/electron) | The cross-platform desktop runtime |

Plus the wider dependency ecosystem such as [uv](https://github.com/astral-sh/uv) (Python environment bootstrap).

**License note**: the code in this repository keeps the [MIT LICENSE](LICENSE) inherited from its fork origin. BabelDOC is AGPL-3.0 and is downloaded as a separate process on first translation use; it is not bundled in this installer.

## Data & privacy

- All data lives in your local user directory `~/.paperreader` (library, sessions, study profiles, translation cache)
- Chat requires signing in as prompted (the DeepSeek Harness account system); your questions are sent to the model service you configure
- Translation uses your own configured `translate` endpoint; translations are cached locally

## Disclaimer

An independent community open-source project. It is not affiliated with, sponsored by, authorized by, or endorsed by DeepSeek; nor is it affiliated with the DSH Desktop team. Contributors shown by GitHub come from the fork's inherited commit history.

## Feedback

Bugs and suggestions: [Issues](https://github.com/GGboya/PaperReader/issues).
