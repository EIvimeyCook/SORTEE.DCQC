<p align="center">
  <img src="https://github.com/SORTEE/DCQC/blob/main/inst/DCQC/www/circle_black.png" width = "200"/>
</p>

<div align="center">
 <h1>DCQC</h1>
</div>

## Installation
Currently the DCQC package is not on CRAN, but you can install the development version from GitHub using the devtools package:

```{r}
install.packages("devtools")
devtools::install_github("SORTEE/DCQC")
library(DCQC)
```

## Running DCQC
The only function in DCQC is DCQC().

```{r}
library(DCQC)
DCQC()
```
