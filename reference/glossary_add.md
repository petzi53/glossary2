# Add a definition

Write a term and definition to an existing glossary file.

## Usage

``` r
glossary_add(term, def, path = glossary_path(), replace = FALSE)
```

## Arguments

- term:

  The term to define

- def:

  The definition to add

- path:

  The path to the glossary file; set default with
  [`glossary_path`](https://www.peter-baumgartner.net/glossary2/reference/glossary_path.md)

- replace:

  Whether to replace an existing definition

## Value

NULL; Called for side effects

## Examples

``` r
# make a new glossary file
path <- tempfile("glossary", fileext = ".yml")
glossary_path(path, create = TRUE)
#> /tmp/Rtmpmb0Gc5/glossary19b81aa331aa.yml did not exist; it has been created

# add an entry for "joins"
glossary_add("joins", "Ways to combine data from two tables")

# now you can access the definition
glossary("joins")
#> [1] "<a class='glossary'>joins<span class='def'>Ways to combine data from two tables</span></a>"
```
