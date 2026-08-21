# Load all definitions

Load all the definitions in a glossary file, usually for subsequent
display using
[`glossary_table`](https://www.peter-baumgartner.net/glossary2/reference/glossary_table.md)

## Usage

``` r
glossary_load_all(path = glossary_path())
```

## Arguments

- path:

  The path to the glossary file; set default with
  [`glossary_path`](https://www.peter-baumgartner.net/glossary2/reference/glossary_path.md)

## Value

NULL; Called for side effects

## Examples

``` r
demo_glossary <- system.file("glossary.yml", package = "glossary2")
glossary_load_all(demo_glossary)

glossary_table(FALSE) # get table as a data frame
#>                              term
#> SESOI                       SESOI
#> alpha                       alpha
#> alpha (graphics) alpha (graphics)
#> effect size           effect size
#> html                         html
#> joins                       joins
#> p-value                   p-value
#> power                       power
#>                                                                                                                                                                                                                                                                                                                                                                                                        definition
#> SESOI                                                                                                                                                    Smallest Effect Size of Interest: the smallest effect that is theoretically or practically meaningful\n\nSee [Equivalence Testing for Psychological Research](https://doi.org/10.1177/2515245918770963) for a tutorial on methods for choosing an SESOI.
#> alpha            The threshold chosen in Neyman-Pearson hypothesis testing to distinguish test results that lead to the decision to reject the null hypothesis, or not, based on the desired upper bound of the Type 1 error rate. An alpha level of 5% is most commonly used, but other alpha levels can be used as long as they are determined and preregistered by the researcher before the data is analyzed.
#> alpha (graphics)                                                                                                                                                                                                                                                                                                                     A value between 0 and 1 used to control the levels of transparency in a plot
#> effect size                                                                                                                                                                                                                                             'quantitative reflection of the magnitude of some phenomenon that is used for the purpose of addressing a question of interest' (Kelley & Preacher, 2012)
#> html                                                                                                                                                                                                                                                                                            This is a paragraph with a [link](https://url.com).\n\nAnd another paragraph before a list:\n\n* Item 1\n* List 2
#> joins                                                                                                                                                                                                                                                                                                                                                                        Ways to combine data from two tables
#> p-value                                                                                                                                                                               The probability of the observed data, or more extreme data, if the null hypothesis is true. The lower the p-value, the higher the test statistic, and less likely it is to observe the data if the null hypothesis is true.
#> power                                                                                                                                                                                                                                                        The probability of rejecting the null hypothesis when it is false, for a specific analysis, effect size, sample size, and criteria for significance.
```
