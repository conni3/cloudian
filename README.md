# Cloudian

Cloudian is my personal blog where I record what I learn during my internship at CALAS and throughout my studies. It’s mostly a place for notes, tutorials, and occasional deep dives into topics that catch my interest \:D

[![Hugo Theme: Blowfish](https://img.shields.io/badge/Hugo%20Theme-Blowfish-blue)](https://github.com/nunocoracao/blowfish)

**Live site:** [https://cloudian-sand.vercel.app/](https://cloudian-sand.vercel.app/)

---

## What you’ll find here

* **Notes & Tutorials**
  Markdown from my Obsidian vault transformed into Hugo posts without extra steps.
* **Light & Dark Modes**
  A theme that adapts to your system preference.
* **Responsive Layout**
  Optimized for mobile, tablet, and desktop.
* **Syntax Highlighting**
  Clean code blocks for whatever I’m working on.

---

## Getting started

1. Clone the repo:

   ```bash
   git clone https://github.com/conni3/cloudian.git
   cd cloudian
   ```
2. Install Hugo (v0.110+ recommended)
3. (Optional) Install and build assets if you customize them:

   ```bash
   npm install
   npm run build
   ```
4. Run the development server:

   ```bash
   hugo server --minify --disableFastRender
   ```
5. Open `http://localhost:1313/` in your browser.

---

## Obsidian → Hugo pipeline

I wrote a small Python script (`scripts/convert.py`) to:

* Convert `[[WikiLinks]]` into Hugo-friendly URLs
* Change image embeds like `![[image.png]]` into standard Markdown

To use it:

```bash
python scripts/convert.py --input notes/ --output content/posts/
```

Drop your Obsidian vault into `notes/`, and you’ll get ready-to-publish posts in `content/posts/`.

---

## Deployment

I deploy on Vercel with zero configuration:

* **Build command:** `hugo --gc --minify`
* **Production ignores drafts** by default

```bash
vercel --prod
```

---

I’ll keep updating this blog as I learn more at CALAS and in my courses. Expect random explorations, practical guides, and code snippets as I go along :>
