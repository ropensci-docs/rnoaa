# Get NOAA tornado data.

This function gets spatial paths of tornadoes from NOAA's National
Weather Service Storm Prediction Center Severe Weather GIS web page.

## Usage

``` r
tornadoes(...)
```

## Arguments

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (optional)

## Value

A Spatial object is returned of class SpatialLinesDataFrame.

## Note

See
[torn_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## References

https://www.spc.noaa.gov/gis/svrgis/

## Examples

``` r
if (FALSE) { # \dontrun{
shp <- tornadoes()
library('sp')
if (interactive()) {
  # may take 10 sec or so to render
  plot(shp)
}
} # }
```
