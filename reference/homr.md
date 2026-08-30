# Historical Observing Metadata Repository (HOMR) station metadata

Historical Observing Metadata Repository (HOMR) station metadata

## Usage

``` r
homr(
  qid = NULL,
  qidMod = NULL,
  station = NULL,
  state = NULL,
  county = NULL,
  country = NULL,
  name = NULL,
  nameMod = NULL,
  platform = NULL,
  date = NULL,
  begindate = NULL,
  enddate = NULL,
  headersOnly = FALSE,
  phrData = NULL,
  combine = FALSE,
  ...
)
```

## Arguments

- qid:

  One of COOP, FAA, GHCND, ICAO, NCDCSTNID, NWSLI, TRANS, WBAN, or WMO,
  or any of those plus `a-z0-9`, or just `a-z0-9`. (qid = qualified ID)

- qidMod:

  (character) One of: is, starts, ends, contains. Specifies how the ID
  portion of the qid parameter should be applied within the search. If a
  qid is passed but the qidMod parameter is not used, qidMod is assumed
  to be IS.

- station:

  (character) A station id.

- state:

  (character) A two-letter state abbreviation. Two-letter code for US
  states, Canadian provinces, and other Island areas.

- county:

  (character) A two letter county code. US county names, best used with
  a state identifier.

- country:

  (character) A two letter country code. See here for a list of valid
  country names.

- name:

  (character) One of `0-9A-Z+`. Searches on any type of name we have for
  the station.

- nameMod:

  (character) `is|starts|ends|contains`. Specifies how the name
  parameter should be applied within the search. If a name is passed but
  the nameMod parameter is not used, nameMod is assumed to be IS.

- platform:

  (character) (aka network)
  `ASOS|USCRN|USHCN|NEXRAD|AL USRCRN|USRCRN|COOP`. Limit the search to
  stations of a certain platform/network type.

- date:

  (character) `YYYY-MM-DD|all` Limits values to only those that occurred
  on a specific date. Alternatively, date=all will return all values for
  matched stations. If this field is omitted, the search will return
  only the most recent values for each field.

- begindate, enddate:

  `YYYY-MM-DD`. Limits values to only those that occurred within a date
  range.

- headersOnly:

  (logical) Returns only minimal information for each station found
  (NCDC Station ID, Preferred Name, Station Begin Date, and Station End
  Date), but is much quicker than a full query. If you are performing a
  search that returns a large number of stations and intend to choose
  only one from that list to examine in detail, headersOnly may give you
  enough information to find the NCDC Station ID for the station that
  you actually want.

- phrData:

  (logical) The HOMR web service now includes PHR (element-level) data
  when available, in an elements section. Because of how this data is
  structured, it can substantially increase the size of any result which
  includes it. If you don't need this data you can omit it by including
  phrData=false. If the parameter is not set, it will default to
  phrData=true.

- combine:

  (logical) Combine station metadata or not.

- ...:

  Curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)
  (optional)

## Value

A list, with elements named by the station ids.

## Details

Since the definitions for variables are always the same, we don't
include the ability to get description data in this function. Use
[`homr_definitions()`](https://docs.ropensci.org/rnoaa/reference/homr_definitions.md)
to get descriptions information.

## References

https://www.ncdc.noaa.gov/homr/api

## Examples

``` r
if (FALSE) { # \dontrun{
homr(qid = 'COOP:046742')
homr(qid = ':046742')
homr(qidMod='starts', qid='COOP:0467')
homr(headersOnly=TRUE, state='DE')
homr(headersOnly=TRUE, country='GHANA')
homr(headersOnly=TRUE, state='NC', county='BUNCOMBE')
homr(name='CLAYTON')
res <- homr(state='NC', county='BUNCOMBE', combine=TRUE)
res$id
res$head
res$updates
homr(nameMod='starts', name='CLAY')
homr(headersOnly=TRUE, platform='ASOS')
homr(qid='COOP:046742', date='2011-01-01')
homr(qid='COOP:046742', begindate='2005-01-01', enddate='2011-01-01')
homr(state='DE', headersOnly=TRUE)
homr(station=20002078)
homr(station=20002078, date='all', phrData=FALSE)

# Optionally pass in curl options
homr(headersOnly=TRUE, state='NC', county='BUNCOMBE', verbose = TRUE)
} # }
```
