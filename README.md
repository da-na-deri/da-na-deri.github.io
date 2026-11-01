# Dana Naderi — personal academic website

Source of the website published at **https://da-na-deri.github.io/**.

The site is built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages.
Pushing to the `main` branch rebuilds and publishes the site automatically; there is
nothing else to deploy.

---

## Where to edit what

| I want to change… | Edit this file |
|---|---|
| Name, title, email, social links | `_config.yml` (top of the file) |
| About, Research Interests, News | `_config.yml` → `about_content:` block (HTML) |
| Site colours and dark mode | `_config.yml` → `palette:` and `darkmode:` |
| Education | `_data/education.yml` |
| Experience / positions | `_data/experience.yml` |
| Publications | `_data/publication.yml` |
| Software shown on the homepage | `_data/projects.yml` |
| Software page (one card per page in `_posts/`) | `_posts/` — the page lists project posts |
| CV page (PDF shown in the page) | put the file at `files/cv.pdf` |
| Skills page (not in the menu) | `_data/skills.yml` → `/skills` |
| Links to blog posts hosted elsewhere | `_data/blog_posts.yml` |
| Navigation menu | `_data/menu_items/menu.yml` |
| Long project write-ups (one page each) | `_posts/YYYY-MM-DD-slug.md` → published at `/projects/slug/` |
| Blog posts written on this site | `_blog_posts/YYYY-MM-DD-slug.md` → published at `/blog/slug/` |
| Profile photo | `images/profile.jpg` (referenced in `_config.yml` and `index.md`) |
| Citation style for blog references | `_config.yml` → `citation_style:` (apa, ieee, chicago, vancouver) |

Everything else (`_layouts/`, `_includes/`, `_sass/`, `_pages/`, `assets/`) is the theme.
It rarely needs touching.

Rules of thumb for the YAML data files:

- Each entry starts with `- layout: ...`. Copy an existing block, paste it below, edit the text.
- Indentation matters. Use two spaces, never tabs.
- A data file with no real entries must contain a single line `[]`, otherwise the build fails.

---

## Adding content

### A publication (`_data/publication.yml`)

```yaml
- layout: left-publication
  title: "Paper title"
  venue: Journal or conference name
  year: 2026
  publication_type: Journal Article
  authors:
    - Dana Naderi
    - Co-author Name
  paper: https://doi.org/...            # "Paper" button
  code: https://github.com/...           # "Code" button (optional)
  website: https://...                   # "Website" button (optional)
  link: https://arxiv.org/abs/...        # "Publication" button (optional)
  image: /images/figure.png              # thumbnail (optional)
  cite:                                  # CSL-JSON used for the "Cite" box
    - id: naderi_2026_short
      type: article-journal
      authors:
        - family: Naderi
          given: Dana
      title: "Paper title"
      container-title: "Journal name"
      issued:
        year: 2026
      DOI: 10.xxxx/xxxxx
  details: |
    **Abstract:** Markdown text shown when the entry is expanded.
```

### A project page (`_posts/`)

Create `_posts/2026-01-31-my-project.md`:

```markdown
---
layout: post
title: My project
author: Dana Naderi
image: images/my-project.png        # card thumbnail (optional)
image_dark: images/my-project-dark.png   # optional variant shown in dark mode
featured: false                     # true = show in the Featured row
hidden: false                       # true = build the page but hide it from listings
excerpt: One-sentence summary shown on the card.
description: Longer description used for search engines.
tags: [bayesian, r]
---

Body text in Markdown. Inline math `$x^2$`, display math `$$ \int f $$`, code blocks, images.
```

### A blog post (`_blog_posts/`)

Same front matter as a project page, plus `date: 2026-01-31` and optionally
`categories: [Statistics]`. Citations work without plugins:

```markdown
As shown in <cite data-key="robert2007"></cite> ...

<div class="bibliography-data" style="display:none;">
@book{robert2007, author = {Robert, Christian P.}, title = {The Bayesian Choice}, year = {2007}}
</div>
```

Figures, tables and equations can be auto-numbered with the `academic-figure`,
`academic-table` and `academic-equation` classes; see `assets/js/academic-numbering.js`
for the exact markup.

### Badges in the About / News text

```html
<span class="badge badge-new">New</span>
<span class="badge badge-new badge-pulse">New</span>
<span class="badge badge-update">Updated</span>
<span class="badge badge-accent">Featured</span>
```

---

## Previewing locally

A local preview shows changes instantly and keeps mistakes off the public site.

**macOS** (one-time setup):

```bash
brew install ruby
echo 'export PATH="/opt/homebrew/opt/ruby/bin:$PATH"' >> ~/.zshrc && source ~/.zshrc
gem install bundler
```

**Windows** (one-time setup): install Git from https://git-scm.com/ and Ruby+Devkit from
https://rubyinstaller.org/ (tick "run ridk install" at the end), then open a new terminal.

**Every time** (both systems), from the project folder:

```bash
bundle install                          # first time, and after Gemfile changes
bundle exec jekyll serve --livereload
```

Open http://localhost:4000 in a browser. Stop the server with `Ctrl+C`.

---

## Working from two computers

```bash
git pull                                # 1. get the latest version before editing
# ... edit files, preview locally ...
git add -A                              # 2. stage everything you changed
git commit -m "Describe the change"     # 3. record it
git push                                # 4. publish (GitHub Pages rebuilds in ~1 minute)
```

Always start with `git pull` so the two machines never diverge.

---

## Credits and licenses

- Based on [modern-resume-theme](https://github.com/sproogen/modern-resume-theme) by
  James Grant, MIT License (see [LICENSE](LICENSE)), extended with academic features
  (publications with citations, projects, blog with MathJax, dark mode).
- Loaded from CDNs at runtime: [Bootstrap](https://getbootstrap.com/) 3.3.5 (MIT),
  [Font Awesome](https://fontawesome.com/) 6.5.1 Free (CC BY 4.0 / SIL OFL / MIT),
  [MathJax](https://www.mathjax.org/) 3 (Apache 2.0), [jQuery](https://jquery.org/) (MIT),
  Google Fonts Roboto and Fira Code.
- Jekyll plugins: jekyll-seo-tag, jekyll-sitemap, jekyll-feed, jekyll-redirect-from (all MIT).

Site content (text, images, publications) © Dana Naderi.
