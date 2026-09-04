source "https://rubygems.org"

# GitHub Pages builds this site with its own pinned gem set (Pages "legacy"
# build). Using the github-pages gem locally keeps `bundle exec jekyll serve`
# on exactly the same Jekyll + plugin versions that github.com will use, so a
# site that builds here builds there.
gem "github-pages", group: :jekyll_plugins

# Plugins listed in _config.yml. All four are on the GitHub Pages allowlist.
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-paginate"
  gem "jekyll-seo-tag"
end

# Windows and JRuby do not include zoneinfo files.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1", platforms: [:mingw, :x64_mingw, :mswin]

# Ruby 3.4 no longer ships these as default gems.
gem "csv"
gem "base64"
gem "bigdecimal"
gem "logger"
