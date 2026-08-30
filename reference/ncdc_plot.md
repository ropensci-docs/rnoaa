# Plot NOAA climate data.

Plot NOAA climate data.

## Usage

``` r
ncdc_plot(..., breaks = NULL, dateformat = "%d/%m/%y")
```

## Arguments

- ...:

  Input noaa object or objects.

- breaks:

  Regularly spaced date breaks for x-axis. See examples for usage. See
  date_breaks. Default: `NULL` (uses ggplot2 default break sformatting)

- dateformat:

  Date format using standard POSIX specification for labels on x-axis.
  See `date_format()`

## Value

ggplot2 plot

## Details

This function accepts directly output from the
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) function,
not other functions.

This is a simple wrapper function around some ggplot2 code. There is
indeed a lot you can modify in your plots, so this function just does
some basic stuff. Look at the internals for what the function does.

## See also

Other ncdc:
[`ncdc_combine()`](https://docs.ropensci.org/rnoaa/reference/ncdc_combine.md),
[`ncdc_datacats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datacats.md),
[`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md),
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md),
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)

## Examples

``` r
if (FALSE) { # \dontrun{
# Search for data first, then plot
out <- ncdc(datasetid='GHCND', stationid='GHCND:USW00014895', datatypeid='PRCP',
   startdate = '2010-05-01', enddate = '2010-10-31', limit=500)
ncdc_plot(out)
ncdc_plot(out, breaks="14 days")
ncdc_plot(out, breaks="1 month", dateformat="%d/%m")
ncdc_plot(out, breaks="1 month", dateformat="%d/%m")

# Combine many calls to ncdc function
out1 <- ncdc(datasetid='GHCND', stationid='GHCND:USW00014895', datatypeid='PRCP',
   startdate = '2010-03-01', enddate = '2010-05-31', limit=500)
out2 <- ncdc(datasetid='GHCND', stationid='GHCND:USW00014895', datatypeid='PRCP',
   startdate = '2010-09-01', enddate = '2010-10-31', limit=500)
df <- ncdc_combine(out1, out2)
ncdc_plot(df)
## or pass in each element separately
ncdc_plot(out1, out2, breaks="45 days")
} # }
```
