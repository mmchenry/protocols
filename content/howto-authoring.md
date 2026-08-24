---
title: "How to author protocol pages"
description: Formatting reference for images, PDFs, callout annotations, and other content patterns used in this site.
draft: false
aliases:
  - Reference/Howto - Authoring.md
---

# How to author protocol pages

This page is a normal Markdown file under **`content/`**—it is built and published with the rest of the site.

This page covers common formatting patterns: **images**, **PDFs**, and **callout blocks** for inline annotations. Replace the example filenames with your own.

## Where to put files

Put images and PDFs in an **`attachments`** folder **next to the Markdown file** they belong to (not in `docs/`, which is for Quartz tooling only).

For **this** how-to page (which lives at `content/howto-images-and-pdfs.md`), the example folder is:

```text
content/attachments/
```

**Upload these two example files there** (same names as below):

| File           | Purpose        |
| -------------- | -------------- |
| `exImage.jpg`  | Example photo  |
| `exPDF.pdf`    | Example PDF    |

On GitHub: browse to **`content/attachments/`** → **Add file → Upload files**.  
Locally or in Cursor: copy the files into `content/attachments/`.

> Keep files reasonably small. Do not commit huge videos or datasets; link to lab storage instead (see the repository README).

---

## Site layout reminder

Top-level areas under `content/` are **siblings** in the sidebar (e.g. **Reference** vs **McHenry Lab Protocols**). You can nest topic folders inside them. For any note, put an `attachments` folder **in the same directory as that note**, for example:

```text
content/McHenryLab Protocols/Some Topic/my-note.md
content/McHenryLab Protocols/Some Topic/attachments/scan.png
```

This page uses `content/attachments/` because the note itself sits directly in `content/`.

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

Use a **relative** path from the `.md` file. If the note is `content/Some Area/My Note.md`, use `content/Some Area/attachments/` and paths like `attachments/yourfile.png`.

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

---

## Callout blocks (annotating protocol pages)

Quartz supports **Obsidian-style callouts** — colored, icon-labeled boxes that stand out from normal text. These are useful for adding lab-specific annotations alongside a generic protocol or manual, making it clear which content is original and which is a local note.

**Syntax:**

```markdown
> [!type] Optional title
> Body text of the callout.
> Can span multiple lines.
```

**Common types and when to use them:**

| Type | Use for |
|------|---------|
| `[!note]` | Lab-specific definitions, clarifications, or context |
| `[!tip]` | Shortcuts or preferred methods used in our setup |
| `[!warning]` | Departures from the manual, or steps that can go wrong |
| `[!info]` | Background context or cross-references |

**Example — defining a term from a manual:**

```markdown
The arm should sit close to the center of the range (R28 brings the arm to center).

> [!note] Lab definition — "center of its range"
> The manual's "center of the mechanical range" is the arm position where LENGTH OUT reads **0.000 V**.
> On our 310C this corresponds to the arm pointing roughly perpendicular to the motor body.
> Verify with the DVM connected to LENGTH OUT before starting tuning.
```

**Example — flagging a deviation from the manual:**

```markdown
> [!warning] Our procedure differs here
> The manual says to use a 20 g weight for the 300C force calibration.
> Our unit reads correctly with 18.5 g due to a lever arm length difference — use the lab brass weight set, not the nominal value.
```

Callouts render as colored boxes on the published site and display normally as blockquotes in plain Markdown editors (GitHub, VS Code). The title is optional — omit it if the type label is self-explanatory.
