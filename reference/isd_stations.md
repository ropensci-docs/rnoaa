# Get NOAA ISD/ISH station data from NOAA FTP server.

Get NOAA ISD/ISH station data from NOAA FTP server.

## Usage

``` r
isd_stations(refresh = FALSE)
```

## Arguments

- refresh:

  (logical) Download station data from NOAA ftp server again. Default:
  `FALSE`

## Value

a tibble (data.frame) with the columns:

- usaf - USAF number, character

- wban - WBAN number, character

- station_name - station name, character

- ctry - Country, if given, character

- state - State, if given, character

- icao - ICAO number, if given, character

- lat - Latitude, if given, numeric

- lon - Longitude, if given, numeric

- elev_m - Elevation, if given, numeric

- begin - Begin date of data coverage, of form YYYYMMDD, numeric

- end - End date of data coverage, of form YYYYMMDD, numeric

## Details

The data table is cached, but you can force download of data from NOAA
by setting `refresh=TRUE`

## Note

See
[isd_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## References

https://ftp.ncdc.noaa.gov/pub/data/noaa/

## See also

Other isd:
[`isd_read()`](https://docs.ropensci.org/rnoaa/reference/isd_read.md),
[`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md),
[`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get station table
(stations <- isd_stations())

## plot stations
### remove incomplete cases, those at 0,0
df <- stations[complete.cases(stations$lat, stations$lon), ]
df <- df[df$lat != 0, ]
### make plot
library("leaflet")
leaflet(data = df) %>%
  addTiles() %>%
  addCircles()
} # }
```
