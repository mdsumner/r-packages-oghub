# R packages

Here is a quick introduction to creating R packages. 

## Preparation

Please install first

```R
if (!requireNamespace("remotes")) install.packages("remotes") 
remotes::install_cran(c("devtools", "roxygen2", "testthat", "spelling", "usethis", "pkgdown"))

```

## Code for a package 

Please use your own functions in a new package you create, but you may use one or all three of these example functions. 

R functions - put these into R/files.R, can be separate files or just in one file - personal choice. 

```R
# assigns numbers as names to columns of a data frame
give_col_numbers <- function(x, prefix = "col."){
  names(x) <- paste0(prefix, seq(1,ncol(x), 1))
  return(x)
}

# convert integers into bit format
int_2_bit <- function(x, bit.type = 8) { 
  x <- list(x)
  l <- lapply(x, function(y) as.integer(intToBits(y)[bit.type:1]))
  return(l)
}

# function to calculate Mean Square Error
mse <- function(predicted, observed) {
 mean((predicted - observed)**2, na.rm = T)   
 }
```

# Overview

* Contents of a package
* Tools for package creation
* See the [R Packages book](http://r-pkgs.had.co.nz/) for details. 
* Use the `usethis` package to work through all the boring details
* Use the `devtools` package to develop and test your package

# Step 1 - name

This is the hardest part. 

What is your package *name*?  
"zooperdanke"   ## no underscores, dots, spaces, dashes, profanity, etc. 

# Step 2 - create package folder and parts

Create the package skeleton. Open this as a project with RStudio if you like. 

Running this code will automatically open it as a project. 

```R
usethis::create_package("mypackage")
```

# Step 3 - add code

Put your R code into R files in  `R/files.R`

# Step 4 - package metadata and doc

Fill out the [DESCRIPTION file](http://r-pkgs.had.co.nz/description.html). 

[Document the functions](http://r-pkgs.had.co.nz/man.html) by using [roxygen2](https://roxygen2.r-lib.org/) putting the documentation right next to the code in the .R files. 

* Consider use of the [RMarkdown formatting](https://cran.r-project.org/web/packages/roxygen2/vignettes/markdown.html) for R documentation, to enable this run
* **VERY IMPORTANT:** if using RStudio, go to Tools/Project Options/ - set "Generate documentation with roxygen2" in Build Tools. 


```R
usethis::use_roxygen_md()
```


# Step 5 - build and use

Build the package, use `devtools::load_all()`, `devtools::build()`, `devtools::check()`. 

# Step 6 - formal testing

Write tests with [testthat](https://testthat.r-lib.org/). 


# Optional, put package on Github

Requires Git installed. See the [R Packages book](http://r-pkgs.had.co.nz/) for details. 

* Create a repository on Github
* Initiate Git in your project, link it to Github repository




