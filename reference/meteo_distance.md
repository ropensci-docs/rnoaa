# Find all monitors within a radius of a location

This function will identify all weather stations with a specified radius
of a location. If no radius is given, the function will return a
dataframe of all available monitors, sorted by distance to the location.
The `limit` argument can be used to limit the output dataframe to the
`x` closest monitors to the location.

## Usage

``` r
meteo_distance(
  station_data,
  lat,
  long,
  units = "deg",
  radius = NULL,
  limit = NULL
)
```

## Arguments

- station_data:

  The output of
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md),
  which is a current list of weather stations available through NOAA for
  the GHCND dataset. The format of this is a dataframe with one row per
  weather station. Latitude and longitude for the station locations
  should be in columns with the names "latitude" and "longitude",
  consistent with the output from
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md).
  To save time, run the `ghcnd_stations` call and save the output to an
  object, rather than rerunning the default every time (see the examples
  in
  [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)).

- lat:

  Latitude of the location. Southern latitudes should be given as
  negative values.

- long:

  Longitude of the location. Western longitudes should be given as
  negative values.

- units:

  Units of the latitude and longitude values. Possible values are:

  - `deg`: Degrees (default);

  - `rad`: Radians.

- radius:

  A numeric vector giving the radius (in kilometers) within which to
  search for monitors near a location.

- limit:

  An integer giving the maximum number of monitors to include for each
  location. The `x` closest monitors will be kept. Default is NULL (pull
  everything available, within the radius if the radius is specified).

## Value

A dataframe of weather stations near the location. This is the
single-location version of the return value for
[`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)

## Author

Alex Simmons <a2.simmons@qut.edu.au>, Brooke Anderson
<brooke.anderson@colostate.edu>

## Examples

``` r
if (FALSE) { # \dontrun{
station_data <- ghcnd_stations()
meteo_distance(station_data, -33, 151, radius = 10, limit = 10)
meteo_distance(station_data, -33, 151, radius = 10, limit = 3)

# FIXME - units param is ignored
#meteo_distance(station_data, -33, 151, units = 'rad', radius = 10, limit = 3)
} # }
```
