# i am ONE with — Project Guide for Claude

> Read this entire file before making any changes. It contains business context, technical setup, and links to detailed docs.

---

## The Business

**i am ONE with** is a holistic wellness and spiritual healing practice based in Australia, run by Kristie Steers.

The core mission is helping people **return to themselves** — to remember who they truly are at the deepest level. This is described as returning to "zero point", to source, to God, to wholeness — whatever that means to the individual.

### Services (current & planned)

| Service | Status |
|---|---|
| Reiki healing sessions | Active — needs online booking |
| Psychic readings | Active — needs online booking |
| Energy work | Active |
| 1:1 coaching / programs | In development |
| Meditations | Planned |
| Group programs | Planned |
| Retreats | Planned |
| Print on demand (merch) | Needs setup |
| YouTube channel hub | Planned |

### Brand pillars
- **Mind · Body · Spirit** — the three core focus areas
- Helping people reconnect with their intuition
- Returning to source / zero point / wholeness
- Energy healing, chakra work, breathwork
- Teen wellbeing
- Community and group work

### Tone & voice
Warm, grounded, spiritual but not alienating. Speaks to people who are open to energy work but may be new to it. Not preachy. Inviting and safe.

### Target audience
People feeling disconnected, lost, or like something is missing. Open-minded individuals seeking healing beyond conventional medicine. Parents of teens needing emotional support tools. People curious about their intuition and psychic abilities.

---

## Brand

- **Logo:** `/public/logo.png` (landscape crop of the Facebook version — "i am ONE with" wordmark)
- **Full logo folder:** `~/Desktop/untitled folder/Logo - I am ONE with/` — contains multiple versions including transparent PNGs, social sizes, brochure
- **Colours:**
  - Navy `#1a3a5c` — primary dark, trust, depth
  - Teal `#3d9e96` — healing, growth, calm
  - Gold `#c9a227` — wisdom, warmth, divinity
  - Crimson `#bf3a6b` — energy, passion, heart
  - Warm off-white `#f7f6f4` — background, softness
- **Typography:** Cormorant Garamond (display/headings) + Inter (body)

---

## Website

**Live URL:** https://iamonewith.com.au  
**Staging URL:** https://website-c8q.pages.dev  
**GitHub:** https://github.com/Iamonewith/website  
**Platform:** Astro 6 (static) deployed to Cloudflare Pages  

### Pages to build
- [ ] Home (done — placeholder content, needs real copy)
- [ ] About / Kristie's story
- [ ] Services (Reiki, Psychic Readings, Energy Work)
- [ ] Programs (future)
- [ ] Retreats (future)
- [ ] Events / Bookings
- [ ] Blog / YouTube hub
- [ ] Shop (print on demand)
- [ ] Contact
- [ ] Gift cards

### Integrations needed
- **Booking system** — for Reiki and psychic reading appointments (e.g. Acuity, Calendly, or similar)
- **Print on demand** — merch store (e.g. Printful + Shopify or similar)
- **YouTube embed hub** — channel aggregation page
- **Social links** — Instagram, Facebook, and others

---

## Tech Setup

### Node.js
Installed at `~/node/bin` — NOT system-wide. Always prefix shell with:
```bash
export PATH="$HOME/node/bin:$PATH"
```

### Deploy command
```bash
export PATH="$HOME/node/bin:$PATH"
source .env.local
npm run build
npx wrangler pages deploy dist --project-name=website --branch=main --commit-dirty=true
```

### Dev server
```bash
export PATH="$HOME/node/bin:$PATH"
npm run dev
# → http://localhost:4321
```

### GitHub CLI
Also at `~/node/bin`. Auth stored in `~/.config/gh/hosts.yml`.

---

## Environment Variables

Stored in `.env.local` (gitignored — never commit this file):

| Variable | Purpose | How to recreate |
|---|---|---|
| `CLOUDFLARE_API_TOKEN` | Deploy via Wrangler (Pages/Workers) | dash.cloudflare.com → API Tokens → "Edit Cloudflare Workers" template |
| `CLOUDFLARE_DNS_TOKEN` | Manage DNS records | dash.cloudflare.com → API Tokens → "Edit zone DNS" template |

Cloudflare account: `Contact@iamonewith.com.au`  
Account ID: `740542a2d4113137db2db89ed75c7a45`  
Zone ID: `e82fc829236915d05852ed3c86b7ce98`  

---

## Skills Installed

| Skill | Location | Purpose |
|---|---|---|
| `frontend-design` | `~/.claude/skills/frontend-design/` | Distinctive UI/UX design guidance |
| `impeccable` | `.claude/skills/impeccable/` | Advanced frontend design system |
| `remotion-best-practices` | `.agents/skills/remotion-best-practices/` | Video creation in React/Remotion |

---

## Business Docs

The following files contain detailed business context. **Read these before making content or design decisions:**

- [`docs/business-profile.md`](docs/business-profile.md) — Full business questionnaire answers (owner, services, pricing, story)
- [`docs/brand-voice.md`](docs/brand-voice.md) — Tone, language, what to avoid
- [`docs/integrations.md`](docs/integrations.md) — Booking, shop, social, YouTube setup decisions

> ⚠️ If these files are missing or incomplete, run through the questionnaire at [`docs/questionnaire.md`](docs/questionnaire.md) with Kristie before writing any copy or making structural decisions.

---

## Key Rules for Claude

1. **Never commit `.env.local`** — tokens live there, it's gitignored
2. **Always `source .env.local`** before running wrangler commands
3. **Always `export PATH="$HOME/node/bin:$PATH"`** — node/npm/gh are not in system PATH
4. **Deploy = build then wrangler** — GitHub auto-deploy is connected but manual deploy is the fallback
5. **Email DNS is live** — never delete MX or TXT records from Cloudflare DNS
6. **Ask before deleting anything** — existing DNS records, content, or images may be in use
7. **Read `docs/business-profile.md` before writing any copy** — don't invent services, prices, or Kristie's story
