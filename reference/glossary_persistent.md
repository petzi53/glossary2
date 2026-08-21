# Set or get the path to a persistent table object

Quarto books render each chapter in a separate environment, so you need
to set a persistent table if you want to display all glossary items in a
table in a separate chapter. Set the persistent table at the top of each
chapter, after loading the glossary package, and it will automatically
add any glossary entries to the persistent table.

## Usage

``` r
glossary_persistent(path)
```

## Arguments

- path:

  the path to the persistent table, or TRUE for the default table name
  ("glossary-persistent.yml"), or FALSE for no persistence

## Value

path to persistent table object, or FALSE if not set

## Examples

``` r
p <- glossary_persistent() # get current path

# set default persistent table path
glossary_persistent(TRUE)

# set non-default path
glossary_persistent(p)
```
