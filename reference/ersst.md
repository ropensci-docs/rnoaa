# NOAA Extended Reconstructed Sea Surface Temperature (ERSST) data

NOAA Extended Reconstructed Sea Surface Temperature (ERSST) data

## Usage

``` r
ersst(year, month, overwrite = TRUE, version = "v5", ...)
```

## Arguments

- year:

  (numeric) A year. Must be \> 1853. The max value is whatever the
  current year is. Required

- month:

  A month, character or numeric. If single digit (e.g. 8), we add a zero
  in front (e.g., 08). Required

- overwrite:

  (logical) To overwrite the path to store files in or not, Default:
  `TRUE`

- version:

  (character) ERSST version. one of "v5" (default) or "v4"

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

An `ncdf4` object. See ncdf4 for parsing the output

## Details

See
[ersst_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

`ersst()` currently defaults to use ERSST v5 - you can set v4 or v5
using the `version` parameter

If a request is unsuccesful, the file written to disk is deleted before
the function exits.

If you use this data in your research please cite rnoaa
(`citation("rnoaa")`), and cite NOAA ERSST (see citations at link above)

## References

https://www.ncdc.noaa.gov/data-access/marineocean-data/extended-reconstructed-sea-surface-temperature-ersst-v5

## Examples

``` r
if (FALSE) { # \dontrun{
# October, 2015
ersst(year = 2015, month = 10)

# May, 2015
ersst(year = 2015, month = 5)
ersst(year = 2015, month = "05")

# February, 1890
ersst(year = 1890, month = 2)

# Process data
library("ncdf4")
res <- ersst(year = 1890, month = 2)
## varibles
names(res$var)
## get a variable
ncdf4::ncvar_get(res, "ssta")
} # }
```
