# tl-tianyi-li.github.io

Personal academic website of Tianyi Li, built with the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme (v1.2).

## Where the content lives

The text and data are kept in plain files in the `website-content` folder, which sits next to this repository:

| Content | File in `website-content` |
|---|---|
| Bio, education, positions, awards, patents | `bio.md` |
| Research themes and funding | `research.md`, `grants-service-talks.yml` |
| Publications | `publications.bib` |
| News | `news.yml` |
| Teaching | `teaching.yml` |
| Lab page: intro, members, alumni, Lab Life | `lab.md`, `people.yml`, `lab-life.yml` |
| Service, talks, media | `grants-service-talks.yml` |
| Prospective students | `prospective-students.md` |
| Name, photo, links, CV | `site-settings.yml` |

After editing those files, regenerate the site's pages:

```bash
ruby bin/build_content.rb
```

This rewrites `_pages/*.md` (except `publications.md`, `news.md` and `404.md`), `_news/` and `_bibliography/papers.bib`. Don't edit the generated files directly; they will be overwritten.

Paper PDFs go in `assets/pdf/`, named after the BibTeX key (for example `li2018crowdia.pdf`). The script links them automatically.

Paper thumbnails go in `assets/img/publication_preview/`, also named after the BibTeX key (for example `zhou2026expeerience.png`; `.jpg` and `.webp` work too). A 4:3 image of the paper's main figure works best.

Students listed in `people.yml` are marked with a dotted underline on publication lists. The list is regenerated into `_data/students.yml`.

## Lab photos

Website-ready photos (resized, hidden metadata removed) go in three folders under `assets/img/people/`. Everything in them is published, so never put raw uploads here; lab members upload originals to the lab's shared Teams folder instead. File names must not start with `_`.

- `Profile Photos/`: headshots, square, about 400×400 px. Add `photo: firstname-lastname.jpg` under that person in `people.yml`; members without a photo show their initials.
- `Lab Photos/`: group photos. Set `group_photo:` in `site-settings.yml`; it appears at the top of the Lab page.
- `Lab Activities/`: Lab Life photos, about 1600 px wide, listed in `lab-life.yml`.

Only add photos with each person's permission. The old `/students/` address redirects to `/lab/`.

## Lab Life

`website-content/lab-life.yml` lists photos (with captions) shown at the bottom of the Lab page, newest first; the section is hidden while the list is empty. Photos go in `assets/img/people/Lab Activities/`, resized with hidden metadata removed.

## Design

Colors, fonts and components follow `website-content/design-language.md` and live in `_sass/_custom.scss`. Theme files overridden in this repository: `_layouts/about.liquid` (adds a page class), `_layouts/bib.liquid` (linked titles, student authors), `_includes/news.liquid` (date pills), plus the new `_includes/theme_cards.liquid`.

## Publishing

Pushing to `master` runs `.github/workflows/deploy.yml`, which builds the site and publishes it to the `gh-pages` branch. In the repository's **Settings → Pages**, the source must be set to the `gh-pages` branch.
