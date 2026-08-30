# Read NOAA ISD/ISH local file

Read NOAA ISD/ISH local file

## Usage

``` r
isd_read(
  path,
  additional = TRUE,
  parallel = FALSE,
  cores = getOption("cl.cores", 2),
  progress = FALSE
)
```

## Arguments

- path:

  (character) path to the file. required.

- additional:

  (logical) include additional and remarks data sections in output.
  Default: `TRUE`. Passed on to
  [`isdparser::isd_parse()`](https://rdrr.io/pkg/isdparser/man/isd_parse.html)

- parallel:

  (logical) do processing in parallel. Default: `FALSE`

- cores:

  (integer) number of cores to use: Default: 2. We look in your option
  "cl.cores", but use default value if not found.

- progress:

  (logical) print progress - ignored if `parallel=TRUE`. The default is
  `FALSE` because printing progress adds a small bit of time, so if
  processing time is important, then keep as `FALSE`

## Value

A tibble (data.frame)

## Details

`isd_read` - read a `.gz` file as downloaded from NOAA's website

## References

https://ftp.ncdc.noaa.gov/pub/data/noaa/

## See also

[`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md),
[`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md),
[`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)

Other isd:
[`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md),
[`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md),
[`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
file <- system.file("examples", "011490-99999-1986.gz", package = "rnoaa")
isd_read(file)
isd_read(file, additional = FALSE)
} # }
```
