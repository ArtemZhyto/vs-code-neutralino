# CodeXplorer

A VS Code-inspired desktop code editor built with **NeutralinoJS**, **CodeMirror 5**, and **HuggingFace AI**. Runs as a lightweight native desktop app on Windows with no Electron overhead.

---

## Features

### Editor
- **Multi-file tabbed editing** — open multiple files simultaneously, switch between tabs, close individual tabs
- **Modified indicator** — unsaved files show a dot (●) on the tab
- **Syntax highlighting** for 17+ languages via CodeMirror themes:
  - Dark mode uses `one-dark` (purple keywords, green strings, blue functions)
  - Light mode uses `eclipse` (classic light theme)
- **Language auto-detection** from file extension — JS, TS, Python, C, C++, Java, C#, Rust, Go, HTML, CSS, JSON, Markdown, Shell, Ruby, PHP, and more
- **Code folding** — collapse functions and blocks via gutter arrows
- **Bracket matching & auto-close** — highlights matching brackets, auto-inserts closing pair
- **Active line highlight** — current line is subtly highlighted
- **Word wrap toggle** — `Alt+Z` or the Wrap button; state persists across sessions
- **Font zoom** — `Ctrl+=` zoom in, `Ctrl+-` zoom out, `Ctrl+0` reset; persists across sessions
- **Autocomplete** — `Ctrl+Space` triggers word-based completion hints

### Find & Replace
- **Find bar** — `Ctrl+F` opens inline find bar with match count (e.g. `3/12`)
- **Replace bar** — `Ctrl+H` adds replace row; Replace One or Replace All
- **Navigation** — `F3` / `Shift+F3` or arrow buttons to jump between matches
- **Match highlighting** — all matches highlighted in yellow, active match in orange
- **No-match indicator** — input turns red when search string is not found

### File Explorer
- **Multi-folder workspace** — open multiple root folders at once via `+Folder`
- **File tree** — expandable/collapsible directory tree, sorted directories-first then alphabetically
- **Extension badges** — coloured file-type icons next to each filename
- **Polling** — file tree refreshes every 3 seconds to reflect external changes (new files, deletes)
- **Context menu** (right-click on any file or folder):
  - Open / Edit
  - New File Here
  - New Folder Here
  - Rename
  - Delete (recursive for folders)
  - Remove Folder from Workspace (right-click on the workspace root header)
- **New File / Refresh** buttons in the sidebar header

### Search in Files
- **Ctrl+Shift+F** opens the Search panel in the sidebar
- Searches all text files in all open workspace folders using PowerShell `Select-String`
- Results grouped by filename with line numbers
- Click any result to open the file and jump to that exact line
- Limited to 200 results for performance

### Image & Video Preview
- **Image preview** — opens PNG, JPG, JPEG, GIF, SVG, WEBP, BMP, ICO inline in the editor area with filename and dimensions info
- **Video player** — opens MP4, WEBM, OGV, MOV, AVI, MKV in a modal player with autoplay
- **Binary file guard** — EXE, DLL, ZIP, PDF, MP3, WAV and other binary formats are blocked from opening in the text editor with a clear message

### Integrated Terminal
- **Run current file** with `Ctrl+Enter` or the Run button — automatically selects the right interpreter or compiler
- **Supported runtimes:**

  | Language | How it runs |
  |----------|-------------|
  | Python | `python` interpreter |
  | JavaScript | `node` |
  | C | `gcc` compile → run |
  | C++ | `g++` compile → run |
  | Java | `javac` compile → `java` run |
  | Rust | `rustc` compile → run |
  | Go | `go run` |
  | Ruby | `ruby` |
  | PHP | `php` |
  | Shell / Batch | direct execution |
  | HTML | opens in default browser |

- **Manual commands** — type any shell command in the terminal input and press Enter
- **Command history** — `Arrow Up/Down` navigates previous commands
- **Color-coded output:**
  - Cyan — info / system messages
  - Green — success / program exit
  - Red — stderr / errors
  - Blue — commands echoed
  - Yellow — warnings
