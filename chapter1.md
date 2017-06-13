---
title       : Introducing R
description : A first look at how to use R




--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:b09ceba535
## Welcome to the command line!

R is probably quite different to other computer programs you've used because you control it with the *command line*. That means that rather than clicking on icons or menus, you need to *type commands*. Of course the tricky bit is knowing what to type!

So let's get started on something simple. R can be used as a (massively overpowered) calculator. In the **R Console** on the right, just type in the calculation (but leave off the equals sign) and hit enter.

- Type `2 + 4` and hit enter.
- Now try typing the same, but put a hash symbol `#` first.

What was your outcome?

*** =instructions
- R gave the result in both cases
- R gave the result only when # used
- R gave the result only when # not used
- R gave the result in neither case

*** =hint

- Type `2 + 4` and hit enter
- Type `# 2 + 4` and hit enter

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg1 = "Try that again - make sure you type `#` at the start of the line then see if you get an answer to the calculation."
msg2 = "Try that again, and check you've got it the right way round"
msg3 = "Well done. `#` tells R to ignore that line - it's useful for writing comments."
msg4 = "Try that again - carefuly type `2 + 4` and hit enter, then try `# 2 + 4` and hit enter."
test_mc(correct = 3, feedback_msgs = c(msg1, msg2, msg3, msg4))
```



--- type:NormalExercise lang:r xp:100 skills:1 key:57331075c7
## Simple calculations

This time you'll notice there's another panel on the right. You can still try out code in the **R console** at the bottom, but this time you type your answer in the **script.R** panel at the top. When you click **Submit Answer** it'll run your script and tell you if you got it right.

Just be aware that you can use the following operators in R:

`*` multiply
`/` divide
`^` to the power (eg. 3 squared is 3^2)

*** =instructions

Fill in the following calculations in the gaps

- 256 divided by 34
- 2 to the power 4
- The sum of 253 and 34, divided by 12


*** =hint

Below each comment on the right, just type out the calculation.
The first should be `256 / 34`
Try the rest.

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# 256 divided by 34


# 2 to the power 4


# The sum of 253 and 34, divided by 12


```

*** =solution
```{r}
# 256 divided by 34
256 / 34

# 2 to the power 4
2^4

# The sum of 253 and 34 divided by 12
(253 + 34) / 12
```

*** =sct
```{r}
test_output_contains(7.529, incorrect_msg = "Oops, try again")
test_output_contains(16, incorrect_msg = "Oops, try again")
test_output_contains(23.916, incorrect_msg = "Make sure you've got some brackets in the last calculation")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:33ebc4dfc7
## Introducing variables

In R, you use `<-` to store data in variables.

Eg. `a <- 3` assigns the value 3 to the variable 'a'

The arrow points to where the value will be stored.

*** =instructions

Using the example above, assign the value 5 to variable 'b'

*** =hint
Type `<-` by combing the `<` and `-` symbols.
*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Assign 5 to variable b

```

*** =solution
```{r}
# Assign 5 to variable b
b <- 5
```

*** =sct
```{r}
test_object("b")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:a46e1208ed
## Scalar variables

A variable storing a single value is called a **scalar**.

Once you've stored a variable, it's clearly useful to be able to recall it later. You do this by simply typing the variable name.

Eg. to find the value stored in variable `x`, just type `x` and hit enter.

*** =instructions
Complete the code to print the value of b
*** =hint
Type the variable name below the second comment.
*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Assign 5 to variable b
b <- 5

# Print the value of b

```

*** =solution
```{r}
# Assign 5 to variable b
b <- 5

# Print the value of b
b
```

*** =sct
```{r}
test_object("b")
test_output_contains("b")
test_error()
```


--- type:NormalExercise lang:r xp:100 skills:1 key:23c80e0b6e
## Scalar variable types

In addition to storing numbers, variables can also store text or logical values (True or False).

When you're storing text, remember to put it in "quotes".

*** =instructions

Store the word apples in variable c

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Store apples in c


# Print the value of c


```

*** =solution
```{r}
# Store apples in c
c <- "apples"

# Print the value of c
c

```

*** =sct
```{r}
test_object("c")
test_output_contains("c")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:5ef7f7a5e2
## Vector variables

Variables can hold more than one value. These are called **vectors** and you create them using `c()` (the 'c' stands for combine).

Eg. `d <- c(3, 7, 1)` stores a vector of 3, 7, 1 with the label `d` 

*** =instructions
Store the values 2, 4, 6 and 8 in e
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Store 2, 4, 6, 8 in e

```

*** =solution
```{r}
# Store 2, 4, 6, 8 in e
e <- c(2, 4, 6, 8)
```

*** =sct
```{r}
test_object("e")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:dc71438b53
## Accessing vectors

