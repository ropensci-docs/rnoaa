# Defunct functions in rnoaa

- `noaa`: Function name changed, prefixed with ncdc now

- `noaa_datacats`: Function name changed, prefixed with ncdc now

- `noaa_datasets`: Function name changed, prefixed with ncdc now

- `noaa_datatypes`: Function name changed, prefixed with ncdc now

- `noaa_locs`: Function name changed, prefixed with ncdc now

- `noaa_locs_cats`: Function name changed, prefixed with ncdc now

- `noaa_stations`: Function name changed, prefixed with ncdc now

- `noaa_plot`: Function name changed, prefixed with ncdc now

- `noaa_combine`: Function name changed, prefixed with ncdc now

- `noaa_seaice`: Function name changed to seaice

- `erddap_data`: See package rerddap

- `erddap_clear_cache`: See package rerddap

- `erddap_datasets`: Moved to package rerddap

- `erddap_grid`: Moved to package rerddap

- `erddap_info`: Moved to `rerddap::info()`

- `erddap_search`: Moved to `rerddap::ed_search`

- `erddap_table`: Moved to `rerddap::tabledap`

- `ncdc_leg_variables`: Removed. See `NCDC Legacy` below

- `ncdc_leg_sites`: Removed. See `NCDC Legacy` below

- `ncdc_leg_site_info`: Removed. See `NCDC Legacy` below

- `ncdc_leg_data`: Removed. See `NCDC Legacy` below

- `seaice`: Replaced with
  [`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md)

- `lcd_cleanup`: No longer available. See `lcd` docs

- `ghcnd_clear_cache`: No longer available. See
  [rnoaa_caching](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)

- `storm_shp`: Function defunct.

- `storm_shp_read`: Function defunct.

- `storm_data`: Function defunct.

- `storm_meta`: Function defunct.

## Details

The functions for working with GEFS ensemble forecast data (prefixed
with "gefs") are defunct, but may come back to rnoaa later:

- [`gefs()`](https://docs.ropensci.org/rnoaa/reference/gefs-defunct.md)

- [`gefs_dimension_values()`](https://docs.ropensci.org/rnoaa/reference/gefs_dimension_values-defunct.md)

- [`gefs_dimensions()`](https://docs.ropensci.org/rnoaa/reference/gefs_dimensions-defunct.md)

- [`gefs_ensembles()`](https://docs.ropensci.org/rnoaa/reference/gefs_ensembles-defunct.md)

- [`gefs_latitudes()`](https://docs.ropensci.org/rnoaa/reference/gefs_latitudes-defunct.md)

- [`gefs_longitudes()`](https://docs.ropensci.org/rnoaa/reference/gefs_longitudes-defunct.md)

- [`gefs_times()`](https://docs.ropensci.org/rnoaa/reference/gefs_times-defunct.md)

- [`gefs_variables()`](https://docs.ropensci.org/rnoaa/reference/gefs_variables-defunct.md)

## NCDC Legacy

The NCDC legacy API is too unreliable and slow. Use the newer NCDC API
via the functions
[`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md),
[`ncdc_datacats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datacats.md),
[`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md),
[`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md),
[`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md),
[`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md),
[`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md),
[`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md),
and
[`ncdc_combine()`](https://docs.ropensci.org/rnoaa/reference/ncdc_combine.md)
