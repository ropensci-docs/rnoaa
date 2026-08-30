# Get NOAA buoy data from the National Buoy Data Center

Get NOAA buoy data from the National Buoy Data Center

## Usage

``` r
buoy(dataset, buoyid, year = NULL, datatype = NULL, ...)

buoys(dataset)

buoy_stations(refresh = FALSE, ...)
```

## Arguments

- dataset:

  (character) Dataset name to query. See below for Details. Required

- buoyid:

  Buoy ID, can be numeric/integer/character. Required

- year:

  (integer) Year of data collection. Optional. Note there is a special
  value `9999` that, if found, contains the most up to date data.

- datatype:

  (character) Data type, one of 'c', 'cc', 'p', 'o'. Optional

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  Optional. A number of different HTTP requests are made internally, but
  we only pass this on to the request to get the netcdf file in the
  internal function `get_ncdf_file()`

- refresh:

  (logical) Whether to use cached data (`FALSE`) or get new data
  (`FALSE`). Default: `FALSE`

## Value

If netcdf data has lat/lon variables, then we'll parse into a tidy
data.frame. If not, we'll give back the ncdf4 object for the user to
parse (in which case the data.frame will be empty).

## Details

Functions:

- buoy_stations - Get buoy stations. A cached version of the dataset is
  available in the package. Beware, takes a long time to run if you do
  `refresh = TRUE`

- buoys - Get available buoys given a dataset name

- buoy - Get data given some combination of dataset name, buoy ID, year,
  and datatype

Options for the dataset parameter. One of:

- adcp - Acoustic Doppler Current Profiler data

- adcp2 - MMS Acoustic Doppler Current Profiler data

- cwind - Continuous Winds data

- dart - Deep-ocean Assessment and Reporting of Tsunamis data

- mmbcur - Marsh-McBirney Current Measurements data

- ocean - Oceanographic data

- pwind - Peak Winds data

- stdmet - Standard Meteorological data

- swden - Spectral Wave Density data with Spectral Wave Direction data

- wlevel - Water Level data

## References

http://www.ndbc.noaa.gov/, http://dods.ndbc.noaa.gov/

## Examples

``` r
if (FALSE) { # \dontrun{
if (crul::ok("https://dods.ndbc.noaa.gov/thredds", timeout_ms = 1000)) {

# Get buoy station information
x <- buoy_stations()
# refresh stations as needed, takes a while to run
# you shouldn't need to update very often
# x <- buoy_stations(refresh = TRUE)
if (interactive() && requireNamespace("leaflet")){
library("leaflet")
z <- leaflet(data = na.omit(x))
z <- leaflet::addTiles(z)
leaflet::addCircles(z, ~lon, ~lat, opacity = 0.5)
}

# year=9999 to get most current data - not always available
buoy(dataset = "swden", buoyid = 46012, year = 9999)

# Get available buoys
buoys(dataset = 'cwind')

# Get data for a buoy
## if no year or datatype specified, we get the first file
buoy(dataset = 'cwind', buoyid = 46085)

# Including specific year
buoy(dataset = 'cwind', buoyid = 41001, year = 1999)

# Including specific year and datatype
buoy(dataset = 'cwind', buoyid = 45005, year = 2008, datatype = "c")
buoy(dataset = 'cwind', buoyid = 41001, year = 1997, datatype = "c")

# Other datasets
buoy(dataset = 'ocean', buoyid = 41029)

# curl debugging
buoy(dataset = 'cwind', buoyid = 46085, verbose = TRUE)

# some buoy ids are character, case doesn't matter, we'll account for it
buoy(dataset = "stdmet", buoyid = "VCAF1")
buoy(dataset = "stdmet", buoyid = "wplf1")
buoy(dataset = "dart", buoyid = "dartu")

}
} # }
```
