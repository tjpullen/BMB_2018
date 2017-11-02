---
title       : STAT2 - Introducing Exploratory Data Analysis
description : Taking a first look at the data



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:5035c2a062
## Data Layout

Before we start looking at the data, it's helpful to get it into the correct format.

The standard layout has each column representing a different variable (eg. height, sex, BMI), and each row representing a different subject or replicate.

This differs from the layout people often use with spreadsheets where they put each condition (eg treated/untreated) in separate columns.

Take a look at the `mice_1` and `mice_2` dataframes by printing them in the **R Console**. These give the weight of mice and their genotype ('WT' is wild-type and 'KO' is knock-out).

Which dataframe(s) is/are in the standard layout?

*** =instructions
- Neither in standard layout
- `mice_1` in standard layout
- `mice_2` in standard layout
- Both in standard layout
*** =hint
Remember you can just type the dataframe name in the **R Console** to view it.

If you're not sure which layout is correct, check the column names: each should represent a different measurement, not the same measurement under different conditions.
*** =pre_exercise_code
```{r}
mice_1 <- data.frame(WT = c(28, 29, 29, 31), KO = c(26, 31, 27, 30))
mice_2 <- data.frame(genotype = c("WT", "KO", "WT", "KO", "WT", "KO", "WT", "KO"), weight = c(28, 26, 29, 31, 29, 27, 31, 30))
```

*** =sct
```{r}
test_mc(correct = 3)

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0ecf808280
## Data Layout 2

If you're wondering why we arrange the data like that, consider this:
Say we want to record some additional information about the mice. For example the sex of the mice.

Take another look at `mice_1` and `mice_2`. Which layout can accommodate additional data more easily?

*** =instructions
- Neither
- `mice_1`
- `mice_2`
- Both

*** =hint
How would you insert the sex of the mice into each dataframe? It's much easier with one of them.
*** =pre_exercise_code
```{r}
mice_1 <- data.frame(WT = c(28, 29, 29, 31), KO = c(26, 31, 27, 30))
mice_2 <- data.frame(genotype = c("WT", "KO", "WT", "KO", "WT", "KO", "WT", "KO"), weight = c(28, 26, 29, 31, 29, 27, 31, 30))
```

*** =sct
```{r}
test_mc(correct = 3)
success_msg("That's right! You could just add `sex` as an additional column to `mice_2`. It's hard to see how you'd add it to `mice_1`")
```
--- type:NormalExercise lang:r xp:100 skills:1 key:305787a638
## Data Layout 3

Now we've got the data in the standard layout, let's take a closer look.

*** =instructions

- List the column names in `mice`
- Print the whole `mice` dataframe
*** =hint
You need to use the `names()` function to list column names.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# List column names in mice


# Print mice dataframe


```

*** =solution
```{r}
# List column names in mice
names(mice)

# Print mice dataframe
mice

```

*** =sct
```{r}
test_function("names", args = "x")
test_output_contains("mice")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2cab1b45d3
## Data Layout 4

Print out the `mice` dataframe again in the **R Console**.

These data relate to a transgenic mouse line.

The columns are:

* Weight - weight of mice in grams
* Sex - sex of mice coded as 1 = female, 2 = male.
* Genotype - genotype of mice coded as WT = wild type, KO = knock-out for the gene of interest.
 
How many mice are there in this dataset?

*** =instructions
- 10
- 20
- 60
- 80

*** =hint
There is one individual or replicate per line in this layout. In this case, one mouse per line.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sct
```{r}
test_mc(correct = 2)
```
--- type:NormalExercise lang:r xp:100 skills:1 key:54d9179ca8
## Plotting Data

Did you spot any trends or patterns in the data?

Actually, it's pretty hard to make sense of a list of numbers like that by just eyeballing them, and impossible with large datasets. It's easier to use summary statistics or graphs to give an overall impression of the data.

Let's take a look at the distribution of mouse weights in a histogram.

*** =instructions

Use the `hist()` function to plot a histogram of the `weight` column of `mice`.

*** =hint

Remember last week you used `hist(cars$hp)` to plot a histogram of the `hp` column of the `cars` dataframe. Can you work out how to do the same with this data?

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# Plot a histogram of the weight column of mice

```

