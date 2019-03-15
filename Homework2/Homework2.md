---
title: "Homework2"
author: "Zachary Rabow"
date: "March 14, 2019"
output: 
  html_document:
    keep_md: yes
---


```r
library('tidyverse')
```

```
## ── Attaching packages ───────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.1.0     ✔ purrr   0.2.5
## ✔ tibble  2.0.1     ✔ dplyr   0.7.8
## ✔ tidyr   0.8.2     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.3.0
```

```
## ── Conflicts ──────────────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```


```r
msleep
```

```
## # A tibble: 83 x 11
##    name  genus vore  order conservation sleep_total sleep_rem sleep_cycle
##    <chr> <chr> <chr> <chr> <chr>              <dbl>     <dbl>       <dbl>
##  1 Chee… Acin… carni Carn… lc                  12.1      NA        NA    
##  2 Owl … Aotus omni  Prim… <NA>                17         1.8      NA    
##  3 Moun… Aplo… herbi Rode… nt                  14.4       2.4      NA    
##  4 Grea… Blar… omni  Sori… lc                  14.9       2.3       0.133
##  5 Cow   Bos   herbi Arti… domesticated         4         0.7       0.667
##  6 Thre… Brad… herbi Pilo… <NA>                14.4       2.2       0.767
##  7 Nort… Call… carni Carn… vu                   8.7       1.4       0.383
##  8 Vesp… Calo… <NA>  Rode… <NA>                 7        NA        NA    
##  9 Dog   Canis carni Carn… domesticated        10.1       2.9       0.333
## 10 Roe … Capr… herbi Arti… lc                   3        NA        NA    
## # … with 73 more rows, and 3 more variables: awake <dbl>, brainwt <dbl>,
## #   bodywt <dbl>
```

```r
?msleep
```


```r
summary(msleep)
```

```
##      name              genus               vore          
##  Length:83          Length:83          Length:83         
##  Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character  
##                                                          
##                                                          
##                                                          
##                                                          
##     order           conservation        sleep_total      sleep_rem    
##  Length:83          Length:83          Min.   : 1.90   Min.   :0.100  
##  Class :character   Class :character   1st Qu.: 7.85   1st Qu.:0.900  
##  Mode  :character   Mode  :character   Median :10.10   Median :1.500  
##                                        Mean   :10.43   Mean   :1.875  
##                                        3rd Qu.:13.75   3rd Qu.:2.400  
##                                        Max.   :19.90   Max.   :6.600  
##                                                        NA's   :22     
##   sleep_cycle         awake          brainwt            bodywt        
##  Min.   :0.1167   Min.   : 4.10   Min.   :0.00014   Min.   :   0.005  
##  1st Qu.:0.1833   1st Qu.:10.25   1st Qu.:0.00290   1st Qu.:   0.174  
##  Median :0.3333   Median :13.90   Median :0.01240   Median :   1.670  
##  Mean   :0.4396   Mean   :13.57   Mean   :0.28158   Mean   : 166.136  
##  3rd Qu.:0.5792   3rd Qu.:16.15   3rd Qu.:0.12550   3rd Qu.:  41.750  
##  Max.   :1.5000   Max.   :22.10   Max.   :5.71200   Max.   :6654.000  
##  NA's   :51                       NA's   :27
```

```r
str(msleep)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	83 obs. of  11 variables:
##  $ name        : chr  "Cheetah" "Owl monkey" "Mountain beaver" "Greater short-tailed shrew" ...
##  $ genus       : chr  "Acinonyx" "Aotus" "Aplodontia" "Blarina" ...
##  $ vore        : chr  "carni" "omni" "herbi" "omni" ...
##  $ order       : chr  "Carnivora" "Primates" "Rodentia" "Soricomorpha" ...
##  $ conservation: chr  "lc" NA "nt" "lc" ...
##  $ sleep_total : num  12.1 17 14.4 14.9 4 14.4 8.7 7 10.1 3 ...
##  $ sleep_rem   : num  NA 1.8 2.4 2.3 0.7 2.2 1.4 NA 2.9 NA ...
##  $ sleep_cycle : num  NA NA NA 0.133 0.667 ...
##  $ awake       : num  11.9 7 9.6 9.1 20 9.6 15.3 17 13.9 21 ...
##  $ brainwt     : num  NA 0.0155 NA 0.00029 0.423 NA NA NA 0.07 0.0982 ...
##  $ bodywt      : num  50 0.48 1.35 0.019 600 ...
```

