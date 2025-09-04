# Codex CLI DevContainer Template

This repository is a template to quickly start using Codex CLI in a VS Code devcontainer. It ships a Node.js-based container with Codex CLI and common development utilities, and persists history and settings via volumes.

## Requirements

- Docker installed and running
- VS Code with the Dev Containers extension

## Usage

1. Open this folder in VS Code
2. Run “Dev Containers: Open Folder in Container…” from the Command Palette
3. After the container starts, verify Codex CLI is available in the integrated terminal:

```bash
codex --help
codex --version
```

4. Start using Codex CLI in the project directory

```bash
cd sample-project
codex
```

## Configuration

- `.devcontainer/Dockerfile`: Based on Node 22; installs `git`/`gh`/`jq`, `fzf`, `uv` (Python package manager), and Codex CLI
- `.devcontainer/devcontainer.json`: VS Code settings, persistent volumes (command history and `~/.codex`), and workspace bind configuration
- `sample-project/`: Sample directory for quick checks

## Persistence (Volumes)

- Command history: `source=codex-cli-bashhistory` → `/commandhistory`
- Codex settings: `source=codex-cli-config` → `/home/node/.codex`

## .codex Directory (user settings and session history) Location

- Absolute: `/home/node/.codex`
- Relative to the workspace root: `../home/node/.codex`

### Optionally copy project `.codex` to `/home/node/.codex`

The `.codex` directory at the project root contains Codex CLI settings and agent guidelines. If helpful, you can copy the following files into your home directory at `/home/node/.codex`.

- Files:
  - `.codex/config.toml`: Codex CLI settings
  - `.codex/AGENTS.md`: Agent guidelines (global instruction)
