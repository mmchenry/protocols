# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **McHenry Lab Protocols** repository — a public documentation site built with **Quartz 4** (a static site generator that works well with Markdown folders and optional Obsidian-style features) and deployed automatically to GitHub Pages via GitHub Actions.

- **Content root:** `/content/` — lab members edit Markdown here using **VS Code, Cursor, GitHub’s web editor, Obsidian,** or any editor; open this folder as the vault root in Obsidian if using it, not the repo root
- **Site is public** — never commit sensitive data, private student info, or unpublished proprietary results

## Local Development

```bash
npm install                    # Install Quartz dependencies (repo root)
npx quartz build --serve       # Build and serve locally at http://localhost:8080
npx quartz build               # Build static site only (output: /public/)
```

Deployment is automatic on push to `main` via `.github/workflows/static.yml`.

## Architecture

**Content authoring:** Markdown under `/content/` using **sibling folders** for major areas (e.g. `/content/Reference/`, `/content/McHenryLab Protocols/` with nested topic folders inside). Editors push changes to `main` (see repo `README.md`). Conventions:
- Attachments stored in `attachments/` subfolders
- Links as relative paths (and `[[wikilinks]]` where supported by Quartz)

**Site configuration (repo root, outside vault):**
- `quartz.config.ts` — site title, search, global metadata
- `quartz.layout.ts` — sidebar structure, Graph view, Backlinks, component placement
- `quartz/styles/custom.scss` — visual styling and colors

**CI/CD:** GitHub Actions builds with Node 22 (`npm ci` + `npx quartz build`), deploys artifact from `/public/` to GitHub Pages on every push to `main`.

## Content Rules

- No large binaries (`.mp4`, `.mov`, `.mat`, `.csv`) — use the lab Synology system and link instead
- Always place images/PDFs in an `attachments/` folder within the relevant content directory