*** =solution
```{r}
# Plot a histogram of the weight column of mice
hist(mice$weight)
```

*** =sct
```{r}
test_function("hist", args = "x")

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2a26719018
## Histograms

Plot the histogram of weights again in the **R Console** and press enter, then take a closer look at it.

This shows the weight distribution of the mice, with most mice concentrated around a peak. Most mice are close in weight to the peak value with fewer mice showing greater difference.

What is the approximate value of this peak?

*** =instructions
- 27
- 29
- 31
- 33
- 35
*** =hint

Type the same command as you did in the previous exercise. Click the left arrow at the top to go back and have a look if you've forgotten.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sct
```{r}
test_mc(correct = 2)
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:df2e61f034
## Histograms 2

Plot the histogram of weights again in the **R Console**, and take another look at it.

What is the approximate shape of this distribution?

*** =instructions
- Flat
- Left-skewed
- Normal
- Right-skewed
*** =hint

If you're unclear what these terms mean, look them up in a text book or search on the internet.

Briefly,
- a flat distribution is where all outcomes are equally likely, so the distribution is a flat line.
- a normal distribution is a symmetrical 'bell-shaped' curve.
- a left-skewed distribution could be similar to the normal distribution but has a longer 'tail' of data points extending further to the left of the peak than the right.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sct
```{r}
test_mc(correct = 3, feedback_msgs = c("Incorrect. A flat distribution would have roughly equal numbers of mice at each weight", "Incorrect. There is no tail on the left-hand side of the distribution", "Correct. Although not perfectly symmetrical, these data are approximately normally distributed", "Incorrect, but an understandable mistake. The 2 mice over 34 give the impression of a longer tail on the right of the distribution. Although not perfectly symmetrical, these data are approximately normally distributed"))
```
--- type:NormalExercise lang:r xp:100 skills:1 key:e3d4c6e324
## Boxplots

Boxplots are way to summarise data graphically. These provide less information than histograms, but can make it easier to compare data.

*** =instructions
Use the `boxplot()` function to plot the `weight` column from `mice`.
*** =hint

You enter exactly the same argument in the `boxplot()` function as you used for the `histogram()` function in the previous exercise.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# Generate a boxplot of the weight column from mice

```

*** =solution
```{r}
# Generate a boxplot of the weight column from mice
boxplot(mice$weight)
```

*** =sct
```{r}
test_function("boxplot", args = "x")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:5db9edaedd
## Boxplots 2

Plot the boxplot of weights again in the **R Console**, and take a closer look at it.

The thick line in the middle shows the median value. The box around that shows 1st and 3rd quartiles. The 'whiskers' reaching outside the box show the overall range of values.

By definition, a quarter of the values will fall within each quartile. Approximately half of the weight values will fall within which interval?

**Tip:** If the plot is too small, resize it by dragging the boundaries. Alternatively, click the double arrow symbol in the **Plots** tab to view it in a pop-up window (you may have to allow pop-ups).

*** =instructions
- 24 - 28
- 28 - 29
- 24 - 36
- 31 - 36
- 28 - 31
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sct
```{r}
test_mc(correct = 5)
```


--- type:NormalExercise lang:r xp:100 skills:1 key:ebc8f12e72
## Boxplots by Group

As I mentioned, boxplots are useful for quickly comparing data. In this case let's see whether the weight of mice depends on their genotype.

The `boxplot()` function can produce multiple plots if you give it a variable to group the data by. We do this in the format `boxplot(a ~ b)`, where `a` is the variable that is plotted and `b` is the variable for grouping the data.

Of course if `a` and `b` are columns in dataframe `data`, you would need to include the dataframe name too: `boxplot(data$a ~ data$b)`

*Tip:* Get used to the `a ~ b` format since it's widely used in statistics. More generally, the arguments to the left of the ~ are the *response* variable(s) and the *explanatory* variables.

*** =instructions
Produce a boxplot of `weight` grouped by `genotype` from the `mice` dataframe.

*** =hint

