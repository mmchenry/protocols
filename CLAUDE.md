# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **McHenry Lab Protocols** repository — a public documentation site built with **Quartz 4** (a static site generator optimized for Obsidian vaults) and deployed automatically to GitHub Pages via GitHub Actions.

- **Content root:** `/content/` (open this subfolder as an Obsidian vault, not the repo root)
- **Site is public** — never commit sensitive data, private student info, or unpublished proprietary results

## Local Development

```bash
npm install                    # Install Quartz dependencies (repo root)
npx quartz build --serve       # Build and serve locally at http://localhost:8080
npx quartz build               # Build static site only (output: /public/)
```

Deployment is automatic on push to `main` via `.github/workflows/static.yml`.

## Architecture

**Content authoring:** Markdown files in `/content/McHenryLab Protocols/`. Lab members edit via Obsidian with:
- Attachments stored in `attachments/` subfolders
- Links as relative paths

**Site configuration (repo root, outside vault):**
- `quartz.config.ts` — site title, search, global metadata
- `quartz.layout.ts` — sidebar structure, Graph view, Backlinks, component placement
- `quartz/styles/custom.scss` — visual styling and colors

**CI/CD:** GitHub Actions builds with Node 22 (`npm ci` + `npx quartz build`), deploys artifact from `/public/` to GitHub Pages on every push to `main`.

## Content Rules

- No large binaries (`.mp4`, `.mov`, `.mat`, `.csv`) — use the lab Synology system and link instead
- Always place images/PDFs in an `attachments/` folder within the relevant content directory
