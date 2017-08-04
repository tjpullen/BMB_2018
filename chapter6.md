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
# test_function("plot", args = c("formula", "data"))
test_function("plot")
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

Great! The positive linear relationship was fairly clear to spot. It shows what you probably suspected, that as the speed increases, the distance required to stop a car also increases.

For the rest of the chapter we'll also use a dataframe called `data`. This contains five continous variables in separate columns (labelled `a` to `e`), and you'll investigate whether each of them is associated with column `a`.

Let's start by seeing if the data in column `b` is associated with `a` with a scatter plot.

*** =instructions
Plot `b` against `a` from dataframe `data` using the plot() function. (ie. `b` explained by `a`).
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))

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
test_function('plot', args = c('formula', 'data))
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
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
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
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
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
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
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
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
plot(e ~ a, data = data)
```

*** =sct
```{r}
test_mc(correct = 3)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:c373d5a45c
## A shortcut for scatter plots

If you want to draw scatter plots between several columns of a dataframe, the `pairs()` function is handy.

You just enter the name of the dataframe as the argument for this function and it returns a scatterplot for each pair of columns.

Try it with `data`.

*** =instructions
Draw scatter plots between each column of `data` using the `pairs()` function.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
```

*** =sample_code
```{r}
# Pairwise scatter plots of data


```

*** =solution
```{r}
# Pairwise scatter plots of data
pairs(data)


```

*** =sct
```{r}
test_function("pairs", args = "x")
```
--- type:NormalExercise lang:r xp:100 skills:1 key:72c39a1ab0
## Correlation

Visually inspecting a scatter plot gives a good indication of the association between two variables. However, you will often need to quantify this.

Correlation gives a measure of:

- the strength of an association 
- the direction of the relationship
 
The `cor()` function gives the correlation coefficient for two variables. Actually, if you give it a dataframe, it'll return the correlation coefficient between every possible pair of columns.

*** =instructions
Use the `cor()` function to return the correlation between all pairs of columns in `data`.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
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
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/STAT8v2.rdata"))
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

While correlation indicates the strength and direction of an association, you may need to define the relationship in more detail. Linear regression fits a straight line to the relationship which then allows us to predict the response variable from the explanatory variable.

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
lm(dist ~ speed, data = cars)
```

*** =sct
```{r}
test_function("lm", args = c("formula", "data"))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:9411f0e035
## Linear regression (2)

Type `lm(dist ~ speed, data = cars)` into the console and look at the output.

The general formula for a line is: $$y = ax + b$$
Where

- $a$ is the slope
- $b$ is the intercept
- $x$ is the explanatory variable
- $y$ is the response variable

You should be familiar with the formula of a straight line from school maths. Take a look at the output and see if you can work out what the slope of the line is.

*** =instructions
- -17.579
- 3.932
*** =hint

*** =pre_exercise_code
```{r}
lm(dist ~ speed, data = cars)
```

*** =sct
```{r}
test_mc(correct = 2)
```


--- type:NormalExercise lang:r xp:100 skills:1 key:44b471e84d
## Linear Regression (3)

You can use the output of `lm()` for a variety of purposes.

Firstly, let's use it to plot the fitted line on a scatter plot. You can do this by saving the output of `lm()` to an object, then use this object as the argument in the `abline()` function (which draws a straight line over a plot).

*** =instructions
- Generate a scatter plot of `dist` against `speed` from `cars`.
- Use the `lm()` function on `dist` and `speed` and direct the output to an object called `fit`
- Use the `abline()` function to draw the line determined by `fit`
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Generate a scatter plot of dist against speed from cars


# Store the output of lm() on dist and speed in fit
fit <- 

# Add the fitted line to the scatter plot


```

*** =solution
```{r}
# Generate a scatter plot of dist against speed from cars
plot(dist ~ speed, data = cars)

# Store the output of lm() on dist and speed in fit
fit <- lm(dist ~ speed, data = cars)

# Add the fitted line to the scatter plot
abline(fit)

```

*** =sct
```{r}
test_function("plot", args = c("formula", "data"))
test_function("lm", args = c("formula", "data"))
test_function("abline", args = "a")

```




--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:9d6dd0aa65
## Linear Regression (4)

Take a look at the plot. Do you think the line is a good fit through the points?

In a good fit, the line should go through the middle of the points and the point should


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
# Generate a scatter plot of dist against speed from cars
plot(dist ~ speed, data = cars)

# Store the output of lm() on dist and speed in fit
fit <- lm(dist ~ speed, data = cars)

# Add the fitted line to the scatter plot
abline(fit)
```

*** =sct
```{r}

```
--- type:VideoExercise lang:r xp:50 skills:1 key:76ab416d66
## Fitted values and residuals


*** =video_link
//player.vimeo.com/video/228184212



--- type:NormalExercise lang:r xp:100 skills:1 key:a93eb24885
## Fitted values and residuals (2)



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
--- type:NormalExercise lang:r xp:100 skills:1 key:c31076e0c5
## Linear Regression Output


*** =instructions
Use the `summary()` function to give a detailed output of `fit`
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Store the output of lm() on dist and speed in fit
fit <- lm(dist ~ speed, data = cars)

# Summary of fit


```

*** =solution
```{r}
# Store the output of lm() on dist and speed in fit
fit <- lm(dist ~ speed, data = cars)

# Summary of fit
summary(fit)

```

*** =sct
```{r}
test_function("summary", args = "object")
```
