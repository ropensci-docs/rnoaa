# Get all GHCND data from a single weather site

This function uses ftp to access the Global Historical Climatology
Network daily weather data from NOAA's FTP server for a single weather
site. It requires the site identification number for that site and will
pull the entire weather dataset for the site.

## Usage

``` r
ghcnd(stationid, refresh = FALSE, ...)

ghcnd_read(path, ...)
```

## Arguments

- stationid:

  (character) A character vector giving the identification of the
  weather stations for which the user would like to pull data. To get a
  full and current list of stations, the user can use the
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md)
  function. To identify stations within a certain radius of a location,
  the user can use the
  [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)
  function.

- refresh:

  (logical) If `TRUE` force re-download of data. Default: `FALSE`

- ...:

  In the case of `ghcnd()` additional curl options to pass through to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).
  In the case of `ghcnd_read` further options passed on to `read.csv`

- path:

  (character) a path to a file with a `.dly` extension - already
  downloaded on your computer

## Value

A tibble (data.frame) which contains data pulled from NOAA's FTP server
for the queried weather site. A README file with more information about
the format of this file is available from NOAA
(https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt). This file
is formatted so each line of the file gives the daily weather
observations for a single weather variable for all days of one month of
one year. In addition to measurements, columns are included for certain
flags, which add information on observation sources and quality and are
further explained in NOAA's README file for the data.

## Details

This function saves the full set of weather data for the queried site
locally in the directory specified by the `path` argument.

You can access the path for the cached file via `attr(x, "source")`

You can access the last modified time for the cached file via
`attr(x, "file_modified")`

Messages are printed to the console about file path and file last
modified time which you can suppress with
[`suppressMessages()`](https://rdrr.io/r/base/message.html)

For those station ids that are not found, we will delete the file
locally so that a bad station id file is not cached. The returned data
for a bad station id will be an empty data.frame and the attributes are
empty strings.

## Note

See
[ghcnd_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## Base URL

The base url for data requests can be changed. The allowed urls are:
https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/all (default),
https://ncei.noaa.gov/pub/data/ghcn/daily/all

You can set the base url using the `RNOAA_GHCND_BASE_URL` environment
variable; see example below.

The reason for this is that sometimes one base url source is temporarily
down, but another base url may work. It doesn't make sense to allow an
arbitrary base URL; open an issue if there is another valid base URL for
GHNCD data that we should add to the allowed set of base urls.

## See also

To generate a weather dataset for a single weather site that has been
cleaned to a tidier weather format, the user should use the
[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
function, which calls `ghcnd()` and then processes the output, or
[`meteo_tidy_ghcnd()`](https://docs.ropensci.org/rnoaa/reference/meteo_tidy_ghcnd.md),
which wraps the
[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
function to output a tidy dataframe. To pull GHCND data from multiple
monitors, see
[`meteo_pull_monitors()`](https://docs.ropensci.org/rnoaa/reference/meteo_pull_monitors.md)

## Author

Scott Chamberlain <myrmecocystus@gmail.com>, Adam Erickson
<adam.erickson@ubc.ca>

## Examples

``` r
if (FALSE) { # \dontrun{
# Get data
ghcnd(stationid = "AGE00147704")

stations <- ghcnd_stations()
ghcnd(stations$id[40])

library("dplyr")
ghcnd(stations$id[80300]) %>% select(id, element) %>% slice(1:3)

# manipulate data
## using built in fxns
dat <- ghcnd(stationid = "AGE00147704")
(alldat <- ghcnd_splitvars(dat))

## using dplyr
library("dplyr")
dat <- ghcnd(stationid = "AGE00147704")
filter(dat, element == "PRCP", year == 1909)

# refresh the cached file
ghcnd(stationid = "AGE00147704", refresh = TRUE)

# Read in a .dly file you've already downloaded
path <- system.file("examples/AGE00147704.dly", package = "rnoaa")
ghcnd_read(path)

# change the base url for data requests
Sys.setenv(RNOAA_GHCND_BASE_URL =
  "https://ncei.noaa.gov/pub/data/ghcn/daily/all")
ghcnd(stations$id[45], verbose = TRUE)
## must be in the allowed set of urls
# Sys.setenv(RNOAA_GHCND_BASE_URL = "https://google.com")
# ghcnd(stations$id[58], verbose = TRUE)
} # }
```
