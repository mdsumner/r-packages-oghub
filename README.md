# R package

Here is a quick introduction to creating R packages. 

Please install first

```R
install.packages("remotes") 
remotes::install_cran(c("devtools", "roxygen2", "testthat", "spelling", "usethis"))

```

R functions

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
* Resources, R Packages book

# Step 1

This is the hardest part. 

What is your package *name*?  


"mypackage"   ## no underscores, dots, spaces, dashes, profanity, etc. 




# Step 2

Create the package skeleton. Open this as a project with RStudio if you like. 

Running this code will automatically open it as a project. 

```R
usethis::create_package("mypackage")
```

# Step 3

Put your R code into R files in  `R/files.R`

# Step 4

Fill out the DESCRIPTION file and document the functions. 

# Step 5

Build the package, use `devtools::load_all()`, `devtools::build()`, `devtools::check()`. 

# Optional, put package on Github

Requires Git installed. See the [R Packages book](http://r-pkgs.had.co.nz/) for details. 

* Create a repository on Github
* Initiate Git in your project, link it to Github repository




