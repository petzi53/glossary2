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

## Current focus (as of 2026-08-19)

Working on branch `fix-grep-matching`: term lookup previously used
`grep(term, names(gloss), ignore.case = TRUE)`, which matched substrings
(e.g., "API" matched "Capital income", "alpha" matched "alpha (graphics)").
Fixed to use exact case-insensitive matching. `inst/glossary.yml` has
extra terms specifically added to cover these regression cases in tests.

## Conventions

Follow the `r-package-development` and `peter-global` skills for coding
style, testing conventions, and NEWS.md bullet formatting. Notable
project-specific points:
- Roxygen uses markdown (`Roxygen: markdown = TRUE`); re-document with
  `devtools::document()` after any roxygen comment change.
- `Config/testthat/edition: 3`.
