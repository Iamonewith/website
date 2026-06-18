# Website — Claude Code Guide

This is an [Astro](https://astro.build) marketing site deployed to [Cloudflare Pages](https://pages.cloudflare.com).

## Quick reference

| Task | What to say to Claude |
|---|---|
| Change text or copy | "Update the heading on the homepage to say X" |
| Add a new section | "Add a services section below the hero" |
| Change colours or fonts | "Make the primary colour blue" |
| Add a new page | "Create an About page" |
| Deploy changes | "Deploy the site" |
| Preview locally | "Start the dev server" |

---

## Project structure

```
src/
  pages/       ← one file = one page (index.astro is the homepage)
  components/  ← reusable building blocks (header, footer, etc.)
  layouts/     ← page templates
  styles/      ← global CSS
public/        ← images and static files (just drop files in here)
```

---

## How to deploy

Claude can do this for you — just say **"deploy the site"**.

Manually, the steps are:
```bash
export PATH="$HOME/node/bin:$PATH"
source .env.local
npm run build
npx wrangler pages deploy dist --project-name=website --branch=main
```

The live site URL is: **https://website-c8q.pages.dev**

---

## How to run locally (preview before deploying)

Say **"start the dev server"** and Claude will handle it, or run:
```bash
export PATH="$HOME/node/bin:$PATH"
npm run dev
```
Then open http://localhost:4321 in your browser. Press Ctrl+C to stop.

---

## Tech stack

- **Astro 6** — page framework
- **Cloudflare Pages** — hosting (free tier)
- **Wrangler** — Cloudflare's deploy tool (already installed)
- **Node.js 22** — installed at `~/node/bin` (not system-wide)
- **GitHub** — source code at https://github.com/Iamonewith/website

## Environment / secrets

- `.env.local` — contains the Cloudflare API token (never committed to git)
- If the token stops working, create a new one at https://dash.cloudflare.com/profile/api-tokens using the "Edit Cloudflare Workers" template and update `.env.local`
