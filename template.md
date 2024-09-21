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
  vec_factor = factor(c("low", "medium", "high", "low", "medium", 
                          "high", "low", "medium", "high", "low"))
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

    ## [1] 1.102634

``` r
mean(pull(hw1_df, norm_samp_pos))
```

    ## [1] 0.9

When taking the mean of each variable in the dataframe, I realized that
I could only take the mean of the numeric variables.

``` r
as.numeric(pull(hw1_df, norm_samp_pos))
```

    ##  [1] 1 1 1 1 1 1 1 0 1 1

``` r
as.numeric(factor(pull(hw1_df, vec_char)))
```

    ##  [1] 4 5 7 3 4 2 8 1 6 9

``` r
as.numeric(pull(hw1_df, vec_factor))
```

    ##  [1] 2 3 1 2 3 1 2 3 1 2

When converting the logical variable to numeric, it converts TRUE to 1
and FALSE to 0 to facilitate calculating the mean.

When converting the character variable to numeric, I first have to
convert it to a factor so that it can be converted to numeric. I notice
that each character value is assigned a number based on alphabetical
order.

When converting the factor variable to numeric, it assigns a number to
each factor level
