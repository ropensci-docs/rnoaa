# Search NOAA datasets

From the NOAA API docs: All of our data are in datasets. To retrieve any
data from us, you must know what dataset it is in.

## Usage

``` r
ncdc_datasets(
  datasetid = NULL,
  datatypeid = NULL,
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

  (optional) Accepts a single valid dataset id. Data returned will be
  from the dataset specified.

- datatypeid:

  Accepts a valid data type id or a vector or list of data type ids.
  (optional)

- stationid:

  Accepts a valid station id or a vector or list of station ids

- locationid:

  Accepts a valid location id or a vector or list of location ids
  (optional)

- startdate:

  (optional) Accepts valid ISO formated date (yyyy-mm-dd) or date time
  (YYYY-MM-DDThh:mm:ss). Data returned will have data after the
  specified date. The date range must be less than 1 year.

- enddate:

  (optional) Accepts valid ISO formated date (yyyy-mm-dd) or date time
  (YYYY-MM-DDThh:mm:ss). Data returned will have data before the
  specified date. The date range must be less than 1 year.

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
  (optional)

## Value

A data.frame for all datasets, or a list of length two, each with a
data.frame.

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
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md),
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get a table of all datasets
ncdc_datasets()

# Get details from a particular dataset
ncdc_datasets(datasetid='ANNUAL')

# Get datasets with Temperature at the time of observation (TOBS) data type
ncdc_datasets(datatypeid='TOBS')
## two datatypeid's
ncdc_datasets(datatypeid=c('TOBS', "ACMH"))

# Get datasets with data for a series of the same parameter arg, in this case
# stationid's
ncdc_datasets(stationid='COOP:310090')
ncdc_datasets(stationid=c('COOP:310090','COOP:310184','COOP:310212'))

# Multiple datatypeid's
ncdc_datasets(datatypeid=c('ACMC','ACMH','ACSC'))
ncdc_datasets(datasetid='ANNUAL', datatypeid=c('ACMC','ACMH','ACSC'))
ncdc_datasets(datasetid='GSOY', datatypeid=c('ACMC','ACMH','ACSC'))

# Multiple locationid's
ncdc_datasets(locationid="FIPS:30091")
ncdc_datasets(locationid=c("FIPS:30103", "FIPS:30091"))
} # }
```
