# Search for and get NOAA NCDC data

Search for and get NOAA NCDC data

## Usage

``` r
ncdc(
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
  includemetadata = TRUE,
  add_units = FALSE,
  ...
)
```

## Arguments

- datasetid:

  (required) Accepts a single valid dataset id. Data returned will be
  from the dataset specified, see
  [`ncdc_datasets`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md)

- datatypeid:

  Accepts a valid data type id or a vector or list of data type ids.
  (optional)

- stationid:

  Accepts a valid station id or a vector or list of station ids

- locationid:

  Accepts a valid location id or a vector or list of location ids
  (optional)

- startdate:

  (character/date) Accepts valid ISO formated date (yyyy-mm-dd) or date
  time (YYYY-MM-DDThh:mm:ss). Data returned will have data after the
  specified date. The date range must be less than 1 year. required.

- enddate:

  (character/date) Accepts valid ISO formated date (yyyy-mm-dd) or date
  time (YYYY-MM-DDThh:mm:ss). Data returned will have data before the
  specified date. The date range must be less than 1 year. required.

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

- includemetadata:

  Used to improve response time by preventing the calculation of result
  metadata. Default: TRUE. This does not affect the return object, in
  that the named part of the output list called "meta" is still
  returned, but is NULL. In practice, I haven't seen response time's
  improve, but perhaps they will for you.

- add_units:

  (logical) whether to add units information or not. default: `FALSE`.
  If `TRUE`, after getting data from NOAA we add a new column `units`.
  See "Adding units" in Details for more

