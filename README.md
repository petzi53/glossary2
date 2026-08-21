
<!-- README.md is generated from README.Rmd. Please edit that file -->

# glossary2: Community-Maintained Fork <a href="https://github.com/petzi53/glossary2"><img src="man/figures/logo.png" align="right" height="120" /></a>

<!-- badges: start -->

<!-- badges: end -->

A maintained fork of the excellent
[glossary](https://github.com/debruine/glossary) package by [Lisa
DeBruine](https://github.com/debruine).

## About This Fork

The original `glossary` package is no longer actively maintained by Lisa
DeBruine (no updates since 2023). This fork maintains the package with:

- **Critical bugfix:** Exact case-insensitive term matching (fixes
  substring-matching bugs where “API” would incorrectly match “Capital
  income”)
- **Enhanced functionality:** Improved term lookup and edge case
  handling
- **Community support:** Best-effort maintenance and issue responses

**Attribution:** This is a fork of Lisa DeBruine’s work. The original
package remains licensed under CC BY 4.0, and DeBruine is credited as
the original author in all distributions.

**Maintenance note:** This is a community fork maintained on a
best-effort basis. While issues and PRs are welcome, response times may
vary due to time constraints. If you need urgent support or want to
contribute significantly, please consider the original repository or
reach out via issues.

## What is glossary?

There is a lot of necessary jargon to learn for coding. The goal of
glossary is to provide a lightweight solution for making glossaries in
educational materials written in quarto or R Markdown. This package
provides functions to link terms in text to their definitions in an
external glossary file, as well as create a glossary table of all linked
terms at the end of a section.

## Installation

You can install glossary2 from GitHub with:

``` r
# install.packages("devtools")
devtools::install_github("petzi53/glossary2")
```

## Example

Click on the terms to see a popup definition.

``` r
library(glossary2) 
glossary_path("inst/glossary.yml")
glossary_style("purple", "underline")
```

<style>
a.glossary {
  color: purple;
  text-decoration: underline;
  cursor: help;
  position: relative;
}
&#10;/* only needed for popup = "click" */
/* popup-definition */
a.glossary .def {
  display: none;
  position: absolute;
  z-index: 1;
  width: 200px;
  bottom: 100%;
  left: 50%;
  margin-left: -100px;
  background-color: #333;
  color: white;
  padding: 5px;
  border-radius: 6px;
}
/* show on click */
a.glossary:active .def {
  display: inline-block;
}
/* triangle arrow */
a.glossary:active .def::after {
  content: ' ';
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #333 transparent transparent transparent;
}
</style>

To calculate <a class='glossary'>power<span class="def">The probability
of rejecting the null hypothesis when it is false, for a specific
analysis, effect size, sample size, and criteria for
significance.</span></a>, you need to know the intended sample size,
expected <a class='glossary'>effect size<span class="def">‘quantitative
reflection of the magnitude of some phenomenon that is used for the
purpose of addressing a question of interest’ (Kelley & Preacher,
2012)</span></a> (e.g.,
<a class='glossary'>SESOI<span class="def">Smallest Effect Size of
Interest: the smallest effect that is theoretically or practically
meaningful \| See Equivalence Testing for Psychological Research for a
tutorial on methods for choosing an SESOI.</span></a>), and
<a class='glossary'>alpha<span class="def">The threshold chosen in
Neyman-Pearson hypothesis testing to distinguish test results that lead
to the decision to reject the null hypothesis, or not, based on the
desired upper bound of the Type 1 error rate. An alpha level of 5% is
most commonly used, but other alpha levels can be used as long as they
are determined and preregistered by the researcher before the data is
analyzed.</span></a> criterion.

<table class="table" style="margin-left: auto; margin-right: auto;">

<thead>

<tr>

<th style="text-align:left;">

term
</th>

<th style="text-align:left;">

definition
</th>

</tr>

</thead>

<tbody>

<tr>

<td style="text-align:left;">

alpha
</td>

<td style="text-align:left;">

The threshold chosen in Neyman-Pearson hypothesis testing to distinguish
test results that lead to the decision to reject the null hypothesis, or
not, based on the desired upper bound of the Type 1 error rate. An alpha
level of 5% is most commonly used, but other alpha levels can be used as
long as they are determined and preregistered by the researcher before
the data is analyzed.
</td>

</tr>

<tr>

<td style="text-align:left;">

effect size
</td>

<td style="text-align:left;">

‘quantitative reflection of the magnitude of some phenomenon that is
used for the purpose of addressing a question of interest’ (Kelley &
Preacher, 2012)
</td>

</tr>

<tr>

<td style="text-align:left;">

power
</td>

<td style="text-align:left;">

The probability of rejecting the null hypothesis when it is false, for a
specific analysis, effect size, sample size, and criteria for
significance.
</td>

</tr>

<tr>

<td style="text-align:left;">

SESOI
</td>

<td style="text-align:left;">

Smallest Effect Size of Interest: the smallest effect that is
theoretically or practically meaningful

See [Equivalence Testing for Psychological
Research](https://doi.org/10.1177/2515245918770963) for a tutorial on
methods for choosing an SESOI.
</td>

</tr>

</tbody>

</table>

## Third-Party Glossaries

You can load glossaries from external GitHub repositories. For example,
to load Peter Baumgartner’s personal glossary:

``` r
library(glossary2)
glossary_load_all("https://raw.githubusercontent.com/petzi53/glossary-pb/main/glossary.yml")
glossary_style("blue", "underline")
```

See [glossary-pb](https://github.com/petzi53/glossary-pb) for more
details.

## More Information

See the `vignette("glossary")`, the [full documentation
site](https://www.peter-baumgartner.net/glossary2/), or
[FORK_NOTES.md](FORK_NOTES.md) for more details.
