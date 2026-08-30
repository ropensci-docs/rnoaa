# Get meta-data on the GHCND daily data

These function allow you to pull the current versions of certain
meta-datasets for the GHCND, including lists of country and state
abbreviations used in some of the weather station IDs and information
about the current version of the data.

## Usage

``` r
ghcnd_states(...)

ghcnd_countries(...)

ghcnd_version(...)
```

## Arguments

- ...:

  In the case of
  [`ghcnd()`](https://docs.ropensci.org/rnoaa/reference/ghcnd.md)
  additional curl options to pass through to
  [crul::HttpClient](https://docs.ropensci.org/crul/reference/HttpClient.html).
  In the case of `ghcnd_read` further options passed on to `read.csv`

## Details

Functions:

- `ghcnd_version`: Get current version of GHCND data

- `ghcnd_states`: Get US/Canada state names and 2-letter codes

- `ghcnd_countries`: Get country names and 2-letter codes

## Author

Scott Chamberlain <myrmecocystus@gmail.com>, Adam Erickson
<adam.erickson@ubc.ca>

## Examples

``` r
if (FALSE) { # \dontrun{
ghcnd_states()
ghcnd_countries()
ghcnd_version()
} # }
```