- **Clear** button or `Ctrl+L`; **Toggle** button or `Ctrl+`` ` `` to show/hide the terminal panel

### AI Assistant (HuggingFace)
- Powered by **Qwen2.5-Coder-32B-Instruct** via the HuggingFace Inference API
- **Chat interface** — full conversation history per session with user/assistant message bubbles
- **Quick actions** (work on selected text or the whole file if no selection):
  - **Explain** — asks the AI to explain the code
  - **Fix** — asks the AI to find and fix bugs
  - **Refactor** — asks the AI to improve code structure
- **Code blocks** in AI responses are rendered with a language label and a one-click **Copy** button
- **Insert** button — inserts the last generated code at the cursor position in the editor
- **Clear chat** — resets the conversation
- **API key management** — enter your key once, it is saved to localStorage; status indicator shows ok / error / warning
- Get a free API key at [hf.co/settings/tokens](https://huggingface.co/settings/tokens)

### Themes
- **Dark** (default) — VS Code-inspired dark palette, `one-dark` editor theme
- **Light** — clean white palette, `eclipse` editor theme
- Toggle with the button in the title bar; preference persists across sessions

### Session Restore
- On startup, CodeXplorer automatically restores:
  - All previously opened workspace folders
  - All previously opened file tabs
  - The previously active file
- Editor settings (theme, font size, word wrap, API key) are all persisted in `localStorage`

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+S` | Save current file |
| `Ctrl+Enter` | Run current file |
| `Ctrl+`` ` `` | Toggle terminal panel |
| `Ctrl+F` | Open Find bar |
| `Ctrl+H` | Open Find & Replace bar |
| `F3` | Find next match |
| `Shift+F3` | Find previous match |
| `Ctrl+Shift+F` | Open Search-in-Files panel |
| `Ctrl+=` | Zoom in (increase font size) |
| `Ctrl+-` | Zoom out (decrease font size) |
| `Ctrl+0` | Reset font size |
| `Alt+Z` | Toggle word wrap |
| `Ctrl+Space` | Trigger autocomplete |
| `Escape` | Close find bar / context menu |
| `Arrow Up/Down` | Navigate terminal history |

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop runtime | [NeutralinoJS](https://neutralino.js.org/) v6.4.0 |
| Editor | [CodeMirror 5](https://codemirror.net/5/) v5.65.16 |
| AI backend | [HuggingFace Inference API](https://huggingface.co/inference-api) |
| Language | Vanilla JS, HTML, CSS (no bundler) |
| Shell integration | PowerShell via `Neutralino.os.execCommand` |

---

## Getting Started

### Prerequisites
- [NeutralinoJS CLI](https://neutralino.js.org/docs/getting-started/your-first-neutralinojs-app) installed globally
- For code execution: language runtimes installed and on `PATH` (Python, Node.js, GCC, Java, etc.)

### Run in development
```bash
neu run
```

### Build for distribution
```bash
neu build
```
Outputs a standalone binary + resources bundle in the `dist/` folder.

---

## Project Structure

```
vs-code-neutralino/
├── resources/
│   ├── index.html        # App shell — layout, context menu, modals
│   ├── styles.css        # All styling — themes, layout, components
│   └── js/
│       ├── main.js       # All app logic (~1900 lines)
│       └── neutralino.js # NeutralinoJS client library
├── neutralino.config.json # App config — window size, API permissions
└── README.md
```

---

## Configuration

`neutralino.config.json` controls:
- Window size (default 1400×860, min 900×600)
- Maximized on launch
- Native API permissions (`filesystem`, `os`, `window`, `debug`)
- Binary name and version

---

## Known Limitations

- **No `.gitignore` filtering** — file tree shows `node_modules`, `.git`, `__pycache__` etc.
- **No LSP / IntelliSense** — autocomplete is word-based only, not language-aware
- **No linting** — no inline error squiggles; errors appear only at runtime
- **No debugging** — no breakpoints or step-through execution
- **Folder rename not supported** — rename works for files only
- **Search-in-files is Windows-only** — uses PowerShell `Select-String`
- **AI requires internet** — HuggingFace API calls need network access

---

## License

MIT
