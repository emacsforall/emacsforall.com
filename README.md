# emacsforall.com

Modern Emacs for Everyone — tutorials, workflows, and community.

Built with [Hugo](https://gohugo.io/) + [ox-hugo](https://ox-hugo.scripter.co/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod).

## Writing Content

All content is authored in a single org-mode file and exported to Hugo-compatible Markdown via ox-hugo.

1. Edit `content-org/emacsforall.org`
2. Export with `C-c C-e H H` (ox-hugo export to file)
3. Preview locally with `hugo server -D`
4. Commit and push — Netlify auto-deploys

### Adding a New Post

Add a new subtree under `* Posts` in the org file:

```org
** DONE Your Post Title  :tag1:tag2:
:PROPERTIES:
:EXPORT_FILE_NAME: your-post-slug
:EXPORT_DATE: 2026-02-07
:EXPORT_HUGO_CUSTOM_FRONT_MATTER: :series ["Series Name"]
:END:

Your content here.
```

Set the TODO state to `DONE` to publish, or leave it as `TODO`/`DRAFT` to keep it as a draft.

### Embedding YouTube Videos

Use the Hugo shortcode syntax inside an export block:

```org
#+begin_export hugo
{{< youtube VIDEO_ID >}}
#+end_export
```

Or use the privacy-enhanced version:

```org
#+begin_export hugo
{{< youtube-enhanced VIDEO_ID >}}
#+end_export
```

## Local Development

```shell
# Install ox-hugo in Emacs (if not already)
# M-x package-install RET ox-hugo RET

# Start the dev server
hugo server -D

# Production build
hugo --minify
```

## Deployment

The site auto-deploys to Netlify on push to `main`. See `netlify.toml` for build config.
