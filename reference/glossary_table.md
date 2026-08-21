# Display glossary table

All terms defined with
[`glossary`](https://debruine.github.io/glossary/reference/glossary.md)
(since the last call to
[`glossary_reset`](https://debruine.github.io/glossary/reference/glossary_reset.md))
are added to a list, which this function displays using kable (or
outputs as a data frame).

## Usage

``` r
glossary_table(as_kable = TRUE)
```

## Arguments

- as_kable:

  if the output should be a kableExtra table or a data frame

## Value

kable table or data frame

## Examples

``` r
# \donttest{
glossary_reset()
# add a definition to the table
glossary("term", def = "definition", path = NULL)
#> [1] "<a class='glossary'>term<span class='def'>definition</span></a>"

glossary_table() # show table as kable
#> <table class="table" style="margin-left: auto; margin-right: auto;">
#>  <thead>
#>   <tr>
#>    <th style="text-align:left;"> term </th>
#>    <th style="text-align:left;"> definition </th>
#>   </tr>
#>  </thead>
#> <tbody>
#>   <tr>
#>    <td style="text-align:left;"> term </td>
#>    <td style="text-align:left;"> definition </td>
#>   </tr>
#> </tbody>
#> </table>
glossary_table(FALSE) # or as a data frame
#>      term definition
#> term term definition
# }
```
