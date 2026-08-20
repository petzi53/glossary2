# Fork Notes: glossary2

## About This Fork

`glossary2` is a community-maintained fork of Lisa DeBruine's [glossary](https://github.com/debruine/glossary) 
R package. The original package is no longer actively maintained (last update in 2023), but remains 
an excellent and thoughtfully-designed solution for adding glossaries to educational materials in 
Quarto and R Markdown.

This fork preserves that original work while addressing critical bugs and providing ongoing community 
support on a best-effort basis.

## Differences from Upstream

### Critical Bug Fixes

#### 1. **Term Matching: Exact Case-Insensitive Match**

**Problem:** The original package used `grep(term, names(gloss), ignore.case = TRUE)` to look up 
glossary terms. This approach performed **substring matching**, not exact matching. This caused 
serious bugs where:
- Looking up "API" would incorrectly match "Capital income"
- Looking up "alpha" would match "alpha (graphics)"
- Any term could potentially match unintended entries

**Solution:** Replaced substring grep matching with exact case-insensitive matching using:
```r
tolower(trimws(term)) %in% tolower(trimws(names(gloss)))
```

This ensures term lookup is case-insensitive but **exact**, eliminating false matches.

**Files affected:**
- `R/glossary.R` — Main glossary lookup function
- `inst/glossary.yml` — Added regression test terms ("API", "Capital income", etc.)
- `tests/testthat/test-glossary.R` — Comprehensive test coverage for edge cases

**Related upstream issue:** While no single issue in the original repo captured this, it was 
flagged during fork development as a critical flaw in the matching logic.

### Enhancements

None yet beyond the bugfix. The core functionality remains true to the original design.

### Version Changes

| Aspect | Upstream (glossary) | Fork (glossary2) |
|--------|---------------------|------------------|
| Package name | `glossary` | `glossary2` |
| Version | 1.0.1 | 1.0.1 |
| Repository | https://github.com/debruine/glossary | https://github.com/petzi53/glossary2 |
| Maintained by | Lisa DeBruine (inactive) | Peter Baumgartner (community, best-effort) |

## License & Attribution

- **License:** CC BY 4.0 (unchanged from original)
- **Original author:** Lisa DeBruine
- **Maintained by:** Peter Baumgartner (since 2026)
- **Copyright:** Lisa DeBruine (original work)

All distributions of glossary2 maintain full attribution to DeBruine's original work.

## How to Contribute

Issues and pull requests are welcome. When submitting contributions:

1. **For bug reports:** Please be specific about which terms/definitions trigger the issue
2. **For PRs:** Keep changes focused; large refactors should be discussed in an issue first
3. **Attribution:** Ensure commit messages and code comments reference original upstream work where relevant

## Migration from glossary to glossary2

If you're currently using the original `glossary` package, you can switch to `glossary2` with:

```r
# Remove old installation
remove.packages("glossary")

# Install glossary2
devtools::install_github("petzi53/glossary2")
```

The API is identical; no code changes needed. All existing glossary files (YAML) and Quarto/R Markdown 
documents will work without modification.

## Contact & Collaboration

If you have questions or suggestions:

- **GitHub Issues:** Open an issue at https://github.com/petzi53/glossary2/issues
- **PR feedback:** Feel free to submit PRs; expect best-effort review within 2–4 weeks

If the original `glossary` maintainer (Lisa DeBruine) expresses interest in re-engaging with the 
package, I'm open to collaboration or (preferably) handing back maintenance.

---

**Last updated:** 2026-08-20
