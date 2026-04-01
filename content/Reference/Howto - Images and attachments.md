---
title: "How to add images and PDFs"
description: Examples for embedding images and linking PDFs in protocol pages.
---

# How to add images and PDFs

This page shows the usual patterns for **images** (shown on the page) and **PDFs** (opened or downloaded when clicked). Replace the example filenames with your own.

## Where to put files

Put images and PDFs in an **`attachments`** folder **next to the Markdown file** they belong to (not in `docs/`, which is for Quartz tooling only).

For **this** how-to page, the folder is:

```text
content/Reference/attachments/
```

**Upload these two example files there** (same names as below):

| File           | Purpose        |
| -------------- | -------------- |
| `exImage.jpg`  | Example photo  |
| `exPDF.pdf`    | Example PDF    |

On GitHub: browse to that `attachments` folder → **Add file → Upload files**.  
Locally or in Cursor: copy the files into `content/Reference/attachments/`.

> Keep files reasonably small. Do not commit huge videos or datasets; link to lab storage instead (see the repository README).

---

## Site layout reminder

Top-level areas under `content/` are **siblings** in the sidebar (e.g. **Reference** vs **McHenry Lab Protocols**). You can nest folders inside each area; put `attachments/` beside each note that needs files, for example:

```text
content/McHenryLab Protocols/Some Topic/attachments/scan.png
```

---

## Embed an image (shows on the page)

**Standard Markdown** (works everywhere: GitHub, VS Code, Cursor, Obsidian):

```markdown
![Short description for screen readers](attachments/exImage.jpg)
```

**Live example** (after you add `exImage.jpg`):

![Example image for the how-to](attachments/exImage.jpg)

**Obsidian-style wikilink** (also works in this site if you prefer):

```markdown
![[attachments/exImage.jpg]]
```

Use a **relative** path: start from the folder that contains your `.md` file. If the note lives in `content/Some Area/My Note.md`, put assets in `content/Some Area/attachments/` and use `attachments/yourfile.png`.

---

## Link a PDF (click to open or download)

**Markdown link:**

```markdown
[Open the example PDF](attachments/exPDF.pdf)
```

**Live example:**

[Open the example PDF](attachments/exPDF.pdf)

**Wikilink style:**

```markdown
[[attachments/exPDF.pdf|Open the example PDF]]
```

Browsers usually open PDFs in a new tab or download them, depending on settings.

---

## Quick reference

| Goal              | Pattern |
| ----------------- | ------- |
| Image on page     | `![alt text](attachments/filename.jpg)` |
| Clickable PDF     | `[link text](attachments/filename.pdf)` |
| Same, wikilink    | `![[attachments/filename.jpg]]` — labeled links: see **Wikilink style** under PDFs above |

After adding or changing files, commit and push to `main`; the site rebuilds automatically.
