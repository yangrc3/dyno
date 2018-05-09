
<!-- README.md is generated from README.Rmd. Please edit that file -->
Inferring trajectories using dyno <img src="docs/dyno.gif" align="right" />
===========================================================================

The dyno package guides the user through the full path of trajectory inference on single-cell data, starting from the selection of the most optimal methods, to the running of these methods, right to the interpretation and visualisation of the trajectories.

Installation
------------

You can install dyno from github using:

``` r
# install.packages("devtools")
devtools::install_github("dynverse/dyno")
```

Example
-------

Inferring and interpreting trajectories consists of three main steps

``` r
library(dyno)
#> Warning: replacing previous import 'dplyr::vars' by 'ggplot2::vars' when
#> loading 'dynmethods'

data("fibroblast_reprogramming_treutlein")
task <- fibroblast_reprogramming_treutlein
```

### Selection of the best methods

``` r
methods <- c("slngsht")
```

### Running the methods

``` r
start_dynmethods_docker()

model %<-% infer_trajectory(task, methods)
```

### Selecting relevant features and plotting the trajectory

``` r
plot_dimred(model, expression_source = task$expression, dimred_method = dimred_mds, grouping_assignment = task$grouping)
```

<img src="man/figures/README-unnamed-chunk-4-1.png" width="100%" />

``` r
plot_heatmap(model, expression_source = task$expression, grouping_assignment = task$grouping, features_oi = 50)
```

<img src="man/figures/README-unnamed-chunk-5-1.png" width="100%" />