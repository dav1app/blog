# davifigueiredo — blog

A personal blog built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub
Pages, using the [Mundana](https://www.wowthemes.net/mundana-jekyll-theme/)
theme by WowThemes.

## Running it locally

With Docker (nothing to install on the host):

```sh
docker compose up          # -> http://localhost:4000
```

With a local Ruby (3.0+):

```sh
bundle install
bundle exec jekyll serve    # -> http://localhost:4000
```

`Gemfile.lock` is intentionally not committed — the `github-pages` gem pins the
whole dependency set to whatever GitHub Pages is currently running, so a fresh
`bundle install` matches production.

## Publishing

GitHub Pages builds the `master` branch automatically on push; there is no
Actions workflow to maintain. The site is served at:

    https://dav1app.github.io/blog/

`_config.yml` must match wherever the site is served from:

```yaml
url: 'https://dav1app.github.io'   # scheme + host
baseurl: '/blog'                   # subpath, '' at a domain root
```

`baseurl` is a **path**, not a URL. Putting a full URL in it breaks every
internal link — that was the original bug here.

### Moving to a custom domain later

1. Register the domain and point DNS at GitHub Pages (`A` records to GitHub's
   four Pages IPs, or a `CNAME` record to `dav1app.github.io`).
2. Add a `CNAME` file at the repo root containing just the domain.
3. Set `url:` to `https://that-domain` and `baseurl:` to `''`.

Do step 1 first. A `CNAME` naming a domain that has no DNS records makes Pages
redirect the site to an address that does not resolve, which takes the blog
offline — that is exactly what had happened here.

## Writing a post

Add a file to `_posts/` named `YYYY-MM-DD-some-slug.markdown`:

```yaml
---
layout: post
title: "Post title"
image: /assets/images/something.png
categories: [linux, networking]
tags: [debian, vpn]
---
```

`layout: post` and `author: davi` are applied automatically by the `defaults:`
block in `_config.yml`, so they can be omitted.

- `categories` and `tags` drive `/categories.html` and `/tags.html`. Posts with
  neither simply do not appear on those pages.
- Adding `featured` to a post's `tags` puts it in the homepage sidebar; adding
  `sticky` pins it to a banner on the homepage.
