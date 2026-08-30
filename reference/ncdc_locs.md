# Get metadata about NOAA NCDC locations.

From the NOAA NCDC API docs: Locations can be a specific
latitude/longitude point such as a station, or a label representing a
bounding area such as a city.

## Usage

``` r
ncdc_locs(
  datasetid = NULL,
  locationid = NULL,
  locationcategoryid = NULL,
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

  A valid dataset id or a vector or list of dataset id's. Data returned
  will be from the dataset specified, see datasets() (required)

- locationid:

  A valid location id or a vector or list of location ids.

- locationcategoryid:

  A valid location id or a vector or list of location category ids

- startdate:

  A valid ISO formatted date (yyyy-mm-dd). Data returned will have data
  after the specified date. Paramater can be use independently of
  enddate (optional)

- enddate:

  Accepts valid ISO formatted date (yyyy-mm-dd). Data returned will have
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

A list containing metadata and the data, or a single data.frame.

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
[`ncdc_datacats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datacats.md),
[`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md),
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md),
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# All locations, first 25 results
ncdc_locs()

# Fetch more information about location id FIPS:37
ncdc_locs(locationid='FIPS:37')

# Fetch available locations for the GHCND (Daily Summaries) dataset
ncdc_locs(datasetid='GHCND')
ncdc_locs(datasetid=c('GHCND', 'ANNUAL'))
ncdc_locs(datasetid=c('GSOY', 'ANNUAL'))
ncdc_locs(datasetid=c('GHCND', 'GSOM'))

# Fetch all U.S. States
ncdc_locs(locationcategoryid='ST', limit=52)

# Many locationcategoryid's
## this apparently works, but returns nothing often with multiple
## locationcategoryid's
ncdc_locs(locationcategoryid=c('ST', 'ZIP'))

# Fetch list of city locations in descending order
ncdc_locs(locationcategoryid='CITY', sortfield='name', sortorder='desc')
} # }
```
