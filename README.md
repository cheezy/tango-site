# Let's Tango website

Static site built with [Hugo](https://gohugo.io/) and the [Mainroad](https://github.com/Vimux/Mainroad) theme.

## Run locally

```sh
hugo server
```

Then open http://localhost:1313/.

## Content

| File | Page |
|---|---|
| `content/_index.md` | Home page intro |
| `content/about.md` | About |
| `content/services.md` | Services (placeholder) |
| `content/contact.md` | Contact (placeholder) |
| `content/posts/` | Blog posts (create with `hugo new posts/my-post.md`) |

New posts start as drafts. Change `draft = true` to `false` to publish. `hugo server -D` shows drafts locally.

Logos and icons are in `static/` and `static/img/`. Site settings (title, menu, sidebar, accent colour) are in `hugo.toml`.

## Theme

Mainroad is copied into `themes/mainroad` from upstream commit `13e04b3` (6 Sep 2024). It isn't a Git submodule, so the site builds without one. To customise a theme template, copy it to the same path under `layouts/` and edit the copy. Don't edit the files in `themes/` directly.

## Deploy to Cloudflare Pages

1. Push this folder to a Git repository.
2. In Cloudflare, go to **Workers & Pages → Create → Pages → Connect to Git** and choose the repository.
3. Build settings:
   - Framework preset: **Hugo**
   - Build command: `hugo --gc --minify`
   - Build output directory: `public`
   - Environment variable: `HUGO_VERSION` = `0.166.0` (match `hugo version` locally)
4. After adding a custom domain, set `baseURL` in `hugo.toml` to that domain.

`wp-export/` holds the original WordPress content and images for reference. Hugo ignores it, and you can delete it once you no longer need it.
