# Changelog

## rnoaa 1.4.0

CRAN release: 2023-04-27

- All API changed base URL and endpoints so current package does not
  work to pull new data
- Started the process of archiving the package
- Fixed roxygen documentation to have autoplot as function not s3method
  in the NAMESPACE
- autoplot.meteo_coverage changed to autoplot_meteo_coverage to avoid S3
  generic naming convention
- Removed argo bouy data functions since API is gone

## rnoaa 1.3.9

#### BUG FIXES

- changed default location of cache file writing from hoardr to match
  requirements of CRAN for Mac OS
- added cache cleanup in tests
- updated homr API base url to
  <https://www.ncei.noaa.gov/access/homr/services/station/>

## rnoaa 1.3.8

CRAN release: 2021-12-01

- changed location of temporary cache file writing in the ersst tests to
  match requirements of CRAN for Mac OS. Missed on v1.3.7 release.
- removed rappsdir from Imports now that using tools to create cache
  directories
- removed a couple other internal tests from CRAN with skip_on_cran()

rnoaa 1.3.7

#### BUG FIXES

- changed location of temporary file writing to match requirements of
  CRAN for Mac OS
- removed checks on Ubuntu 16.04. Replaced with checks on latest Ubuntu
  version

## rnoaa 1.3.4

CRAN release: 2021-05-19

#### MINOR IMPROVEMENTS

