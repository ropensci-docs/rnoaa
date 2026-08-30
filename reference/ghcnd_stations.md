# Get information on the GHCND weather stations

This function returns an object with a dataframe with meta-information
about all available GHCND weather stations.

## Usage

``` r
ghcnd_stations(refresh = FALSE, ...)
```

## Arguments

- refresh:

  (logical) If `TRUE` force re-download of data. Default: `FALSE`

- ...:

  In the case of
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)
  additional curl options to pass through to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).
  In the case of `ghcnd_read` further options passed on to `read.csv`

## Value

This function returns a tibble (dataframe) with a weather station on
each row with the following columns:

- `id`: The weather station's ID number. The first two letters denote
  the country (using FIPS country codes).

- `latitude`: The station's latitude, in decimal degrees. Southern
  latitudes will be negative.

- `longitude`: The station's longitude, in decimal degrees. Western
  longitudes will be negative.

- `elevation`: The station's elevation, in meters.

- `name`: The station's name.

- `gsn_flag`: "GSN" if the monitor belongs to the GCOS Surface Network
  (GSN). Otherwise either blank or missing.

- `wmo_id`: If the station has a WMO number, this column gives that
  number. Otherwise either blank or missing.

- `element`: A weather variable recorded at some point during that
  station's history. See the link below in "References" for definitions
  of the abbreviations used for this variable.

- `first_year`: The first year of data available at that station for
  that weather element.

- `last_year`: The last year of data available at that station for that
  weather element.

If a weather station has data on more than one weather variable, it will
be represented in multiple rows of this output dataframe.

## Note

Since this function is pulling a large dataset by ftp, it may take a
while to run.

## References

For more documentation on the returned dataset, see
http://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt

## Examples

``` r
if (FALSE) { # \dontrun{
# Get stations, ghcnd-stations and ghcnd-inventory merged
(stations <- ghcnd_stations())

library(dplyr)
# filter by state
stations %>% filter(state == "IL")
stations %>% filter(state == "OR")
# those without state values
stations %>% filter(state == "")
# filter by element
stations %>% filter(element == "PRCP")
# filter by id prefix
stations %>% filter(grepl("^AF", id))
stations %>% filter(grepl("^AFM", id))
# filter by station long name
stations %>% filter(name == "CALLATHARRA")
} # }
```