Once you've stored a vector, you can print the whole vector by just entering it's name.

However, you can also access individual values in the vector using square brackets `[]`.

Eg. `d[2]` would access the second value stored in d

*** =instructions
- Print the complete vector e
- Print the third value store in e
*** =hint
*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Store 2, 4, 6, 8 in e
e <- c(2, 4, 6, 8)

# Print the whole vector e


# Print the third value in e


```

*** =solution
```{r}
# Store 2, 4, 6, 8 in e
e <- c(2, 4, 6, 8)

# Print the whole vector e
e

# Print the third value in e
e[3]

```

*** =sct
```{r}
test_object("e")
test_output_contains("e")
test_output_contains(6)
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:d6f620f67e
## Introducing dataframes

Of course, most of the data you'll come across on this course will not be just one or a few values. R can store data in tables called **dataframes**.

We've entered some data about car specifications in a dataframe called `cars`.

*** =instructions
Print the full dataframe
*** =hint
Remember how you printed out variable in previous exercises?
*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Display dataframe

```

*** =solution
```{r}
# Display dataframe
cars
```

*** =sct
```{r}
test_object("cars")
test_output_contains("cars")
test_error()
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8e7905f76c
## Dataframe columns

Did you notice what columns were included in the `cars` dataframe?

Print out the full dataframe in the **R console** on the right. Which columns does it contain?

Tip: you'll notice the list of car names on the left doesn't have a column heading. That's because these are the row names, and not counted as a proper column.

*** =instructions
- mpg, cyl, wt, gear
- mpg, cyl, disp, hp
- cyl, disp, wt, gear
- cyl, hp, wt, carb
*** =hint

*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sct
```{r}
test_mc(correct = 2)
```
--- type:NormalExercise lang:r xp:100 skills:1 key:6681153027
## Dataframe column names

Now you have a list of columns in the `cars` dataframe: mpg, cyl, disp, hp

You can refer to invidual columns in dataframes by their names.

Eg. `cars$mpg` refers to the `mpg` column of the `cars` dataframe.

*** =instructions

Print the `hp` column of the `cars` dataframe

*** =hint
Type the dataframe name, then a dollar sign, then the column name, without any spaces.
*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Print the hp column

```

*** =solution
```{r}
# Print the hp column
cars$hp
```

*** =sct
```{r}
test_output_contains("cars$hp")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:30b9776cde
## Dataframe columns by numbers

You can also use column numbers to access dataframe columns.

Do you remember how we used square brackets to access a single element of a vector? Well you can do the same with dataframes, but since since a dataframe has 2 dimensions you use a comma to distinguish between rows and columns.

The syntax is *dataframe_name*[*row_number*,*column_number*]
If you leave the *row_number* space blank, it will return all the rows.

Eg. `cars[,1]` will return the first column of `cars`

*** =instructions

Return the `disp` column of the `cars` dataframe, using the column number.

Tip: if you can't remember the order of columns, print out the full dataframe in the **R console**. Remember that the row names don't count as a column. 

*** =hint
Type `cars` in the **R console** to display the full dataframe.
Count which column number is `disp`.
Type `cars` and put the column number within square brackets and after a comma.
*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Print the disp column using column number

```

*** =solution
```{r}
# Print the disp column using column number
cars[,3]
```

*** =sct
```{r}
test_output_contains("cars[,3]", incorrect_msg = "Oops, that's not correct. `disp` is the third column and remember that in R the column identifer goes second")
test_student_typed(c("cars[,3]", "cars[ ,3]", "cars[ ,3]", "cars[ ,3 ]"), not_typed_msg = "You need to access `disp` by referring to the column number: it's column 3")
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:9f33ab526f
## Introducing functions

The real power of R lies in its functions.

The functions perform a particular operation on your data. They range from simple to highly complex, but they all use the same format. That is *function_name*(*argument*)

Tip: *argument* in this context just means the input for the function.

Eg. `mean(e)` would return the mean (average) of the values in your vector `e`

*** =instructions
Calculate the mean fuel efficiency (mpg) of the `cars`.

If this seems too tricky, you can always look back through previous exercises using the arrows at the top of the page.

Alternatively, take a hint (but lose some points!).

*** =hint
To do this, you need to remember how to access the `mpg` column of `cars`, using the `$` symbol.

Then you need to give this data to the `mean()` function by typing it between the round brackets.

*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Calculate the mean mpg of cars

```

*** =solution
```{r}
# Calculate the mean mpg of cars
mean(cars$mpg)
```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_function("mean", args = "x", not_called_msg = "You need to use the `mean()` function. Check you typed it correctly", args_not_specified_msg = "You need to specify an input for this function", incorrect_msg = "You've got the right function but not the correct input. Check you're referring to the `mpg` column of `cars` correctly.")

```

