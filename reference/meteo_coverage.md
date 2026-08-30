# Determine the "coverage" for a station data frame

Call this function after pulling down observations for a set of stations
to retrieve the "coverage" (i.e. how complete each field is). If either
or both `obs_start_date` or `obs_end_date` are specified, the coverage
test will be limited to that date range.

## Usage

``` r
meteo_coverage(
  meteo_df,
  obs_start_date = NULL,
  obs_end_date = NULL,
  verbose = FALSE
)
```

## Arguments

- meteo_df:

  a *meteo* `data.frame`

- obs_start_date:

  specify either or both (obs_start_date, obs_end_date) to constrain
  coverate tests. These should be `Date` objects.

- obs_end_date:

  specify either or both (obs_start_date, obs_end_date) to constrain
  coverate tests. These should be `Date` objects.

- verbose:

  if `TRUE` will display the coverage summary along with returning the
  coverage data.frame

## Value

a `list` containing 2 `data.frame`s named 'summary' and 'detail'. The
'summary' `data.frame` contains columns:


    $ id         (chr)
    $ start_date (time)
    $ end_date   (time)
    $ total_obs  (int)

with additional fields (and their coverage percent) depending on which
weather variables were queried and available for the weather station.
The `data.frame` named 'detail' contains the same columns as the
`meteo_df` input data, but expands the rows to contain `NA`s for days
without data.

## Examples

``` r
if (FALSE) { # \dontrun{

monitors <- c("ASN00095063", "ASN00024025", "ASN00040112", "ASN00041023",
             "ASN00009998", "ASN00066078", "ASN00003069", "ASN00090162",
             "ASN00040126", "ASN00058161")
obs <- meteo_pull_monitors(monitors)
obs_covr <- meteo_coverage(obs)

} # }
```
