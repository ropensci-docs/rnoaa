# Get metadata about NOAA NCDC stations.

From the NOAA NCDC API docs: Stations are where the data comes from (for
most datasets) and can be considered the smallest granual of location
data. If you know what station you want, you can quickly get all manner
of data from it

## Usage

``` r
ncdc_stations(
  stationid = NULL,
  datasetid = NULL,
  datatypeid = NULL,
  locationid = NULL,
  startdate = NULL,
  enddate = NULL,
  sortfield = NULL,
  sortorder = NULL,
  limit = 25,
  offset = NULL,
  datacategoryid = NULL,
  extent = NULL,
  token = NULL,
  dataset = NULL,
  station = NULL,
  location = NULL,
  locationtype = NULL,
  page = NULL,
  ...
)
```

## Arguments

- stationid:

  A single valid station id, with datasetid namespace, e.g.,
  GHCND:USW00014895

- datasetid:

  (optional) Accepts a valid dataset id or a vector or list of them.
  Data returned will be from the dataset specified.

- datatypeid:

  Accepts a valid data type id or a vector or list of data type ids.
  (optional)

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

- datacategoryid:

  (character, optional) Accepts a valid data category id or a vector or
  list of data category ids.

- extent:

  (numeric, optional) The geographical extent for which you want to
  search. Give four values that defines a bounding box, lat and long for
  the southwest corner, then lat and long for the northeast corner. For
  example: `c(minlat, minlong, maxlat, maxlong)`.

- token:

  This must be a valid token token supplied to you by NCDC's Climate
  Data Online access token generator. (required) See **Authentication**
  section below for more details.

- dataset:

  THIS IS A DEPRECATED ARGUMENT. See datasetid.

- station:

  THIS IS A DEPRECATED ARGUMENT. See stationid.

- location:

  THIS IS A DEPRECATED ARGUMENT. See locationid.

- locationtype:

  THIS IS A DEPRECATED ARGUMENT. There is no equivalent argument in v2
  of the NOAA API.

- page:

  THIS IS A DEPRECATED ARGUMENT. There is no equivalent argument in v2
  of the NOAA API.

- ...:

  Curl options passed on to
  [`HttpClient`](https://docs.ropensci.org/crul/reference/HttpClient.html)
  (optional)

## Value

A list of metadata.

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
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get metadata on all stations
ncdc_stations()
ncdc_stations(limit=5)

# Get metadata on a single station
ncdc_stations(stationid='COOP:010008')

# For many stations use lapply or similar
lapply(c("COOP:010008", "COOP:010063", "COOP:010116"), function(z) {
  ncdc_stations(
   startdate = "2013-01-01",
   enddate = "2014-11-01",
   stationid = z)
}$data)

# Displays all stations within GHCN-Daily (100 Stations per page limit)
ncdc_stations(datasetid = 'GHCND')
ncdc_stations(datasetid = 'ANNUAL')
ncdc_stations(datasetid = 'GSOY')

# Station
ncdc_stations(datasetid='NORMAL_DLY', stationid='GHCND:USW00014895')

# datatypeid
ncdc_stations(datatypeid="ANN-HTDD-NORMAL")
ncdc_stations(datatypeid=c("ANN-HTDD-NORMAL", "ACSC"))

# locationid
ncdc_stations(locationid="CITY:AG000001")
ncdc_stations(locationid="FIPS:30091")
ncdc_stations(locationid=c("FIPS:30103", "FIPS:30091"))

# datacategoryid
ncdc_stations(datacategoryid="ANNPRCP")
ncdc_stations(datacategoryid="AUAGR")
ncdc_stations(datacategoryid=c("ANNPRCP", "AUAGR"))

# Displays all stations within GHCN-Daily (Displaying page 10 of the results)
ncdc_stations(datasetid='GHCND')

# Specify datasetid and locationid
ncdc_stations(datasetid='GHCND', locationid='FIPS:12017')

# Specify datasetid, locationid, and station
ncdc_stations(datasetid='GHCND', locationid='FIPS:12017', stationid='GHCND:USC00084289')

# Specify datasetid, locationidtype, locationid, and station
ncdc_stations(datasetid='GHCND', locationid='FIPS:12017', stationid='GHCND:USC00084289')

# Displays list of stations within the specified county
ncdc_stations(datasetid='GHCND', locationid='FIPS:12017')

# Displays list of Hourly Precipitation locationids between 01/01/1990 and 12/31/1990
ncdc_stations(datasetid='PRECIP_HLY', startdate='19900101', enddate='19901231')

# Search for stations by spatial extent
## Search using a bounding box, w/ lat/long of the SW corner, then of NE corner
ncdc_stations(extent=c(47.5204,-122.2047,47.6139,-122.1065))
} # }
```
