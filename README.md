# McHenry Lab Protocols

This repository contains the Markdown source files for our lab's information resource. It is built using **Quartz 4** and automatically deployed to **GitHub Pages** via **GitHub Actions** whenever changes land on `main`.

## Overview

- **Public Website:** https://mmchenry.github.io/protocols/
- **Content root:** All protocols and notes live in the `/content` directory.
- **Home page / TOC:** `content/index.md` — add links there so new pages are easy to find from the home page.
- **Search:** Built into the website via the search bar (top-right corner).

You do **not** need Obsidian. Any workflow that edits Markdown under `content/` and pushes to `main` is valid.

---

## How to edit

### On GitHub (in your browser)

Best for small fixes (typos, a single section, one new file) when you do not want to install anything.

1. Open the repository on GitHub: [github.com/mmchenry/protocols](https://github.com/mmchenry/protocols).
2. Browse to the file you need under **`content/`** (for example `content/index.md` or a note under `content/McHenryLab Protocols/`).
3. Click the **pencil** (Edit this file), make your changes, and use **Commit changes**.
4. Commit directly to **`main`** (or open a pull request if your team uses PRs). Pushing to `main` starts the **Deploy Quartz site to GitHub Pages** workflow; when it succeeds, the live site updates after a short delay.

**Tips**

- **New page:** Use **Add file → Create new file**, place it under `content/` (for example `content/McHenryLab Protocols/My Protocol.md`), then edit **`content/index.md`** and add a Markdown link to the new page so it appears in the table of contents.
- **Images or PDFs:** Use **Add file → Upload files** into an **`attachments/`** folder next to the related notes (see [Important Rules](#important-rules)). Reference them with **relative** paths from the Markdown file.
- **Preview:** The web editor does not run the full Quartz site. For an exact preview, use **local preview** (VS Code/Cursor section below) or fix any build errors reported in the **Actions** tab if a deploy fails.

---

### In VS Code or Cursor

Best for steady editing, search across files, and optional local preview before you push.

#### 1. Clone and stay up to date

```bash
git clone https://github.com/mmchenry/protocols.git
cd protocols
git pull origin main
```

#### 2. Open the folder

- **Recommended:** Open the **repository root** (`protocols/`) so you see `content/`, `package.json`, and Quartz config. That makes local preview commands below work without path confusion.
- **Docs-only view:** You may open only the **`content/`** folder if you prefer a minimal tree; you will still run Git from the full repo clone when committing.

#### 3. Edit Markdown

- Work under **`content/`**. Use **relative links** between notes (same style as on the published site).
- Put images and PDFs in an **`attachments/`** folder in the relevant content directory.

#### 4. Optional: preview the site locally

Requires **Node.js ≥ 22** ([nodejs.org](https://nodejs.org)).

```bash
npm install           # first time only
npx quartz build --serve
```

Open **http://localhost:8080**. Reload after saving files.

#### 5. Publish your changes

```bash
git pull origin main
git add .
git commit -m "Brief description of your update"
git push origin main
```

If the **Actions** workflow fails, open the failed run and read the log for the step that errored (often **Install Dependencies** or **Build Quartz**).

---

### In Obsidian (optional)

Obsidian is optional; it is a comfortable vault-style editor for the same Markdown files.

1. Install [Obsidian](https://obsidian.md/download).
2. **Open folder as vault** and choose the **`content`** subfolder inside your clone (not the repo root). That keeps build files out of the vault and matches how links are organized.
3. Under **Settings → Files & Links**, use **`attachments`** as the attachment subfolder and **relative paths** for new links.

**Troubleshooting: missing `index.md`**

If you do not see `index.md`, the vault root is wrong. It must be **`content/`**, not `content/McHenryLab Protocols/`. The home page is **`content/index.md`**.

You can use the **Obsidian Git** community plugin to commit and push from Obsidian, or use the terminal commands in the VS Code/Cursor section.

---

## Shared tasks (any workflow)

### Adding a new page

1. Create a new `.md` file under **`content/`** (for example `content/McHenryLab Protocols/My Protocol.md`).
2. Add a link to it from **`content/index.md`** so it appears in the home TOC. Pages are still searchable even if not linked.

### Syncing with Git (local clones)

Always **`git pull`** before editing and **`git push`** when finished so you avoid overwriting others' work.

---

## Website management (admin / site layout)

Site configuration lives in the **repo root** (outside the main content tree):

- `quartz.config.ts` — site title, search, global metadata
- `quartz.layout.ts` — sidebar, Graph, Backlinks, layout
- `quartz/styles/custom.scss` — styling

Local preview uses the same commands as in the VS Code/Cursor section above.

---

## Important Rules

- **Public visibility:** This is a **public** website. Never commit sensitive data, private student information, or unpublished proprietary results.
- **Large files:** Do not upload large videos (`.mp4`, `.mov`) or heavy datasets (`.mat`, `.csv`). Use the lab's server system and link to files there instead.
- **Attachments:** Always place images or PDFs in an **`attachments/`** folder within the relevant content directory.

---

*Questions? Contact the PI or the designated Lab Manager.*
