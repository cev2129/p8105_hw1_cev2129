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

\#Question 2

``` r
library(tidyverse)
hw1_df = tibble(
  norm_samp = rnorm(10, mean = 1),
  norm_samp_pos = norm_samp > 0,
  vec_char =c("im", "not", "sure", "if", "im", "doing", "this",
              "correctly","oh", "well"),
  vec_factor = factor(c("low", "medium", "high", "low", "high", 
                          "medium", "low", "high", "medium", "low"))
)

mean(pull(hw1_df, vec_char))
```

    ## Warning in mean.default(pull(hw1_df, vec_char)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(hw1_df,vec_factor))
```

    ## Warning in mean.default(pull(hw1_df, vec_factor)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(hw1_df, norm_samp))
```

    ## [1] 0.9635257

``` r
mean(pull(hw1_df, norm_samp_pos))
```

    ## [1] 0.9

When taking the mean of each variable in the dataframe, I realized that
I could only take the mean of the numeric variables.
