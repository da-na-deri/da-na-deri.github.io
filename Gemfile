source "https://rubygems.org"

# This is the standard GitHub Pages Gemfile.
# The `github-pages` gem pins all of Jekyll's dependencies to the exact
# versions GitHub Pages uses to build sites — so what works locally will
# also work when deployed.
gem "github-pages", group: :jekyll_plugins

# Plugins enabled for this site. These must also be listed under `plugins:`
# in _config.yml. Only plugins that GitHub Pages whitelists will work in the
# Pages build — see https://pages.github.com/versions/ for the current list.
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-seo-tag"
  gem "jekyll-redirect-from"
  gem "jekyll-paginate"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :install_if => Gem.win_platform?

# Required for Ruby 3.0+
gem "webrick", "~> 1.7"

# Ruby 3.4+ no longer bundles these; Jekyll 3.9 still needs them for local preview.
# GitHub Pages ignores this file, so they have no effect on the published site.
gem "csv"
gem "base64"
gem "bigdecimal"
