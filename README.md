# Personal site

Workspace for the new personal site that will be served from `ljs.me.uk`.

## Current state (as of 2026-04-08)

- Existing site lives at https://github.com/LukeJStuart/ljs-static-site — a basic, incomplete fork of a colleague's hackathon project.
- It is served via GitHub Pages with `ljs.me.uk` and `www.ljs.me.uk` pointed at GitHub's Pages IPs (`185.199.108-111.153`).
- The Caddy reverse proxy on the VPS only handles `bookstack.ljs.me.uk` and `vikunja.ljs.me.uk` — the apex is entirely a GitHub Pages story.

## Decision: start fresh, not continue the fork

- The "forked from" badge on the existing repo is permanent (only removable via a GitHub Support ticket) and reads as "this isn't really mine" on a repo whose whole purpose is personal branding.
- All existing content will be replaced anyway, so there is no sunk cost.
- A fresh repo gives clean git history with Luke as author from commit 1, and the chance to claim the canonical `lukejstuart.github.io` repo name (one-shot per GitHub account).

## Cutover plan

The DNS leg already points at GitHub Pages, so no DNS changes are needed. The change is in *which repo GitHub serves for the `ljs.me.uk` hostname*.

1. Create the new repo (consider `lukejstuart.github.io`).
2. Build the new site and push it.
3. In the **old** repo's Pages settings: clear the custom domain field (releases the `ljs.me.uk` claim).
4. In the **new** repo's Pages settings: set custom domain to `ljs.me.uk` (claims it).
5. Archive the old `ljs-static-site` repo (preserves the hackathon as a read-only artifact).

Steps 3 and 4 must be back-to-back — GitHub refuses simultaneous claims, so there is a brief 404 window between them.

## Open questions before investing significant time

- **Domain retention.** Vikunja task `#33` flags `ljs.me.uk` as currently limited-term. Resolve the registrar/contract situation before pouring effort into branding tied to this domain.
- **Stack choice.** Static-site generator vs framework, hosting target (sticking with GitHub Pages or moving to Caddy on the VPS like the subdomains).
- **Scope.** Personal blog content, professional portfolio, Claude integrations on subdomains — all on the table per Vikunja project 8.
