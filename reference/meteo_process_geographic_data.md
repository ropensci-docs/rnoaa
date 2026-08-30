# Calculate the distances between a location and all available stations

This function takes a single location and a dataset of available weather
stations and calculates the distance between the location and each of
the stations, using the great circle method. A new column is added to
the dataset of available weather stations giving the distance between
each station and the input location. The station dataset is then sorted
from closest to furthest distance to the location and returned as the
function output.

## Usage

``` r
meteo_process_geographic_data(station_data, lat, long, units = "deg")
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

## Value

The `station_data` dataframe that is input, but with a `distance` column
added that gives the distance to the location (in kilometers), and
re-ordered by distance between each station and the location (closest
weather stations first).

## Author

Alex Simmons <a2.simmons@qut.edu.au>, Brooke Anderson
<brooke.anderson@colostate.edu>

## Examples

``` r
if (FALSE) { # \dontrun{
station_data <- ghcnd_stations()
meteo_process_geographic_data(station_data, lat=-33, long=151)
} # }
```
