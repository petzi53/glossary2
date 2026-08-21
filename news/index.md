# Changelog

## glossary2 (development version)

### Version 1.0.1 — Community Fork

This is the first release of **glossary2**, a fork of Lisa DeBruine’s
[glossary](https://github.com/debruine/glossary) package. The original
package is no longer actively maintained, but remains an excellent
solution for adding glossaries to Quarto and R Markdown documents.

**Original author:** Lisa DeBruine (<https://github.com/debruine>)  
**Current maintainer:** Peter Baumgartner (community, best-effort
support)  
**License:** CC BY 4.0 (unchanged)

#### Critical Bug Fixes

##### Term Matching: Exact Case-Insensitive Match

- **Fixed:** The original package used substring grep matching for term
  lookup, causing serious bugs where “API” would match “Capital income”
  and “alpha” would match “alpha (graphics)”.
- **Solution:** Replaced with exact case-insensitive matching. Terms are
  now matched after `trimws(tolower())` on both the query and the
  glossary names—exact equality, not substring matching.

##### psyteachr Links: HTML Escaping and Quote Handling

- **Fixed:** Links in the term column of
  [`glossary_table()`](https://www.peter-baumgartner.net/glossary2/reference/glossary_table.md)
  were being HTML-escaped and had their quotes mangled when rendered
  through
  [`rmarkdown::render()`](https://pkgs.rstudio.com/rmarkdown/reference/render.html)
  or Quarto. The bug was a combination of two issues:
  1.  Missing `format` argument to
      [`kableExtra::kable()`](https://rdrr.io/pkg/knitr/man/kable.html),
      causing unreliable format detection
  2.  Hand-built anchor tags with single quotes, which Pandoc’s markdown
      parser then reinterpreted and autolinked when the tag wasn’t
      recognized as raw HTML
- **Solution:**
  1.  Use `kableExtra::cell_spec(format = "html", link = url)` to safely
      build links with proper HTML quoting
  2.  Explicitly pass `format = "html"` (or `"latex"` for LaTeX output)
      to `kable()` to prevent format detection ambiguity

------------------------------------------------------------------------
