# rnoaa options

rnoaa options

## Usage

``` r
rnoaa_options(cache_messages = TRUE)
```

## Arguments

- cache_messages:

  (logical) whether to emit messages with information on caching status
  for function calls that can cache data. default: `TRUE`

## Details

rnoaa package level options; stored in an internal package environment
`roenv`

## See also

[rnoaa_caching](https://docs.ropensci.org/rnoaa/reference/rnoaa_caching.md)
for managing cached files

## Examples

``` r
if (FALSE) { # \dontrun{
rnoaa_options(cache_messages = FALSE)
} # }
```