**1. A quantitative, theoretical framework for understanding mammalian sleep**
**2. Summary fnc: 83 names, genus, vore, order, sleep time, awake time, sleep cycle, sleep total  **

**3**

```r
msleep %>%
    select(name,genus,bodywt) %>% 
  arrange(desc(bodywt))
```

```
## # A tibble: 83 x 3
##    name                 genus         bodywt
##    <chr>                <chr>          <dbl>
##  1 African elephant     Loxodonta      6654 
##  2 Asian elephant       Elephas        2547 
##  3 Giraffe              Giraffa         900.
##  4 Pilot whale          Globicephalus   800 
##  5 Cow                  Bos             600 
##  6 Horse                Equus           521 
##  7 Brazilian tapir      Tapirus         208.
##  8 Donkey               Equus           187 
##  9 Bottle-nosed dolphin Tursiops        173.
## 10 Tiger                Panthera        163.
## # … with 73 more rows
```

**4. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 1kg body weight and large as greater than or equal to 200kg body weight. For our study, we are interested in body weight and sleep total Make two new dataframes (large and small) based on these parameters.  **



```r
small <- msleep %>%
  select(name, genus, bodywt, sleep_total) %>%
  filter(bodywt<=1) %>%
  arrange(desc(bodywt))
small
```

```
## # A tibble: 36 x 4
##    name                      genus        bodywt sleep_total
##    <chr>                     <chr>         <dbl>       <dbl>
##  1 African giant pouched rat Cricetomys    1             8.3
##  2 Arctic ground squirrel    Spermophilus  0.92         16.6
##  3 Tenrec                    Tenrec        0.9          15.6
##  4 European hedgehog         Erinaceus     0.77         10.1
##  5 Squirrel monkey           Saimiri       0.743         9.6
##  6 Guinea pig                Cavis         0.728         9.4
##  7 Desert hedgehog           Paraechinus   0.55         10.3
##  8 Owl monkey                Aotus         0.48         17  
##  9 Chinchilla                Chinchilla    0.42         12.5
## 10 Thick-tailed opposum      Lutreolina    0.37         19.4
## # … with 26 more rows
```


```r
large <- msleep %>%
  select(name, genus, bodywt, sleep_total) %>%
  filter(bodywt>=200) %>%
  arrange(desc(bodywt))
large
```

```
## # A tibble: 7 x 4
##   name             genus         bodywt sleep_total
##   <chr>            <chr>          <dbl>       <dbl>
## 1 African elephant Loxodonta      6654          3.3
## 2 Asian elephant   Elephas        2547          3.9
## 3 Giraffe          Giraffa         900.         1.9
## 4 Pilot whale      Globicephalus   800          2.7
## 5 Cow              Bos             600          4  
## 6 Horse            Equus           521          2.9
## 7 Brazilian tapir  Tapirus         208.         4.4
```

**5. avg sleep dur large= 3.3**


```r
mean(large$sleep_total)
```

```
## [1] 3.3
```




```r
mean(small$sleep_total)
```

```
## [1] 12.65833
```
**6. avg sleep dur small= 12.65**

**7. Which animals sleep at least 18 hours per day? Be sure to show the name, genus, order, and sleep total.  **


```r
eighteen <- msleep %>%
  filter(sleep_total>= 18) %>%
  select(name, genus, order, sleep_total) %>%
  arrange(order, sleep_total)
eighteen
```

```
## # A tibble: 5 x 4
##   name                   genus      order           sleep_total
##   <chr>                  <chr>      <chr>                 <dbl>
## 1 Big brown bat          Eptesicus  Chiroptera             19.7
## 2 Little brown bat       Myotis     Chiroptera             19.9
## 3 Giant armadillo        Priodontes Cingulata              18.1
## 4 North American Opossum Didelphis  Didelphimorphia        18  
## 5 Thick-tailed opposum   Lutreolina Didelphimorphia        19.4
```
** 5 animals sleep longer than 18 hours, big brown bat, little brown bat, giant armadillo, north american opossum, thick tailed opposum**
