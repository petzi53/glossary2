# glossary2 (development version)

## Version 1.0.1 — Community Maintenance Fork

This is the first release of **glossary2**, a community-maintained fork of Lisa DeBruine's 
[glossary](https://github.com/debruine/glossary) package. The original package is no longer 
actively maintained, but remains an excellent solution for adding glossaries to Quarto and 
R Markdown documents.

**Original author:** Lisa DeBruine (https://github.com/debruine)  
**Current maintainer:** Peter Baumgartner (community, best-effort support)  
**License:** CC BY 4.0 (unchanged)

### Critical Bug Fixes

#### Term Matching: Exact Case-Insensitive Match

* **Fixed:** The original package used substring grep matching for term lookup, causing serious 
  bugs where "API" would match "Capital income" and "alpha" would match "alpha (graphics)".
* **Solution:** Replaced with exact case-insensitive matching. Terms are now matched after 
  `trimws(tolower())` on both the query and the glossary names—exact equality, not substring 
  matching.

#### psyteachr Links: HTML Escaping and Quote Handling

* **Fixed:** Links in the term column of `glossary_table()` were being HTML-escaped and had 
  their quotes mangled when rendered through `rmarkdown::render()` or Quarto. The bug was a 
  combination of two issues:
  1. Missing `format` argument to `kableExtra::kable()`, causing unreliable format detection
  2. Hand-built anchor tags with single quotes, which Pandoc's markdown parser then 
     reinterpreted and autolinked when the tag wasn't recognized as raw HTML
* **Solution:** 
  1. Use `kableExtra::cell_spec(format = "html", link = url)` to safely build links with 
     proper HTML quoting
  2. Explicitly pass `format = "html"` (or `"latex"` for LaTeX output) to `kable()` to prevent 
     format detection ambiguity

---

# Upstream Release Notes (glossary package, for reference)

# glossary 1.0.9003

* Fixed a bug where terms could have multiple matches (e.g., "alpha" would match both "alpha" and "alpha (graphics)")

# glossary 1.0.9002

* Added `add_to_quarto()` to set up a quarto book with a persistent glossary
* `glossary_style()` now has an `inline` argument (default TRUE) for easier use in creating inline css versus writing to a linked CSS file

# glossary 1.0.9001

* Added `glossary_load_all()` to load all definitions in a glossary file 
* Added `glossary_persistent()` to create a persistent list of used definitions that loads between chapters when creating quarto books or other projects where definitions are added across multiple environments

# glossary 1.0.0

# glossary 0.0.0.9002

* Cleaned up popup display of definitions with lists or line breaks
* Fixed bug when setting `glossary_path(NULL)`
* Added `create` argument to `glossary_path()` to control whether a new file should be created if it doesn't exist
* Fixed bug in link to psyteachr glossary

# glossary 0.0.0.9001

* Added a `NEWS.md` file to track changes to the package.
* Added popup styles and default to "click"
