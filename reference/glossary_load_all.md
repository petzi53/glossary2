# Load all definitions

Load all the definitions in a glossary file, usually for subsequent
display using
[`glossary_table`](https://debruine.github.io/glossary/reference/glossary_table.md)

## Usage

``` r
glossary_load_all(path = glossary_path())
```

## Arguments

- path:

  The path to the glossary file; set default with
  [`glossary_path`](https://debruine.github.io/glossary/reference/glossary_path.md)

## Value

NULL; Called for side effects

## Examples

``` r
demo_glossary <- system.file("glossary.yml", package = "glossary")
glossary_load_all(demo_glossary)
#> Error in glossary_load_all(demo_glossary): The file  does not exist

glossary_table(FALSE) # get table as a data frame
#>        term                           definition
#> alpha alpha                                     
#> joins joins Ways to combine data from two tables
```