Remember you previously typed `boxplot(mice$weight)`. Now you need to add the grouping symbol `~` followed by the grouping variable `mice$genotype` inside the brackets.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# Boxplot of weight grouped by genotype

```

*** =solution
```{r}
# Boxplot of weight grouped by genotype
boxplot(mice$weight ~ mice$genotype)
```

*** =sct
```{r}
test_function("boxplot", args = "formula")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:bc520bbc5f
## Summary Statistics

Plots are great for visually comparing data, but it's also useful to have a numerical summary.

The `summary()` function neatly and easily provides several summary statistics.

*** =instructions
Use the `summary()` function to produce summary statistics for `weight` from the `mice` dataframe.

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# Summary statistics of weight

```

*** =solution
```{r}
# Summary statistics of weight
summary(mice$weight)
```

*** =sct
```{r}
test_function("summary", args = "object")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4d7138ed9f
## Summary Statistics 2

Produce the summary statistics for `mice$weight` again in the **R Console** and take a look at the output.

Which of the following is *not* given.

*** =instructions
- median
- first quartile
- mean
- number of values
- maximum value
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sct
```{r}
test_mc(correct = 4)
```


--- type:NormalExercise lang:r xp:100 skills:1 key:75c91d9b3f
## Dataframe Summary Statistics

The `summary()` function is nice because you can just give it a whole dataframe, and it'll summarise each column.

*** =instructions

Produce summary statistics for the whole `mice` dataframe.

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
```

*** =sample_code
```{r}
# Summary statistics for mice

```

*** =solution
```{r}
# Summary statistics for mice
summary(mice)
```

*** =sct
```{r}
test_function("summary", args = "object")
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:9bcf0ecb66
## Variable Types

First, take a look at the whole `mice` dataframe in the **R console**.

Then, take another look at the summary statistics for `mice`.

Which columns are summarised in a useful way by the `summary()` function?

*** =instructions
- weight
- sex
- genotype
- weight and sex
- weight and genotype
- sex and genotype
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
```

*** =sct
```{r}
test_mc(correct = 1, feedback_msgs = c("Correct!", "Incorrect. Although it calculates the mean, median, etc for `sex` it doesn't make much sense. What does a mean sex of 1.6 actually mean?", "Incorrect. The output for `genotype` is pretty cryptic.", "Incorrect. Although it calculates the mean, median etc. for `sex` it doesn't make much sense. What does a mean sex of 1.6 actually mean?", "Incorrect. The output for `genotype` is pretty cryptic", "Incorrect. The output for `genotype` is pretty cryptic."))
```



--- type:NormalExercise lang:r xp:100 skills:1 key:c6cde06965
## Categorical Variables

Let's deal with `sex` first.

`sex` isn't a **numerical variable**. Although it's stored as numbers here, those numbers are just code for female/male and have no intrinsic meaning as numbers. Calculating the median or mean isn't very useful. A better summary would just be to know the number of female and male mice. To get this, we first need to tell R that `sex` is a **categorical variable**.

Categorical variables are called **factors** in R.
You use the `factor()` function to convert numerical values to factors.

*** =instructions

- Print out the `sex` column from `mice`.
- Now use the `factor()` function to convert the `sex` column from `mice` into a factor

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
```

*** =sample_code
```{r}
# Print the sex column from mice


# Convert the sex column from mice to a factor


```

*** =solution
```{r}
# Print the sex column from mice
mice$sex

# Convert the sex column from mice to a factor
factor(mice$sex)


```

*** =sct
```{r}
test_function("factor", args = "x")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:74cf0d7f9b
## Storing Categorical Variables

Although you converted `sex` into a factor, the output won't be stored unless you tell it to.

So you should now store the data in that format. You do that by assigning the converted data to the `sex` column, where it will overwrite the current column contents.

**Note:** Use the `class()` function to display how `sex` is stored before and after the conversion.

*** =instructions

- Convert the `sex` column into a factor again, but this time assign this (store it in) to the `sex` column.
- Display how the `sex` colum is stored after the conversion using the `class()` function.

*** =hint

Remember you use `<-` to assign some data to a variable. This works with columns as well. So your code should start with `mice$sex <-` to assign the converted data to the sex column.

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
```

