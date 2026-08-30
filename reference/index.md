# Package index

## rnoaa

High level overview of package

- [`rnoaa-package`](https://docs.ropensci.org/rnoaa/reference/rnoaa-package.md)
  [`rnoaa`](https://docs.ropensci.org/rnoaa/reference/rnoaa-package.md)
  : rnoaa
- [`rnoaa-defunct`](https://docs.ropensci.org/rnoaa/reference/rnoaa-defunct.md)
  : Defunct functions in rnoaa
- [`rnoaa_options()`](https://docs.ropensci.org/rnoaa/reference/rnoaa_options.md)
  : rnoaa options
- [`rnoaa_caching`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`isd_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`cpc_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`arc2_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`lcd_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`bsw_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`ersst_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`torn_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`ghcnd_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  [`stormevents_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  : rnoaa caching

## datasets

rnoaa datasets

- [`fipscodes`](https://docs.ropensci.org/rnoaa/reference/fipscodes.md)
  : FIPS codes for US states.

## Africa Rainfall Climatology

- [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md) : Arc2 -
  Africa Rainfall Climatology version 2

## Argo buoy data

## Blended sea winds

- [`bsw()`](https://docs.ropensci.org/rnoaa/reference/bsw.md) : Blended
  sea winds (BSW)

## National Buoy Data Center

- [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  [`buoys()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  [`buoy_stations()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  : Get NOAA buoy data from the National Buoy Data Center

## CO-OPS (Tides and Currents)

- [`coops_search()`](https://docs.ropensci.org/rnoaa/reference/coops.md)
  : Get NOAA co-ops data

## Climate Prediction Center

- [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md)
  : Precipitation data from NOAA Climate Prediction Center (CPC)

## Extended Reconstructed Sea Surface Temperature

- [`ersst()`](https://docs.ropensci.org/rnoaa/reference/ersst.md) : NOAA
  Extended Reconstructed Sea Surface Temperature (ERSST) data

## Global Historical Climatology Network Daily

- [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)
  [`ghcnd_read()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) :
  Get all GHCND data from a single weather site

- [`ghcnd_states()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md)
  [`ghcnd_countries()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md)
  [`ghcnd_version()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md)
  : Get meta-data on the GHCND daily data

- [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
  : Get a cleaned version of GHCND data from a single weather site

- [`ghcnd_splitvars()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_splitvars.md)
  :

  Split variables in data returned from `ghcnd`

- [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md)
  : Get information on the GHCND weather stations

- [`meteo_clear_cache()`](https://docs.ropensci.org/rnoaa/reference/meteo_clear_cache.md)
  :

  Clear *meteo* cached files

- [`meteo_coverage()`](https://docs.ropensci.org/rnoaa/reference/meteo_coverage.md)
  : Determine the "coverage" for a station data frame

- [`meteo_distance()`](https://docs.ropensci.org/rnoaa/reference/meteo_distance.md)
  : Find all monitors within a radius of a location

- [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)
  : Find weather monitors near locations

- [`meteo_process_geographic_data()`](https://docs.ropensci.org/rnoaa/reference/meteo_process_geographic_data.md)
  : Calculate the distances between a location and all available
  stations

- [`meteo_pull_monitors()`](https://docs.ropensci.org/rnoaa/reference/meteo_pull_monitors.md)
  : Pull GHCND weather data for multiple weather monitors

- [`meteo_show_cache()`](https://docs.ropensci.org/rnoaa/reference/meteo_show_cache.md)
  :

  Show the *meteo* cache directory

- [`meteo_spherical_distance()`](https://docs.ropensci.org/rnoaa/reference/meteo_spherical_distance.md)
  : Calculate the distance between two locations

- [`meteo_tidy_ghcnd()`](https://docs.ropensci.org/rnoaa/reference/meteo_tidy_ghcnd.md)
  : Create a tidy GHCND dataset from a single monitor

- [`meteo_tidy_ghcnd_element()`](https://docs.ropensci.org/rnoaa/reference/meteo_tidy_ghcnd_element.md)
  : Restructure element of ghcnd_search list

- [`vis_miss()`](https://docs.ropensci.org/rnoaa/reference/vis_miss.md)
  : Visualize missingness in a dataframe

- [`autoplot_meteo_coverage()`](https://docs.ropensci.org/rnoaa/reference/autoplot_meteo_coverage.md)
  : autoplot method for meteo_coverage objects

## Historical Observing Metadata Repository

- [`homr()`](https://docs.ropensci.org/rnoaa/reference/homr.md) :
  Historical Observing Metadata Repository (HOMR) station metadata
- [`homr_definitions()`](https://docs.ropensci.org/rnoaa/reference/homr_definitions.md)
  : Historical Observing Metadata Repository (HOMR) station metadata -
  definitions

## Integrated Surface Data

- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) : Get and
  parse NOAA ISD/ISH data
- [`isd_read()`](https://docs.ropensci.org/rnoaa/reference/isd_read.md)
  : Read NOAA ISD/ISH local file
- [`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md)
  : Get NOAA ISD/ISH station data from NOAA FTP server.
- [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  : Search for NOAA ISD/ISH station data from NOAA FTP server.

## Local Climitalogical Data

- [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) : Local
  Climatological Data from NOAA

## National Climatic Data Center

- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) : Search
  for and get NOAA NCDC data
- [`ncdc_combine()`](https://docs.ropensci.org/rnoaa/reference/ncdc_combine.md)
  : Coerce multiple outputs to a single data.frame object.
- [`ncdc_datacats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datacats.md)
  : Get possible data categories for a particular datasetid, locationid,
  stationid, etc.
- [`ncdc_datasets()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datasets.md)
  : Search NOAA datasets
- [`ncdc_datatypes()`](https://docs.ropensci.org/rnoaa/reference/ncdc_datatypes.md)
  : Get possible data types for a particular dataset
- [`ncdc_locs()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs.md)
  : Get metadata about NOAA NCDC locations.
- [`ncdc_locs_cats()`](https://docs.ropensci.org/rnoaa/reference/ncdc_locs_cats.md)
  : Get metadata about NOAA location categories.
- [`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md)
  : Plot NOAA climate data.
- [`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md)
  : Get metadata about NOAA NCDC stations.

## Sea Ice

- [`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md) :
  Get sea ice data.
- [`sea_ice_tabular()`](https://docs.ropensci.org/rnoaa/reference/sea_ice_tabular.md)
  : Sea ice tabular data
- [`theme_ice()`](https://docs.ropensci.org/rnoaa/reference/theme_ice.md)
  : ggplot2 map theme

## Storm Events

- [`se_data()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md)
  [`se_files()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md)
  : NOAA Storm Events data

## Severe Weather Data Inventor

- [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md) : Get
  NOAA data for the Severe Weather Data Inventory (SWDI)

## Tornadoes

- [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md)
  : Get NOAA tornado data.
