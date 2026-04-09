# personal-site

Source for [ljs.me.uk](https://ljs.me.uk).

Hugo, with hand-written brutalist templates — no theme.

## Local development

```sh
hugo server -D
```

Serves at `http://localhost:1313/`. The `-D` flag includes draft posts.

## Adding a post

```sh
hugo new posts/some-slug.md
```

Edit the new file under `content/posts/`. Drafts (`draft: true` in front matter) are excluded from production builds.

## Deployment

Pushes to `main` trigger `.github/workflows/deploy.yml`, which builds with Hugo and publishes to GitHub Pages. The custom domain (`ljs.me.uk`) is configured at the repository level and is also baked into the build via `static/CNAME`.

## Layout

- `content/` — markdown source
- `layouts/` — Hugo templates (`baseof.html`, `index.html`, `_default/{single,list}.html`)
- `static/` — static assets copied verbatim into the build (CSS, `CNAME`)
- `hugo.toml` — site config
