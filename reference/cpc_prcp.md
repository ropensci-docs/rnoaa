# Precipitation data from NOAA Climate Prediction Center (CPC)

Precipitation data from NOAA Climate Prediction Center (CPC)

## Usage

``` r
cpc_prcp(date, us = FALSE, drop_undefined = FALSE, ...)
```

## Arguments

- date:

  (date/character) date in YYYY-MM-DD format

- us:

  (logical) US data only? default: `FALSE`

- drop_undefined:

  (logical) drop undefined precipitation values (values in the `precip`
  column in the output data.frame). default: `FALSE`

- ...:

  curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

a data.frame, with columns:

- lon - longitude (0 to 360)

- lat - latitude (-90 to 90)

- precip - precipitation (in mm) (see Details for more information)

## Details

Rainfall data for the world (1979-present, resolution 50 km), and the US
(1948-present, resolution 25 km).

## Note

See
[cpc_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## Data processing in this function

Internally we multiply all precipitation measurements by 0.1 as per the
CPC documentation.

Values of -99.0 are classified as "undefined". These values can be
removed by setting `drop_undefined = TRUE` in the `cpc_prcp` function
call. These undefined values are not dropped by default - so do remember
to set `drop_undefined = TRUE` to drop them; or you can easily do it
yourself by e.g., `subset(x, precip >= 0)`

## References

https://www.cpc.ncep.noaa.gov/
https://ftp.cpc.ncep.noaa.gov/precip/CPC_UNI_PRCP
https://ftp.cpc.ncep.noaa.gov/precip/CPC_UNI_PRCP/GAUGE_CONUS/DOCU/PRCP_CU_GAUGE_V1.0CONUS_0.25deg.README
https://ftp.cpc.ncep.noaa.gov/precip/CPC_UNI_PRCP/GAUGE_GLB/DOCU/PRCP_CU_GAUGE_V1.0GLB_0.50deg_README.txt
https://psl.noaa.gov/data/gridded/data.unified.daily.conus.html

## Examples

``` r
if (FALSE) { # \dontrun{
x = cpc_prcp(date = "2017-01-15")
cpc_prcp(date = "2015-06-05")
cpc_prcp(date = "2017-01-15")
cpc_prcp(date = "2005-07-09")
cpc_prcp(date = "1979-07-19")

# United States data only
cpc_prcp(date = "2005-07-09", us = TRUE)
cpc_prcp(date = "2009-08-03", us = TRUE)
cpc_prcp(date = "1998-04-23", us = TRUE)

# drop undefined values (those given as -99.0)
cpc_prcp(date = "1998-04-23", drop_undefined = TRUE)
} # }
```
