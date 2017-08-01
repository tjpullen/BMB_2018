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

In R, you use the `~` symbol to denote 'is explained by'. So `dist ~ speed` means 'is the stopping distance explained by speed?'

*** =instructions
Generate a scatter plot showing the extent to which `dist` is explained by `speed` using the `plot()` command.

Note: you should include the argument `data = cars` to indicated where the data are located.
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
plot(dist ~ speed, data = cars)

```

*** =sct
```{r}
test_function("plot", args = "x")

```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:16406d9a7c
## Visual assessment of association

Now you've generated the scatter plot, take a closer look at it. (If it's too small you can drag the boundaries to expand it).

Scatter plots give a good visual indication of the relationship (or lack of one) between two variables. Consider the following questions:

- Is there a clear association between `dist` and `speed`?
- If so, does the relationship appear linear (ie. the shape of a straight line) or non-linear?
- Is the relationship positive (increased `speed` is associated with increased `dist`) or negative?

Pick the best description of the relationship between `speed` and `dist`.
*** =instructions
- No clear association
- linear positive association
- linear negative association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
plot(cars$dist ~ cars$speed)
```

*** =sct
```{r}
test_mc(correct = 2)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:e7eae34d07
## Visual assessment of association (2)

Great! The positive linear relationship was fairly clear to spot. For the rest of the chapter we'll use a dataframe called `data`. This contains a number of continous variables in separate columns, and you'll investigate whether each of them is associated with column `a`.

Let's start by seeing if column `b` is associated with `a` with a scatter plot.

*** =instructions
Plot `b` against `a` from dataframe `data` using the plot() function. (ie. `b` explained by `a`).
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))

```

*** =sample_code
```{r}
# Scatter plot of `b` against `a` from `data`

```

*** =solution
```{r}
# Scatter plot of `b` against `a` from `data`
plot(b ~ a, data = data)
```

*** =sct
```{r}
test_function('plot', args = c('x', 'data))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d388f233eb
## Visual assessment of association (3)

Now take a look at the plot of `b` against `a` and choose which description of the association best fits the data.

*** =instructions
- No clear association
- linear positive association
- linear negative association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
plot(b ~ a, data = data)
```

*** =sct
```{r}
test_mc(correct = 1)
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1f6ef98255
## Visual assessment of association (4)

Look at the plot of `c ~ a` and choose which description of the association best fits the data.

*** =instructions
- No clear association
- linear positive association
- linear negative association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
plot(c ~ a, data = data)
```

*** =sct
```{r}
test_mc(correct = 4)
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ee344d20d6
## Visual assessment of association (5)

Look at the plot of `d ~ a` and choose which description of the association best fits the data.

*** =instructions
- No clear association
- linear positive association
- linear negative association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
plot(d ~ a, data = data)
```

*** =sct
```{r}
test_mc(correct = 2)
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1e2307476a
## Visual assessment of association (6)

Look at the plot of `e ~ a` and choose which description of the association best fits the data.

*** =instructions
- No clear association
- linear positive association
- linear negative association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
plot(e ~ a, data = data)
```

*** =sct
```{r}
test_mc(correct = 3)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:72c39a1ab0
## Correlation

Visually inspecting a scatter plot gives a good indication of the association between two variables. However, you will often need to quantify this.

Correlation indicates:

- the strength of an association 
- the direction of the relationship
 
The 'cor()` function gives the correlation coefficient for two variables. Actually, if you give it a dataframe, it'll return the correlation coefficient between every possible pair of columns.

*** =instructions
Use the `cor()` function to return the correlation between all pairs of columns in `data`.
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
```

*** =sample_code
```{r}
# Correlation between columns in `data`

```

*** =solution
```{r}
# Correlation between columns in `data`
cor(data)
```

*** =sct
```{r}
test_function('cor', args = 'x')
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:6f843ca2f9
## Correlation (2)

Compare the correlation coefficients with the scatterplots comparing each variable to `a`.

Correlation coefficients range from 0 to 1, with 1 representing the strongest association.

Which type of relationship gives the highest correlation coefficient?

*** =instructions
- No clear association
- linear association
- non-linear association
*** =hint

*** =pre_exercise_code
```{r}
load(url(http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8.Rdata))
par(mfrow = c(2,2))
plot(b ~ a, data = data)
plot(c ~ a, data = data)
plot(d ~ a, data = data)
plot(e ~ a, data = data)
cor(data)
```

*** =sct
```{r}
test_mc(correct = 2)
```


--- type:NormalExercise lang:r xp:100 skills:1 key:70238af6b2
## Linear regression

While correlation indicates the strength and direction of an association, you may need to define the relationship in more detail. Linear regression fits a straight line to the relationship which allows us to predict the response variable from the explanatory variable.

The `lm()` function performs linear regression and you enter data in the same format you used for scatter plots.

*** =instructions
Use the `lm()` function to describe the relationship between 'dist' and 'speed' in the 'cars' dataset.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Linear regression on `dist` against `speed` from `cars`

```

*** =solution
```{r}
# Linear regression on `dist` against `speed` from `cars`
lm(dist ~ speed, ddata = cars)
```

*** =sct
```{r}
test_function("lm", args = c("x", "data"))
```
