# Calculate the distance between two locations

This function uses the haversine formula to calculate the great circle
distance between two locations, identified by their latitudes and
longitudes.

## Usage

``` r
meteo_spherical_distance(lat1, long1, lat2, long2, units = "deg")
```

## Arguments

- lat1:

  Latitude of the first location.

- long1:

  Longitude of the first location.

- lat2:

  Latitude of the second location.

- long2:

  Longitude of the second location.

- units:

  Units of the latitude and longitude values. Possible values are:

  - `deg`: Degrees (default);

  - `rad`: Radians.

## Value

A numeric value giving the distance (in kilometers) between the pair of
locations.

## Note

This function assumes an earth radius of 6,371 km.

## Author

Alex Simmons <a2.simmons@qut.edu.au>, Brooke Anderson
<brooke.anderson@colostate.edu>

## Examples

``` r

meteo_spherical_distance(lat1 = -27.4667, long1 = 153.0217,
                         lat2 = -27.4710, long2 = 153.0234)
#> [1] 0.5067013
```
