Relationship between variables and MPG
========================================================
author: Dzaringana Mate
date:   24 May 2015
mtcars dataset

Deployed Apps
========================================================

Below are the deployed apps

- Part 1 :  **https://matdza.shinyapps.io/DataPrdPrj/**
- Part 2 :  **http://rpubs.com/matdza/82470**  
- Part 1 Source code @ : **https://github.com/matdza/DataPrdPrj**
- Part 2 Source code @ : **https://github.com/matdza/Part2DevProd**

mtcars dataset - Description
========================================================
Motor Trend Car Road Tests
- The data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973-74 models).
Source
- Henderson and Velleman (1981), Building multiple regression models interactively. Biometrics, 37, 391-411.

```r
library(datasets)
head(mtcars, 3)
```

```
               mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4     21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag 21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710    22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
```

mtcars dataset - Format
========================================================
**A data frame with 32 observations on 11 variables.**

| Index | Field | Detail |
------- | ----- | ------ |
| [, 1] | mpg | Miles/(US) gallon |
| [, 2]  | cyl | Number of cylinders |
| [, 3]  | disp | Displacement (cu.in.) |
| [, 4]	| hp | Gross horsepower |
| [, 5]	| drat | Rear axle ratio |
| [, 6]	| wt | Weight (lb/1000) |
| [, 7]	| qsec | 1/4 mile time |
| [, 8]	| vs | V/S |
| [, 9]	| am | Transmission (0 = automatic, 1 = manual) |
| [,10]	| gear | Number of forward gears |
| [,11]	| carb | Number of carburetors |

 Analysis - main code
========================================================
```r
  formulaTextPoint <- reactive({
    paste("mpg ~", "as.integer(", input$variable, ")")  })
  
  fit <- reactive({
    lm(as.formula(formulaTextPoint()), data=mpgData)  })
  ...
  output$fit <- renderPrint({
    summary(fit()) })
  
  output$mpgPlot <- renderPlot({
    with(mpgData, {
      plot(as.formula(formulaTextPoint()))
      abline(fit(), col=2)
    })  })

```
