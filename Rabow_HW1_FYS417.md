---
title: "HW 1"
output: 
  html_document: 
    keep_md: yes
---


```r
4*2
```

```
## [1] 8
```


```r
5-3*2
```

```
## [1] -1
```


```r
8/2**2
```

```
## [1] 2
```


```r
(5-3)*2
```

```
## [1] 4
```


```r
(8/2)*2*2
```

```
## [1] 16
```


```r
blackjack <- c(140,-20,70,-120, 240)
roulette <- c(60, 50, 120, -300, 10)
```



```r
days <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
names(blackjack) <- days
names(roulette) <- days
```


```r
total_blackjack <- sum(blackjack)
total_blackjack
```

```
## [1] 310
```


```r
total_roulette <- sum(roulette)
total_roulette
```

```
## [1] -60
```

```r
total_week <- c(blackjack+roulette)
total_week
```

```
##    Monday   Tuesday Wednesday  Thursday    Friday 
##       200        30       190      -420       250
```

```r
total_week <- sum(roulette)
total_roulette
```

```
## [1] -60
```



```r
Blackjack_or_Roulette <- total_blackjack>total_roulette
Blackjack_or_Roulette
```

```
## [1] TRUE
```


```r
roulette_or_blackjack <- total_blackjack<total_roulette
roulette_or_blackjack
```

```
## [1] FALSE
```

blackjack is the better choice
