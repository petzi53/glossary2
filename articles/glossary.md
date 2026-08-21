# glossary

## Setup

``` r

library(glossary2)
```

## Definition File

Set the default path to the definition file.

``` r

glossary_path("glossary.yml")
```

### Definition YAML File

You can store definitions in a YAML file. Use markdown to create
paragraphs, links, and lists. Make sure each new line in a definition is
indented two spaces (sorry YAML is a bit picky, but it’s the best
human-editable solution).

    SESOI: |
      Smallest Effect Size of Interest: the smallest effect that is theoretically or practically meaningful

      See [Equivalence Testing for Psychological Research](https://doi.org/10.1177/2515245918770963) for a tutorial on methods for choosing an SESOI.
    p-value: |
      The probability of the observed data, or more extreme data, if the null hypothesis is true. The lower the p-value, the higher the test statistic, and less likely it is to observe the data if the null hypothesis is true.

### Add Definitions with Code

Alternatively, you can add definitions to the file with code. You don’t
need to indent new lines if you add definitions this way.

``` r
glossary_add(term = "power",
             def = "The probability of rejecting the null hypothesis when it is false, for a specific analysis, effect size, sample size, and criteria for significance."
")
```

### PsyTeachR Glossary

If you want to use the [PsyTeachR
Glossary](https://psyteachr.github.io/glossary/), set the path to
“psyteachr”. This will produce links to the online glossary when you
click on the term, so it’s best to use with the “hover” popup type (see
below).

``` r

glossary_path("psyteachr")
glossary_popup("hover")
```

``` r

# Example: inline term linked to the live PsyTeachR glossary
glossary("absolute path")
```

## Popup Type

Set the popup type with
[`glossary_popup()`](https://debruine.github.io/glossary/reference/glossary_popup.md);
options are “click” (default), “hover”, and “none”.

``` r

glossary_popup("none")
```

alpha

``` r

glossary_popup("hover")
```

alpha

``` r

glossary_popup("click")
```

alphaThe threshold chosen in Neyman-Pearson hypothesis testing to
distinguish test results that lead to the decision to reject the null
hypothesis, or not, based on the desired upper bound of the Type 1 error
rate. An alpha level of 5% is most commonly used, but other alpha levels
can be used as long as they are determined and preregistered by the
researcher before the data is analyzed.

## Style

If your popup type is “click”, you must add a style with the
[`glossary_style()`](https://debruine.github.io/glossary/reference/glossary_style.md)
function for the popups to work. If you set the popup type to “hover”,
or “none”, you can omit this and the in-text glossary terms will be
styled like other links in your document.

Set the style at the top of your document (set the code chunk to
`results='asis'`). The code below shows the default options.

``` r

glossary_style(color = "purple", 
               text_decoration = "underline",
               def_bg = "#333",
               def_color = "white")
```

Alternatively, you can add your own CSS to your document (inline or in
an external linked file) to create a more customised appearance. Just
copy the text returned by the
[`glossary_style()`](https://debruine.github.io/glossary/reference/glossary_style.md)
function and customise it.

``` r

# append default styles to an external CSS file
write(glossary_style(), "glossary.css", append = TRUE)
```

## In-Text Terms

There are a few ways to customise the glossary term display.

- Look up a term from the glossary file with `glossary("alpha")`:
  alphaThe threshold chosen in Neyman-Pearson hypothesis testing to
  distinguish test results that lead to the decision to reject the null
  hypothesis, or not, based on the desired upper bound of the Type 1
  error rate. An alpha level of 5% is most commonly used, but other
  alpha levels can be used as long as they are determined and
  preregistered by the researcher before the data is analyzed.

- Display a different value for the term with
  `glossary("alpha", "$\\alpha$")`: $`\alpha`$The threshold chosen in
  Neyman-Pearson hypothesis testing to distinguish test results that
  lead to the decision to reject the null hypothesis, or not, based on
  the desired upper bound of the Type 1 error rate. An alpha level of 5%
  is most commonly used, but other alpha levels can be used as long as
  they are determined and preregistered by the researcher before the
  data is analyzed.

- Use an inline definition instead of the glossary file with
  `glossary("beta", def = "The second letter of the Greek alphabet")`:
  betaThe second letter of the Greek alphabet

- Just show the term (no hover) with
  `glossary("effect size", show = "term")`: effect size‘quantitative
  reflection of the magnitude of some phenomenon that is used for the
  purpose of addressing a question of interest’ (Kelley & Preacher,
  2012)

- Just show the definition with `glossary("p-value", show = "def")`: The
  probability of the observed data, or more extreme data, if the null
  hypothesis is true. The lower the p-value, the higher the test
  statistic, and less likely it is to observe the data if the null
  hypothesis is true.

## Glossary Table

Show the table of terms defined on this page (or since the last reset)
with
[`glossary_table()`](https://debruine.github.io/glossary/reference/glossary_table.md):

| term | definition |
|:---|:---|
| alpha | The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed. |
| beta | The second letter of the Greek alphabet |
| effect size | ‘quantitative reflection of the magnitude of some phenomenon that is used for the purpose of addressing a question of interest’ (Kelley & Preacher, 2012) |
| p-value | The probability of the observed data, or more extreme data, if the null hypothesis is true. The lower the p-value, the higher the test statistic, and less likely it is to observe the data if the null hypothesis is true. |

You can reset the glossary table between sections with
[`glossary_reset()`](https://debruine.github.io/glossary/reference/glossary_reset.md).

## Quarto Books

Since quarto book chapters are each rendered in a new environment, you
will need to load the glossary package for each chapter, and do any
setup.

The function
[`add_to_quarto()`](https://debruine.github.io/glossary/reference/add_to_quarto.md)
will set this up for you (this function is still experimental, so make
sure you’ve committed a version of your project before using). If your
working directory is the quarto project, run the following code to set
it up. This will create and link a css file to setup popup styles, and
create a demo glossary.yml file if you don’t already have one. It will
also add the required setup code to a file called \_setup.R, and source
this file in the .Rprofile for this project, so that it will run before
each chapter in the book.

``` r

add_to_quarto(quarto_dir = ".",
              css_path = "glossary.css",
              glossary_path = "glossary.yml",
              script_path = "_setup.R")
```

You can set up a book in another directory by changing the `quarto_dir`
argument. Specify an existing `css_path` to append the popup styles to
it. You can also specify an existing glossary path. Set `script_path` to
`FALSE` to use a different method for pre-chapter setup.

``` r

add_to_quarto(quarto_dir = "~/mybook",
              css_path = "style.css",
              glossary_path = "my_glossary.yml",
              script_path = FALSE)
```

If you don’t use the .Rprofile and \_setup.R script method, you will
need to start each chapter with a setup chunk that sets the appropriate
defaults for your project.

``` r

library(glossary2)
glossary_path("my_glossary.yml")
glossary_persistent(TRUE)
```

Now, when you display the glossary table, it will show all items added
since the last call to
[`glossary_reset()`](https://debruine.github.io/glossary/reference/glossary_reset.md)
in the project.
