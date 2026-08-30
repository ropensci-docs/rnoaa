# Visualize missingness in a dataframe

Gives you an at-a-glance ggplot of the missingness inside a dataframe,
colouring cells according to missingness, where black indicates a
present cell and grey indicates a missing cell. As it returns a `ggplot`
object, it is very easy to customize and change labels, and so on.

## Usage

``` r
vis_miss(x, cluster = FALSE, sort_miss = FALSE)
```

## Arguments

- x:

  a data.frame

- cluster:

  logical `TRUE`/`FALSE`. `TRUE` specifies that you want to use
  hierarchical clustering (mcquitty method) to arrange rows according to
  missingness. `FALSE` specifies that you want to leave it as is.

- sort_miss:

  logical `TRUE`/`FALSE`. `TRUE` arranges the columns in order of
  missingness.

## Details

`vis_miss` visualises a data.frame to display missingness. This is taken
from the visdat package, currently only available on github:
https://github.com/tierneyn/visdat

## Examples

``` r
if (FALSE) { # \dontrun{
  monitors <- c("ASN00003003", "ASM00094299")
  weather_df <- meteo_pull_monitors(monitors)
  vis_miss(weather_df)
} # }
```
