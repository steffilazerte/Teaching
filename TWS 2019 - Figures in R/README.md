
# R Workshop for The Wildlife Society Manitoba Chapter 2019

## Workshop files

  - [HTML version](intro_with_figures.html)
  - [PDF version](intro_with_figures.pdf)
  - [Sleep Data (new\_sleep.csv)](new_sleep.csv)

The `new_sleep.csv` data file was created with the following
    code:

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
sleep <- msleep %>%
  filter(!is.na(sleep_rem)) %>%
  mutate(body_size = if_else(bodywt > median(bodywt), "Large", "Small"),
         vore = replace(vore, is.na(vore), "unknown")) %>%
  select(name, vore, conservation, sleep_total, sleep_rem, sleep_cycle, 
         awake, bodywt, body_size)

write_csv(sleep, "new_sleep.csv")
```
