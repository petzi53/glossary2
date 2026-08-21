# Fork Notes: Development and Design Decisions

## Fork Notes: glossary2

### About This Fork

`glossary2` is a fork of Lisa DeBruine’s
[glossary](https://github.com/debruine/glossary) R package. DeBruine’s
original design is elegant and thoughtfully crafted for adding
interactive glossaries to Quarto and R Markdown documents. This fork
addresses a critical bug in term matching.

### Differences from Upstream

#### Term Matching: Exact Case-Insensitive Lookup

**Problem:** The original package used
`grep(term, names(gloss), ignore.case = TRUE)` to look up glossary
terms. This performed **substring matching**, causing serious bugs
where: - Looking up “API” would incorrectly match “Capital income” -
Looking up “alpha” would match “alpha (graphics)” - Any term could
potentially match unintended entries

**Solution:** Replaced substring matching with exact case-insensitive
matching. The key change in `R/glossary.R` (lines 75–81):

``` r

clean_term <- trimws(tolower(term))
clean_names <- trimws(tolower(names(gloss)))
index <- which(clean_term == clean_names)
if (length(index)) term <- names(gloss)[index[[1]]]
```

This ensures term lookup is **exact** (no substring matches) while
remaining **case-insensitive**.

**Test coverage:** - `tests/testthat/test-glossary.R` includes
regression tests for exact matching, case insensitivity, and edge
cases - `inst/glossary.yml` includes terms designed to catch
substring-matching bugs (“API” vs “Capital income”, “alpha” vs “alpha
(graphics)”)

#### Scope of Changes

Beyond the critical bugfix, the core functionality remains true to
DeBruine’s original design.

#### Version Changes

| Aspect | Upstream (glossary) | Fork (glossary2) |
|----|----|----|
| Package name | `glossary` | `glossary2` |
| Version | 1.0.1 | 1.0.1 |
| Repository | <https://github.com/debruine/glossary> | <https://github.com/petzi53/glossary2> |
| Maintained by | Lisa DeBruine | Peter Baumgartner |

### License & Attribution

- **License:** CC BY 4.0 (unchanged from original)
- **Original author:** Lisa DeBruine
- **Maintained by:** Peter Baumgartner (since 2026)
- **Copyright:** Lisa DeBruine (original work)

All distributions of glossary2 maintain full attribution to DeBruine’s
original work.

### How to Contribute

Issues and pull requests are welcome. When submitting contributions:

1.  **For bug reports:** Please be specific about which
    terms/definitions trigger the issue
2.  **For PRs:** Keep changes focused; large refactors should be
    discussed in an issue first
3.  **Attribution:** Ensure commit messages and code comments reference
    original upstream work where relevant

### Migration from glossary to glossary2

If you’re currently using the original `glossary` package, you can
switch to `glossary2` with:

``` r

# Remove old installation
remove.packages("glossary")

# Install glossary2
devtools::install_github("petzi53/glossary2")
```

The API is identical; no code changes needed. All existing glossary
files (YAML) and Quarto/R Markdown documents will work without
modification.

### Contact & Collaboration

If you have questions or suggestions:

- **GitHub Issues:** Open an issue at
  <https://github.com/petzi53/glossary2/issues>
- **Pull requests:** Feel free to submit PRs

If the original `glossary` maintainer (Lisa DeBruine) expresses interest
in re-engaging with the package, I’m open to collaboration or
transferring the fork back to her.

------------------------------------------------------------------------

**Last updated:** 2026-08-20
