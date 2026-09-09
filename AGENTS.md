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

- Build locally with `make` (runs `latexmk -pdf cv.tex`).
- Use `make clean` to remove intermediate build files, or `make distclean` to
  also remove the generated PDF.
- After changes to TeX or bibliography files, run `make` and resolve errors,
  warnings that affect output, overflow, missing references, and undefined
  citations. Visually inspect `cv.pdf` when layout may have changed.

## Style

- Keep the CV concise, professional, and ATS-friendly.
- Prefer existing LaTeX packages, commands, spacing, and typography before
  introducing new dependencies or global formatting changes.
- Preserve URL and email formatting through `\\href` and the established Font
  Awesome icon conventions.

