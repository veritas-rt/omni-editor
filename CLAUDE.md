# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`md-editor.html` is a **single-file, zero-dependency Markdown editor** that runs entirely in the browser. No build step, no server, no npm — just open the HTML file in Chrome or Edge.

It is written in Japanese UI text with English code. Requires Chrome/Edge for the [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_API) (`showDirectoryPicker`, `FileSystemDirectoryHandle`).

## Running / Testing

Open `md-editor.html` directly in Chrome or Edge. There is no build, lint, or test toolchain.

```bash
# Quick way to serve locally (avoids some browser restrictions):
python3 -m http.server 8080
# then open http://localhost:8080/md-editor.html
```

## Architecture

The entire application is one IIFE in `<script>` at the bottom of the file (line 1620–2953). All state is module-scoped within that IIFE.

### Key state variables (lines 1622–1671)
| Variable | Purpose |
|---|---|
| `vaultHandle` | `FileSystemDirectoryHandle` for the open vault |
| `fileTree` | Nested array of `{name, kind, handle, path, children}` |
| `allFiles` | Flat list of all file entries (used for search/grep) |
| `currentFileHandle` | `FileSystemFileHandle` for the currently open file |
| `currentMode` | `'edit'` / `'preview'` / `'split'` / `'viewer'` |

### Persistence
- **Vault handle**: stored in IndexedDB (`MDEditorDB` / `vaults` store) so the vault can be re-opened across sessions without another directory picker.
- **UI state** (sidebar width, mode, sidebar collapsed): `localStorage` via `saveState()` / `loadState()`.
- **Last opened file**: `localStorage` key `md-editor-last-file`.
- **Auto-save**: debounced 3 s write via `createWritable()` on the current file handle.
- **Settings** (autosave, auto-restore, theme): `localStorage` keys `md-editor-autosave`, `md-editor-auto-restore`, `md-editor-theme`.

### Markdown pipeline
`marked.js` with a custom `Renderer` → `processAlerts()` for GitHub-style `[!NOTE]` / `[!WARNING]` blocks → `hljs.highlightElement()` for code blocks → `renderMermaid()` for Mermaid diagrams → `resolveImages()` to replace vault-relative `src` with blob URLs → `interceptLinks()` to intercept relative `.md` links and navigate within the vault.

### Major features and their entry points
| Feature | Function(s) |
|---|---|
| Open vault | `openVault()`, `tryRestoreVault()` |
| File tree render | `buildTree()`, `refreshTree()`, `renderTree()` / `renderNodes()` |
| Open file | `openFile(node)` |
| Save file | `saveFile()` |
| Mode switching | `setMode(mode)` |
| Full-text search (filename) | `openSearch()`, `renderSearchResults()` |
| Full-text grep (content) | `openGrep()`, `runGrep()` |
| Wiki link converter | `openConverter()`, `scanWikiLinks()`, `resolveWikiPath()` |
| Daily Note | `createDailyNote()` |
| Image resolution | `resolveImages()` — uses a `blobCache` Map to avoid redundant reads |

### External CDN dependencies (loaded at runtime)
- `highlight.js` 11.9.0 — syntax highlighting
- `marked` (latest) — Markdown parsing
- `mermaid` 11 — diagram rendering
- Google Fonts: Inter + JetBrains Mono
