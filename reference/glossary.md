# Display glossary entry

Display a glossary term with an optional popup of the definition, and
add the term to the table created by
[`glossary_table`](https://www.peter-baumgartner.net/glossary2/reference/glossary_table.md).
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
  [`glossary_table`](https://www.peter-baumgartner.net/glossary2/reference/glossary_table.md)

- show:

  whether to show the term or just the definition

- popup:

  whether to show the popup on "click" or "hover" (or "none"); set
  default with
  [`glossary_popup`](https://www.peter-baumgartner.net/glossary2/reference/glossary_popup.md)

- path:

  the path to the glossary file, or NULL for local definitions; set
  default with
  [`glossary_path`](https://www.peter-baumgartner.net/glossary2/reference/glossary_path.md)

## Value

character string

## Details

If the path is set to "psyteachr", the glossary term will link to the
[PsyTeachR glossary](https://psyteachr.github.io/glossary/). Set
`show = "def"` to just show the definition.

## Examples

``` r
# set glossary path to example file
path <- system.file("glossary.yml", package = "glossary2")
glossary_path(path)

glossary("alpha")
#> [1] "<a class='glossary'>alpha<span class='def'>The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed.</span></a>"
glossary("alpha", "$\\alpha$")
#> [1] "<a class='glossary'>$\\alpha$<span class='def'>The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed.</span></a>"
glossary("alpha", def = "The first letter of the Greek alphabet")
#> [1] "<a class='glossary'>alpha<span class='def'>The first letter of the Greek alphabet</span></a>"
glossary("alpha", show = "term")
#> [1] "<a class='glossary'>alpha<span class='def'>The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed.</span></a>"
glossary("alpha", show = "def")
#> [1] "The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed."
```