*** =sample_code
```{r}
# Print the sex column from mice
mice$sex

# Convert the sex column from mice to a factor
factor(mice$sex)

# Convert the sex column from mice to a factor and store in the sex column of mice


# Storage format of sex after conversion


```

*** =solution
```{r}
# Print the sex column from mice
mice$sex

# Convert the sex column from mice to a factor
factor(mice$sex)

# Convert the sex column from mice to a factor and store in the sex column of mice
mice$sex <- factor(mice$sex)

# Storage format of sex after conversion
class(mice$sex)

```

*** =sct
```{r}
test_function("factor", args = "x", index = 1)
test_function("factor", args = "x", index = 2)
test_function("class", args = "x")

```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:7113b53b22
## Summarising Categorical Variables

Now you've converted `sex` to the appropriate format, produce summary statistics for the `mice` dataframe in the **R Console**.

How many female mice are there in the dataset?

Note: the coding is female = 1, male = 2.

*** =instructions
- 1
- 2
- 8
- 12
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
mice$sex <- factor(mice$sex)
```

*** =sct
```{r}
test_mc(correct = 3)
```



--- type:NormalExercise lang:r xp:100 skills:1 key:5f14737159
## Storing Categorical Variables 2

Now that `sex` is stored correctly, let's take a look at `genotype`.

`genotype` is currently stored as character data, meaning it's made up of text characters. You can convert this to a factor in the same way as for `sex`.

*** =instructions

Convert the `genotype` column to a factor and store the converted values back in the `genotype` column.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
mice$sex <- factor(mice$sex)
```

*** =sample_code
```{r}
# Convert genotype column to factor

```

*** =solution
```{r}
# Convert genotype column to factor
mice$genotype <- factor(mice$genotype)

```

*** =sct
```{r}
test_function("factor", args = "x")
```
--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:407ebc6976
## Summarising Categorical Variables 2

Great. Now check your conversion by producing summary statistics for the `mice` dataframe in the **R Console**.

All three variables are now summarised in a sensible way.

How many wild-type mice are in the dataset?
*** =instructions
- 6
- 8
- 12
- 14

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
mice$sex <- factor(mice$sex)
mice$genotype <- factor(mice$genotype)
```

*** =sct
```{r}
test_mc(correct = 1)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:b77229794d
## Summary Statistics by Group

Remember how you produced boxplots by group?

You used this command to plot mouse weights grouped by genotype: `boxplot(mice$weight ~ mice$genotype)`

Wouldn't it be handy to produce summary statistics by group too?

The easiest way to do this is using the `describeBy()` function.

This function takes two arguments in the format `describeBy(a, group = b)` where `a` is the object to be summarised and the data is grouped by variable `b`.

**Tip:** unlike the functions we've used so far, `describeBy()` isn't a *base function* (ie. comes pre-installed). Instead it's part of the `psych` package which you'll need to install if you want to use this function on your own computer. We've installed and loaded the package here to save time.

*** =instructions

Summarise the `weight` column from `mice` grouped by `genotype` using the `describeBy` function.

*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
mice$sex <- factor(mice$sex)
mice$genotype <- factor(mice$genotype)
library(psych)
```

*** =sample_code
```{r}
# Summary statistics for weight grouped by genotype

```

*** =solution
```{r}
# Summary statistics for weight grouped by genotype
describeBy(mice$weight, group = mice$genotype)

```

*** =sct
```{r}
test_function("describeBy", args = c("x", "group"))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8564df1c6c
## Summary Statistics by Group 2

Take another look at `weight` summarised by `genotype` in the console.

This function produces more numbers than `summary()`, so it's less clear.

Can you work out what the mean `weight` of wild-type mice is?

*** =instructions
- 28.45
- 28.86
- 30.02
- 30.15
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_4315/datasets/mice5.rdata"))
mice <- mice[,c(3,1,2)]
mice$sex <- factor(mice$sex)
mice$genotype <- factor(mice$genotype)
library(psych)
```

*** =sct
```{r}
test_mc(correct = 1)
success_msg("You've completed the pre-session material for STAT2")
```