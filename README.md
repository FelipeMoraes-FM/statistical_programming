---
title: "Inference Homework"
author: "Felipe Moraes"
format: html
embed-resources: true
---

```{r}
#| label: setup
#| message: false
library(tidyverse)
library(rstatix)
library(ggpubr)
carseats_real <- ISLR2::Carseats 
```


##Problem 1 

```{r}
ggplot(carseats_real, aes(sample = Price)) +
  geom_qq() + 
  geom_qq_line(color = "blue") +
  labs(title = "Q-Q Plot for Car Seat Prices",
       x = "Sample Quantities",
       y = "Theoretical Quantities")
```
As we can see, the null hypothesis μ = $110 and the alternate hypothesis 
μ ≠ $110.

##Problem 2

```{r}
get_summary_stats(carseats_real["Price"], type = "mean_sd")

result <- t.test(carseats_real$Price, mu = 110, conf.level = 0.90)
result

error <- 115.795 - 110
error
```
As we can see, the sample is 115.80 and the margin of error is 5.80 (approximately)

##Problem 3

```{r}
penguins_real <- penguins

peng_table <- table(penguins_real$species, penguins_real$island)
addmargins(peng_table)
```
