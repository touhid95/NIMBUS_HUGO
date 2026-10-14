# Nimbus Research

A content-first Hugo research site inspired by scientific/editorial publishing rather than conventional SaaS UI.

## Stack

- Hugo (recommended: current release)
- Plain HTML templates
- Plain CSS
- Tiny vanilla JS for mobile navigation only
- Markdown page bundles for research projects
- No npm, no React, no runtime API, no database

## 1. Install Hugo

Windows (official recommended package manager route):

```powershell
winget install Hugo.Hugo.Extended
```

Then verify:

```powershell
hugo version
```

## 2. Run locally

Windows:

```powershell
.\dev.bat
```

macOS/Linux:

```bash
./dev.sh
```

Open `http://localhost:1313`.

Hugo watches content, layouts, assets/static files, and config. Saving a file triggers rebuild + LiveReload.

## 3. Add a new research project

The core workflow is one folder = one project.

```text
content/
└── projects/
    └── my-new-project/
        ├── index.md
        ├── hero.jpg
        └── diagram.svg
```

Create the project with:

```powershell
.\scripts\new-project.ps1 my-new-project
```

or:

```bash
./scripts/new-project.sh my-new-project
```

Then edit `content/projects/my-new-project/index.md`.

Set:

```yaml
draft: false
```

when it is ready. The project automatically appears in the Research archive and homepage list based on its date.

## 4. Project front matter

```yaml
---
title: "Project title"
date: 2026-08-19T10:00:00+06:00
draft: false
summary: "One-sentence research summary."
typeLabel: "Systems"
status: "Working paper"
featured: true
authors:
  - "Nimbus Research"
topics:
  - "Agents"
  - "Memory"
hero: "hero.jpg"
links:
  - label: "Code"
    url: "https://example.com"
---
```

Everything after the front matter is normal Markdown.

## 5. Add a note

Create a page bundle under `content/news/` and add `index.md` with title/date/summary.

## 6. Production build

```powershell
.\build.bat
```

or:

```bash
./build.sh
```

The generated static site is written to `/public`.

## Design system

Nimbus uses a warm paper canvas, near-black ink, muted blue-green accents, editorial serif display typography, small sans/mono metadata, very large whitespace, hairline separators, and technical diagrams. The UI intentionally avoids card-heavy SaaS patterns.

## Where to edit

- Brand/site settings: `hugo.yaml`
- Homepage: `layouts/index.html`
- Project archive: `layouts/projects/list.html`
- Project page: `layouts/projects/single.html`
- Global layout: `layouts/_default/baseof.html`
- Navigation: `layouts/partials/header.html`
- Visual system: `static/css/main.css`
- Content: `content/`
