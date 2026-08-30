# rnoaa caching

Manage data caches

## Details

To get the cache directory for a data source, see the method
`x$cache_path_get()`

`cache_delete` only accepts 1 file name, while `cache_delete_all`
doesn't accept any names, but deletes all files. For deleting many
specific files, use `cache_delete` in a
[`lapply()`](https://rdrr.io/r/base/lapply.html) type call

Note that cached files will continue to be used until they are deleted.
It's possible to run into problems when changes happen in your R setup.
For example, at least one user reported changing versions of this
package and running into problems because a cached data file from a
previous version of rnoaa did not work with the newer version of rnoaa.
You should occasionally delete all cached files.

## Useful user functions

Assuming x is a `HoardClient` class object, e.g., `lcd_cache`

- `x$cache_path_get()` get cache path

- `x$cache_path_set()` set cache path

- `x$list()` returns a character vector of full path file names

- `x$files()` returns file objects with metadata

- `x$details()` returns files with details

- `x$delete()` delete specific files

- `x$delete_all()` delete all files, returns nothing

## Caching objects for each data source

- [`isd()`](https://docs.ropensci.org/rnoaa/reference/isd.md)/[`isd_stations()`](https://docs.ropensci.org/rnoaa/reference/isd_stations.md):
  `isd_cache`

- [`cpc_prcp()`](https://docs.ropensci.org/rnoaa/reference/cpc_prcp.md):
  `cpc_cache`

- [`arc2()`](https://docs.ropensci.org/rnoaa/reference/arc2.md):
  `arc2_cache`

- [`lcd()`](https://docs.ropensci.org/rnoaa/reference/lcd.md):
  `lcd_cache`

- [`bsw()`](https://docs.ropensci.org/rnoaa/reference/bsw.md):
  `bsw_cache`

- [`ersst()`](https://docs.ropensci.org/rnoaa/reference/ersst.md):
  `ersst_cache`

- [`tornadoes()`](https://docs.ropensci.org/rnoaa/reference/tornadoes.md):
  `torn_cache`

- [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)/[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md):
  `ghcnd_cache`

- [`se_data()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md)/[`se_files()`](https://docs.ropensci.org/rnoaa/reference/storm_events.md):
  `stormevents_cache`

## See also

[`rnoaa_options()`](https://docs.ropensci.org/rnoaa/reference/rnoaa_options.md)
for managing whether you see messages about cached files when you
request data
