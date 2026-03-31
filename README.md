# McHenry Lab Protocols

This repository contains the Markdown source files for our lab's information resource. It is built using **Quartz 4** and automatically deployed to GitHub Pages via **GitHub Actions**.

## Overview

- **Public Website:** https://mmchenry.github.io/protocols/
- **Content Root:** All protocols and notes live in the `/content` directory.
- **Home page / TOC:** `content/index.md` — edit this file to add links to new pages.
- **Search:** Built into the website via the search bar (top-right corner).

---

## Client-Side Setup (For Lab Members)

### 1. Clone the Repository

```bash
git clone https://github.com/mmchenry/protocols.git
cd protocols
```

### 2. Working in Obsidian (Recommended)

Download Obsidian from [https://obsidian.md/download](https://obsidian.md/download), then:

1. Open Obsidian and select **"Open folder as vault."**
2. Select the `content` subfolder as the vault root (not the repo root). This keeps build files hidden and ensures links work correctly.
3. Go to `Settings > Files & Links` and confirm:
   - **Default location for new attachments:** `In subfolder under current folder` (name it `attachments`)
   - **New link format:** `Relative path to file`

#### Troubleshooting: "I don't see `index.md` in Obsidian"

If `index.md` is missing from the Obsidian file browser, the vault was likely opened at the wrong level.

- Correct vault root: `content/`
- Common mistake: opening `content/McHenryLab Protocols/` as the vault

`index.md` lives at `content/index.md`, so it is only visible when the vault root is `content`.

To fix:
1. In Obsidian, choose **File → Open folder as vault...**
2. Select the `content` folder (not `content/McHenryLab Protocols`)

### 3. Adding a New Page

1. Create a new note anywhere inside the vault (e.g., `content/McHenryLab Protocols/My Protocol.md`).
2. Add a wiki-link to it in the relevant section of `content/index.md` so it appears in the TOC.

Every page is indexed for search automatically, even if not linked from the TOC.

### 4. Syncing Changes

Always **Pull** before writing and **Push** when finished.

```bash
git pull origin main
# ... make edits in Obsidian ...
git add .
git commit -m "Brief description of your update"
git push origin main
```

Alternatively, use the **Obsidian Git Plugin** via the "Source Control" sidebar to commit and push without leaving the app.

---

## Website Management (For Admin/PI)

Site configuration lives in the **repo root** (outside the Obsidian vault):

- `quartz.config.ts` — site title, search settings, global metadata
- `quartz.layout.ts` — sidebar structure, Graph view, Backlinks, component placement
- `quartz/styles/custom.scss` — visual styling and colors

### Local Preview

Requires **Node.js ≥ 22** ([nodejs.org](https://nodejs.org)).

```bash
npm install           # first time only
npx quartz build --serve
```

View the site at `http://localhost:8080`. Changes to content are picked up on reload.

---

## Important Rules

- **Public visibility:** This is a **public** website. Never commit sensitive data, private student information, or unpublished proprietary results.
- **Large files:** Do not upload large videos (`.mp4`, `.mov`) or heavy datasets (`.mat`, `.csv`). Use the lab's Synology system and link to files there instead.
- **Attachments:** Always place images or PDFs in an `attachments/` folder within the relevant content directory.

---

*Questions? Contact the PI or the designated Lab Manager.*
