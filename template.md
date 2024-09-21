Simple document
================

\#Question 1

``` r
data("penguins", package = "palmerpenguins")
```

The variables of the dataset are species, island, bill_length_mm,
bill_depth_mm, flipper_length_mm, body_mass_g, sex, year. The dataset
has 8 columns and 344 rows. The mean flipper length is 200.9152047.

``` r
scatterplot <- ggplot(data = penguins, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) + geom_point()

print(scatterplot)
```

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](template_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
ggsave("hw1_scatterplot.png", plot = scatterplot)
```

    ## Saving 7 x 5 in image

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).
