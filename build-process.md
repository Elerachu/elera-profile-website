# How This Project Was Built

This document walks through the process behind **Project 1: Personal Profile
Website**, step by step, from a blank folder to a live deployed site.

## 1. Project setup

- Created the project folder `personal-profile-website` (later renamed to
  match the GitHub repo name).
- Created `index.html` as the entry point, and an `assets/css/` folder for
  the stylesheet, per the assignment's file-organization requirement.
- Followed the naming rule from the brief: lowercase letters, numbers, and
  dashes only — no spaces, no capitals — for every file and folder.

## 2. Bare HTML skeleton

Started with the minimum valid HTML5 document: `<!DOCTYPE html>`, an
`<html lang="en">` root, a `<head>` with charset + viewport meta tags and a
`<title>`, and an empty `<body>`.

## 3. Semantic structure

Before writing any real content, the page skeleton was built with semantic
HTML5 elements:

- `<header>` containing an `<h1>` (page owner's name) and a `<nav>`
- `<main>` wrapping six `<section>` elements, one per required content area:
  Know Me, Education, Projects, Superpowers, My Fun, Hit Me Up
- `<footer>` at the bottom

Each `<section>` was given a unique, lowercase-dash `id` (e.g. `know-me`,
`super-powers`) so the nav could link to it with anchor links
(`<a href="#know-me">`).

## 4. Filling in content, section by section

- **Know Me** — an `<h2>`, a bio `<p>`, and a profile `<img>`.
- **Education** — a proper `<table>` with a `<thead>` (Institution /
  Qualification / Year) and a `<tbody>` with one row per school.
- **Projects** — three `<article>` elements, each a self-contained
  write-up of one project.
- **Superpowers** — a `<ul>` of skills.
- **My Fun** — a paragraph about hobbies and interests.
- **Hit Me Up** — contact links: a `mailto:` link for email, plus external
  links to GitHub and LinkedIn (opened in a new tab via `target="_blank"`).

## 5. Bootstrap integration

The assignment required HTML, CSS, **and Bootstrap**. Bootstrap was added
via its CDN `<link>` (CSS) and `<script>` (JS bundle), then actually used
for layout, not just linked:

- The **Know Me** section uses Bootstrap's grid (`row` / `col-md-4` /
  `col-md-8`) to lay the profile photo and bio side by side on desktop.
- The **Projects** section uses a `row` of three `col-md-4` columns so the
  three project cards sit side by side on desktop, and stack automatically
  on smaller screens (Bootstrap's grid collapses below the `md` breakpoint
  with no extra code needed).

## 6. External CSS

All styling lives in `assets/css/style.css`, linked in `<head>` **after**
Bootstrap's stylesheet so custom rules can override Bootstrap's defaults.
The stylesheet includes well beyond the required 5 classes/IDs, covering:

- Base typography and page background
- The header/nav bar (color, layout via Flexbox, hover states)
- Section spacing and a `max-width` + `margin: auto` layout pattern to keep
  content readable on wide screens
- A rounded, bordered profile photo
- `.project-card` styling with hover effects (lift + glow shadow)
- `.skills-list` chip styling
- `.social-links` / `.social-btn` styling with a hover shine-sweep animation
- Table styling (padding, border separators) for the Education section
- A cursive font applied specifically to the bio paragraph, layered on top
  of a bubbly pink/purple color palette using CSS gradients and HSL colors

## 7. Responsiveness

A media query (`@media (max-width: 600px)`) adjusts the nav (stacks
vertically instead of staying in a row), shrinks the header name and the
profile photo, and reduces section padding on small screens. This was
tested using the browser's device toolbar (`Ctrl+Shift+M` in Chrome/Edge),
confirming the nav stacks, nothing is cut off, and text scales sensibly on
a simulated phone width.

## 8. Debugging along the way

A few real issues came up during development and were fixed:

- A missing/incorrect image path (`assets/img/Chuu/Me.jpg` vs. the actual
  file location and casing) caused the profile photo not to display —
  fixed by confirming the exact file name and correcting the `src` path.
- File and folder names originally included capital letters (violating the
  assignment's lowercase-dash rule) — fixed by renaming the image files and
  removing the extra nested folder, then re-committing.
- After a path fix, the live GitHub Pages site briefly kept serving a
  cached older version — resolved by waiting for CDN propagation and
  hard-refreshing.

## 9. Version control and deployment

```
git init
git add .
git commit -m "Initial commit: personal profile website"
git branch -M main
git remote add origin https://github.com/Elerachu/elera-profile-website.git
git push -u origin main
```

Then, in the repo's **Settings → Pages**, the source was set to "Deploy
from a branch," branch `main`, folder `/ (root)`. GitHub Pages built and
published the site automatically, viewable at:

**Live site:** https://elerachu.github.io/elera-profile-website/

Every subsequent fix (image paths, content edits, styling changes) followed
the same cycle: edit locally → `git add .` → `git commit -m "..."` →
`git push` → GitHub Pages rebuilds automatically within about a minute.

## 10. Submission

The Canvas submission is a PDF containing:

1. A wireframe sketch of the page layout (built in Microsoft Word)
2. The GitHub repository URL
3. The live GitHub Pages URL
