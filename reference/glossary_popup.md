# Set or get the default popup type

Set or get the default popup type

## Usage

``` r
glossary_popup(popup)
```

## Arguments

- popup:

  If NULL, get the current default popup type, or set to one of "click",
  "hover", or "none"

## Value

string if popup is NULL

## Examples

``` r
# get current popup style
popstyle <- glossary_popup()

# change popup to click style
glossary_popup("click")

# change back to original popup style
glossary_popup(popstyle)
```
