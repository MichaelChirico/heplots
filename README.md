
<!-- README.md is generated from README.Rmd. Please edit that file and knit again -->
<!-- badges: start -->

[![Lifecycle:
stable](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://lifecycle.r-lib.org/articles/stages.html#stable)
[![CRAN_Status_Badge](http://www.r-pkg.org/badges/version/heplots)](http://cran.r-project.org/package=heplots)
[![](http://cranlogs.r-pkg.org/badges/grand-total/heplots)](https://cran.r-project.org/package=heplots)
[![License](https://img.shields.io/badge/license-GPL%20%28%3E=%202%29-brightgreen.svg?style=flat)](https://www.gnu.org/licenses/gpl-2.0.html)
[![DOI](https://zenodo.org/badge/13908453.svg)](https://zenodo.org/badge/latestdoi/13908453)
<!-- badges: end -->

# heplots <img src="man/figures/logo.png" height="200" style="float:right; height:200px;" />

## **Visualizing Hypothesis Tests in Multivariate Linear Models**

Version 1.4-0

## Description

The `heplots` package provides functions for visualizing hypothesis
tests in multivariate linear models (MANOVA, multivariate multiple
regression, MANCOVA, and repeated measures designs).

HE plots represent sums-of-squares-and-products matrices for linear
hypotheses (**H**) and for error (**E**) using ellipses (in two
dimensions), ellipsoids (in three dimensions), or by line segments in
one dimension. For the theory and applications, see:

-   Fox, Friendly and Monette (2009) for a brief introduction,
-   Friendly (2010) for the application of these ideas to repeated
    measure designs,
-   Friendly, Monette and Fox (2013) for a general discussion of the
    role of elliptical geometry in statistical understanding, and
-   Friendly & Sigal (2017) for an applied R tutorial.

Other topics now addressed here include:

-   robust MLMs, using iteratively re-weighted least squared to
    down-weight observations with large multivariate residuals,
    `robmlm()`.
-   `Mahalanobis()` calculates classical and robust Mahalanobis squared
    distances using MCD and MVE estimators of center and covariance.
-   visualizing tests for equality of covariance matrices in MLMs (Box’s
    M test), `boxM()` and `plot.boxM()`.
-   $\chi^2$ Q-Q plots for MLMs (`cqplot()`) to detect outliers and
    assess multivariate normality of residuals.
-   bivariate coefficient plots showing elliptical confidence regions
    (`coefplot()`).

In this respect, the `heplots` package now aims to provide a wide range
of tools for analyzing and visualizing multivariate response linear
models.

-   The related [`candisc`](http://github.com/friendly/candisc) package
    provides HE plots in **canonical discriminant** space, the space of
    linear combinations of the responses that show the maximum possible
    effects and for canonical correlation in multivariate regression
    designs.

-   Another package,
    [`mvinfluence`](https://friendly.github.io/mvinfluence/), provides
    diagnostic measures and plots for influential observations in MLM
    designs.

Several tutorial vignettes are also included. See
`vignette(package="heplots")`.

## Installation

|                     |                                               |
|---------------------|-----------------------------------------------|
| CRAN version        | `install.packages("heplots")`                 |
| Development version | `remotes::install_github("friendly/heplots")` |

<!-- This installs the package from the source and creates the package vignettes,  -->
<!-- so you will need to have R Tools installed on your system.  [R Tools for Windows](https://cran.r-project.org/bin/windows/Rtools/) -->
<!-- takes you to the download page for Windows.  [R Tools for Mac OS X](https://cran.r-project.org/bin/macosx/tools/) -->
<!-- has the required programs for Mac OS X. -->

## HE plot functions

The graphical functions contained here all display multivariate model
effects in variable (**data**) space, for one or more response variables
(or contrasts among response variables in repeated measures designs).

-   `heplot()` constructs two-dimensional HE plots for model terms and
    linear hypotheses for pairs of response variables in multivariate
    linear models.

-   `heplot3d()` constructs analogous 3D plots for triples of response
    variables.

-   The `pairs` method, `pairs.mlm()` constructs a scatterplot matrix of
    pairwise HE plots.

-   `heplot1d()` constructs 1-dimensional analogs of HE plots for model
    terms and linear hypotheses for single response variables.

## Other functions

-   `glance.mlm()` extends `broom::glance.lm()` to multivariate response
    models, giving a one-line statistical summary for each response
    variable.

-   `boxM()` Calculates Box’s *M* test for homogeneity of covariance
    matrices in a MANOVA design. A `plot` method displays a visual
    representation of the components of the test. Associated with this,
    `bartletTests()` and `levineTests()` give the univariate tests of
    homogeneity of variance for each response measure in a MLM.

-   `covEllipses()` draw covariance (data) ellipses for one or more
    group, optionally including the ellipse for the pooled within-group
    covariance.

### Repeated measure designs

For repeated measure designs, between-subject effects and within-subject
effects must be plotted separately, because the error terms (**E**
matrices) differ. For terms involving within-subject effects, these
functions carry out a linear transformation of the matrix **Y** of
responses to a matrix **Y M**, where **M** is the model matrix for a
term in the intra-subject design and produce plots of the H and E
matrices in this transformed space. The vignette `"repeated"` describes
these graphical methods for repeated measures designs. (At present, this
vignette is only available at [HE plots for repeated measures
designs](http://www.jstatsoft.org/v37/i04/paper).)

## Datasets

The package also provides a large collection of data sets illustrating a
variety of multivariate linear models of the types listed above,
together with graphical displays.

``` r
vcdExtra::datasets("heplots")[, c("Item", "Title")] |> knitr::kable()
```

| Item             | Title                                                       |
|:-----------------|:------------------------------------------------------------|
| AddHealth        | Adolescent Health Data                                      |
| Adopted          | Adopted Children                                            |
| Bees             | Captive and maltreated bees                                 |
| Diabetes         | Diabetes Dataset                                            |
| FootHead         | Head measurements of football players                       |
| Headache         | Treatment of Headache Sufferers for Sensitivity to Noise    |
| Hernior          | Recovery from Elective Herniorrhaphy                        |
| Iwasaki_Big_Five | Personality Traits of Cultural Groups                       |
| MockJury         | Effects Of Physical Attractiveness Upon Mock Jury Decisions |
| NLSY             | National Longitudinal Survey of Youth Data                  |
| NeuroCog         | Neurocognitive Measures in Psychiatric Groups               |
| Oslo             | Oslo Transect Subset Data                                   |
| Parenting        | Father Parenting Competence                                 |
| Plastic          | Plastic Film Data                                           |
| Pottery2         | Chemical Analysis of Romano-British Pottery                 |
| Probe1           | Response Speed in a Probe Experiment                        |
| Probe2           | Response Speed in a Probe Experiment                        |
| RatWeight        | Weight Gain in Rats Exposed to Thiouracil and Thyroxin      |
| ReactTime        | Reaction Time Data                                          |
| Rohwer           | Rohwer Data Set                                             |
| RootStock        | Growth of Apple Trees from Different Root Stocks            |
| Sake             | Taste Ratings of Japanese Rice Wine (Sake)                  |
| Skulls           | Egyptian Skulls                                             |
| SocGrades        | Grades in a Sociology Course                                |
| SocialCog        | Social Cognitive Measures in Psychiatric Groups             |
| TIPI             | Data on the Ten Item Personality Inventory                  |
| VocabGrowth      | Vocabulary growth data                                      |
| WeightLoss       | Weight Loss Data                                            |
| mathscore        | Math scores for basic math and word problems                |
| schooldata       | School Data                                                 |

## Examples

This example illustrates HE plots using the classic `iris` data set. How
do the means of the flower variables differ by `Species`?

A basic HE plot shows the **H** and **E** ellipses for the first two
response variables (here: `Sepal.Length` and `Sepal.Width`). The
multivariate test is significant (by Roy’s test) *iff* the **H** ellipse
projects *anywhere* outside the **E** ellipse.

The positions of the group means show how they differ on the two
response variables shown, and provide an interpretation of the
orientation of the **H** ellipse: it is long in the directions of
differences among the means.

``` r
iris.mod <- lm(cbind(Sepal.Length, Sepal.Width, Petal.Length, Petal.Width) ~ 
                 Species, data=iris)
heplot(iris.mod)
```

<img src="man/figures/README-iris1-1.png" width="70%" />

Contrasts or other linear hypotheses can be shown as well, and the
ellipses look better if they are filled. We create contrasts to test the
differences between `versacolor` and `virginca` and also between
`setosa` and the average of the other two. Each 1 df contrast plots as
degenerate 1D ellipse– a line.

Because these contrasts are orthogonal, they add to the total 2 df
effect of `Species`. Note how the first contrast, labeled `V:V`,
distinguishes the means of *versicolor* from *virginica*; the second
contrast, `S:VV` distinguishes `setosa` from the other two.

``` r
par(mar=c(4,4,1,1)+.1)
contrasts(iris$Species)<-matrix(c(0, -1, 1, 
                                  2, -1, -1), nrow=3, ncol=2)
contrasts(iris$Species)
#>            [,1] [,2]
#> setosa        0    2
#> versicolor   -1   -1
#> virginica     1   -1
iris.mod <- lm(cbind(Sepal.Length, Sepal.Width, Petal.Length, Petal.Width) ~ 
                 Species, data=iris)

hyp <- list("V:V"="Species1","S:VV"="Species2")
heplot(iris.mod, hypotheses=hyp, 
       fill=TRUE, fill.alpha=0.1)
```

<img src="man/figures/README-iris2-1.png" width="70%" />

All pairwise HE plots are produced using the `pairs` method for MLM
objects.

``` r
pairs(iris.mod, hypotheses=hyp, hyp.labels=FALSE,
      fill=TRUE, fill.alpha=0.1)
```

<img src="man/figures/README-iris3-1.png" width="100%" />

## References

Fox, J.; Friendly, M. & Monette, G. (2009). [Visualizing hypothesis
tests in multivariate linear models: The heplots package for
R](http://datavis.ca/palers/FoxFriendlyMonette-2009.pdf) *Computational
Statistics*, **24**, 233-246.

Friendly, M. (2010). [HE plots for repeated measures
designs](http://www.jstatsoft.org/v37/i04/paper). *Journal of
Statistical Software*, **37**, 1–37.

Friendly, M.; Monette, G. & Fox, J. (2013). [Elliptical Insights:
Understanding Statistical Methods Through Elliptical
Geometry](http://datavis.ca/palers/ellipses-STS402.pdf) *Statistical
Science*, **28**, 1-39.

Friendly, M. & Sigal, M. (2017). [Graphical Methods for Multivariate
Linear Models in Psychological Research: An R
Tutorial.](https://doi.org/10.20982/tqmp.13.1.p020) *The Quantitative
Methods for Psychology*, **13**, 20-45.
