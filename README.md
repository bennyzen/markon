<div align="center">
  <h1>
    <img valign="middle" src="public/wordmark.png" alt="logo" height="64" />
  </h1>
  <strong>
    Minimal distraction-free live Markdown editor
  </strong>
  <br>
  <br>
  <a href="https://getmarkon.com">
    <img src="https://img.shields.io/badge/PWA-Installable-blue?style=for-the-badge&logo=pwa&logoColor=white" alt="PWA Installable" />
  </a>
  <h2>
    <a href="https://getmarkon.com">getmarkon.com</a>
  </h2>
</div>
<hr>
<div align="center">
  <a href="#features">Features</a> • <a href="#shortcuts">Shortcuts</a> • <a href="#themes">Themes</a> • <a href="#development">Development</a>
	<img src="public/screenshots.png" width="80%" />
</div>

## Features

- **GFM**: GitHub Flavored Markdown + alerts
- **Syntax**: 250+ languages with highlighting
- **Split views**: resizable editor & preview
- **Reader mode**: full-width preview without editor
- **Sync views**: bidirectional scroll sync
- **Auto save**: localStorage persistence
- **Color schemes**: 14 presets with dark/light modes
- **Preview themes**: 10 typographic styles (Billboard, GitHub, Terminal, Magazine, etc.)
- **File handler**: opens `.md` files from your OS file manager
- **Print/PDF**: print stylesheet for clean PDF export via `Ctrl+P`
- **FPS profiler**: latency metrics overlay
- **Spell checker**: toggleable browser spellcheck
- **Hotkeys**: keyboard shortcuts
- **Offline**: no network required

## Shortcuts

| Key | Action |
|-----|--------|
| `Ctrl+E` | Toggle reader mode |
| `Ctrl+J` | Cycle preview theme |
| `Ctrl+M` | Toggle dark/light mode |
| `Ctrl+Shift+M` | Cycle color scheme |
| `Ctrl+S` | Save as file |
| `Ctrl+O` | Open file |
| `Ctrl+K` | Toggle spell checker |
| `Ctrl+B` | Toggle scroll sync |
| `Ctrl+Shift+C` | Copy to clipboard |
| `Ctrl+Shift+V` | Paste from clipboard |
| `Ctrl+/` | Settings |
| `Ctrl+P` | Print / Save as PDF |

## Language Loading & Caching

**markon** uses **lazy loading** for syntax highlighting to keep the app fast and lightweight:

- **On-demand loading**: Language modules are only loaded when you use them
- **Smart caching**: Once loaded, languages work offline in future sessions
- **250+ languages**: Full highlight.js support with minimal initial bundle size
- **PWA optimized**: Cached languages persist across app updates

> [!TIP]
> **Offline behavior**: Languages you've used before will work offline. New languages require an internet connection to load initially.

---

## Development

```bash
npm run dev      # start dev server
npm run build    # build for production
npm run check    # lint code
npm run fix      # fix lint issues
```

<details>
<summary id="themes">Themes & Color Schemes</summary>

![screenshot](public/themes.png)

**markon** separates **color schemes** (palette) from **preview themes** (typography & layout). These are independent — any color scheme works with any preview theme.

### Color Schemes

14 built-in schemes, each with dark and light modes: Panda, Muted, Nord, Monokai, Dracula, Solarized, GitHub, One Dark, Gruvbox, Tokyo Night, Ayu, Catppuccin, Tomorrow.

### Preview Themes

10 typographic styles that control how rendered markdown looks:

- **Default** — System fonts, balanced spacing
- **GitHub** — Familiar README style, underlined headings
- **Academic** — Serif, indented paragraphs, scholarly feel
- **Terminal** — Monospace, `#` heading prefixes, `>` list markers
- **Magazine** — Serif, drop caps, generous line-height
- **Compact** — Small type, tight spacing, information-dense
- **Notebook** — Warm serif, wavy link underlines, cozy reading
- **Billboard** — Public Sans, ultralight oversized headings
- **Prose** — Source Serif, indented paragraphs, accent underlines
- **Geometric** — Space Grotesk, sharp edges, accent heading borders

### CSS Variables

Themes are defined using CSS custom properties. All available variables:

**Base colors:**

- `--bg`: Background color
- `--bg-light`: Light background (panels, cards)
- `--text`: Text color

**Main colors:**

- `--brand`: Brand/primary action color
- `--accent`: Accent/interactive color
- `--primary`: Primary UI color
- `--secondary`: Secondary UI color

**Syntax highlighting:**

- `--comment`: Code comments
- `--meta`: Metadata/imports
- `--operator`: Operators
- `--keyword`: Keywords
- `--regex`: Regular expressions
- `--property`: Object properties
- `--string`: Strings
- `--literal`: Literals/numbers
- `--hint`: Hints/tooltips

**Status colors:**

- `--success`: Success indicators
- `--warning`: Warning indicators
- `--info`: Info indicators
- `--error`: Error indicators

### Creating Custom Themes

Define themes in `src/themes.css` using this structure:

```css
html[data-theme="panda"][data-mode="dark"] {
  --bg: #1a0f1f;
  --bg-light: #2d1a2d;
  --text: #f0f0e8;
  --brand: #ff1100;
  --accent: #8866ff;
  --primary: #bb66ff;
  --secondary: #22aa88;
  --comment: #bbbbbb;
  --meta: #ff1100;
  --operator: #bb88ee;
  --keyword: #ff88bb;
  --regex: #ff99cc;
  --property: #4488ff;
  --string: #22aa88;
  --literal: #ffbb66;
  --hint: #8866dd;

  --success: #22bb11;
  --warning: #ffaa00;
  --info: #1199cc;
  --error: #ff1100;
}

html[data-theme="panda"][data-mode="light"] {
  --bg: #f5f5f0;
  --bg-light: #ffffff;
  --text: #1a1a1a;
  --brand: #d73a49;
  --accent: #0366d6;
  --primary: #8b5cf6;
  --secondary: #28a745;
  --comment: #6a737d;
  --meta: #6f42c1;
  --operator: #0366d6;
  --keyword: #d73a49;
  --regex: #e36209;
  --property: #0366d6;
  --string: #032f62;
  --literal: #6f42c1;
  --hint: #28a745;

  --success: #22bb11;
  --warning: #ffaa00;
  --info: #1199cc;
  --error: #cc6600;
}
```

Themes are automatically detected and appear in the settings dialog. Both `dark` and `light` modes should be defined for each theme.

</details>

---

## Roadmap

- [ ] **VIMODE**: codemirror-vim
- [x] **Autosave**: local persistence
- [x] **Export**: print/PDF via `Ctrl+P`
- [x] **File handler**: open `.md` files from OS file manager
- [x] **Mobile**: touch gestures
- [x] **Preview themes**: 10 typographic styles
- [x] **PWA**: installable, offline cache
- [x] **Reader mode**: full-width preview
- [x] **Scroll**: toggle scroll follow
- [ ] **Share**: ~~url hash content~~
- [x] **Snap**: split resize snapping
- [x] **Shortcuts**: command palette
- [x] **Color schemes**: 14 presets with dark/light modes
- [x] **Preview themes**: independent typography & layout themes

> [!NOTE]
> _in no particular order_

<a href="https://getmarkon.com">getmarkon.com</a>

---

## License

[AGPL-3.0](LICENSE)
