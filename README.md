
# staplr <img src="logo.png" align="right" height="150"/>

[![Project Status: Active - The project has reached a stable, usable
state and is being actively
developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![Licence](https://img.shields.io/badge/licence-GPL--3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)
[![Build
Status](https://travis-ci.org/pridiltal/staplr.svg?branch=master)](https://travis-ci.org/pridiltal/staplr)

-----

[![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/staplr)](https://cran.r-project.org/package=staplr)
[![packageversion](https://img.shields.io/badge/Package%20version-1.1.0-orange.svg?style=flat-square)](commits/master)

-----

[![Last-changedate](https://img.shields.io/badge/last%20change-2018--03--23-yellowgreen.svg)](/commits/master)

<!-- README.md is generated from README.Rmd. Please edit that file -->

# staplr

This package provides functions to manipulate PDF files:

    - merge multiple PDF files: staple_pdf()
    - splits single input PDF file into individual pages: split_pdf()
    - remove selected pages from a file: remove_pages()
    - rename multiple files in a directory: rename_files()
    - fill out PDF forms: get_fields() and set_fields()

This package is still under development and this repository contains a
development version of the R package *staplr*.

## Installation

#### First Install pdftk

download and install
[pdftk](https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/) NB: this
is not an R package\!

#### Then Install staplr

You can install the stable version from CRAN.

``` r
install.packages('staplr', dependencies = TRUE)
```

You can install staplr from github with:

``` r
# install.packages("devtools")
devtools::install_github("pridiltal/staplr")
```

## Example

``` r
library(staplr)
# Merge multiple PDF files into one
staple_pdf()

# This command promts the user to select the file interactively. 
# Remove page 2 and 3 from the selected file.
remove_pages(rmpages = c(2,3))

# This function splits a single input PDF document into individual pages
split_pdf()

# This function writes renamed files back to directory
#if the directory contains 3 PDF files
rename_files(new_names = paste("file",1:3))

# These functions are to fill out pdf forms
get_fields() 
set_fields()
# This includes 2 external functions `get_fields` and `set_fields` 
# and files to use as examples.
# This is what the example file looks like
```

![image](https://user-images.githubusercontent.com/6352379/37745585-bc7bb8e8-2d32-11e8-918c-e52a0a549118.png)

``` r
# If you get path to this file by
pdfFile = system.file('testForm.pdf',package = 'staplr')

# And do
fields = get_fields(pdfFile)
# You'll get a list of fields that the pdf contains 
# along with some additional information about the fields.

# You make modifications in any of the fields by
fields$TextField1$value = 'this is text'
set_fields(pdfPath, 'newFile.pdf', fields)

# This will create a filled pdf file
```

![image](https://user-images.githubusercontent.com/6352379/37745838-65986038-2d34-11e8-9d16-5d6514ef24ab.png)

## References

  - <https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/>
