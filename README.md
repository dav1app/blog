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
Actions workflow to maintain. The live URL is set in two places that must agree:

| File          | Setting                                        |
| ------------- | ---------------------------------------------- |
| `CNAME`       | the custom domain, e.g. `example.com`           |
| `_config.yml` | `url:` (scheme + host) and `baseurl:` (subpath) |

`baseurl` is a **path**, not a URL — it is `''` when the site is served from the
root of a domain, and `/blog` when served from `https://<user>.github.io/blog/`.
Putting a full URL in `baseurl` breaks every internal link.

The domain in `CNAME` must also have a DNS record pointing at GitHub Pages, or
Pages will redirect the site to an address that does not resolve.

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
