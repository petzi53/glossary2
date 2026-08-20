# AGENTS.md — glossary2

Project-specific context for `glossary2`, an R package for adding glossaries to
Markdown/Quarto documents by tagging individual terms with popup or linked
definitions.

Note: this is a fork/revamp of the original CRAN package `glossary`
(https://github.com/debruine/glossary) by Lisa DeBruine; DESCRIPTION still
reflects the upstream metadata (author, URL, license CC BY 4.0).

## Package layout

- `R/` — one file per feature area:
  - `glossary.R` — main `glossary()` function + `glossary_add_to_table()` helper
  - `glossary_add.R` — `glossary_add()` to append a term/definition to a YAML file
  - `glossary_options.R` — `glossary_options()`, `glossary_reset()`,
    `glossary_path()`, `glossary_popup()`, `glossary_persistent()`
  - `glossary_style.R` — `glossary_style()` CSS generation
  - `glossary_table.R` — `glossary_table()` to render collected terms
  - `glossary_load_all.R` — `glossary_load_all()` to bulk-load a glossary file
  - `add_to_quarto.R` — `add_to_quarto()` scaffolds a Quarto book for a
    persistent glossary (copies YAML/CSS, edits `_setup.R`/`.Rprofile`)
  - `zzz.R` — `.onLoad()` sets default options; `is_latex()` helper
- `tests/testthat/` — one `test-{name}.R` per `R/{name}.R` file, testthat
  edition 3
- `inst/glossary.yml` — bundled example glossary used in package examples/tests
  (includes deliberately tricky terms, e.g. "alpha" vs "alpha (graphics)",
  "API" vs "Capital income", to guard against substring-matching bugs)
- `vignettes/glossary.yml` — a separate, smaller example glossary used only by
  `vignettes/glossary.Rmd`; not the same file as `inst/glossary.yml`
- `vignettes/glossary.Rmd` — the shipped package vignette

## Glossary YAML schema

Plain YAML mapping of term -> definition (definitions are pipe-block strings,
markdown allowed):

```yaml
alpha: |
  The threshold chosen in Neyman-Pearson ...

alpha (graphics): |
  A value between 0 and 1 ...
```

Term lookup is case-insensitive but must be an **exact** match after
`trimws(tolower())` on both sides — not substring matching. This was a recent
bug fix (see "Current focus" below); don't reintroduce `grep()`-based
substring matching for term lookup.

## Root-level scratch/draft files (not vignettes, not shipped)

- `glossary-package-revamped.qmd` (+ `_files/`, `.html`) — draft write-up of
  the grep-matching bug fix; a working note, not documentation
- `test-glossary.qmd` (+ `_files/`, `.html`) — ad hoc manual test of
  `glossary()` in a Quarto doc

These are working files left at the repo root; treat them as scratch unless
told otherwise (don't polish, document, or ship them).

## Current focus (as of 2026-08-20)

**MAJOR SETUP COMPLETE:**
- ✅ Fixed DESCRIPTION metadata (fork status, authors, URLs)
- ✅ Package check passes cleanly (0 errors/warnings/notes)
- ✅ Set up independent GitHub Pages documentation via pkgdown
- ✅ Created GitHub Actions workflow for auto-deployment
- ✅ Integrated third-party glossary loading (glossary-pb example)
- ✅ Extended project plan with Phases 5-7 (glossary integration, GitHub Pages, cross-linking)

**COMPLETED TASKS (from 2026-08-19 Plan):**
1. ✅ Update DESCRIPTION metadata
2. ✅ Update README.md with fork header and third-party glossary example
3. ✅ Create FORK_NOTES.md (documenting differences from upstream)
4. ✅ GitHub repo already exists (glossary2)
5. ✅ Git remote verified
6. ✅ devtools::check() passes cleanly
7. ⏳ GitHub Release (v1.0.1) — pending manual creation
8. ⏳ Contact DeBruine via GitHub issue — pending

**NEXT STEPS:**
- Enable GitHub Pages in repo settings (Settings → Pages → GitHub Actions)
  Site will deploy to: https://petzi53.github.io/glossary2
- Create GitHub release tag v1.0.1 with FORK_NOTES.md reference
- Open GitHub issue on debruine/glossary repo (respectful outreach)

## Integration with glossary-pb

Users can load the personal glossary from glossary-pb:

```r
library(glossary2)
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
```

The glossary-pb README should include this example and link to glossary2 documentation.

## Conventions

Follow the `r-package-development` and `peter-global` skills for coding
style, testing conventions, and NEWS.md bullet formatting. Notable
project-specific points:
- Roxygen uses markdown (`Roxygen: markdown = TRUE`); re-document with
  `devtools::document()` after any roxygen comment change.
- `Config/testthat/edition: 3`.

