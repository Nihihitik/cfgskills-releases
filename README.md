# cfgskills

A small desktop app that brings together everything you need to manage **Codex CLI** and **Claude Code CLI** on your Mac or PC: a skills catalog and toggle switches for the CLIs' own feature flags.

<img width="1530" height="1030" alt="CleanShot 2026-05-03 at 23 13 18" src="https://github.com/user-attachments/assets/a6bf9c77-fad9-4d7f-abe7-573d6c536928" />


> _Screenshot: the main application window._

---

## Why

If you use Codex CLI and/or Claude Code CLI, you've probably run into these problems:

- skills (`SKILL.md` directories) live in two separate places — `~/.codex/skills` and `~/.claude/skills` — and moving them between the two by hand is tedious;
- CLI settings are buried in plain-text config files (`~/.codex/config.toml`, `~/.claude/settings.json`); to enable a feature or beta flag you have to open an editor and remember the exact key name;
- there was no companion utility — every config tweak meant memorising flag names.

**cfgskills** solves both in a single window.

---

## Features

### 🗂 Skills catalog

Browse, preview, copy and delete Codex and Claude Code skills without leaving the app.

<img width="1005" height="676" alt="CleanShot 2026-05-03 at 23 13 35" src="https://github.com/user-attachments/assets/7aca4480-dad5-4a54-be3e-51773da87731" />


- Search by skill name.
- Open `SKILL.md` content in a side dialog.
- "Open in Finder / Explorer" button for each skill folder.
- Copy a skill between Codex ↔ Claude Code in one click (with a conflict warning if the same skill already exists on the other side).
- Delete a skill — empty parent folders are pruned automatically.

<img width="1530" height="1030" alt="CleanShot 2026-05-03 at 23 14 06" src="https://github.com/user-attachments/assets/4ad0e3b9-f924-4193-ba38-5142ada7bc06" />


---

### ⚙️ CLI configuration toggles

Flip CLI features and beta flags through checkbox-style switches — the app updates the underlying config files directly while **preserving your comments and formatting**.

<img width="1530" height="1030" alt="CleanShot 2026-05-03 at 23 14 42" src="https://github.com/user-attachments/assets/182b46c7-4d41-4b21-ab68-0ee375707d88" />


- **Codex** (`~/.codex/config.toml`):
  - `disable_response_storage`, `hide_agent_reasoning`, `show_raw_agent_reasoning`,
  - experimental: `tools.web_search`, `experimental_use_exec_command_tool`, `experimental_use_unified_exec_tool`,
  - every flag inside the `[features]` table and the `enabled` toggle for each plugin — discovered automatically.
- **Claude Code** (`~/.claude/settings.json`):
  - `includeCoAuthoredBy`, `verbose`, `enableAllProjectMcpServers`,
  - experimental: `skipAutoPermissionPrompt`, `remoteControlAtStartup`, `agentPushNotifEnabled`,
  - every plugin from `enabledPlugins` — also discovered automatically.

Each row is labelled in plain language, beta flags are tagged "experimental", and unset flags show a "default" badge so you always know where you stand. The "Open folder" button takes you straight to the config directory if you'd rather edit by hand.

---

## Install

1. Open the latest release page: **[github.com/nihihitik/cfgskills-releases/releases/latest](https://github.com/nihihitik/cfgskills-releases/releases/latest)**.
2. Download the file for your system:
   - **macOS (Apple Silicon)** — `.dmg`,
   - **Windows 10/11 (x64)** — `.exe` (NSIS installer).
3. Install it like any normal app.

After install the app keeps itself up to date.

---

## System requirements

- **macOS 12** Monterey or newer (Apple Silicon).
- **Windows 10 / 11** (x64).
- Codex CLI and/or Claude Code CLI installed — cfgskills works against the existing `~/.codex` and `~/.claude` directories.

If neither directory exists yet, the app simply shows empty lists. The first time you flip a toggle the relevant folder and config file are created automatically.

---

## Safety

- All filesystem operations (read, write, delete, reveal) run on the native Rust backend through Tauri — the embedded webview has no direct FS access.
- Every command canonicalises the input path and **refuses to operate outside** `~/.codex` and `~/.claude`. The app cannot read or delete a file outside those directories.
- The app sends nothing anywhere — it only checks for updates against GitHub Releases.

---

## License

Proprietary. © Nikita.