--- type:NormalExercise lang:r xp:100 skills:1 key:b5f5f2fd36
## A few more functions

You recall how you can find the columnn names in a dataframe by printing the whole dataframe. Well, that's fine with a small dataframe, but not that helpful when your dataframe has thousands of rows. Here are a few helpful functions to get column names from dataframes:

`names()` returns the column names of a dataframe
`head()` returns the column names and top few rows of a dataframe

In both cases, just put the dataframe name inside the brackets.

*** =instructions
Use both of these functions to return

- column names of `cars`
- top few rows of `cars`
*** =hint

*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# List the column names of cars


# Return the top few rows of cars


```

*** =solution
```{r}
# List the column names of cars
names(cars)

# Return the top few rows of cars
head(cars)


```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_function("names", args = "x")
test_function("head", args = "x")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:8a513ee7f6
## Functions: more arguments

You may have noticed that `head()` actually returned the full dataframe in that last example. That's because `head()` usually returns the first 10 rows and `cars` has only got six rows.

If we just want to return the first 2 rows of a dataframe, we have to enter another argument in the function. In all functions, arguments are separated by commas. In `head()` we need to use the `n = ` argument to define how many rows to return.

Eg. `head(data, n=5)` would return the first 5 rows of `data`

*** =instructions

Return the first 2 rows of `cars`

*** =hint

*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Return the first 2 rows of cars

```

*** =solution
```{r}
# Return the first 2 rows of cars
head(cars, n=2)
```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_function("head", args = c("x","n"))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:f7a008a500
## Graphs

You can also use functions to create graphs.

One of the most useful is the `hist()` function which draws histograms.

*** =instructions
Draw a histogram of horsepower (hp) from `cars`.

If you find this tricky, use the hint.
*** =hint
You need to access the `hp` column from `cars` and enter this information in the `hist()` function by typing it between the brackets.

*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sample_code
```{r}
# Histogram of hp

```

*** =solution
```{r}
# Histogram of hp
hist(cars$hp)
```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_function("hist", args = "x")
success_msg("Before you go on, take a look at the histogram you created")
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:544897a878
## Histograms

Use the **R console** to draw that histogram of `hp` from `cars` again.

Take a look at the data and you'll notice that most of the cars have a similar power. What range of hp do most cars fall within


*** =instructions
- 80 - 100 hp
- 100 - 120 hp
- 120 - 140 hp
- 160 - 180 hp
*** =hint
Type `hist(cars$hp)` in the R console.
*** =pre_exercise_code
```{r}
cars <- mtcars[c(1:6),c(1:4)]
```

*** =sct
```{r}
test_mc(correct = 2)
```


--- type:NormalExercise lang:r xp:100 skills:1 key:0a778d0899
## Revision exercise

Let's see how much you can remember from this session.

*** =instructions

- Store the value 3 in a variable named f
- Store the values 2, 7, 9 and 3 in a vector named g
- Calculate the mean of g
*** =hint
You can look back at previous exercises if you can't remember anything.
You will need to use the following operators and functions:
`<-` `c()` `mean()`
*** =pre_exercise_code
```{r}
```

*** =sample_code
```{r}
# Store 3 in f


# Store 2, 7, 9, 3 in g


# Calculate the mean of g



```

*** =solution
```{r}
# Store 3 in f
f <- 3

# Store 2, 7, 9, 3 in g
g <- c(2, 7, 9, 3)

# Calculate the mean of g
mean(g)


```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_object("f")
test_object("g")
test_function("mean", args = "x")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:25ba817d71
## Revision exercise 2

A bit more revision...

You've been given a dataframe `people`.

*** =instructions
Perform the following operations on this dataframe.

- List the column names of `people`
- Calculate the mean height
- Draw a histogram of ages
*** =hint
You'll need to use the following functions: `hist()` `names()` `mean()`
*** =pre_exercise_code
```{r}
people <- data.frame(age = c(23,27,21,19,43,22), gender = c("m", "f", "f", "m", "f", "m"), height = c(177, 165, 172, 173, 161, 169))
```

*** =sample_code
```{r}
# List column names of people


# Calculate mean height of people


# Draw histogram of ages from people



```

*** =solution
```{r}
# List column names of people
names(people)

# Calculate mean height of people
mean(people$height)

# Draw histogram of ages from people
hist(people$age)

```

*** =sct
```{r}
test_error(incorrect_msg = "Your code produces an error. Carefully check the spelling and syntax of your entry.")
test_function("names", args = "x")
test_function("mean", args = "x")
test_function("hist", args = "x")
```