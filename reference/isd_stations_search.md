# Search for NOAA ISD/ISH station data from NOAA FTP server.

Search for NOAA ISD/ISH station data from NOAA FTP server.

## Usage

``` r
isd_stations_search(lat = NULL, lon = NULL, radius = NULL, bbox = NULL)
```

## Arguments

- lat:

  (numeric) Latitude, in decimal degree

- lon:

  (numeric) Latitude, in decimal degree

- radius:

  (numeric) Radius (in km) to search from the lat,lon coordinates

- bbox:

  (numeric) Bounding box, of the form: min-longitude, min-latitude,
  max-longitude, max-latitude

## Value

a data.frame with the columns:

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

- distance - distance (km) (only present if using lat/lon/radius
  parameter combination)

## Details

We internally call
[`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md)
to get the data.frame of ISD stations, which is quite fast as long as
it's not the first time called since we cache the table. Before
searching, we clean up the data.frame, removing stations with no
lat/long coordinates, those with impossible lat/long coordinates, and
those at 0,0.

When lat/lon/radius input we use
[`meteo_distance()`](https://docs.ropensci.org/rnoaa/reference/meteo_distance.md)
to search for stations, while when bbox is input, we simply use
[`dplyr::filter()`](https://dplyr.tidyverse.org/reference/filter.html)

## References

https://ftp.ncdc.noaa.gov/pub/data/noaa/

## See also

Other isd:
[`isd_read()`](https://docs.ropensci.org/rnoaa/reference/isd_read.md),
[`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md),
[`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## lat, long, radius
isd_stations_search(lat = 38.4, lon = -123, radius = 250)

x <- isd_stations_search(lat = 60, lon = 18, radius = 200)

if (requireNamespace("leaflet")) {
  library("leaflet")
  leaflet() %>%
    addTiles() %>%
    addCircles(lng = x$lon,
               lat = x$lat,
               popup = x$station_name) %>%
    clearBounds()
}

## bounding box
bbox <- c(-125.0, 38.4, -121.8, 40.9)
isd_stations_search(bbox = bbox)
} # }
```
