# Get possible data categories for a particular datasetid, locationid, stationid, etc.

Data Categories represent groupings of data types.

## Usage

``` r
ncdc_datacats(
  datasetid = NULL,
  datacategoryid = NULL,
  stationid = NULL,
  locationid = NULL,
  startdate = NULL,
  enddate = NULL,
  sortfield = NULL,
  sortorder = NULL,
  limit = 25,
  offset = NULL,
  token = NULL,
  ...
)
```

## Arguments

- datasetid:

  Accepts a valid dataset id or a vector or list of dataset id's. Data
  returned will be from the dataset specified, see datasets() (required)

- datacategoryid:

  A valid data category id. Data types returned will be associated with
  the data category(ies) specified

- stationid:

  Accepts a valid station id or a vector or list of station ids
  (optional)

- locationid:

  Accepts a valid location id or a vector or list of location id's.
  (optional)

- startdate:

  Accepts valid ISO formated date (yyyy-mm-dd). Data returned will have
  data after the specified date. Paramater can be use independently of
  enddate (optional)

- enddate:

  Accepts valid ISO formated date (yyyy-mm-dd). Data returned will have
  data before the specified date. Paramater can be use independently of
  startdate (optional)

- sortfield:

  The field to sort results by. Supports id, name, mindate, maxdate, and
  datacoverage fields (optional)

- sortorder:

  Which order to sort by, asc or desc. Defaults to asc (optional)

- limit:

  Defaults to 25, limits the number of results in the response. Maximum
  is 1000 (optional)

- offset:

  Defaults to 0, used to offset the resultlist (optional)

- token:

  This must be a valid token token supplied to you by NCDC's Climate
  Data Online access token generator. (required) See **Authentication**
  section below for more details.

- ...:

  Curl options passed on to
  [`HttpClient`](https://docs.ropensci.org/crul/reference/HttpClient.html)

## Value

A `data.frame` for all datasets, or a list of length two, each with a
data.frame.

## Details

Note that calls with both startdate and enddate don't seem to work,
though specifying one or the other mostly works.

## Authentication

Get an API key (aka, token) at https://www.ncdc.noaa.gov/cdo-web/token
You can pass your token in as an argument or store it one of two places:

- your .Rprofile file with the entry
  `options(noaakey = "your-noaa-token")`

- your .Renviron file with the entry `NOAA_KEY=your-noaa-token`

See [`Startup`](https://rdrr.io/r/base/Startup.html) for information on
how to create/find your .Rrofile and .Renviron files

## References

https://www.ncdc.noaa.gov/cdo-web/webservices/v2

## See also

Other ncdc:
[`ncdc_combine()`](https://docs.ropensci.org/rnoaa/reference/ncdc_combine.md),
[`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md),
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md),
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Limit to 10 results
ncdc_datacats(limit=10)

## by datasetid
ncdc_datacats(datasetid="ANNUAL")
ncdc_datacats(datasetid=c("ANNUAL", "PRECIP_HLY"))

## Single data category
ncdc_datacats(datacategoryid="ANNAGR")

## Fetch data categories for a given set of locations
ncdc_datacats(locationid='CITY:US390029')
ncdc_datacats(locationid=c('CITY:US390029', 'FIPS:37'))

## Data categories for a given date
ncdc_datacats(startdate = '2013-10-01')

# Get data categories with data for a series of the same parameter arg, in this case
# stationid's
ncdc_datacats(stationid='COOP:310090')
ncdc_datacats(stationid=c('COOP:310090','COOP:310184','COOP:310212'))

## Curl debugging
ncdc_datacats(limit=10, verbose = TRUE)
} # }
```
