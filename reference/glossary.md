# Display glossary entry

Display a glossary term with an optional popup of the definition, and
add the term to the table created by
[`glossary_table`](https://debruine.github.io/glossary/reference/glossary_table.md).
This function is mainly meant to be used via inline R in R Markdown or
quarto documents, e.g.:

`` `r glossary("Alpha")` `` does not always have to equal .05.

## Usage

``` r
glossary(
  term,
  display = term,
  def = NULL,
  add_to_table = TRUE,
  show = c("term", "def"),
  popup = glossary_popup(),
  path = glossary_path()
)
```

## Arguments

- term:

  The glossary term to link to, can contain spaces

- display:

  The text to display (if different than the term)

- def:

  The short definition to display on hover and in the glossary table; if
  NULL, this will be looked up from the file in the `path` argument

- add_to_table:

  whether to add to the table created by
  [`glossary_table`](https://debruine.github.io/glossary/reference/glossary_table.md)

- show:

  whether to show the term or just the definition

- popup:

  whether to show the popup on "click" or "hover" (or "none"); set
  default with
  [`glossary_popup`](https://debruine.github.io/glossary/reference/glossary_popup.md)

- path:

  the path to the glossary file, or NULL for local definitions; set
  default with
  [`glossary_path`](https://debruine.github.io/glossary/reference/glossary_path.md)

## Value

character string

## Details

If the path is set to "psyteachr", the glossary term will link to the
[PsyTeachR glossary](https://psyteachr.github.io/glossary/). Set
`show = "def"` to just show the definition.

## Examples

``` r
# set glossary path to example file
path <- system.file("glossary.yml", package = "glossary")
glossary_path(path)
#> Error in glossary_path(path): The file  does not exist

glossary("alpha")
#> Warning: The definition for "alpha" was not found in 
#> [1] "<a class='glossary'>alpha<span class='def'></span></a>"
glossary("alpha", "$\\alpha$")
#> Warning: The definition for "alpha" was not found in 
#> [1] "<a class='glossary'>$\\alpha$<span class='def'></span></a>"
glossary("alpha", def = "The first letter of the Greek alphabet")
#> [1] "<a class='glossary'>alpha<span class='def'>The first letter of the Greek alphabet</span></a>"
glossary("alpha", show = "term")
#> Warning: The definition for "alpha" was not found in 
#> [1] "<a class='glossary'>alpha<span class='def'></span></a>"
glossary("alpha", show = "def")
#> Warning: The definition for "alpha" was not found in 
#> [1] ""
```
