# Let's Tango website

Static site built with [Hugo](https://gohugo.io/) and the [Mainroad](https://github.com/Vimux/Mainroad) theme.

## Run locally

```sh
hugo server
```

Then open <http://localhost:1313/>.

## Content

| File | Page |
| --- | --- |
| `content/_index.md` | Home page intro |
| `content/about.md` | About |
| `content/services.md` | Services (placeholder) |
| `content/contact.md` | Contact (placeholder) |
| `content/posts/` | Blog posts (create with `hugo new posts/my-post.md`) |

New posts start as drafts. Change `draft = true` to `false` to publish. `hugo server -D` shows drafts locally.

Logos and icons are in `static/` and `static/img/`. Site settings (title, menu, sidebar, accent colour) are in `hugo.toml`.

## Theme

Mainroad is copied into `themes/mainroad` from upstream commit `13e04b3` (6 Sep 2024). It isn't a Git submodule, so the site builds without one. To customise a theme template, copy it to the same path under `layouts/` and edit the copy. Don't edit the files in `themes/` directly.

## Deploy to Cloudflare (Workers)

The site is served as static assets by a Cloudflare Worker. The settings are in `wrangler.toml`. The `name` in that file must match the Worker's name in the Cloudflare dashboard.

Cloudflare dashboard settings (**Worker → Settings → Build**):

- Build command: `hugo --gc --minify`
- Deploy command: `npx wrangler deploy` (the default)
- Build variable: `HUGO_VERSION` = `0.166.0` (match `hugo version` locally; Cloudflare's default Hugo is older)

Every push to `main` rebuilds and deploys. To test the deploy config locally without uploading: `hugo --gc --minify && npx wrangler deploy --dry-run`.

After adding a custom domain (**Worker → Settings → Domains & Routes**), make sure `baseURL` in `hugo.toml` matches it.

`wp-export/` holds the original WordPress content and images for reference. Hugo ignores it, and you can delete it once you no longer need it.
