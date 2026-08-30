# Split variables in data returned from `ghcnd`

This function is a helper function for
[`ghcnd_search()`](https://docs.ropensci.org/rnoaa/reference/ghcnd_search.md).
It helps with cleaning up the data returned from
[`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md), to get
it in a format that is easier to work with.

## Usage

``` r
ghcnd_splitvars(x)
```

## Arguments

- x:

  An object returned from
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)

## Note

See [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)
examples

## Author

Scott Chamberlain, Adam Erickson, Elio Campitelli
