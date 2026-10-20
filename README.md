# Noted!

A lightweight, AI-powered desktop notepad for Windows. Multi-tab rich-text notes, local storage, and one-click AI enhancement with the LLM provider of your choice.

## Features

- **Multi-note tabs** – create, rename, delete, and switch between notes
- **Rich text** – bold, italic, underline, strikethrough, headings (H1–H3), bulleted/numbered lists
- **AI enhancement** – fixes grammar, clarity, and readability while keeping your formatting
- **Multiple AI providers** – Gemini, OpenAI, Anthropic (Claude), Groq, Mistral, OpenRouter, Ollama (local, no key), or any custom OpenAI-compatible endpoint
- **Find** – search across all notes
- **File support** – open text/HTML files, Save, Save As, Print
- **Dark/light theme**
- **Live word count**
- **Multiple windows**
- **Auto-persisted notes** – saved locally between launches
- **Secure API keys** – stored in Windows Credential Manager (falls back to `settings.json`)
- **Keyboard shortcuts**

## Requirements

- Windows
- Python 3.9+
- An API key for your chosen provider (not needed for Ollama)

## Install & Run

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
python main.py
```

`requirements.txt`: `pywebview>=5.3`, `litellm`, `keyring`

## Using Noted!

### Write notes
1. Launch the app and start typing.
2. Use the menu bar (**File / Edit / Format / AI / View**) or the toolbar for formatting.
3. Notes auto-save locally. Use **File → New Note** (`Ctrl+N`) to add more tabs.

### Set up AI (one time)
1. Open **AI → AI Settings...**
2. Choose a **Provider**; the default model fills in (editable, LiteLLM model name).
3. Paste your **API key** (get one from the provider's console).
4. Optional: set an **API base URL** (required for Ollama/custom endpoints).
5. Click **Test**, then **Save**.

### Enhance a note
1. Write or paste text.
2. Click **Enhance with AI** or press `Alt+A`.
3. The note is rewritten for clarity and grammar; formatting is preserved. Undo with `Ctrl+Z`.

### Save & share
- **Save** (`Ctrl+S`) / **Save As** (`Ctrl+Shift+S`) – write to a file
- **Open** (`Ctrl+O`) – import a file as a new note
- **Print** – print the current note

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+N` / `Ctrl+T` | New note |
| `Ctrl+W` | Delete note |
| `Ctrl+R` | Rename note |
| `Ctrl+S` | Save |
| `Ctrl+Shift+S` | Save As |
| `Ctrl+O` | Open file |
| `Ctrl+F` | Find |
| `Ctrl+Z` | Undo |
| `Ctrl+Tab` / `Ctrl+Shift+Tab` | Next / previous note |
| `Alt+A` | Enhance with AI |

## Limits & Safety

- Open: files up to 10 MB; binary files are rejected; `.html/.htm/.doc` content is sanitized (scripts, images, styles stripped)
- Paste/drop: plain text only
- AI enhance: notes up to 100,000 characters; AI output is sanitized
- Notes are stored in browser storage; if storage is full, a warning appears — use Save As

## Data Locations

- Settings: `%APPDATA%\Noted\settings.json`
- Notes (webview storage): `%APPDATA%\Noted\webview`
- API keys: Windows Credential Manager (service `Noted`)

## Build an .exe (optional)

```bash
pip install pyinstaller
pyinstaller --noconsole --onefile --add-data "templates;templates" main.py
```

## Tech Stack

Python · pywebview · LiteLLM · keyring · HTML/CSS/JS

## License

MIT © 2026 Soorya Prakash R
