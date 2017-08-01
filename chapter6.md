---
title       : Correlation and Regression
description : Investigating the association between two continuous variables




--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8780720741
## Analysing two continuous variables

This chapter covers looking at two continuous variables. We're often interested in whether two variables are related to each other, because that may indicate that one influences the other. The simplest way to investigate that is to plot the two variables against each other.

Let's try this with one of the built-in datasets in R, the `cars` dataset. This has a range of speeds and their associated stopping distances for a car. We would expect there to be a fairly close relationship between these two variables because one will influence the other.

As a first step, classify these as *explanatory* and *response* variable.

Which is which?

*** =instructions
- `speed` is the response variable and `dist` is the explanatory variable
- `dist` is the response variable and `speed` is the explanatory variable
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 2)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:377c84540a
## Plotting continuous variables

Since you would expect speed to influence stopping distance, speed is the explanatory variable and stopping distance the response variable. In other words, we want to investigate how much of the variation in stopping distance 'is explained by' changes in speed.

In R, you use the `~` symbol to denote 'is explained by'. So `cars$dist ~ cars$speed` means 'is the stopping distance explained by speed?'

*** =instructions
Plot a scatter plot to see to what extent `cars$dist` is explained by `cars$speed` using the `plot()` command.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Scatterplot of dist explained by speed

```

*** =solution
```{r}
# Scatterplot of dist explained by speed
plot(cars$dist ~ cars$speed)

```

*** =sct
```{r}
test_function("plot", args = "x")

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:16406d9a7c
## <<<New Exercise>>>

Now you've generated the scatter plot, take a closer look at it. (If it's too small you can drag the boundaries to stretch it).



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
plot(cars$dist ~ cars$speed)
```

*** =sct
```{r}

```
