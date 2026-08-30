# NOAA Storm Events data

NOAA Storm Events data

## Usage

``` r
se_data(year, type, overwrite = TRUE, ...)

se_files(...)
```

## Arguments

- year:

  (numeric) a four digit year. see output of `se_files()` for available
  years. required.

- type:

  (character) one of details, fatalities, locations, or legacy.
  required.

- overwrite:

  (logical) To overwrite the path to store files in or not, Default:
  `TRUE`

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (optional)

## Value

A tibble (data.frame)

## Note

See
[stormevents_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## References

https://www.ncdc.noaa.gov/stormevents/

## Examples

``` r
if (FALSE) { # \dontrun{
# get list of files and their urls
res <- se_files()
res
tail(res)

# get data
x <- se_data(year = 2013, type = "details")
x

z <- se_data(year = 1988, type = "fatalities")
z

w <- se_data(year = 2003, type = "locations")
w

leg <- se_data(year = 2003, type = "legacy")
leg
} # }
```
