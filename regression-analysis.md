Regression Analysis
================
Tingyi Li
2023-12-03

\#Part 1

\#Multiple Linear Regression for Happiness Score Prediction

``` r
happiness_score = read_csv("./Data/combined_happiness.csv")
```

    ## Rows: 782 Columns: 11
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): country, region
    ## dbl (9): year, rank, score, gdp_per_capita, social_support, health_life_expe...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
predicted_model = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = happiness_score)

predicted_model|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 2.1750674 | 0.0799098 | 27.219021 | 0.0000000 |
| gdp_per_capita               | 1.1359972 | 0.0841455 | 13.500396 | 0.0000000 |
| social_support               | 0.6458962 | 0.0809226 |  7.981656 | 0.0000000 |
| health_life_expectancy       | 1.0127106 | 0.1320119 |  7.671359 | 0.0000000 |
| freedom_to_make_life_choices | 1.4812709 | 0.1634584 |  9.062068 | 0.0000000 |
| perception_of_corruption     | 0.8582286 | 0.2234402 |  3.840976 | 0.0001326 |
| generosity                   | 0.5924416 | 0.1757022 |  3.371851 | 0.0007837 |

The variable “freedom to make life choices” exhibits the largest
coefficient (1.4812709) with a highly significant p-value, indicating it
exerts the most substantial effect on happiness scores. Following this,
“GDP per capita”, “Health life expectancy”, and “Social support” are
also significant contributors to happiness in order of their estimates.
“Perception of corruption” and “Generosity” also significantly impact
happiness but to a lesser extent, based on their estimates and p-values.

\#Part 2

\#Multiple linear Regression for Happiness Score Prediction in 2015

``` r
data_2015 = happiness_score|>
  filter(year == 2015)

model2015 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = data_2015)

model2015|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 1.8601849 | 0.1904824 | 9.7656541 | 0.0000000 |
| gdp_per_capita               | 0.8606572 | 0.2203113 | 3.9065501 | 0.0001409 |
| social_support               | 1.4088916 | 0.2226751 | 6.3271187 | 0.0000000 |
| health_life_expectancy       | 0.9753090 | 0.3162930 | 3.0835619 | 0.0024325 |
| freedom_to_make_life_choices | 1.3334329 | 0.3850157 | 3.4633211 | 0.0006944 |
| perception_of_corruption     | 0.7845381 | 0.4365328 | 1.7972032 | 0.0743018 |
| generosity                   | 0.3889329 | 0.3910029 | 0.9947057 | 0.3214707 |

\#Multiple linear Regression for Happiness Score Prediction in 2016

``` r
data_2016 = happiness_score|>
  filter(year == 2016)

model2016 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = data_2016)

model2016|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error |  statistic |   p.value |
|:-----------------------------|----------:|----------:|-----------:|----------:|
| (Intercept)                  | 2.1902936 | 0.1583237 | 13.8342722 | 0.0000000 |
| gdp_per_capita               | 0.7214128 | 0.2171212 |  3.3226274 | 0.0011204 |
| social_support               | 1.2297543 | 0.2297496 |  5.3525847 | 0.0000003 |
| health_life_expectancy       | 1.4364028 | 0.3489120 |  4.1168054 | 0.0000632 |
| freedom_to_make_life_choices | 1.5139349 | 0.3879659 |  3.9022369 | 0.0001435 |
| perception_of_corruption     | 0.9189270 | 0.4647615 |  1.9772014 | 0.0498518 |
| generosity                   | 0.1594941 | 0.3621060 |  0.4404626 | 0.6602362 |

\#Multiple linear Regression for Happiness Score Prediction in 2017

``` r
data_2017 = happiness_score|>
  filter(year == 2017)

model2017 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = data_2017)

model2017|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 1.7430289 | 0.1873581 |  9.303195 | 0.0000000 |
| gdp_per_capita               | 0.7844334 | 0.2045131 |  3.835615 | 0.0001849 |
| social_support               | 1.1177711 | 0.2020608 |  5.531856 | 0.0000001 |
| health_life_expectancy       | 1.2888803 | 0.3215255 |  4.008640 | 0.0000965 |
| freedom_to_make_life_choices | 1.4757152 | 0.3425093 |  4.308541 | 0.0000298 |
| perception_of_corruption     | 0.8266072 | 0.4843307 |  1.706700 | 0.0899751 |
| generosity                   | 0.3807181 | 0.3293271 |  1.156049 | 0.2495240 |

\#Multiple linear Regression for Happiness Score Prediction in 2018

``` r
data_2018 = happiness_score|>
  filter(year == 2018)

model2018 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = data_2018)

model2018|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 1.8234561 | 0.1977108 |  9.222845 | 0.0000000 |
| gdp_per_capita               | 0.9017459 | 0.2423630 |  3.720642 | 0.0002816 |
| social_support               | 1.1150219 | 0.2117195 |  5.266505 | 0.0000005 |
| health_life_expectancy       | 0.9671218 | 0.3425058 |  2.823666 | 0.0054021 |
| freedom_to_make_life_choices | 1.3984419 | 0.3185447 |  4.390096 | 0.0000214 |
| perception_of_corruption     | 0.7277888 | 0.5277904 |  1.378935 | 0.1699951 |
| generosity                   | 0.5235668 | 0.4717544 |  1.109829 | 0.2688726 |