- update URL for tornadoes data to include data from 2019
  ([\#386](https://github.com/ropensci/rnoaa/issues/386)) thanks
  [@ryanscharf](https://github.com/ryanscharf)

#### BUG FIXES

- fix for all `ncdc*` functions - response header content type changed -
  we had a check for proper content type - that check is now more
  general so that any json content type will be okay
  ([\#390](https://github.com/ropensci/rnoaa/issues/390))

## rnoaa 1.3.2

CRAN release: 2021-02-15

#### MINOR IMPROVEMENTS

- remove ropenaq from Suggests as its been archived on CRAN
  ([\#385](https://github.com/ropensci/rnoaa/issues/385))
- test fixes ([\#382](https://github.com/ropensci/rnoaa/issues/382))

## rnoaa 1.3

#### NEW FEATURES

- [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) now
  accepts more than 1 station identifier
  ([\#373](https://github.com/ropensci/rnoaa/issues/373)) PR from
  [@eliocamp](https://github.com/eliocamp)
- [`ersst()`](https://docs.ropensci.org/rnoaa/reference/ersst.md): use
  new v5 version of their service - see
  [`?ersst`](https://docs.ropensci.org/rnoaa/reference/ersst.md) docs
  for details ([\#381](https://github.com/ropensci/rnoaa/issues/381))
  thanks [@vonStadarhraun](https://github.com/vonStadarhraun) for the
  tip

#### MINOR IMPROVEMENTS

- update [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  docs to state that a special value of `9999` passsed to the `year`
  parameter will give the most up to date data (aka current data) - and
  an example added using it
  ([\#377](https://github.com/ropensci/rnoaa/issues/377))
- update to current dplyr functions from deprecated ones
  ([\#375](https://github.com/ropensci/rnoaa/issues/375))
- update description of units TMAX and TMIN for dataset GHCND when using
  function [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)
  with `add_units = TRUE`
  ([\#378](https://github.com/ropensci/rnoaa/issues/378))
  ([\#379](https://github.com/ropensci/rnoaa/issues/379)) PR from
  [@amcdavid](https://github.com/amcdavid)

#### BUG FIXES

- changed
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)
  handling of unknown/bad/invalid station identifiers: now returns an
  empty data.frame and gives back empty strings for the two attributes
  `source` and `file_modified`
  ([\#374](https://github.com/ropensci/rnoaa/issues/374))

## rnoaa 1.2.0

CRAN release: 2020-10-06

#### DEFUNCT

- The following IBTrACS storm functions are now defunct because they are
  too cumbersome to maintain:
  [`storm_data()`](https://docs.ropensci.org/rnoaa/reference/storm_data-defunct.md),
  [`storm_meta()`](https://docs.ropensci.org/rnoaa/reference/storm_data-defunct.md),
  [`storm_shp()`](https://docs.ropensci.org/rnoaa/reference/storm_shp-defunct.md),
  and
  [`storm_shp_read()`](https://docs.ropensci.org/rnoaa/reference/storm_shp-defunct.md).
  associated package datasets `storm_columns` and `storm_names` removed
  ([\#306](https://github.com/ropensci/rnoaa/issues/306))

#### MINOR IMPROVEMENTS

- vignettes are now all pre-built, and all URLs are now unlinked
  ([\#367](https://github.com/ropensci/rnoaa/issues/367))
- [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) returns a
  tibble now instead of a tibble with S3 class `lcd` attached
  ([\#369](https://github.com/ropensci/rnoaa/issues/369))
- created manual file entry for `stormevents_cache`
- drop `sf` from Suggests, only used in an example

#### BUG FIXES

- [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md) fix:
  when using `bbox` parameter, it would not have worked as intended,
  fixed now ([\#372](https://github.com/ropensci/rnoaa/issues/372))

## rnoaa 1.1.0

CRAN release: 2020-07-08

#### MINOR IMPROVEMENTS

- fix coops test ([\#364](https://github.com/ropensci/rnoaa/issues/364))
- remove deprecated parameters in argo and ncdc\* functions
  ([\#361](https://github.com/ropensci/rnoaa/issues/361))

## rnoaa 1.0.0

CRAN release: 2020-06-13

#### NEW FEATURES

- the `argo` functions that were not working because of a down API are
  working again, see `?argo`
  ([\#358](https://github.com/ropensci/rnoaa/issues/358))
- most of the defunct functions have been removed from the package, but
  are still referenced in the `?rnoaa-defunct` manual file. `gefs`
  functions are still in the package as those functions may come back at
  some point. ([\#359](https://github.com/ropensci/rnoaa/issues/359))
- two things for
  [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md): 1) now
  accepts more than 1 date; 2) gains new parameter `box` to accept a
  bounding box to spatially filter results (uses
  [`dplyr::filter`](https://dplyr.tidyverse.org/reference/filter.html)
  on the data.frame of spatial data)
  ([\#351](https://github.com/ropensci/rnoaa/issues/351))

#### Documentation

Regarding the documentation site at <https://docs.ropensci.org/rnoaa>

- the function reference page
  <https://docs.ropensci.org/rnoaa/reference/index.html> has been
  improved; grouping functions by topic area and data source - for
  easier browsing
  ([\#360](https://github.com/ropensci/rnoaa/issues/360))
- a getting started vignette has been added, see the “Get Started” tab
  ([\#357](https://github.com/ropensci/rnoaa/issues/357))

#### MINOR IMPROVEMENTS

- `ghncd()` (and all functions that build on
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)) can
  now be altered to use a specific base URL for requests. See the “Base
  URL” section of the
  [`?ghcnd`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) docs
  ([\#353](https://github.com/ropensci/rnoaa/issues/353))
- [`ghcnd_splitvars()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_splitvars.md)
  speedup, using `data.table` instead of dplyr for manipulation
  ([\#352](https://github.com/ropensci/rnoaa/issues/352))
  ([\#355](https://github.com/ropensci/rnoaa/issues/355))
- use
  [`tibble::as_tibble`](https://tibble.tidyverse.org/reference/as_tibble.html)
  throughout package instead of
  [`dplyr::tbl_df`](https://dplyr.tidyverse.org/reference/defunct.html)
  ([\#354](https://github.com/ropensci/rnoaa/issues/354))

#### BUG FIXES

- fix for
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md):
  internal method `get_inventory()` was not creating a directory first
  before trying to download a file into that directory
  ([\#349](https://github.com/ropensci/rnoaa/issues/349))
  ([\#350](https://github.com/ropensci/rnoaa/issues/350))

## rnoaa 0.9.6

CRAN release: 2020-04-07

#### NEW FEATURES

- new function
  [`rnoaa_options()`](https://docs.ropensci.org/rnoaa/reference/rnoaa_options.md)
  to toggle package level options; only option for now is
  `cache_messages`, a boolean to toggle whether the user gets messages
  about cached files or not. along with this change, messages about
  cached files and file sizes and locations are now consistently used
  across all functions that cache files on disk
  ([\#331](https://github.com/ropensci/rnoaa/issues/331))
- new manual file
  [`?rnoaa_caching`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md) -
  with information on how to access and manage cached files for each of
  the rnoaa functions that caches files on disk
  ([\#346](https://github.com/ropensci/rnoaa/issues/346))
- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) moved to
  using `hoardr` caching - see
  [`?isd_cache`](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
  for details ([\#347](https://github.com/ropensci/rnoaa/issues/347))

#### MINOR IMPROVEMENTS

- remove internal code in many exported functions looking for user input
  `path` parameter and telling them it’s no longer used; been defunct
  for quite a while
- now able to cache http requests for tests that write to disk
  ([\#290](https://github.com/ropensci/rnoaa/issues/290))
  ([\#345](https://github.com/ropensci/rnoaa/issues/345))
- [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md)
  now caching data - first time requests should now take just over 1
  minute, with subsequent requests (assuming cached data isn’t deleted)
  taking ~ 3 seconds
  ([\#164](https://github.com/ropensci/rnoaa/issues/164))
- `autoplot` method
  [`meteo_coverage()`](https://docs.ropensci.org/rnoaa/reference/meteo_coverage.md)
  fix to visually display gaps in data
  ([\#314](https://github.com/ropensci/rnoaa/issues/314))
  ([\#333](https://github.com/ropensci/rnoaa/issues/333)) thanks
  [@philipshirk](https://github.com/philipshirk)

#### BUG FIXES

- fix for ncdc functions to fail better - NOAA was returning HTML on
  request failures instead of JSON - catch that better and give proper
  http status code response
  ([\#338](https://github.com/ropensci/rnoaa/issues/338))
- [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)
  fix: coerce input data.frame to the function to a data.frame before
  remainder of steps - in case user inputs a tibble
  ([\#340](https://github.com/ropensci/rnoaa/issues/340))
- [`coops_search()`](https://docs.ropensci.org/rnoaa/reference/coops.md)
  fix: when `product=predictions`, we get no metadata back - so just
  dont adjust times
  ([\#342](https://github.com/ropensci/rnoaa/issues/342))
- [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) changes:
  gains `lcd_cache` for managing cached files; use a new internal
  function for safely reading each csv file, with more informative error
  messages; ([\#344](https://github.com/ropensci/rnoaa/issues/344))
- [`meteo_pull_monitors()`](https://docs.ropensci.org/rnoaa/reference/meteo_pull_monitors.md)
  fix: changed internals of
  [`meteo_tidy_ghcnd()`](https://docs.ropensci.org/rnoaa/reference/meteo_tidy_ghcnd.md)
  to set -9999 values to NA slightly differently to avoi failing
  ([\#348](https://github.com/ropensci/rnoaa/issues/348))

## rnoaa 0.9.5

CRAN release: 2019-11-20

#### BUG FIXES

- [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) function
  was unfortunately pulling data from
  `https://www.ncei.noaa.gov/data/global-hourly/access` - whereas it
  should have been pulling data from
  `https://www.ncei.noaa.gov/data/local-climatological-data/access` -
  fixed now; additionaly, `lcd_cleanup` is defunct because lcd data
  coming from the appropriate link has all variable names spelled out
  and data split up
  ([\#334](https://github.com/ropensci/rnoaa/issues/334)) thanks
  [@sayon000](https://github.com/sayon000) !
- all `gefs*` functions are now defunct - they are being taken out for
  now until fixed - see the issues for the details
  ([\#335](https://github.com/ropensci/rnoaa/issues/335))
  ([\#336](https://github.com/ropensci/rnoaa/issues/336))

## rnoaa 0.9.4

CRAN release: 2019-11-07

#### NEW FEATURES

- new gefs function helpers `gefs_dimensions` and `gefs_ensembles`
  ([\#327](https://github.com/ropensci/rnoaa/issues/327))
  ([\#328](https://github.com/ropensci/rnoaa/issues/328))

#### MINOR IMPROVEMENTS

- `gefs` function fixes: fixed failing test on CRAN having to do with a
  date mismatch; `gefs` now cleans up temporary files
  ([\#327](https://github.com/ropensci/rnoaa/issues/327))
  ([\#328](https://github.com/ropensci/rnoaa/issues/328))

#### BUG FIXES

- Some argo buoy functions use an API and some use an FTP server. The
  API is down, and no longer exists. The funitons that use the API
  (`argo_search`, `argo_files`, `argo_qwmo`, `argo_plan`) no longer
  work, while the functions that use the FTP server still work
  (`argo_buoy_files`, `argo`)
  ([\#333](https://github.com/ropensci/rnoaa/issues/333))

## rnoaa 0.9.2

CRAN release: 2019-10-23

#### MINOR IMPROVEMENTS

- gefs gains new parameters `ens` and `time`, that will eventually
  replace the deprecated parameters `ens_idx` and `time_idx`
  ([\#321](https://github.com/ropensci/rnoaa/issues/321))
  ([\#324](https://github.com/ropensci/rnoaa/issues/324))
- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) now using
  fetching data using http instead of ftp

#### BUG FIXES

- fix to
  [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md):
  the URL had changed yet again
  ([\#322](https://github.com/ropensci/rnoaa/issues/322))
  ([\#323](https://github.com/ropensci/rnoaa/issues/323)) thanks
  [@mbjoseph](https://github.com/mbjoseph) !
- fix to gefs, was failing with some examples
  ([\#320](https://github.com/ropensci/rnoaa/issues/320))
  ([\#321](https://github.com/ropensci/rnoaa/issues/321))

## rnoaa 0.9.0

CRAN release: 2019-09-26

#### NEW FEATURES

- gains
  [`sea_ice_tabular()`](https://docs.ropensci.org/rnoaa/reference/sea_ice_tabular.md)
  function for fetching tabular .csv sea ice files instead of using the
  shp files in
  [`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md)
  ([\#194](https://github.com/ropensci/rnoaa/issues/194))
- `seaice()` fxn name has changed to
  [`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md)
  ([\#313](https://github.com/ropensci/rnoaa/issues/313))
- [`sea_ice()`](https://docs.ropensci.org/rnoaa/reference/sea_ice.md)
  gains option to fetch GeoTIFF format data in addition to shp files
  ([\#219](https://github.com/ropensci/rnoaa/issues/219))
  ([\#313](https://github.com/ropensci/rnoaa/issues/313))
- gains new function `lcd_cleanup()` - takes output of call to
  [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md), parsing
  additional columns that contain comma separated strings
  ([\#283](https://github.com/ropensci/rnoaa/issues/283))

#### MINOR IMPROVEMENTS

- update README to link to ncdf4 pkg instead of ncdf pkg, and a note
  about which functions in rnoaa use ncdf4 (b/c ncdf4 is in Suggests)
  ([\#299](https://github.com/ropensci/rnoaa/issues/299)) thanks
  [@denrou](https://github.com/denrou)
- now using markdown docs
  ([\#301](https://github.com/ropensci/rnoaa/issues/301))
- update [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)
  docs to highlight that cached files downloaded with the fxn will be
  used until deleted by the user! See
  [`?isd`](https://docs.ropensci.org/rnoaa/reference/isd.md) docs for
  details ([\#205](https://github.com/ropensci/rnoaa/issues/205))
- lat/lon param definition in `gefs` only mentioned longitude, now both
  vars discussed ([\#317](https://github.com/ropensci/rnoaa/issues/317))
  ([\#318](https://github.com/ropensci/rnoaa/issues/318))
- improve docs for
  [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)
  regarding units, and in readme and vignette as well
  ([\#265](https://github.com/ropensci/rnoaa/issues/265))
  ([\#315](https://github.com/ropensci/rnoaa/issues/315)) from
  [@amoeba](https://github.com/amoeba)

#### BUG FIXES

- fix bug in
  [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md):
  should have allowed dates back to 1948, but only allowed back to 1979
  ([\#300](https://github.com/ropensci/rnoaa/issues/300))
- fix to [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  fxn: datasets that did not have lat/lon variables were failing to be
  parsed by the fxn; now when lat/lon vars missing, we just give. back
  ncdf4 object for the user to deal with themselves
  ([\#303](https://github.com/ropensci/rnoaa/issues/303))
  ([\#304](https://github.com/ropensci/rnoaa/issues/304))
- fix to
  [`gefs()`](https://docs.ropensci.org/rnoaa/reference/gefs-defunct.md):
  longitude on the (-180, 180) scale worked but not on the (0,360) scale
  ([\#316](https://github.com/ropensci/rnoaa/issues/316))
  ([\#318](https://github.com/ropensci/rnoaa/issues/318))
  ([\#319](https://github.com/ropensci/rnoaa/issues/319))
- fix to
  [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md):
  the URL for the data had changed
  ([\#311](https://github.com/ropensci/rnoaa/issues/311))
  ([\#312](https://github.com/ropensci/rnoaa/issues/312)) thanks
  [@mbjoseph](https://github.com/mbjoseph)
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)
  parameters `startdate`/`enddate` weren’t handling dates as input
  values; now handle date and character inputs
  ([\#307](https://github.com/ropensci/rnoaa/issues/307))
- fixed issue in
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md);
  there was an encoding issue with the data returned from NOAA
  ([\#305](https://github.com/ropensci/rnoaa/issues/305))

## rnoaa 0.8.4

CRAN release: 2019-01-14

#### US federal government shutdown

This very long US federal government shutdown has allowed time for
building in nicer failure behavior and more documentation for government
shutdowns. There’s a number of related changes:

- better government shutdown failure behavior for the
  [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md) function
  ([\#298](https://github.com/ropensci/rnoaa/issues/298))
- better government shutdown failure behavior for the
  [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) function
  ([\#295](https://github.com/ropensci/rnoaa/issues/295))
- better failure behavior for all `ncdc*()` functions
  ([\#293](https://github.com/ropensci/rnoaa/issues/293))
  ([\#297](https://github.com/ropensci/rnoaa/issues/297))
- added a package level manual file section “Where data comes from and
  government shutdowns”

#### MINOR IMPROVEMENTS

- [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md): changed
  from downloading data with `download.file` to `crul`
  ([\#298](https://github.com/ropensci/rnoaa/issues/298))
- fix [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md)
  tests to not have hard-coded dates
  ([\#294](https://github.com/ropensci/rnoaa/issues/294))

## rnoaa 0.8.2

#### BUG FIXES

- improvements in failing well when there’s a US government shutdown for
  many functions that work with web REST APIs
  ([\#293](https://github.com/ropensci/rnoaa/issues/293))
  ([\#295](https://github.com/ropensci/rnoaa/issues/295))
- fix to `arc2` tests to not be sensitive to the real year that the test
  is run in, reported in CRAN checks and via email
  ([\#294](https://github.com/ropensci/rnoaa/issues/294))

## rnoaa 0.8.0

CRAN release: 2018-12-03

#### NEW FEATURES

- gains function
  [`bsw()`](https://docs.ropensci.org/rnoaa/reference/bsw.md) for
  Blended Sea Winds data
  ([\#246](https://github.com/ropensci/rnoaa/issues/246))
- gains function
  [`ghcnd_read()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) -
  to read .dly files directly, e.g., files already downloaded
  ([\#223](https://github.com/ropensci/rnoaa/issues/223)) thanks
  [@shabbychef](https://github.com/shabbychef) for the feature request
- gains function
  [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md) for Local
  Climatological Data
  ([\#212](https://github.com/ropensci/rnoaa/issues/212))
- gains functions
  [`se_data()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md)
  and
  [`se_files()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md)
  for the Storm Events Database
  ([\#282](https://github.com/ropensci/rnoaa/issues/282))
- [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) and
  [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
  gain a `refresh` parameter to refresh data for the query even if it’s
  already cached locally. in addition, these functions now print
  messages to tell the user what file path the data is locally cached
  in, and the min and max dates when using
  [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
  ([\#269](https://github.com/ropensci/rnoaa/issues/269)) thanks
  [@kgmccann](https://github.com/kgmccann)
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) gains
  `add_units` parameter (boolean) to toggle adding units to the output
  data.frame. default is `add_units=FALSE`. if `add_units=TRUE` we match
  dataset id and data type id and return units if we have them. do be in
  touch if you see a problem with these units!
  [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) now
  returns tibbles in the `data` slot
  ([\#233](https://github.com/ropensci/rnoaa/issues/233))
  ([\#266](https://github.com/ropensci/rnoaa/issues/266))
  ([\#289](https://github.com/ropensci/rnoaa/issues/289))
  ([\#287](https://github.com/ropensci/rnoaa/issues/287))

#### MINOR IMPROVEMENTS

- spelling fixes to `coops` docs
  ([\#228](https://github.com/ropensci/rnoaa/issues/228)) thanks
  [@jsta](https://github.com/jsta)
- fix in
  [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
  to arrange data by day instead of by month
  ([\#247](https://github.com/ropensci/rnoaa/issues/247)) thanks
  [@asrivas3](https://github.com/asrivas3) for reporting
- move [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md) to
  use `xml2` and `crul` packages instead of `XML` and `httr`
  ([\#275](https://github.com/ropensci/rnoaa/issues/275))
- added [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md)
  tests ([\#239](https://github.com/ropensci/rnoaa/issues/239)) thanks
  [@kevin-ht-ho](https://github.com/kevin-ht-ho)
- [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  no longer renames lat and lon column names
  ([\#238](https://github.com/ropensci/rnoaa/issues/238)) thanks
  [@kevin-ht-ho](https://github.com/kevin-ht-ho)
- add codemeta keywords to description
  ([\#287](https://github.com/ropensci/rnoaa/issues/287))
- replace `httr` with `crul` throughout package
  ([\#186](https://github.com/ropensci/rnoaa/issues/186))
- many tests use `vcr` now for caching, more to do waiting on `vcr`
  being able to handle direct to disk use cases and binary files like
  pdfs ([\#284](https://github.com/ropensci/rnoaa/issues/284))
- fix links in Code of Conduct

#### BUG FIXES

- fixes to
  [`gefs()`](https://docs.ropensci.org/rnoaa/reference/gefs-defunct.md).
  was incorrectly repeating time values within ensembles when it should
  have repeated time values across ensembles so that each ensemble has a
  time value for each time period
  ([\#230](https://github.com/ropensci/rnoaa/issues/230))
  ([\#231](https://github.com/ropensci/rnoaa/issues/231)) thanks for
  report from [@lcsma](https://github.com/lcsma) and fix by
  [@potterzot](https://github.com/potterzot)
- fix bug in
  [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) - fix to
  internal function `parse_ncdc()`, which was failing on
  [`strsplit()`](https://rdrr.io/r/base/strsplit.html) call if
  attributes was `NULL`
  ([\#232](https://github.com/ropensci/rnoaa/issues/232)) thanks for
  reporting [@andypicke](https://github.com/andypicke)
- fix to
  [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md):
  URLs were changed at some point, fixes for this
  ([\#242](https://github.com/ropensci/rnoaa/issues/242))
- fix to
  [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md):
  to read `.gz` files correctly with gzfile instead of file
  ([\#248](https://github.com/ropensci/rnoaa/issues/248))
- fix in [`homr()`](https://docs.ropensci.org/rnoaa/reference/homr.md) -
  NOAA server gives back a 200 OK response even if that’s not the case -
  but we can check content type to see if there was likely an error
  ([\#250](https://github.com/ropensci/rnoaa/issues/250))
- fix to `autoplot.meteo_coverage`
  ([\#258](https://github.com/ropensci/rnoaa/issues/258))
- fix to
  [`buoy_stations()`](https://docs.ropensci.org/rnoaa/reference/buoy.md):
  was getting the wrong station ids - fixed; and use async HTTP requests
  to get data faster
  ([\#261](https://github.com/ropensci/rnoaa/issues/261)) thanks
  [@johnharley](https://github.com/johnharley) for the bug report
- fix to
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md):
  was returning an extra empty row
  ([\#267](https://github.com/ropensci/rnoaa/issues/267)) thanks
  [@joeroe](https://github.com/joeroe) for the bug report
- related to ([\#267](https://github.com/ropensci/rnoaa/issues/267)),
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) was
  giving a trailing row of NA’s - fixed
  ([\#270](https://github.com/ropensci/rnoaa/issues/270))
- [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md):
  `radius` parameter doesn’t work, update docs to tell users not to use
  it ([\#243](https://github.com/ropensci/rnoaa/issues/243))
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) fix: fix
  to internal function `parse_ncdc()`, errored when more than 1 flag
  returned ([\#279](https://github.com/ropensci/rnoaa/issues/279))
  thanks [@ghaines3](https://github.com/ghaines3) for the bug report
- buoy fixes ([\#251](https://github.com/ropensci/rnoaa/issues/251))
- [`storm_shp()`](https://docs.ropensci.org/rnoaa/reference/storm_shp-defunct.md)
  fix: update to use new URL patterns
  ([\#263](https://github.com/ropensci/rnoaa/issues/263))
- make [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md)
  fail better ([\#274](https://github.com/ropensci/rnoaa/issues/274))
  thanks [@OrionDarley](https://github.com/OrionDarley)
- fix
  [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md)
  to coerce character to numeric lat and lon values
  ([\#257](https://github.com/ropensci/rnoaa/issues/257)) thanks
  [@mondorescue](https://github.com/mondorescue) for the bug report
- fix to
  [`meteo_nearby_stations()`](https://docs.ropensci.org/rnoaa/reference/meteo_nearby_stations.md) -
  internally ignored the user supplied column names for lat and lon
  ([\#286](https://github.com/ropensci/rnoaa/issues/286)) thanks
  [@ghaines3](https://github.com/ghaines3) for the bug report
- fixed
  [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md)
  for Windows OS’s:
  [`utils::untar()`](https://rdrr.io/r/utils/untar.html) was failing on
  windows, changed to using
  [`utils::unzip()`](https://rdrr.io/r/utils/unzip.html)
  ([\#203](https://github.com/ropensci/rnoaa/issues/203))
- fixed `argo_buoy_files()`: use `fill=TRUE` in the `read.table` call -
  was erroring on some Windows OS’s
  ([\#235](https://github.com/ropensci/rnoaa/issues/235)) thanks
  [@jonmcalder](https://github.com/jonmcalder) for reporting

## rnoaa 0.7.0

CRAN release: 2017-05-06

Note that some NOAA datasets have changed names:

- `GHCNDMS` is now `GSOM` (Global Summary of the Month)
- `ANNUAL` is now `GSOY` (Global Summary of the Year)

#### NEW FEATURES

- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) gains new
  parameters `additional` to toggle whether the non-mandatory ISD fields
  (additional + remarks) are parsed and returned & `force` to toggle
  whether download new version or use cached version.
  [`isd_read()`](https://docs.ropensci.org/rnoaa/reference/isd_read.md)
  gains new parameter `additional` (see description above)
  ([\#190](https://github.com/ropensci/rnoaa/issues/190))
- New function for Climate Prediction Center data:
  [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md)
  ([\#193](https://github.com/ropensci/rnoaa/issues/193))
- New function
  [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md) to get
  data from Africa Rainfall Climatology version 2
  ([\#201](https://github.com/ropensci/rnoaa/issues/201))

#### MINOR IMPROVEMENTS

- A number of NOAA services now use `https` - changed internal code to
  use `https` from `http` for coops, swdi, ersst, and tornadoes data
  sources ([\#187](https://github.com/ropensci/rnoaa/issues/187))
- Changes to sea ice URLs - just internal
  ([\#185](https://github.com/ropensci/rnoaa/issues/185))
- Fixes to
  [`coops_search()`](https://docs.ropensci.org/rnoaa/reference/coops.md)
  to handle requests better: only certain date combinations allowed for
  certain COOPS products
  ([\#213](https://github.com/ropensci/rnoaa/issues/213))
  ([\#214](https://github.com/ropensci/rnoaa/issues/214)) thanks
  [@tphilippi](https://github.com/tphilippi) !
- Now using `hoardr` package to manage caching in some functions. Will
  roll out to all functions that cache soon
  ([\#191](https://github.com/ropensci/rnoaa/issues/191))
- README img location fix requested by CRAN
  ([\#207](https://github.com/ropensci/rnoaa/issues/207))
- `GHCNDMS` is now `GSOM` and `ANNUAL` is now `GSOY` - added to docs and
  examples of using GSOM and GSOY
  ([\#189](https://github.com/ropensci/rnoaa/issues/189))

#### BUG FIXES

- A number of fixes to
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)
  ([\#168](https://github.com/ropensci/rnoaa/issues/168))
- Fixes to
  [`coops_search()`](https://docs.ropensci.org/rnoaa/reference/coops.md)
  to fix time zone problems
  ([\#184](https://github.com/ropensci/rnoaa/issues/184)) thanks
  [@drf5n](https://github.com/drf5n)
- Fixes to
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) - fix
  some column types that were of inappropriate type before
  ([\#211](https://github.com/ropensci/rnoaa/issues/211))
- Fix to
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md): we
  were coercing factors to integers, which caused nonsense output -
  first coercing to character now, then integer
  ([\#221](https://github.com/ropensci/rnoaa/issues/221))
- There were problems in parsing flags (attributes) for some datasets
  via [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md)
  function. Added metadata to the package to help parse flags
  ([\#199](https://github.com/ropensci/rnoaa/issues/199))

## rnoaa 0.6.6

CRAN release: 2016-11-17

#### NEW FEATURES

- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) now using
  a new package `isdparser` to parse NOAA ISD files. We still fetch the
  file within `rnoaa`, but the file parsing is done by `isdparser`
  ([\#176](https://github.com/ropensci/rnoaa/issues/176))
  ([\#177](https://github.com/ropensci/rnoaa/issues/177))
  ([\#180](https://github.com/ropensci/rnoaa/issues/180)) thanks
  [@mrubayet](https://github.com/mrubayet) for the push

#### MINOR IMPROVEMENTS

- Fixed precipitation units in docs for `meteo_*` functions
  ([\#178](https://github.com/ropensci/rnoaa/issues/178)) thanks
  [@mrubayet](https://github.com/mrubayet)

#### BUG FIXES

- Fixed bug in
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md) where
  internal unexported function was not found
  ([\#179](https://github.com/ropensci/rnoaa/issues/179))
- Fix to
  [`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md)
  and
  [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  to work correctly on Windows
  ([\#181](https://github.com/ropensci/rnoaa/issues/181)) thanks
  [@GuodongZhu](https://github.com/GuodongZhu)
- Changed base URL for all NOAA NCDC functions (those starting with
  `ncdc`) to `https` from `http`
  ([\#182](https://github.com/ropensci/rnoaa/issues/182)) thanks
  [@maspotts](https://github.com/maspotts)
- Changed base URL for all NOAA HOMR functions (those starting with
  `homr`) to `https` from `http`
  ([\#183](https://github.com/ropensci/rnoaa/issues/183))

## rnoaa 0.6.5

CRAN release: 2016-10-22

#### MINOR IMPROVEMENTS

- Added notes to docs of functions that do file caching - where to find
  cached files.
- `meteo_clear_cache` gains parameter `force` to control `force`
  parameter in [`unlink()`](https://rdrr.io/r/base/unlink.html)
- Removed `lubridate` usage in `seaiceurls()` function, just using base
  R functions.

#### BUG FIXES

- Fixed bug which was affecting binary installs only. We accidentally
  determined a path on package build, such that the user of the CRAN
  binary build machine got inserted into the path. This is now fixed.
  ([\#173](https://github.com/ropensci/rnoaa/issues/173))

## rnoaa 0.6.4

CRAN release: 2016-10-07

#### NEW FEATURES

- New function
  [`isd_read()`](https://docs.ropensci.org/rnoaa/reference/isd_read.md)
  to read ISD output from
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) manually
  instead of letting
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) read in
  the data. This is useful when you use
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) but need
  to read the file in later when it’s already cached.
  ([\#169](https://github.com/ropensci/rnoaa/issues/169))
- Some functions in `rnoaa` cache files that are downloaded from various
  NOAA web services. File caching is usually done when data comes from
  FTP servers. In some of these functions where we cache data, we used
  to write to your home directory, but have now changed all these
  functions to write to a proper cache directory in a platform
  independent way. We determine the cache directory using
  [`rappdirs::user_cache_dir()`](https://rappdirs.r-lib.org/reference/user_cache_dir.html).
  Note that this may change your workflow if you’d been depending on
  cached files to be a in particular place on your file system. In
  addition, the `path` parameter in the changed functions is now
  defunct, but you get an informative warning about it
  ([\#171](https://github.com/ropensci/rnoaa/issues/171))

#### MINOR IMPROVEMENTS

- [`storm_data()`](https://docs.ropensci.org/rnoaa/reference/storm_data-defunct.md)
  now returns a tibble/data.frame not inside of a list. We used to
  return a list with a single slot `data` with a data.frame, but this
  was unnecessary.
- [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md)
  now outputs a data.frame (`tbl_df`) by itself, instead of a data.frame
  nested in a list. This may change how you access data from this
  function. ([\#163](https://github.com/ropensci/rnoaa/issues/163))
- Improved docs on token usage for NCDC functions (with prefix
  `ncdc_*()`) ([\#167](https://github.com/ropensci/rnoaa/issues/167))
- Added note to
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) docs that
  when you get an error similar to
  `Error: download failed for ftp://ftp.ncdc.noaa.gov/pub/data/noaa/1955/011490-99999-1955.gz`,
  the file does not exist on NOAA’s ftp servers. If your internet is
  down, you’ll get a different error saying as much
  ([\#170](https://github.com/ropensci/rnoaa/issues/170))

## rnoaa 0.6.0

CRAN release: 2016-08-31

#### NEW FEATURES

- A large PR was merged with a suite of functions. Most functions added
  a prefixed with `meteo_*`, and are meant to find weather monitors near
  locations (`meteo_nearby_stations`), find all monitors within a radius
  of a location (`meteo_distance`), calculate the distances between a
  location and all available stations (`meteo_process_geographic_data`),
  calculate the distance between two locations
  (`meteo_spherical_distance`), pull GHCND weather data for multiple
  weather monitors (`meteo_pull_monitors`), create a tidy GHCND dataset
  from a single monitor (`meteo_tidy_ghcnd`), and determine the
  “coverage” for a station data frame
  ([`meteo_coverage()`](https://docs.ropensci.org/rnoaa/reference/meteo_coverage.md)).
  In addition,
  [`vis_miss()`](https://docs.ropensci.org/rnoaa/reference/vis_miss.md)
  added to visualize missingness in a data.frame. See the [PR diff
  against master](https://github.com/ropensci/rnoaa/pull/159/files) for
  all the changes.
  ([\#159](https://github.com/ropensci/rnoaa/issues/159)) Thanks a ton
  to [@geanders](https://github.com/geanders) *et al*.
  ([@hrbrmstr](https://github.com/hrbrmstr),
  [@maelle](https://github.com/maelle),
  [@jdunic](https://github.com/jdunic),
  [@njtierney](https://github.com/njtierney),
  [@leighseverson](https://github.com/leighseverson),
  [@RyanGan](https://github.com/RyanGan),
  [@mandilin](https://github.com/mandilin),
  [@jferreri](https://github.com/jferreri),
  [@cpatrizio88](https://github.com/cpatrizio88),
  [@ryan-hicks](https://github.com/ryan-hicks),
  [@Ewen2015](https://github.com/Ewen2015),
  [@mgutilla](https://github.com/mgutilla),
  [@hakessler](https://github.com/hakessler),
  [@rodlammers](https://github.com/rodlammers))

#### MINOR IMPROVEMENTS

- [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  changed internal structure. We replaced usage of `geojsonio` and
  `lawn` for faster
  [`dplyr::filter`](https://dplyr.tidyverse.org/reference/filter.html)
  for bbox inputs, and
  [`meteo_distance()`](https://docs.ropensci.org/rnoaa/reference/meteo_distance.md)
  for `lat/long/radius` inputs . This speeds up this function
  significantly. Thanks to
  [@lukas-rokka](https://github.com/lukas-rokka)
  ([\#157](https://github.com/ropensci/rnoaa/issues/157))
- [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  and
  [`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md)
  now return tibble’s instead of data.frame’s
- Removed cached ISD stations dataset within package to reduce package
  size. Only change is now that on first use of the function the user
  has to download the entire thing, but on subsquent uses it will pull
  from the cached version on the users machine.
  [`isd_stations_search()`](https://docs.ropensci.org/rnoaa/reference/isd_stations_search.md)
  now caches using `rappdirs`
  ([\#161](https://github.com/ropensci/rnoaa/issues/161))
- Convert all [`is()`](https://rdrr.io/r/methods/is.html) uses to
  [`inherits()`](https://rdrr.io/r/base/class.html)

#### BUG FIXES

- Fixed
  [`seaiceeurls()`](https://docs.ropensci.org/rnoaa/reference/seaiceeurls.md)
  function that’s used to generate urls for the `seaice()` function -
  due to change in NOAA urls
  ([\#160](https://github.com/ropensci/rnoaa/issues/160))
- Fix to function `ghncd_split_vars()` to not fail on
  [`dplyr::contains`](https://tidyselect.r-lib.org/reference/starts_with.html)
  call ([\#156](https://github.com/ropensci/rnoaa/issues/156)) thanks
  [@lawinslow](https://github.com/lawinslow) !

## rnoaa 0.5.6

CRAN release: 2016-05-05

#### MINOR IMPROVEMENTS

- Fixes for new `httr` version to call encoding explicitly
  ([\#135](https://github.com/ropensci/rnoaa/issues/135))
- Fix to broken link for reference to source code used in `gefs`
  functions ([\#121](https://github.com/ropensci/rnoaa/issues/121))
- Speed ups implemented for the
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) function -
  it’s a time consuming task as we have to parse a nasty string of
  characters line by line - more speed ups to come in future versions
  ([\#146](https://github.com/ropensci/rnoaa/issues/146))
- Replace `dplyr::rbind_all()` with
  [`dplyr::bind_rows()`](https://dplyr.tidyverse.org/reference/bind_rows.html)
  as the former is being deprecated
  ([\#152](https://github.com/ropensci/rnoaa/issues/152))

#### BUG FIXES

- Fix for [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)
  function - was failing on some station names that had leading zeros.
  ([\#136](https://github.com/ropensci/rnoaa/issues/136))
- Fix for
  [`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md) -
  used to allow more than one station id to be passed in, but internally
  only handled one. This is a restriction due to the NOAA NCDC API.
  Documentation now shows an example of how to deal with many station
  ids ([\#138](https://github.com/ropensci/rnoaa/issues/138))
- Fixes to the suite of `ncdc_*()` functions to allow multiple inputs to
  those parameters where allowed
  ([\#139](https://github.com/ropensci/rnoaa/issues/139))
- Fixed bug in
  [`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md)
  due to new `ggplot2` version
  ([\#153](https://github.com/ropensci/rnoaa/issues/153))
- Fixed bugs in `argo()` functions: a) with new `httr`, box input of a
  vector no longer works, now manually make a character vector; b)
  errant file param being passed into the http request, removed
  ([\#155](https://github.com/ropensci/rnoaa/issues/155))

## rnoaa 0.5.2

CRAN release: 2016-01-26

#### NEW FEATURES

- New data source added: ARGO buoy data. See functions starting with
  `argo()` ([\#123](https://github.com/ropensci/rnoaa/issues/123)) for
  more, see <http://www.argo.ucsd.edu/>
- New data source added: CO-OPS tide and current data. See function
  [`coops_search()`](https://docs.ropensci.org/rnoaa/reference/coops.md)
  ([\#111](https://github.com/ropensci/rnoaa/issues/111)) for idea from
  [@fmichonneau](https://github.com/fmichonneau)
  ([\#124](https://github.com/ropensci/rnoaa/issues/124)) for
  implementing [@jsta](https://github.com/jsta) also
  ([\#126](https://github.com/ropensci/rnoaa/issues/126))
  ([\#128](https://github.com/ropensci/rnoaa/issues/128))

#### MINOR IMPROVEMENTS

- `rgdal` moved to Suggests to make usage easier
  ([\#125](https://github.com/ropensci/rnoaa/issues/125))
- Changes to
  [`ncdc_plot()`](https://docs.ropensci.org/rnoaa/reference/ncdc_plot.md) -
  made default brakes to just default to what `ggplot2` does, but you
  can still pass in your own breaks
  ([\#131](https://github.com/ropensci/rnoaa/issues/131))

## rnoaa 0.5.0

CRAN release: 2015-12-02

#### NEW FEATURES

- New data source added: NOAA Global Ensemble Forecast System (GEFS)
  data. See functions
  [`gefs()`](https://docs.ropensci.org/rnoaa/reference/gefs-defunct.md),
  [`gefs_dimension_values()`](https://docs.ropensci.org/rnoaa/reference/gefs_dimension_values-defunct.md),
  [`gefs_dimensions()`](https://docs.ropensci.org/rnoaa/reference/gefs_dimensions-defunct.md),
  [`gefs_latitudes()`](https://docs.ropensci.org/rnoaa/reference/gefs_latitudes-defunct.md),
  [`gefs_longitudes()`](https://docs.ropensci.org/rnoaa/reference/gefs_longitudes-defunct.md),
  and
  [`gefs_variables()`](https://docs.ropensci.org/rnoaa/reference/gefs_variables-defunct.md)
  ([\#106](https://github.com/ropensci/rnoaa/issues/106))
  ([\#119](https://github.com/ropensci/rnoaa/issues/119)) thanks
  [@potterzot](https://github.com/potterzot) - he’s now an author too
- New data source added: NOAA Extended Reconstructed Sea Surface
  Temperature (ERSST) data. See function
  [`ersst()`](https://docs.ropensci.org/rnoaa/reference/ersst.md)
  ([\#96](https://github.com/ropensci/rnoaa/issues/96))
- New function
  [`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md)
  to get ISD station data.
- Added code of conduct to code repository

#### MINOR IMPROVEMENTS

- Swapped `ncdf` package for `ncdf4` package. Windows binaries weren’t
  availiable for `ncdf4` prior to now.
  ([\#117](https://github.com/ropensci/rnoaa/issues/117))
- Proper license info added for javascript modules used inside the
  package ([\#116](https://github.com/ropensci/rnoaa/issues/116))
- Improvements to
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) function
  to do transformations of certain variables to give back data that
  makes more sense
  ([\#115](https://github.com/ropensci/rnoaa/issues/115))
- `leaflet`, `geojsonio`, and `lawn` added in Suggests, used in a few
  functions.
- Note added to
  [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md) function
  man page that the `nldn` dataset is available to military users only
  ([\#107](https://github.com/ropensci/rnoaa/issues/107))

#### BUG FIXES

- Fix to [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md)
  function to accept character class inputs for the `buoyid` parameter.
  the error occurred because matching was not case-insensitive, now
  works regardless of case
  ([\#118](https://github.com/ropensci/rnoaa/issues/118))
- Fixes for new `ggplot2` version
  ([\#113](https://github.com/ropensci/rnoaa/issues/113))
- Built in `GET` request retries for `ghncd` functions as some URLs fail
  unpredictably ([\#110](https://github.com/ropensci/rnoaa/issues/110))

## rnoaa 0.4.2

CRAN release: 2015-07-08

#### MINOR IMPROVEMENTS

- Explicitly import non-base R pkg functions, so importing from `utils`,
  `methods`, and `stats`
  ([\#103](https://github.com/ropensci/rnoaa/issues/103))
- All NCDC legacy API functions are now defunct. See `?rnoaa-defunct`
  for more information
  ([\#104](https://github.com/ropensci/rnoaa/issues/104))
- `radius` parameter removed from
  [`ncdc_stations()`](https://docs.ropensci.org/rnoaa/reference/ncdc_stations.md)
  function ([\#102](https://github.com/ropensci/rnoaa/issues/102)), was
  already removed internally within the function in the last version,
  now not in the function definition, see also
  ([\#98](https://github.com/ropensci/rnoaa/issues/98)) and
  ([\#99](https://github.com/ropensci/rnoaa/issues/99))
- Dropped `plyr` and `data.table` from imports.
  [`plyr::rbind.fill()`](https://rdrr.io/pkg/plyr/man/rbind.fill.html)
  and
  [`data.table::rbindlist()`](https://rdrr.io/pkg/data.table/man/rbindlist.html)
  replaced with
  [`dplyr::bind_rows()`](https://dplyr.tidyverse.org/reference/bind_rows.html).

#### BUG FIXES

- Fixed problem with `httr` `v1` where empty list not allowed to pass to
  the `query` parameter in `GET`
  ([\#101](https://github.com/ropensci/rnoaa/issues/101))

## rnoaa 0.4.0

CRAN release: 2015-06-19

#### NEW FEATURES

- Gains a suite of new functions for working with NOAA GHCND data,
  including
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md),
  `ghcnd_clear_cache()`,
  [`ghcnd_countries()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md),
  [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md),
  [`ghcnd_splitvars()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_splitvars.md)
  [`ghcnd_states()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md),
  [`ghcnd_stations()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_stations.md),
  and
  [`ghcnd_version()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_states.md)
  ([\#85](https://github.com/ropensci/rnoaa/issues/85))
  ([\#86](https://github.com/ropensci/rnoaa/issues/86))
  ([\#87](https://github.com/ropensci/rnoaa/issues/87))
  ([\#88](https://github.com/ropensci/rnoaa/issues/88))
  ([\#94](https://github.com/ropensci/rnoaa/issues/94))
- New contributor Adam Erickson
  ([@DougFirErickson](https://github.com/DougFirErickson))
- All NOAA buoy functions put back into the package. They were
  previously on a separate branch in the GitHub repository.
  ([\#37](https://github.com/ropensci/rnoaa/issues/37))
  ([\#71](https://github.com/ropensci/rnoaa/issues/71))
  ([\#100](https://github.com/ropensci/rnoaa/issues/100))

#### MINOR IMPROVEMENTS

- Minor adjustments to
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) functions,
  including better man file.
- Cleaner package imports - importing mostly only functions used in
  dependencies.
- Startup message gone.
- `callopts` parameter changed to `...` in function
  [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md).
- More robust test suite.
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) requires
  that users do their own paging - previously this was done internally
  ([\#77](https://github.com/ropensci/rnoaa/issues/77))
- Many dependencies dropped, simplifying package: `RCurl`, `maptools`,
  `stringr`, `digest`. A few new ones added: `dplyr`, `tidyr`.

#### DEPRECATED AND DEFUNCT

- All `erddap` functions now defunct - see the package
  [rerddap](https://github.com/ropensci/rerddap), a general purpose R
  client for ERDDAP servers.
  ([\#51](https://github.com/ropensci/rnoaa/issues/51))
  ([\#73](https://github.com/ropensci/rnoaa/issues/73))
  ([\#90](https://github.com/ropensci/rnoaa/issues/90))
  ([\#95](https://github.com/ropensci/rnoaa/issues/95))
- The `extent` function in `noaa_stations()` used to accept either a
  bounding box or a point defined by lat/long. The lat/long option
  dropped as it required two packages, one of which is a pain to install
  for many users ([\#98](https://github.com/ropensci/rnoaa/issues/98))
  ([\#99](https://github.com/ropensci/rnoaa/issues/99))

## rnoaa 0.3.3

CRAN release: 2014-12-20

#### NEW FEATURES

- New data source NOAA legacy API with ISD, daily, and ish data via
  function `ncdc_legacy()`.
  ([\#54](https://github.com/ropensci/rnoaa/issues/54))
- New function
  [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md) to get ISD
  data from NOAA FTP server.
  ([\#76](https://github.com/ropensci/rnoaa/issues/76))
- ERDDAP gridded data sets added. Now tabledap datasets are accessible
  via `erddap_table()`, while gridded datasets are available via
  `erddap_grid()`. Helper function `erddap_search()` was modified to
  search for either tabledap or griddap datasets, and `erddap_info()`
  gets and prints summary information differently for tabledap and
  griddap datasets.
  ([\#63](https://github.com/ropensci/rnoaa/issues/63))

#### MINOR IMPROVEMENTS

- `erddap_data()` defunct, now as functions `erddap_table()` and
  `erddap_grid()`, uses new `store` parameter which takes a function,
  either `disk(path, overwrite)` to store on disk or `memory()` to store
  in R memory.
- `assertthat` library removed, replaced with
  [`stopifnot()`](https://rdrr.io/r/base/stopifnot.html)

## rnoaa 0.3.0

#### NEW FEATURES

- New data source added (NOAA torndoes data) via function
  [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md).
  ([\#56](https://github.com/ropensci/rnoaa/issues/56))
- New data source added (NOAA storm data from IBTrACS) via functions
  `storm_*()`. ([\#57](https://github.com/ropensci/rnoaa/issues/57))
- New data source added (NOAA weather station metadata from HOMR) via
  functions `homr_*()`
  ([\#59](https://github.com/ropensci/rnoaa/issues/59))
- New vignettes for storm data and homr data.
- Some functions in rnoaa now print data.frame outputs as `dplyr`-like
  outputs with a summary of the data.frame, as appropriate.

#### MINOR IMPROVEMENTS

- Across all `ncdc_*` functions changed `callopts` parameter to `...`.
  This parameter allow you to pass in options to
  [`httr::GET`](https://httr.r-lib.org/reference/GET.html) to modify
  curl requests. ([\#61](https://github.com/ropensci/rnoaa/issues/61))
- A new helper function `check_key()` looks for one of two stored keys,
  as an environment variable under the name `NOAA_KEY`, or an option
  variable under the name `noaakey`. Environment variables can be set
  during session like `Sys.setenv(VAR = "...")`, or stored long term in
  your `.Renviron` file. Option variables can be set during session like
  `options(var = "...")`, or stored long term in your `.Rprofile` file.
- `is.*` and `print.*` functions no longer have public man files, but
  can be seen via `rnoaa:::` if needed.

## rnoaa 0.2.0

CRAN release: 2014-07-21

#### NEW FEATURES

- New package imports: `sp`, `rgeos`, `assertthat`, `jsonlite`, and
  `ncdf4`, and new package Suggests: `knitr`, `taxize`
- Most function names changed. All `noaa*()` functions for NCDC data
  changed to `ncdc*()`. `noaa_buoy()` changed to
  [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md).
  `noaa_seaice()` changed to `seaice()`. When you call the old versions
  an error is thrown, with a message pointing you to the new function
  name. See ?rnoaa-defunct.
- New vignettes: NCDC attributes, NCDC workflow, Seaice vignette, SWDI
  vignette, ERDDAP vignette, NOAA buoy vignette.
- New functions to interact with NOAA ERDDAP data: `erddap_info()`,
  `erddap_data()`, and `erddap_search()`.
- New functions to interact with NOAA buoy data:
  [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md),
  including a number of helper functions.
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) now
  splits apart attributes. Previously, the attributes were returned as a
  single column, but now there is column for each attribute so data can
  be easily retrieved. Attribute columns differ for each different
  `datasetid`.
- [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md) function
  has been removed from the CRAN version of `rnoaa`. Install the version
  with [`buoy()`](https://docs.ropensci.org/rnoaa/reference/buoy.md) and
  associated functions via
  `devtools::install_github("ropensci/rnoaa", ref="buoy")`

#### MINOR IMPROVEMENTS

- `noaa_swdi()` (function changed to
  [`swdi()`](https://docs.ropensci.org/rnoaa/reference/swdi.md)) gains
  new parameter `filepath` to specify path to write a file to if
  `format=kmz` or `format=shp`. Examples added for using `format=` csv,
  shp, and kmz.
- Now using internal version of
  [`plyr::compact`](https://rdrr.io/pkg/plyr/man/compact.html).
- Added API response checker/handler to all functions to pass on helpful
  messages on server errors.
- [`ncdc()`](https://docs.ropensci.org/rnoaa/reference/ncdc.md) gains
  new parameter `includemetadata`. If TRUE, includes metadata, if not,
  does not, and response should be faster as does not take time to
  calculate metadata.
- `noaa_stations()` gains new parameter `radius`. If `extent` is a
  vector of length 4 (for a bounding box) then radius is ignored, but if
  you pass in two points to `extent`, it is interpreted as a point, and
  then `radius` is used as the distance upon which to construct a
  bounding box. `radius` default is 10 km.

#### BUG FIXES

- `datasetid`, `startdate`, and `enddate` are often required parameters,
  and changes were made to help users with this.

## rnoaa 0.1.0

CRAN release: 2014-03-03

#### NEW FEATURES

- Submitted to CRAN.

## rnoaa 0.0.8

#### NEW FEATURES

- Wrote new functions for NOAA API v2.
- A working vignette now.

## rnoaa 0.0.1

#### NEW FEATURES

- Wrappers for NOAA API v1 were written, not on CRAN at this point.
