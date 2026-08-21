# Add glossary helper files to a quarto book

Adds the necessary helper files to an existing quarto book project and
gives instructions to edit the \_quarto.yml file accordingly.

## Usage

``` r
add_to_quarto(
  quarto_dir = ".",
  css_path = "glossary.css",
  glossary_path = "glossary.yml",
  script_path = "_setup.R"
)
```

## Arguments

- quarto_dir:

  The base directory for your quarto project

- css_path:

  The relative path to the css file you want to append the glossary
  styles to (creates a new file if it doesn't exist), using the
  quarto_dir as a base directory

- glossary_path:

  The relative path to the glossary file, using the quarto_dir as a base
  directory; if this file does not exist, one will be created

- script_path:

  The relative path to a pre-chapter script, using the quarto_dir as a
  base directory; set to FALSE to omit this step

## Value

No return value, called for side effects.

## Details

The \_quarto.yml file is not edited for you because there is currently
no way to do this that doesn't remove your formatting and comments from
the file.

Since quarto books render each chapter in a separate environment, it is
helpful to have a pre-chapter script that does any common setup. The
code below will be added to a new or existing pre-chapter script, and
this script sourced in the .Rprofile for this project to allow for a
persistent glossary (this project .Rprofile will be run instead of your
global .Rrofile). Set `script_path` to `FALSE` to handle this on your
own.

    library(glossary2)
    glossary_path("glossary.yml")
    glossary_persistent(TRUE)
