# Create CSS styles for glossary entries

Set the color and style of the linked in-text terms and pop-up
definitions. Colors should be a valid CSS color string, such as "purple"
or "#FF0000".

## Usage

``` r
glossary_style(
  color = "purple",
  text_decoration = "underline",
  def_bg = "#333",
  def_color = "white",
  inline = TRUE
)
```

## Arguments

- color:

  Text color of the linked term

- text_decoration:

  Style of the linked term; a valid CSS text-decoration string, such as
  "none", underline" or "red wavy underline"

- def_bg:

  Background color of the definition pop-up

- def_color:

  Text color of the definition pop-up

- inline:

  If TRUE, includes
