# CLAUDE.md

## What this repo is

A Jekyll site hosted on GitHub Pages at https://jonbrauer2.github.io/ehealth/. It has no application code, only Markdown, images, and Jekyll config. It's set up like the sister site `jonbrauer2/ezra-blog`: `remote_theme: jekyll/minima`, built by GitHub Pages ("legacy" build) on every push to `main`.

`baseurl` is `/ehealth`, so absolute links must start with `/ehealth/...` (see `index.md`). The guide in `clean-your-feed/` uses **relative** links only, so it reads correctly both on github.com and on the site.

## How guide pages build

The guide Markdown deliberately has **no front matter**. GitHub Pages' default plugins (configured in `_config.yml`) handle it:
- `jekyll-optional-front-matter` + `defaults: layout: page`: each file becomes a page.
- `jekyll-titles-from-headings` (`strip_title: true`): the first `# ` heading becomes the page title and is removed from the body.
- `jekyll-readme-index`: `clean-your-feed/README.md` is served as `/ehealth/clean-your-feed/`.
- `jekyll-relative-links`: `*.md` links are rewritten to `*.html`.

Keep these conventions when adding a guide: start each file with one `# ` heading, and use relative links and image paths.

## Pictures

Annotated screenshots are SVGs that embed the JPEG as base64 and draw red callouts on top (see `clean-your-feed/SCREENSHOTS.md`). The original screenshots are kept in `clean-your-feed/images/<platform>/real/`.

## Committing and pushing

This is a **personal** repo (account `jonbrauer2`). It uses a repo-local identity (GitHub noreply email) and the credential helper `!gh auth git-credential`. Run `gh auth switch -u jonbrauer2` before pushing and `gh auth switch -u brauerj-gc` afterwards. Don't commit `Gemfile.lock`. `.ai/` holds local AI notes and is gitignored.

## Preview locally

```
bundle install
bundle exec jekyll serve --baseurl ""
```
