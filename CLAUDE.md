# Personal site — Claude Code project instructions

## What this is

Hugo source for [ljs.me.uk](https://ljs.me.uk). Brutalist design: monospace, black-and-white, sharp lines, single column. Hand-written templates — no theme, no JS framework.

## Authorship boundary

Luke is the sole author of all published content. Claude may assist with planning, structure, outlines, and technical feedback on drafts, but **must not write or commit prose that will be published under Luke's name**. This includes blog posts, about text, and any other reader-facing copy. If a task involves content creation, produce an outline or structural suggestion — not finished text.

## Build and preview

```sh
hugo server -D          # local dev with drafts
hugo --gc --minify      # production build (what CI runs)
```

## Git workflow

**All changes go through pull requests.** Nothing is pushed directly to main.

1. Create a feature branch from main
2. Make changes, commit with clear messages
3. Push branch + open a PR via `gh pr create`
4. Luke reviews and merges

This applies to every change — templates, CSS, config, content structure, CI. No exceptions.

## Content conventions

- Blog posts live in `content/posts/` with slug-based permalinks (`/posts/:slug/`)
- Front matter: `title`, `date`, `draft` (set `draft: true` until Luke is ready to publish)
- New posts: `hugo new posts/some-slug.md`

## Design principles

- Brutalist: monospace type, no rounded corners, no decorative elements
- No external fonts, no JS, no tracking/analytics
- Layouts are hand-written in `layouts/` — do not install or use a Hugo theme
- CSS lives in `static/css/main.css` — single file, no preprocessor

## Deployment

Pushes to `main` trigger `.github/workflows/deploy.yml` → Hugo build → GitHub Pages. Custom domain `ljs.me.uk` is configured at the repo level and via `static/CNAME`.

## What not to do

- Do not install Hugo themes or JS frameworks
- Do not add client-side JavaScript unless Luke explicitly requests it
- Do not write or commit reader-facing prose (blog posts, about text, etc.)
- Do not push directly to main
- Do not modify the deploy workflow without explicit approval
- Do not add analytics, tracking pixels, or third-party services
