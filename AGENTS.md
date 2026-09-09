# Repository Guidelines

## Overview

This repository contains a single-page CV built from `cv.tex`. Publication
entries live in `citations.bib`; `index.html` and `CNAME` support the deployed
GitHub Pages site. The GitHub Actions workflow compiles `cv.pdf` and publishes
it to the `build` branch on every push.

## Editing

- Make CV content and layout changes in `cv.tex`. Preserve its existing
  section and custom environment structure unless a redesign is requested.
- Add or update publications in `citations.bib` using valid BibLaTeX syntax.
- Keep personal information, links, dates, and contact details consistent
  across the document.
- Do not commit generated LaTeX artifacts or `cv.pdf`; they are ignored and
  produced by the build.
- Treat `index.html`, `CNAME`, and `.github/workflows/build.yml` as deployment
  configuration. Change them only when the task concerns the web page, custom
  domain, or CI/CD behavior.

## Build and verification

- Build locally with `make` (runs `latexmk -pdf cv.tex`). If `latexmk`/
  `pdflatex` aren't installed (they aren't on every machine), fall back to
  `tectonic cv.tex` — it needs no separate TeX Live install and produces the
  same `cv.pdf`.
- Use `make clean` to remove intermediate build files, or `make distclean` to
  also remove the generated PDF.
- After changes to TeX or bibliography files, run `make` (or `tectonic
  cv.tex`) and resolve errors, warnings that affect output, overflow, missing
  references, and undefined citations. Visually inspect `cv.pdf` when layout
  may have changed.

## CI/CD prerequisite

- The `deploy` job in `.github/workflows/build.yml` pushes to the `build`
  branch using the default `GITHUB_TOKEN`. This requires the repo's Actions
  workflow permissions to be set to "Read and write permissions" (Settings →
  Actions → General → Workflow permissions) — the GitHub default is
  read-only, which makes `deploy` fail with a 403. This setting lives outside
  the repo (it's not in any tracked file), so it's easy to forget after a
  fork or a fresh clone into a new repo.

## Style

- Keep the CV concise, professional, and ATS-friendly.
- Prefer existing LaTeX packages, commands, spacing, and typography before
  introducing new dependencies or global formatting changes.
- Preserve URL and email formatting through `\\href` and the established Font
  Awesome icon conventions.

