# Local Climatological Data from NOAA

Local Climatological Data from NOAA

## Usage

``` r
lcd(station, year, col_types = NULL, ...)
```

## Arguments

- station:

  (character) station code, e.g., "02413099999". we will allow
  integer/numeric passed here, but station ids can have leading zeros,
  so it's a good idea to keep stations as character class. required

- year:

  (integer) year, e.g., 2017. required

- col_types:

  (named character vector) defaults to NULL. Use this argument to change
  the returned column type. For example,"character" instead of
  "numeric". See or use
  [lcd_columns](https://docs.ropensci.org/rnoaa/reference/lcd_columns.md)
  to create a named vector with allowed column names. If the user
  specified type is not compatible, the function will choose a type
  automatically and raise a message. optional

- ...:

  curl options passed on to
  [crul::verb-GET](https://docs.ropensci.org/crul/reference/verb-GET.html)

## Value

a data.frame with many columns. the first 10 are metadata:

- station

- date

- latitude

- longitude

- elevation

- name

- report_type

- source

And the rest should be all data columns. The first part of many column
names is the time period, being one of:

- hourly

- daily

- monthly

- shortduration

So the variable you are looking for may not be the first part of the
column name

## Note

See
[lcd_cache](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## References

Docs:
https://www.ncei.noaa.gov/data/local-climatological-data/doc/LCD_documentation.pdf
Data comes from:
https://www.ncei.noaa.gov/data/local-climatological-data/access

## Examples

``` r
if (FALSE) { # \dontrun{
x = lcd(station = "01338099999", year = 2017)
lcd(station = "01338099999", year = 2015)
lcd(station = "02413099999", year = 2009)
lcd(station = "02413099999", year = 2001)

# pass curl options
lcd(station = "02413099999", year = 2002, verbose = TRUE)
} # }
```