\#Multiple linear Regression for Happiness Score Prediction in 2019

``` r
data_2019 = happiness_score|>
  filter(year == 2019)

model2019 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = data_2018)

model2019|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 1.8234561 | 0.1977108 |  9.222845 | 0.0000000 |
| gdp_per_capita               | 0.9017459 | 0.2423630 |  3.720642 | 0.0002816 |
| social_support               | 1.1150219 | 0.2117195 |  5.266505 | 0.0000005 |
| health_life_expectancy       | 0.9671218 | 0.3425058 |  2.823666 | 0.0054021 |
| freedom_to_make_life_choices | 1.3984419 | 0.3185447 |  4.390096 | 0.0000214 |
| perception_of_corruption     | 0.7277888 | 0.5277904 |  1.378935 | 0.1699951 |
| generosity                   | 0.5235668 | 0.4717544 |  1.109829 | 0.2688726 |

\#Part 3

\#Multiple linear Regression for Happiness Score Prediction in Central
and Eastern Europe

``` r
central_east = happiness_score|>
  filter(region == "Central and Eastern Europe")

model1 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = central_east)

model1|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  3.1506152 | 0.3761585 |  8.3757648 | 0.0000000 |
| gdp_per_capita               |  1.0993611 | 0.2033891 |  5.4052129 | 0.0000003 |
| social_support               |  0.5447398 | 0.1437145 |  3.7904299 | 0.0002240 |
| health_life_expectancy       | -0.1987347 | 0.4097214 | -0.4850485 | 0.6284110 |
| freedom_to_make_life_choices |  1.7050905 | 0.3442244 |  4.9534273 | 0.0000021 |
| perception_of_corruption     | -0.5976465 | 0.5501586 | -1.0863167 | 0.2792328 |
| generosity                   |  0.6492740 | 0.5101488 |  1.2727149 | 0.2052593 |

\#Multiple linear Regression for Happiness Score Prediction in Eastern
Asia

``` r
east_asia = happiness_score|>
  filter(region == "Eastern Asia")

model2 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = east_asia)

model2|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  0.6698077 | 0.9885689 |  0.6775529 | 0.5048144 |
| gdp_per_capita               |  2.6321054 | 0.3987773 |  6.6004398 | 0.0000010 |
| social_support               |  0.1680339 | 0.2050669 |  0.8194102 | 0.4209627 |
| health_life_expectancy       |  1.5122195 | 0.7333569 |  2.0620513 | 0.0506769 |
| freedom_to_make_life_choices |  1.8238357 | 0.9140536 |  1.9953269 | 0.0579853 |
| perception_of_corruption     | -6.1001405 | 1.5633140 | -3.9020571 | 0.0007172 |
| generosity                   |  0.8764310 | 0.8352973 |  1.0492444 | 0.3049665 |

\#Multiple linear Regression for Happiness Score Prediction in Latin
America and Caribbean

``` r
latin_caribbean = happiness_score|>
  filter(region == "Latin America and Caribbean")

model3 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = latin_caribbean)

model3|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  2.9870953 | 0.3603714 |  8.2889347 | 0.0000000 |
| gdp_per_capita               |  1.4869935 | 0.2138900 |  6.9521417 | 0.0000000 |
| social_support               | -0.6315397 | 0.2278693 | -2.7714998 | 0.0066120 |
| health_life_expectancy       |  1.7455082 | 0.3819569 |  4.5699082 | 0.0000135 |
| freedom_to_make_life_choices |  2.4568168 | 0.3534921 |  6.9501327 | 0.0000000 |
| perception_of_corruption     |  1.3409006 | 0.9170861 |  1.4621317 | 0.1467204 |
| generosity                   | -0.3165373 | 0.5087516 | -0.6221843 | 0.5351824 |

\#Multiple linear Regression for Happiness Score Prediction in Middle
East and Northern Africa

``` r
east_africa = happiness_score|>
  filter(region == "Middle East and Northern Africa")

model4 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = east_africa)

model4|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  1.5472699 | 0.2567575 |  6.0261911 | 0.0000000 |
| gdp_per_capita               |  1.5506958 | 0.2511559 |  6.1742356 | 0.0000000 |
| social_support               |  0.4364518 | 0.2065005 |  2.1135633 | 0.0373830 |
| health_life_expectancy       |  2.0670148 | 0.4620345 |  4.4737244 | 0.0000229 |
| freedom_to_make_life_choices |  1.3532650 | 0.4613435 |  2.9333131 | 0.0042752 |
| perception_of_corruption     |  0.3720748 | 0.6673868 |  0.5575099 | 0.5785945 |
| generosity                   | -1.4347645 | 0.4915314 | -2.9189679 | 0.0044584 |

\#Multiple linear Regression for Happiness Score Prediction in North
America

``` r
north_america = happiness_score|>
  filter(region == "North America")

