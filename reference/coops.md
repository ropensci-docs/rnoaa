# Get NOAA co-ops data

Get NOAA co-ops data

## Usage

``` r
coops_search(
  begin_date = NULL,
  end_date = NULL,
  station_name = NULL,
  product,
  datum = NULL,
  units = "metric",
  time_zone = "gmt",
  application = "rnoaa",
  ...
)
```

## Arguments

- begin_date:

  (numeric) Date in yyyymmdd format. Required

- end_date:

  (numeric) Date in yyyymmdd format. Required

- station_name:

  (numeric) a station name. Required

- product:

  (character) Specify the data type. See below for Details. Required

- datum:

  (character) See below for Details. Required for all water level
  products.

- units:

  (character) Specify metric or english (imperial) units, one of
  'metric', 'english'.

- time_zone:

  (character) Time zone, one of 'gmt', 'lst', 'lst_ldt'. For GMT, we
  convert time stamps to GMT. For LST, we look up the time zone of the
  station with its lat/lon values, and assign that time zone. When
  `product="predictions"` we don't adjust times at all.

- application:

  (character) If called within an external package, set to the name of
  your organization. Optional

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  Optional

## Value

List, of length one or two.

- metadata A list of metadata with slots id, name, lat, lon

- data A data.frame with data

## Details

Options for the product paramter. One of:

- water_level - Preliminary or verified water levels, depending on
  availability

- air_temperature - Air temperature as measured at the station

- water_temperature - Water temperature as measured at the station

- wind - Wind speed, direction, and gusts as measured at the station

- air_pressure - Barometric pressure as measured at the station

- air_gap - Air Gap (distance between a bridge and the water's surface)
  at the station

- conductivity - The water's conductivity as measured at the station

- visibility - Visibility from the station's visibility sensor. A
  measure of atmospheric clarity

- humidity - Relative humidity as measured at the station

- salinity - Salinity and specific gravity data for the station

- one_minute_water_level - One minute water level data for the station

- predictions - 6 minute predictions water level data for the station

- hourly_height - Verified hourly height water level data for the
  station

- high_low - Verified high/low water level data for the station

- daily_mean - Verified daily mean water level data for the station

- monthly_mean - Verified monthly mean water level data for the station

- datums - datums data for the stations

- currents - Currents data for currents stations

Maximum Durations in a Single Call:

- Products water_level through predictions allow requests for up to

- Products hourly_height and high_low allow requests for up to

- Products daily_mean and monthly_mean allow requests for up to

Options for the datum parameter. One of:

- MHHW - Mean higher high water

- MHW - Mean high water

- MTL - Mean tide level

- MSL - Mean sea level

- MLW - Mean low water

- MLLW - Mean lower low water

- NAVD - North American Vertical Datum

- STND - Station datum

## References

https://tidesandcurrents.noaa.gov/api/
https://tidesandcurrents.noaa.gov/map/

## Author

Scott Chamberlain, Joseph Stachelek, Tom Philippi

## Examples

``` r
if (FALSE) { # \dontrun{
# Get monthly mean sea level data at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20120301,
  end_date = 20141001, datum = "stnd", product = "monthly_mean")

# Get verified water level data at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, datum = "stnd", product = "water_level")

# Get daily mean water level data at Fairport, OH (9063053)
coops_search(station_name = 9063053, begin_date = 20150927,
  end_date = 20150928, product = "daily_mean", datum = "stnd",
  time_zone = "lst")

# Get air temperature at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, product = "air_temperature")

# Get water temperature at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, product = "water_temperature")

# Get air pressure at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, product = "air_pressure")

# Get wind at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, product = "wind")

# Get hourly water level height at Key West (8724580)
coops_search(station_name = 8724580, begin_date = 20140927,
  end_date = 20140928, product = "hourly_height", datum = "stnd")

# Get high-low water level at Key West (8724580)
coops_search(station_name = 8724580, begin_date = 20140927,
  end_date = 20140928, product = "high_low", datum = "stnd")

# Get currents data at Pascagoula Harbor (ps0401)
coops_search(station_name = "ps0401", begin_date = 20151221,
  end_date = 20151222, product = "currents")

# Get one-minute water level at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140927,
  end_date = 20140928, datum = "stnd", product = "one_minute_water_level")

# Get datums at Fort Myers, FL (8725520)
coops_search(station_name = 8725520, product = "datums")

# Get water level predictions at Vaca Key (8723970)
coops_search(station_name = 8723970, begin_date = 20140928,
  end_date = 20140929, datum = "stnd", product = "predictions")

} # }
```
