# Opencodian

> OpenCode embedded in Obsidian — your vault becomes an AI collaborator with skills, categories, and multi-agent orchestration.

## Overview

Opencodian is an Obsidian plugin that embeds the OpenCode CLI as an AI coding agent in your vault. Your vault becomes the agent's working directory — file read/write, search, bash, and multi-step workflows all work out of the box.

## Architecture & Attribution

```
┌─────────────────────────────────────────────────────────────┐
│                        Opencodian                           │
├─────────────────────────────────────────────────────────────┤
│  Obsidian UI Layer (based on Claudian by YishenTu)          │
│  - Chat sidebar, settings, inline edit, status bar          │
│  - MIT License                                              │
├─────────────────────────────────────────────────────────────┤
│  Backend: OpenCode CLI (replaces Claude Code)               │
│  - Supports GLM, Kimi, DeepSeek, and other models           │
├─────────────────────────────────────────────────────────────┤
│  Features from oh-my-opencode:                              │
│  - Skills system (custom prompts & tools)                   │
│  - Categories (task-based model routing)                    │
│  - Multi-agent orchestration                                │
└─────────────────────────────────────────────────────────────┘
```

### Origin

This project is a derivative work of:
- **Claudian** by YishenTu ([GitHub](https://github.com/YishenTu/claudian)) — MIT License
  - The original Obsidian plugin that embeds Claude Code
  - Opencodian retains the UI layer and modifies the backend

**Key Changes from Claudian**:
1. Backend replaced: Claude Code → OpenCode CLI
2. Added: Skills system from oh-my-opencode
3. Added: Categories for task-based model routing
4. Added: Status bar with agent/model info

## Features

### Core
- **Chat Sidebar** — Talk to the agent in a sidebar chat view
- **File Operations** — Read, write, edit, search files in your vault
- **Model Selection** — Choose from OpenCode's discovered models
- **Permission Modes** — YOLO, Safe, Plan, Build modes
- **Status Bar** — Shows connection status, current agent, and model

### Unique Features (from oh-my-opencode)
- **Skills System** — Load skills from `.opencode/skills/` and `~/.config/opencode/skills/`
- **Categories** — Automatic model routing based on task type:
  - `visual-engineering` → Frontend, UI/UX
  - `deep` → Autonomous research
  - `quick` → Simple changes
  - `ultrabrain` → Hard logic

## Requirements

- **OpenCode CLI** — Install from [opencode.ai](https://opencode.ai)
- **Obsidian** v1.4.5+ (Desktop only)
- **OpenCode-compatible models** — GLM, Kimi, DeepSeek, Minimax, ......etc.

## Installation

### From Source

```bash
cd Opencodian
npm install
npm run build
```

Then copy `main.js` and `manifest.json` to `<vault>/.obsidian/plugins/opencodian/`

## Usage

1. Click the robot icon in the ribbon
2. Type your message and press Enter
3. Select model, mode, category, or skill from the header

### Permission Modes

| Mode | Description |
|------|-------------|
| YOLO | Full access |
| Safe | Ask before bash/edit |
| Plan | Design only |
| Build | Implementation |

### Skills

Skills are loaded from:
- `<vault>/.opencode/skills/*/SKILL.md`
- `~/.config/opencode/skills/*/SKILL.md`

Invoke with `$skill-name` prefix.

### Categories

Configure in Settings → Categories to auto-route tasks to appropriate models.

## License

MIT License

Copyright (c) 2025

This project is a derivative work of Claudian by YishenTu.
Original Claudian code: https://github.com/YishenTu/claudian

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Acknowledgments

- **Claudian** by YishenTu — UI foundation and original plugin architecture
- **OpenCode** — CLI backend for AI coding assistance
- **oh-my-opencode** — Skills and categories system inspiration
- **Obsidian** — Platform and API