- ...:

  Curl options passed on to
  [`HttpClient`](https://docs.ropensci.org/crul/reference/HttpClient.html)
  (optional)

## Value

An S3 list of length two, a slot of metadata (meta), and a slot for data
(data). The meta slot is a list of metadata elements, and the data slot
is a data.frame, possibly of length zero if no data is found. Note that
values in the data slot don't indicate their units by default, so you
will want to either use the `add_units` parameter (experimental, see
Adding units) or consult the documentation for each dataset to ensure
you're using the correct units.

## Details

Note that NOAA NCDC API calls can take a long time depending on the
call. The NOAA API doesn't perform well with very long timespans, and
will time out and make you angry - beware.

Keep in mind that three parameters, datasetid, startdate, and enddate
are required.

Note that the default limit (no. records returned) is 25. Look at the
metadata in `$meta` to see how many records were found. If more were
found than 25, you could set the parameter `limit` to something higher
than 25.

## Authentication

Get an API key (aka, token) at https://www.ncdc.noaa.gov/cdo-web/token
You can pass your token in as an argument or store it one of two places:

- your .Rprofile file with the entry
  `options(noaakey = "your-noaa-token")`

- your .Renviron file with the entry `NOAA_KEY=your-noaa-token`

See [`Startup`](https://rdrr.io/r/base/Startup.html) for information on
how to create/find your .Rrofile and .Renviron files

## Flags

The attributes, or "flags", for each row of the output for data may have
a flag with it. Each `datasetid` has it's own set of flags. The
following are flag columns, and what they stand for. `fl_` is the
beginning of each flag column name, then one or more characters to
describe the flag, keeping it short to maintain a compact data frame.
Some of these fields are the same across datasetids. See the vignette
`vignette("rnoaa_attributes", "rnoaa")` for description of possible
values for each flag.

- fl_c completeness

- fl_d day

- fl_m measurement

- fl_q quality

- fl_s source

- fl_t time

- fl_cmiss consecutive missing

- fl_miss missing

- fl_u units

## GSOM/GSOY Flags

Note that flags are different for GSOM and GSOY datasets. They have
their own set of flags per data class. See
`system.file("extdata/gsom.json", package = "rnoaa")` for GSOM and
`system.file("extdata/gsom.json", package = "rnoaa")` for GSOY. Those
are JSON files. The
[`system.file()`](https://rdrr.io/r/base/system.file.html) call gives
you then path, then read in with
[`jsonlite::fromJSON()`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html)
which will give a data.frame of the metadata. For more detailed info but
plain text, open
`system.file("extdata/gsom_readme.txt", package = "rnoaa")` and
`system.file("extdata/gsoy_readme.txt", package = "rnoaa")` in a text
editor.

## Adding units

The `add_units` parameter is experimental - USE WITH CAUTION! If
`add_units=TRUE` we pull data from curated lists of data used by
matching by datasetid and data type.

We've attempted to gather as much information as possible on the many,
many data types across the many different NOAA data sets. However, we
may have got some things wrong, so make sure to double check data you
get if you do add units.

Get in touch if you find some units that are wrong or missing, and if
you are able to help correct information.

## See also

Other ncdc:
[`ncdc_combine()`](https://docs.ropensci.org/rnoaa/reference/ncdc_combine.md),
[`ncdc_datacats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datacats.md),
[`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md),
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# GHCN-Daily (or GHCND) data, for a specific station
ncdc(datasetid='GHCND', stationid='GHCND:USW00014895',
   startdate = '2013-10-01', enddate = '2013-12-01')
### also accepts dates as class Date
ncdc(datasetid='GHCND', stationid='GHCND:USW00014895',
   startdate = as.Date('2013-10-01'), enddate = as.Date('2013-12-01'))

# GHCND data, for a location by FIPS code
ncdc(datasetid='GHCND', locationid = 'FIPS:02', startdate = '2010-05-01',
   enddate = '2010-05-10')

# GHCND data from October 1 2013 to December 1 2013
ncdc(datasetid='GHCND', startdate = '2013-10-01', enddate = '2013-10-05')

# GHCN-Monthly (or GSOM) data from October 1 2013 to December 1 2013
ncdc(datasetid='GSOM', startdate = '2013-10-01', enddate = '2013-12-01')
ncdc(datasetid='GSOM', startdate = '2013-10-01', enddate = '2013-12-01',
   stationid = "GHCND:AE000041196")

# Normals Daily (or NORMAL_DLY) GHCND:USW00014895 dly-tmax-normal data
ncdc(datasetid='NORMAL_DLY', stationid='GHCND:USW00014895',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Dataset, and location in Australia
ncdc(datasetid='GHCND', locationid='FIPS:AS', startdate = '2010-05-01',
    enddate = '2010-05-31')

# Dataset, location and datatype for PRECIP_HLY data
ncdc(datasetid='PRECIP_HLY', locationid='ZIP:28801', datatypeid='HPCP',
   startdate = '2010-05-01', enddate = '2010-05-10')

# multiple datatypeid's
ncdc(datasetid='PRECIP_HLY', datatypeid = 'HPCP',
   startdate = '2010-05-01', enddate = '2010-05-10')

# multiple locationid's
ncdc(datasetid='PRECIP_HLY', locationid=c("FIPS:30103", "FIPS:30091"),
   startdate = '2010-05-01', enddate = '2010-05-10')

# Dataset, location, station and datatype
ncdc(datasetid='PRECIP_HLY', locationid='ZIP:28801',
   stationid='COOP:310301', datatypeid='HPCP',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Dataset, location, and datatype for GHCND
ncdc(datasetid='GHCND', locationid='FIPS:BR', datatypeid='PRCP',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Normals Daily GHCND dly-tmax-normal data
ncdc(datasetid='NORMAL_DLY', datatypeid='dly-tmax-normal',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Normals Daily GHCND:USW00014895 dly-tmax-normal
ncdc(datasetid='NORMAL_DLY', stationid='GHCND:USW00014895',
   datatypeid='dly-tmax-normal',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Hourly Precipitation data for ZIP code 28801
ncdc(datasetid='PRECIP_HLY', locationid='ZIP:28801', datatypeid='HPCP',
   startdate = '2010-05-01', enddate = '2010-05-10')

# 15 min Precipitation data for ZIP code 28801
ncdc(datasetid='PRECIP_15', datatypeid='QPCP',
   startdate = '2010-05-01', enddate = '2010-05-02')

# Search the NORMAL_HLY dataset
ncdc(datasetid='NORMAL_HLY', stationid = 'GHCND:USW00003812',
   startdate = '2010-05-01', enddate = '2010-05-10')

# Search the GSOY dataset
ncdc(datasetid='ANNUAL', locationid='ZIP:28801', startdate = '2010-05-01',
   enddate = '2010-05-10')

# Search the NORMAL_ANN dataset
ncdc(datasetid='NORMAL_ANN', datatypeid='ANN-DUTR-NORMAL',
   startdate = '2010-01-01', enddate = '2010-01-01')

# Include metadata or not
ncdc(datasetid='GHCND', stationid='GHCND:USW00014895',
   startdate = '2013-10-01', enddate = '2013-12-01')
ncdc(datasetid='GHCND', stationid='GHCND:USW00014895',
   startdate = '2013-10-01', enddate = '2013-12-01', includemetadata=FALSE)

# Many stationid's
stat <- ncdc_stations(startdate = "2000-01-01", enddate = "2016-01-01")
## find out what datasets might be available for these stations
ncdc_datasets(stationid = stat$data$id[10])
## get some data
ncdc(datasetid = "GSOY", stationid = stat$data$id[1:10],
   startdate = "2010-01-01", enddate = "2011-01-01")
} # }

if (FALSE) { # \dontrun{
# NEXRAD2 data
## doesn't work yet
ncdc(datasetid='NEXRAD2', startdate = '2013-10-01', enddate = '2013-12-01')
} # }
```
