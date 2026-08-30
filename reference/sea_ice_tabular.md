# Sea ice tabular data

Collects `.csv` files from NOAA, and binds them together into a single
data.frame. Data across years, with extent and area of ice.

## Usage

``` r
sea_ice_tabular(...)
```

## Arguments

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html) -
  beware that curl options are passed to each http request, for each of
  24 requests.

## Value

A data.frame with columns:

- year (integer)

- mo (integer)

- data.type (character)

- region (character)

- extent (numeric)

- area (numeric)

## Details

An example file, for January, North pole:
`https://sidads.colorado.edu/DATASETS/NOAA/G02135/north/monthly/data/N_01_extent_v3.0.csv`

a value in any cell of -9999 indicates missing data

## See also

[`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md)

## Examples

``` r
if (FALSE) { # \dontrun{
df <- sea_ice_tabular()
df
} # }
```
