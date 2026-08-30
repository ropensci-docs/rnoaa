# Arc2 - Africa Rainfall Climatology version 2

Arc2 - Africa Rainfall Climatology version 2

## Usage

``` r
arc2(date, box = NULL, ...)
```

## Arguments

- date:

  (character/date) one or more dates of the form YYYY-MM-DD

- box:

  (numeric) vector of length 4, of the form `xmin, ymin, xmax, ymax`.
  optional. If not given, no spatial filtering is done. If given, we use
  [`dplyr::filter()`](https://dplyr.tidyverse.org/reference/filter.html)
  on a combined set of all dates, then split the output into tibbles by
  date

- ...:

  curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

a list of tibbles with columns:

- date: date (YYYY-MM-DD)

- lon: longitude

- lat: latitude

- precip: precipitation (mm)

## Note

See
[arc2_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## box parameter

The `box` parameter filters the arc2 data to a bounding box you supply.
The function that does the cropping to the bounding box is
[`dplyr::filter`](https://dplyr.tidyverse.org/reference/filter.html).
You can do any filtering you want on your own if you do not supply `box`
and then use whatever tools you want to filter the data by lat/lon,
date, precip values.

## References

docs:
https://ftp.cpc.ncep.noaa.gov/fews/fewsdata/africa/arc2/ARC2_readme.txt

## Examples

``` r
if (FALSE) { # \dontrun{
x = arc2(date = "1983-01-01")
arc2(date = "2017-02-14")

# many dates
arc2(date = c("2019-05-27", "2019-05-28"))
arc2(seq(as.Date("2019-04-21"), by = "day", length.out = 5))
## combine outputs 
x <- arc2(seq(as.Date("2019-05-20"), as.Date("2019-05-25"), "days"))
dplyr::bind_rows(x)

# bounding box filter
box <- c(xmin = 9, ymin = 4, xmax = 10, ymax = 5)
arc2(date = "2017-02-14", box = box)
arc2(date = c("2019-05-27", "2019-05-28"), box = box)
arc2(seq(as.Date("2019-05-20"), as.Date("2019-05-25"), "days"), box = box)
} # }
```
