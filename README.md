# CodeXplorer

A VS Code-inspired desktop code editor built with **NeutralinoJS**, **CodeMirror 5**, and **HuggingFace AI**. Lightweight native app — no Electron.

---

## Features

- **Multi-file tabbed editor** — syntax highlighting for 17+ languages, code folding, bracket matching, autocomplete
- **Dark / Light themes** — `one-dark` (dark) and `eclipse` (light), toggle in title bar
- **Find & Replace** — inline bar with match count, Replace One / All, match highlighting
- **File Explorer** — multi-folder workspace, file tree with polling, right-click context menu (New, Rename, Delete, Remove Folder, Open in Explorer)
- **Search in Files** — `Ctrl+Shift+F` searches across all workspace folders, click result to jump to line
- **Image & Video preview** — images open inline, videos open in a modal player, binary files are blocked
- **Integrated Terminal** — run Python, JS, C/C++, Java, Rust, Go, Ruby, PHP, Shell, HTML with one shortcut
- **AI Assistant** — HuggingFace-powered chat with Explain / Fix / Refactor quick actions, code insertion at cursor
- **Session Restore** — reopens folders, tabs, and active file on next launch
- **Font zoom & Word wrap** — `Ctrl+=/−/0` and `Alt+Z`, both persist across sessions

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+N` | New file |
| `Ctrl+S` | Save |
| `Ctrl+W` | Close tab |
| `Ctrl+Enter` | Run file |
| `Ctrl+`` ` `` | Toggle terminal |
| `Ctrl+F` | Find |
| `Ctrl+H` | Find & Replace |
| `F3` / `Shift+F3` | Next / Prev match |
| `Ctrl+Shift+F` | Search in files |
| `Ctrl+=` / `Ctrl+-` / `Ctrl+0` | Zoom in / out / reset |
| `Alt+Z` | Word wrap |
| `Ctrl+Space` | Autocomplete |
| Middle-click tab | Close tab |

---

## Getting Started

**Prerequisites:** [NeutralinoJS CLI](https://neutralino.js.org/) + language runtimes on `PATH` (Python, Node, GCC, etc.)

```bash
# Install / update binaries
neu update

# Run in development
neu run

# Build for distribution
neu build
```

---

## Tech Stack

| | |
|-|-|
| Desktop runtime | NeutralinoJS v6.4.0 |
| Editor | CodeMirror 5 v5.65.16 |
| AI | HuggingFace Inference API (Qwen2.5-Coder-32B) |
| Language | Vanilla JS / HTML / CSS — no bundler |

---

## Known Limitations

- File tree shows `node_modules`, `.git` etc. (no `.gitignore` filtering)
- Autocomplete is word-based only (no LSP / IntelliSense)
- No linting, debugging, or folder rename
- Search-in-files uses PowerShell — Windows only
- AI requires internet access

---

## License

MIT
