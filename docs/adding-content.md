# Adding publications, talks, and posters

This site uses [Jekyll](https://jekyllrb.com/) collections. After you add or edit files, **commit and push** to GitHub; the site rebuilds in a few minutes. To preview locally, use `bundle exec jekyll serve` (see the main [README](../README.md)).

---

## Journal articles, conference papers, and books (Publications page)

1. Create a new file under **`_publications/`** named with a **date prefix** and a short slug, e.g. `2026-12-01-my-paper.md`.  
2. Use YAML **front matter** (between `---` lines) at the top, then optional Markdown body (shown on the paper’s detail page).

**`category`** controls which section on the [Publications](../_pages/publications.html) page the item appears under (see `publication_category` in [`_config.yml`](../_config.yml)):

| `category` value  | Section heading   |
|-------------------|-------------------|
| `manuscripts`     | Journal Articles  |
| `conferences`     | Conference Papers |
| `books`           | Books             |

**Common front matter fields:**

| Field         | Purpose |
|---------------|--------|
| `title`       | Paper title |
| `collection`  | Must be `publications` |
| `category`    | `manuscripts`, `conferences`, or `books` |
| `date`        | Use `YYYY-MM-DD` |
| `venue`       | Journal or conference name (shown in the list) |
| `excerpt`     | Short blurb on the list view (can be `''` to omit) |
| `citation`    | Full recommended citation (HTML allowed, e.g. `<i>`) |
| `paperurl`    | Link for “Download Paper” (PDF, DOI, etc.) |
| `slidesurl`   | Link for “Download Slides” |
| `bibtexurl`   | Link for “Download Bibtex” |
| `link`        | If set, the **title** on the list links here instead of the internal page |
| `permalink`   | Optional. Custom URL, e.g. `permalink: /publication/my-paper` (must be unique) |

**Minimal conference paper example:**

```yaml
---
title: "My Conference Paper Title"
collection: publications
category: conferences
date: 2026-09-15
venue: "Proceedings of Example Conference (EXAMPLE)"
excerpt: "One-line summary for the list view."
citation: "Yang, M. et al. (2026). &quot;My Conference Paper Title.&quot; <i>EXAMPLE 2026</i>."
paperurl: "https://mohanyang03.github.io/files/papers/my-paper.pdf"
permalink: /publication/my-paper
---
```

Upload PDFs and BibTeX to **`files/`** (or elsewhere) and point `paperurl` / `bibtexurl` / `slidesurl` at the public URL.

**Optional:** the [`markdown_generator`](../markdown_generator/) folder has scripts/notebooks to generate many publication files from a spreadsheet; you can ignore it if you prefer hand-written Markdown.

---

## Talks and slides (Presentations page)

Oral talks and similar entries use the **`_talks/`** collection. They show up under the **Talks** section on the [Presentations](../_pages/presentation.html) page (when you have at least one talk *or* you are only showing talks without posters—see that file for layout).

1. Add **`_talks/YYYY-MM-DD-short-name.md`**. The **filename** (without `.md`) is part of the default URL, e.g. `2026-01-20-ucla-lab.md` → `/talks/2026-01-20-ucla-lab/`.
2. **Front matter** (body is optional; used on the talk’s own page and as excerpt on the list).

| Field        | Purpose |
|-------------|--------|
| `title`     | Talk title |
| `collection`| Must be `talks` |
| `type`      | e.g. `Talk`, `Invited talk`, `Tutorial` (shown in the list line) |
| `venue`     | Host or event |
| `location`  | City, country |
| `date`      | `YYYY-MM-DD` |
| `link`      | Optional. If set, the **title** on the list links to slides/video (e.g. PDF in `files/`) |
| `excerpt`   | Optional short description on the list |

**Example with external slides PDF:**

```yaml
---
title: "Title of the talk"
collection: talks
type: "Invited talk"
venue: "UCLA CS Department"
location: "Los Angeles, CA"
date: 2026-01-20
link: "https://mohanyang03.github.io/files/slides/my-slides.pdf"
excerpt: "Optional one-line abstract."
---
Longer description for the talk’s detail page in **Markdown** if you want.
```

---

## Posters (Presentations page)

Posters are **not** in `_talks/`. They are listed in **[`_data/posters.yml`](../_data/posters.yml)** and PDFs live under **`files/posters/`**. See the comments in that file; each item needs `title`, `venue`, `date`, and `pdf` (path like `/files/posters/My-Poster.pdf`).

---

## Checklist

- [ ] PDFs and assets live under **`files/`** (or a stable public URL) and use **HTTPS** when linking off-site.  
- [ ] YAML indent is **spaces** (2 spaces per level); no tab characters.  
- [ ] Quotes in titles: use **straight double quotes** around the whole `title` if it contains colons or special characters.  
- [ ] After editing [`_config.yml`](../_config.yml), restart Jekyll locally; GitHub Pages restarts the build on push.

If the build fails, open the **Actions** tab on GitHub and read the Jekyll log (often a YAML syntax error in `_data/` or front matter).
