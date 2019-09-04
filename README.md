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







