---
title       : Type II Diabetes Risk Calculator
subtitle    : A Shiny application to predict the 7-year risk of type II diabetes
author      : Owamo
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : standalone  # {standalone, draft}
knit        : slidify::knit2slides
---

## Diabetes prevalence in the United States

According to the [National Diabetes Statistics Report][1] 29.1 million people of the U.S. population have diabetes.

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png) 

In 2012 there were 1.7 million *new* diabetes cases, **middle-aged adults** (45-64 years) had the highest rates.

[1]: http://www.cdc.gov/diabetes/pubs/statsreport14/national-diabetes-report-web.pdf

--- .class #id

## Why predict diabetes risk?

Accurate diabetes risk information will help:

1. Primary healthcare providers to identify high risk individuals and deliver timely care to manage and reduce their risk.
2. Health and medical insurers to set insurance premiums according to each customer's risk profile, improving company profits.


--- .class #id 

## How does the app work?

The **Type II Diabetes (T2D) Risk Calculator** will generate a 7-year risk prediction based on prediciton rules developed by [Wilson et al. (2007)][1]. In that study, the authors fit a logisitic regression to estimate incidence of new T2D cases over a 7-year period. To obtain our predictions, take the inverse logit transformation of a linear combination of the relevant estimated model parameters.

For example, a 45 year-old male with healthy weight, no other medical conditions, but with elevated fasting glucose levels and parental history of diabetes has a 4.82% chance of developing diabetes in the next 7 years. 

```r
linearComb <- -5.517 - 0.010 + 1.98 + 0.565
1/(1 + exp(-linearComb))
```

```
## [1] 0.04824571
```

[1]: http://archinte.jamanetwork.com/article.aspx?articleid=486842

--- .class #id 

## How well does the algorithm work?

- The [study][1] found this algorithm has good classification results. The area under the ROC curve was 0.852. 
- More complex models have marginally better classification (0.854 area under ROC curve). However it involves  clinical variables that are more costly and difficult to obtain.
- Note that the algorithm works best for populations for which the prediction algorithm was developed, i.e. middle-aged caucasians.

You can start using the **T2D Risk Calculator** by following this [link][2]. Instructions on how to use the application are also there.

[1]: http://archinte.jamanetwork.com/article.aspx?articleid=486842
[2]: https://owamo.shinyapps.io/T2Drisk/

