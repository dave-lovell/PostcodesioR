PostcodesioR
================

# PostcodesioR <img src='man/figures/logo.png' align="right" height="139" />

[![Travis-CI Build
Status](https://travis-ci.org/ropensci/PostcodesioR.svg?branch=master)](https://travis-ci.org/ropensci/PostcodesioR)
[![Package-License](https://img.shields.io/badge/license-GPL--3-brightgreen.svg?style=flat)](https://www.gnu.org/licenses/gpl-3.0.html)
[![](https://badges.ropensci.org/176_status.svg)](https://github.com/ropensci/software-review/issues/176)
[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/)
[![CRAN_Status_Badge](https://www.r-pkg.org/badges/version/PostcodesioR)](https://cran.r-project.org/package=PostcodesioR)
[![DOI](https://joss.theoj.org/papers/10.21105/joss.05334/status.svg)](https://doi.org/10.21105/joss.05334)
![Downloads](https://cranlogs.r-pkg.org/badges/grand-total/PostcodesioR)

An API wrapper around [postcodes.io](https://postcodes.io/) - free UK
postcode lookup and geocoder. This package helps to find and transform
information about UK administrative geography like postcodes, LSOA,
MSOA, constituencies, counties, wards, districts, CCG or NUTS.

The package is based exclusively on open data provided by postcodes.io.
PostcodesioR can be used by data scientists or social scientists working
with geocoded UK data. A common task when working with such data is
aggregating geocoded data on different administrative levels,
e.g. turning postcode-level data into counties or regions. This package
can help in achieving this and in many other cases when changing the
aggregation of geographic data is required.

## Installation

This package can be installed from GitHub (developmental version) or
CRAN (stable).

In order to install PostcodesioR use one of the following commands:

``` r
# stable version
install.packages("PostcodesioR")
```

or

``` r
# developmental version
if(!require("devtools")) {
  install.packages("devtools")
}
devtools::install_github("ropensci/PostcodesioR")
```

## Loading

Load the package by typing

``` r
library(PostcodesioR)
```

## Examples

Where possible, I tried to return a data frame. Unfortunately, a lot of
API calls return more complex data and in those cases it is safer to use
lists. The API limits the number of returned calls. Check functions’
documentation for more details.

For additional information about the returned data and the function
calls see the original [documentation](https://postcodes.io/docs).

The main function of this package provides information related to a
given postcode

``` r
lookup_result <- postcode_lookup("EC1Y8LX")

#overview
str(lookup_result)
```

    ## 'data.frame':    1 obs. of  38 variables:
    ##  $ postcode                       : chr "EC1Y 8LX"
    ##  $ quality                        : int 1
    ##  $ eastings                       : int 532544
    ##  $ northings                      : int 182128
    ##  $ country                        : chr "England"
    ##  $ nhs_ha                         : chr "London"
    ##  $ longitude                      : num -0.0909
    ##  $ latitude                       : num 51.5
    ##  $ european_electoral_region      : chr "London"
    ##  $ primary_care_trust             : chr "Islington"
    ##  $ region                         : chr "London"
    ##  $ lsoa                           : chr "Islington 023D"
    ##  $ msoa                           : chr "Islington 023"
    ##  $ incode                         : chr "8LX"
    ##  $ outcode                        : chr "EC1Y"
    ##  $ parliamentary_constituency     : chr "Islington South and Finsbury"
    ##  $ admin_district                 : chr "Islington"
    ##  $ parish                         : chr "Islington, unparished area"
    ##  $ admin_county                   : logi NA
    ##  $ date_of_introduction           : chr "198001"
    ##  $ admin_ward                     : chr "Bunhill"
    ##  $ ced                            : logi NA
    ##  $ ccg                            : chr "NHS North Central London"
    ##  $ nuts                           : chr "Haringey and Islington"
    ##  $ pfa                            : chr "Metropolitan Police"
    ##  $ admin_district_code            : chr "E09000019"
    ##  $ admin_county_code              : chr "E99999999"
    ##  $ admin_ward_code                : chr "E05013699"
    ##  $ parish_code                    : chr "E43000209"
    ##  $ parliamentary_constituency_code: chr "E14000764"
    ##  $ ccg_code                       : chr "E38000240"
    ##  $ ccg_id_code                    : chr "93C"
    ##  $ ced_code                       : chr "E99999999"
    ##  $ nuts_code                      : chr "TLI43"
    ##  $ lsoa_code                      : chr "E01002704"
    ##  $ msoa_code                      : chr "E02000576"
    ##  $ lau2_code                      : chr "E09000019"
    ##  $ pfa_code                       : chr "E23000001"

Check the
[vignette](https://docs.ropensci.org/PostcodesioR/articles/Introduction.html)
to see all functions in action.

## Citation

Please cite this package if it is used in a publication

`Walczak, E. J., (2023). PostcodesioR: An R package for UK geocoding. Journal of Open Source Software, 8(84), 5334, https://doi.org/10.21105/joss.05334`

BibTeX entry is here:

``` latex
@article{postcodesior:2023,
  title = {{PostcodesioR: An R package for UK geocoding}},
  author = {Eryk J. Walczak},
  journal = {Journal of Open Source Software},
  volume = {8},
  number = {84},
  pages = {5334},
  year = {2023},
  doi = {10.21105/joss.05334},
  note = {R package version 0.3.1},
  url = {https://cran.r-project.org/web/packages/PostcodesioR/},
}
```

## Notes

Currently, there is a limit to the number of API calls that can be made.
However, [postcodes.io](https://postcodes.io/) provides full list of
geolocation data that can be used locally without limitations. The
original data is sourced from [Office for National Statistics Data
Portal](https://geoportal.statistics.gov.uk/). That
[file](https://github.com/ideal-postcodes/postcodes.io/blob/master/latest)
is rather large so I didn’t include it in the package.

Go to the package’s [website](https://docs.ropensci.org/PostcodesioR/)
or to my [blog](https://walczak.org/tag/postcodesior/) for more
examples.

## Code of Conduct

Please note that this project is released with a [Contributor Code of
Conduct](https://github.com/ropensci/PostcodesioR/blob/master/CONDUCT.md).
By participating in this project you agree to abide by its terms.

[![ropensci_footer](https://ropensci.org/public_images/ropensci_footer.png)](https://ropensci.org)
