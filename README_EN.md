# Omni Editor

[日本語 (Japanese)](README.md)

Omni Editor is a versatile, single-file local editor and viewer that runs entirely in your browser. No server or installation is required—just open the HTML file in Chrome or Edge, and you can load and edit your entire local folder (Vault).

It supports not only Markdown writing but also previews for a wide variety of files including images, videos, audio, CSV, and JSON.

## ✨ Key Features

*   **Fully Local & Single-File**: Just open `index.html` in your browser. No backend server is needed.
*   **File System Access API**: Directly reads and writes to a specified local folder, displaying a file tree.
*   **Powerful Markdown Preview**:
    *   GitHub Flavored Markdown (GFM)
    *   **Math (KaTeX)** `$E=mc^2$`
    *   **Diagrams (Mermaid)**
    *   Frontmatter (YAML metadata) rendered as tables
    *   Interactive Checkboxes (click in preview to save state)
*   **Powered by CodeMirror 6**: Features syntax highlighting, line numbers, auto-completion, and Vim keybindings (`Ctrl+Alt+V`).
*   **Universal Viewer**: Previews images, videos (e.g., `.mp4`), audio (e.g., `.mp3`), CSV (auto-parsed into tables), JSON/YAML (highlighted), PDF, HTML, and more natively.
*   **Global Vault Search**:
    *   File name search (`Ctrl+P`)
    *   Full-text search (Grep) (`Ctrl+Shift+F`)
*   **Rich Export**:
    *   Export a single Markdown file to beautifully rendered HTML (`Ctrl+Shift+E`)
    *   Bulk export the entire Vault's Markdown into HTML files (preserving images and link relationships)

## 🚀 How to Use

1.  Download `index.html` or clone this repository.
2.  Open `index.html` in Chrome, Edge, or any browser supporting the File System Access API. (Note: Opening local HTML files directly may restrict some iframe features due to security policies. Using a local server is recommended for full functionality.)
3.  Click **Open Vault** and select the folder you want to edit.
4.  Select a file from the left sidebar to edit or preview it.

### Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl + S` | Save |
| `Ctrl + Shift + O` | Open Vault |
| `Ctrl + P` | Search files |
| `Ctrl + Shift + F` | Full-text search (Grep) |
| `Ctrl + E` | Toggle Edit/Preview/Split modes |
| `Ctrl + H` | Find and Replace |
| `Ctrl + Shift + E` | Export to HTML |
| `Ctrl + Alt + V` | Toggle Vim mode |

## 🛠 Requirements

*   Modern browsers supporting the File System Access API (e.g., Google Chrome, Microsoft Edge).
*   *Note: Safari and Firefox currently do not fully support the File System Access API and cannot be used.*

## 📝 Built With

*   [CodeMirror 6](https://codemirror.net/) (Editor)
*   [Marked](https://marked.js.org/) (Markdown Parser)
*   [Highlight.js](https://highlightjs.org/) (Syntax Highlighting)
*   [KaTeX](https://katex.org/) (Math Typesetting)
*   [Mermaid](https://mermaid.js.org/) (Diagrams)
*   [js-yaml](https://github.com/nodeca/js-yaml) (Frontmatter)

---
*Created as a single-file, highly portable Markdown & Media workspace.*