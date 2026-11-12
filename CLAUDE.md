# crafted-sawan — Sawan Nirala's portfolio

Personal portfolio + blog of **Sawan Nirala**, Lead Software Engineer (Frontend).
Static site, updated regularly with new jobs, projects, blog posts, skills and resume links.

- Live: https://sawannirala.netlify.app (Netlify; build settings live in the Netlify dashboard — no `netlify.toml`; `main` is the only branch)
- Repo: https://github.com/Sawannrl123/crafted-sawan
- Owner socials (used on the site): GitHub `Sawannrl123`, X `sawannirala`, LinkedIn `in/sawannirala`

## Stack

- Astro 4 (static output) with content collections, MDX, sitemap, RSS
- Tailwind CSS 3 + DaisyUI 4 (theme `forest` set on `<html>` in `BaseLayout.astro`) + `@tailwindcss/typography` (`prose` on article pages)
- `astro:assets` `<Image>` for hero images (sharp)
- No tests, no linter. Validation = `npm run build` (Zod schemas fail the build on bad frontmatter)

## Commands

```bash
npm install
npm run dev       # http://localhost:4321
npm run build     # → dist/  (run before every commit; must end with "Complete!")
npm run preview   # serve dist/
```

## Where things live

| What | File |
|------|------|
| Site title + default meta description | `src/config.ts` (`SITE_TITLE`, `SITE_DESCRIPTION`) |
| Home hero (name, headline, intro, LinkedIn + resume buttons) | `src/pages/index.astro` |
| CV page: profile summary, education, experience timeline, skills, awards, NPM modules | `src/pages/cv.astro` (all hard-coded) |
| Projects (one file per company/project) | `src/content/project/*.md` |
| Project logos | `public/projects-image/` |
| Blog posts | `src/content/blog/*.md` |
| Blog hero images | `public/blogs-images/` |
| Content schemas (Zod) | `src/content/config.ts` |
| Sidebar nav + contact email | `src/components/SideBarMenu.astro` |
| Social icons | `src/components/SideBarFooter.astro` |
| SEO/OG tags, default OG image `/profile.jpg` | `src/components/BaseHead.astro` |
| Site URL (sitemap/canonical) | `astro.config.mjs` `site` + `public/robots.txt` |
| GitHub README blurb | `README.md` |

Routes: `/`, `/projects` (paginated, 10/page), `/projects/<slug>`, `/blog`, `/blog/<slug>`,
`/blog/tag/<tag>`, `/cv`, `/rss.xml` (RSS item links use the same `createSlug` as the blog pages).

Slugs are generated from the **title**, not the filename (`GENERATE_SLUG_FROM_TITLE = true`,
`src/lib/createSlug.ts`): lowercased, spaces → `-`, non-word chars dropped
("Bed Bath & Beyond" → `bed-bath--beyond`). **Renaming a title changes its URL.**

## Content schemas

**Project** (`src/content/project/<slug>.md`)

```yaml
title: "Company / Project"        # required, drives URL
description: "1 paragraph summary" # required, shown on cards
period: "Jul 2025 - Current"       # required, free text "Mon YYYY - Mon YYYY|Current"
heroImage: "/projects-image/x.png" # required, file must exist in public/
badge: "Fintech"                   # optional domain label
order: 14                          # required number; HIGHER = shown first (home shows top 3)
tags: [Next.js, React]             # optional, must be unique (build fails on duplicates)
```

Body convention (follow existing files, e.g. `balancehero.md`):
`# [Company](url)` → 2–4 paragraphs of narrative → `## Work Highlights` (bold-label bullets) →
`#### Tech Stack` (Frontend / Backend / Tools lines).

Current order: bluezebra 1 … pocket-fm 12, balancehero 13 (Jul 2025 – Current).
A new project gets `order` = current max + 1.

**Blog** (`src/content/blog/<slug>.md`)

```yaml
title: "..."                       # required, drives URL
description: "..."                 # required
pubDate: "Nov 12 2026"             # required, sorted newest first
updatedDate: "..."                 # optional string
heroImage: "/blogs-images/x.webp"  # optional
badge: "Automation"                # optional
tags: [CSS, Tailwind]              # optional, unique; each tag gets /blog/tag/<tag>
```

Tone of existing posts: friendly, emoji-rich, step-by-step dev guides. Internal links use the
title-derived slug, e.g. `/blog/a-glass-of-standards-step-by-step-guide/`.

## Update checklists

**Job change / new role** — keep all of these consistent:
1. New `src/content/project/<company>.md` with next `order`; set previous role's `period` end date (replace "Current").
2. Logo → `public/projects-image/`.
3. `src/pages/cv.astro` → add a `<TimeLineElement>` at the **top** of Experience; close the previous one's "Current".
4. Headline/intro: `src/pages/index.astro`, `src/config.ts` `SITE_DESCRIPTION`, `README.md`.
5. Add new tools to the `skills` array in `cv.astro` (rendered shuffled) and to project `tags`.

**Years of experience** appears in: `index.astro` intro, `cv.astro` profile paragraph,
`src/config.ts` `SITE_DESCRIPTION`, `README.md`. Career started Jul 2015 — update all together.

**Resume link** ("Hire Me!!!" button): Google Drive URL in `src/pages/index.astro`.

**New blog post**: add `.md` in `src/content/blog/`, image in `public/blogs-images/` (webp),
then build. Home "Latest from blog" shows the newest 3 automatically.

**New NPM package / award**: lists at the bottom of `src/pages/cv.astro`.

## Gotchas

- Anything in `public/` is published as-is — never leave drafts or scratch files there.
- The intro text exists in 3 copies (`index.astro`, `src/config.ts`, `README.md`); edit them together.
- `README.md` "Demo"/"Editor" links point to an old Google IDX workspace, not the live site.

## Working rules for AI assistants

- Content edits only touch the files listed above; don't restructure components or layouts unless asked.
- Smallest change that does the ask. Keep the existing writing style (bold-label bullets, metrics like "50%+").
- Never invent achievements, dates, metrics or employers — ask Sawan for missing facts.
- Run `npm run build` after every change and confirm no schema errors.
- Leave changes uncommitted for Sawan to review unless told to commit/push (assume a push to `main` goes live).
- When a fact here changes (new role, new section, fixed known issue), update this file in the same change.
