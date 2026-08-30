# Restructure element of ghcnd_search list

This function restructures the output of
[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)
to add a column giving the variable name (`key`) and change the name of
the variable column to `value`. These changes facilitate combining all
elements from the list created by
[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md),
to create a tidy dataframe of the weather observations from the station.

## Usage

``` r
meteo_tidy_ghcnd_element(x, keep_flags = FALSE)
```

## Arguments

- x:

  A dataframe with daily observations for a single monitor for a single
  weather variable. This dataframe is one of the elements returned by
  [`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md)

- keep_flags:

  TRUE / FALSE for whether the user would like to keep all the flags for
  each weather variable. The default is to not keep the flags (FALSE).
  See the note below for more information on these flags.

## Value

A dataframe reformatted to allow easy aggregation of all weather
variables for a single monitor.

## Author

Brooke Anderson <brooke.anderson@colostate.edu>
