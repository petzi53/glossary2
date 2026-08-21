# Set or get the default glossary path

Set or get the default glossary path

## Usage

``` r
glossary_path(path, create = FALSE)
```

## Arguments

- path:

  the path to the glossary file, or NULL for local definitions

- create:

  create a new glossary file if it doesn't exist

## Value

path string if path is NULL

## Examples

``` r
path <- glossary_path() # get current path

# create (if doesn't exist) and set path
newpath <- tempfile("glossary", fileext = ".yml")
glossary_path(newpath, create = TRUE)
#> /tmp/Rtmp4De1Ot/glossary19c6306532cf.yml did not exist; it has been created

# set path (assumes file exists)
glossary_path(path)
```
