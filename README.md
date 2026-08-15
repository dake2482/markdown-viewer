# Markdown Viewer

<p align="center">
  <img src="assets/logo.png" width="112" height="112" alt="Markdown Viewer icon">
</p>

<p align="center">
  <b>English</b> | <a href="README.zh-CN.md">简体中文</a>
</p>

A zero-dependency, single-file Markdown viewer. Drop a Markdown file into your browser and read it locally — rendering never leaves your machine.

![Markdown Viewer logo](./assets/logo.png)

## Features

- Drag and drop or pick a single `.md`, `.markdown`, `.mdown` or plain-text file
- Pick a folder containing Markdown files and image assets
- Renders headings, paragraphs, bold, italic, strikethrough, inline code and code blocks
- Renders links, images, blockquotes, ordered/unordered lists and tables
- Resolves relative image paths against the selected folder
- Responsive layout for desktop and mobile

## Privacy

Markdown files are read locally through the browser File API; the app itself has no upload endpoint. Note: if a document references remote images or links, the browser may still request those external addresses.

## Usage

### Open directly

Download [`markdown-viewer.html`](./markdown-viewer.html), open it in a modern browser, then drag in a Markdown file.

### Local HTTP preview

```bash
python3 -m http.server 8000
```

Then visit:

```text
http://127.0.0.1:8000/markdown-viewer.html
```

## Project layout

```text
.
├── assets/
│   └── logo.png          # 512 × 512 brand icon
├── apple-icon.png        # iOS home-screen icon
├── favicon.ico           # browser tab and bookmark icon
├── icon.png              # 192 × 192 high-resolution icon
├── markdown-viewer.html  # the whole app, styles and scripts inlined
├── README.md             # English documentation
└── README.zh-CN.md       # Chinese documentation
```

## Logo

The icon keeps the page's cream, ink-green and deep-blue palette, built from a document sheet, a folded corner and a double down-arrow. The full-size source lives in `assets/logo.png`; the repo also ships `favicon.ico`, `icon.png` and `apple-icon.png`. The production HTML embeds a 32 × 32 PNG as its favicon so it never depends on the hosting site's auth or static-asset routing.

## Deployment

The entire app is one static HTML file — host it on any static server:

```bash
# Example: after copying it into any static directory
python3 -m http.server 8000
```

When migrating or self-hosting, deploy `markdown-viewer.html` together with the standard icon files (`favicon.ico`, `icon.png`, `apple-icon.png`). The HTML already embeds its favicon; the icon files cover hosts that need standalone static assets.

## Verification

After checking HTML syntax and key features, compute the local file hash to compare before and after deployment:

```bash
shasum -a 256 markdown-viewer.html
```

## Known limitations

- Uses the built-in lightweight Markdown parser; full CommonMark/GFM coverage is not guaranteed
- When picking a folder, only the first Markdown file found is opened
- No editing, saving, syncing or collaboration features
- Raw HTML or scripts inside Markdown are not executed

## Maintenance conventions

- The repository is the source of truth; server copies are deployment artifacts only
- No development directly on the server
- Before release: check for sensitive information, HTML syntax and browser behavior
- After release: verify the public page status and its SHA-256
