# glossary2 v1.0.1 Release Notes

**Release Date:** 2026-08-20

## First Release of glossary2: Community-Maintained Fork

This is the initial release of `glossary2`, a community-maintained fork of Lisa DeBruine's 
[glossary](https://github.com/debruine/glossary) R package.

## What's New

### Critical Bug Fix: Exact Term Matching
- **Problem:** The original glossary package used substring matching with `grep()`, causing 
  false positives where "API" would incorrectly match "Capital income" and "alpha" would 
  match "alpha (graphics)".
- **Solution:** Replaced substring grep matching with exact case-insensitive matching using 
  `tolower(trimws(term)) %in% tolower(trimws(names(gloss)))`.
- **Impact:** Eliminates false matches while maintaining case-insensitive term lookup.
- **Testing:** Added comprehensive regression tests to prevent reintroduction of this bug.

## Package Rebrand

- Package name changed from `glossary` to `glossary2` to reflect its independent status
- GitHub repository updated to https://github.com/petzi53/glossary2
- DESCRIPTION updated with new maintainer information
- All examples, vignettes, and tests updated to reference `glossary2`

## Attribution & License

**Original Author:** Lisa DeBruine  
**Maintained By:** Peter Baumgartner (community-maintained, best-effort)  
**License:** CC BY 4.0 (unchanged from original)

Full attribution to DeBruine's original work is maintained throughout the package.

## Installation

Install glossary2 from GitHub:

```r
devtools::install_github("petzi53/glossary2")
```

## Documentation

- **README.md:** Fork status, attribution, and installation instructions
- **FORK_NOTES.md:** Detailed documentation of differences from upstream
- **Vignette:** `vignette("glossary")` provides usage examples
- **Original repo:** https://github.com/debruine/glossary

## Maintenance & Support

This is a community fork maintained on a best-effort basis. 

- **Issue tracking:** https://github.com/petzi53/glossary2/issues
- **Response times:** Best-effort; may vary due to time constraints
- **Contributions:** Pull requests welcome

If you need urgent support or want to contribute significantly, please consider the original 
repository.

## Next Steps

The maintainer has reached out to Lisa DeBruine regarding this fork (via GitHub issue) and 
is open to collaboration or integration of improvements back to the original package if 
the original maintainer re-engages.

---

**Thanks to Lisa DeBruine for creating the excellent glossary package.**
