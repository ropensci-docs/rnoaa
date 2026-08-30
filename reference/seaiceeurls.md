# Make all urls for sea ice data

Make all urls for sea ice data

## Usage

``` r
seaiceeurls(yr = NULL, mo = NULL, pole = NULL, format = "shp")
```

## Arguments

- yr:

  (numeric) a year

- mo:

  (character) a month, as character abbrevation of a month

- pole:

  (character) one of S (south) or N (north)

## Value

A vector of urls (character)

## Examples

``` r
if (FALSE) { # \dontrun{
# Get all urls
seaiceeurls()

# for some range of years
seaiceeurls(yr = 1980:1983)
seaiceeurls(yr = 1980, mo = c("Jan", "Feb", "Mar"))
seaiceeurls(yr = 1980:1983, mo = c("Jan", "Apr", "Oct"))

# Get urls for Feb of all years, both S and N poles
seaiceeurls(mo='Feb')

# Get urls for Feb of all years, just S pole
seaiceeurls(mo='Feb', pole='S')

# Get urls for Feb of 1980, just S pole
seaiceeurls(yr=1980, mo='Feb', pole='S')

# GeoTIFF
seaiceeurls(yr=1980, mo='Feb', pole='S', format = "geotiff")
} # }
```