model5 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = north_america)

model5|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  5.7461328 | 1.1568751 |  4.9669432 | 0.0156747 |
| gdp_per_capita               |  0.2906872 | 0.4853376 |  0.5989381 | 0.5914238 |
| social_support               | -0.2790530 | 0.1790157 | -1.5588190 | 0.2169302 |
| health_life_expectancy       |  0.4041180 | 0.4999375 |  0.8083371 | 0.4780512 |
| freedom_to_make_life_choices |  0.9868637 | 0.8267570 |  1.1936563 | 0.3183984 |
| perception_of_corruption     |  1.4273085 | 0.5532336 |  2.5799383 | 0.0817842 |
| generosity                   |  0.4721823 | 0.4867702 |  0.9700313 | 0.4035808 |

\#Multiple linear Regression for Happiness Score Prediction in
Southeastern Asia

``` r
southeastern_asia = happiness_score|>
  filter(region == "Southeastern Asia")

model6 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = southeastern_asia)

model6|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  3.5557237 | 0.7682308 |  4.6284577 | 0.0000442 |
| gdp_per_capita               |  1.6457687 | 0.3325444 |  4.9490193 | 0.0000165 |
| social_support               |  0.3338875 | 0.3197225 |  1.0443039 | 0.3031200 |
| health_life_expectancy       |  0.7927899 | 0.5905490 |  1.3424625 | 0.1876252 |
| freedom_to_make_life_choices | -0.9335115 | 1.0718734 | -0.8709158 | 0.3894160 |
| perception_of_corruption     | -0.6520931 | 0.6148682 | -1.0605413 | 0.2957725 |
| generosity                   |  0.0954657 | 0.4326026 |  0.2206775 | 0.8265568 |

\#Multiple linear Regression for Happiness Score Prediction in Southern
Asia

``` r
southern_asia = happiness_score|>
  filter(region == "Southern Asia")

model7 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = southern_asia)

model7|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  2.9020228 | 0.3943552 |  7.3589065 | 0.0000001 |
| gdp_per_capita               |  0.1307995 | 0.5138800 |  0.2545332 | 0.8009437 |
| social_support               |  0.3855854 | 0.3180950 |  1.2121705 | 0.2355768 |
| health_life_expectancy       |  1.5212822 | 0.8819818 |  1.7248452 | 0.0955793 |
| freedom_to_make_life_choices | -1.3276433 | 0.8445746 | -1.5719668 | 0.1271914 |
| perception_of_corruption     |  8.8312157 | 2.1766502 |  4.0572507 | 0.0003603 |
| generosity                   |  0.4649207 | 0.9043858 |  0.5140734 | 0.6112343 |

\#Multiple linear Regression for Happiness Score Prediction in
Sub-Saharan Africa

``` r
sub_africa = happiness_score|>
  filter(region == "Sub-Saharan Africa")

model8 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = sub_africa)

model8|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |   estimate | std.error |  statistic |   p.value |
|:-----------------------------|-----------:|----------:|-----------:|----------:|
| (Intercept)                  |  2.6862788 | 0.1737404 | 15.4614553 | 0.0000000 |
| gdp_per_capita               |  0.6020415 | 0.1539281 |  3.9111867 | 0.0001280 |
| social_support               |  0.6583385 | 0.1332112 |  4.9420649 | 0.0000017 |
| health_life_expectancy       | -0.0725829 | 0.2444136 | -0.2969676 | 0.7668173 |
| freedom_to_make_life_choices |  0.9605341 | 0.2729970 |  3.5184786 | 0.0005437 |
| perception_of_corruption     | -0.6583010 | 0.4600525 | -1.4309258 | 0.1541028 |
| generosity                   |  2.0618730 | 0.4998157 |  4.1252665 | 0.0000555 |

\#Multiple linear Regression for Happiness Score Prediction in Western
Europe

``` r
west_europe = happiness_score|>
  filter(region == "Western Europe")

model9 = lm(formula = score ~ gdp_per_capita + social_support + health_life_expectancy + freedom_to_make_life_choices + perception_of_corruption + generosity, 
                     data = west_europe)

model9|>
  broom::tidy()|>
  knitr::kable()
```

| term                         |  estimate | std.error | statistic |   p.value |
|:-----------------------------|----------:|----------:|----------:|----------:|
| (Intercept)                  | 2.1188003 | 0.7020829 |  3.017878 | 0.0032440 |
| gdp_per_capita               | 0.8563506 | 0.3675997 |  2.329574 | 0.0218810 |
| social_support               | 0.7417660 | 0.1914877 |  3.873701 | 0.0001936 |
| health_life_expectancy       | 1.1950538 | 0.5049965 |  2.366459 | 0.0199258 |
| freedom_to_make_life_choices | 0.8686215 | 0.3881809 |  2.237672 | 0.0275070 |
| perception_of_corruption     | 2.7240472 | 0.3798791 |  7.170826 | 0.0000000 |
| generosity                   | 1.2352683 | 0.3167298 |  3.900070 | 0.0001763 |