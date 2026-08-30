# Get sea ice data.

Get sea ice data.

## Usage

``` r
sea_ice(year = NULL, month = NULL, pole = NULL, format = "shp", ...)
```

## Arguments

- year:

  (numeric) a year

- month:

  (character) a month, as character abbrevation of a month

- pole:

  (character) one of S (south) or N (north)

- format:

  (character) one of shp (default), geotiff-extent (for geotiff extent
  data), or geotiff-conc (for geotiff concentration data)

- ...:

  Further arguments passed on to `rgdal::readshpfile()` if
  `format="shp"` or
  [`raster::raster()`](https://rdrr.io/pkg/raster/man/raster.html) if
  not

## Value

data.frame if `format="shp"` (a fortified sp object);
[`raster::raster()`](https://rdrr.io/pkg/raster/man/raster.html) if not

## References

See the "User Guide" pdf at https://nsidc.org/data/g02135

## See also

[`sea_ice_tabular()`](https://docs.ropensci.org/rnoaa/reference/sea_ice_tabular.md)

## Examples

``` r
if (FALSE) { # \dontrun{
if (requireNamespace("raster")) {

## one year, one moth, one pole
sea_ice(year = 1990, month = "Apr", pole = "N")
sea_ice(year = 1990, month = "Apr", pole = "N", format = "geotiff-extent")
sea_ice(year = 1990, month = "Apr", pole = "N", format = "geotiff-conc")

## one year, one month, many poles
sea_ice(year = 1990, month = "Apr")

## one year, many months, many poles
sea_ice(year = 1990, month = c("Apr", "Jun", "Oct"))

## many years, one month, one pole
sea_ice(year = 1990:1992, month = "Sep", pole = "N")

# get geotiff instead of shp data.
x <- sea_ice(year = 1990, month = "Apr", format = "geotiff-extent")
y <- sea_ice(year = 1990, month = "Apr", format = "geotiff-conc")
}

} # }
```
