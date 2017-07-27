---
title       : Probability and Risk
description : Understanding uncertainty


--- type:VideoExercise lang:r xp:50 skills:1 key:a234a254b1
## Welcome to uncertainty


*** =video_link
//player.vimeo.com/video/227280339


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:cd4dd49ae9
## How am I going to die?

What is the risk of being killed by lightning in the next year?

*** =instructions
- 1 in 8000
- 1 in 50 000
- 1 in 500 000
- 1 in 30 000 000
- 1 in 40 000 000
- 1 in 45 000 000
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 4)
```


--- type:VideoExercise lang:r xp:50 skills:1 key:94eafe5ef2
## What is probability?


*** =video_link
//player.vimeo.com/video/227283943


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:d639cec9ad
## Probability is...

Which is the best definition of probability?


*** =instructions

- The exact proportion of a small number of independent trials which give a particular outcome.
- The approximate proportion of a small number of independent trials which give a particular outcome.
- The exact proportion of a large number of independent trials which give a particular outcome.
- The approximate proportion of a large number of independent trials which give a particular outcome.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 4)
```


--- type:VideoExercise lang:r xp:50 skills:1 key:dca74ed106
## What's with the dice?


*** =video_link
//player.vimeo.com/video/227285286


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:068f66a92b
## Mutually exclusive outcomes

When throwing a die, which of the following are NOT mutually exclusive outcomes?

*** =instructions
- 1 or 6
- 1 or an even number
- <3 or 6
- <2 or an even number
- <3 or an even number
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 5)
```

--- type:VideoExercise lang:r xp:50 skills:1 key:a725b73ff0
## Probability distributions


*** =video_link
//player.vimeo.com/video/154783078


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:4e27ebef89
## Independent events

Which of the following are NOT independent events?

*** =instructions
- Tossing two coins
- option 3
- Throwing the same die twice
- option 4
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 2)
```


--- type:VideoExercise lang:r xp:50 skills:1 key:302535fefd
## Probability vs frequency distributions


*** =video_link
//player.vimeo.com/video/154783078



--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:8a8676de5d
## Probability vs frequency distributions (2)

Which distribution remains the same as the number of repliates increases?

*** =instructions
- Probability distribution
- Frequency distribution
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 1)
```


--- type:VideoExercise lang:r xp:50 skills:1 key:0fa695235f
## The binomial distribution


*** =video_link
//player.vimeo.com/video/154783078


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:52c2118876
## The binomial distribution (2)

Which of the following is NOT an example of a binomial distribution.

*** =instructions
- The likelihood of getting 2 wild-type offspring in a litter of 5 (from crossing two heterozygotes).
- The number of coins you have to toss to get 3 heads.
- The proportion of '6s' you get from throwing 3 dice.
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 2)
```

--- type:VideoExercise lang:r xp:50 skills:1 key:fcc69d0787
## The binomial distribution in R


*** =video_link
//player.vimeo.com/video/154783078


--- type:NormalExercise lang:r xp:100 skills:1 key:29adcc84b0
## Binomial calculations

Now it's your turn to have a go.

Remember the `dbinom()` function takes these arguments:
`dbinom(x, size, prob)`

*** =instructions
What is the probability of getting **exactly 3 heads** from 4 coins?
*** =hint

*** =pre_exercise_code
```{r}
barplot(dbinom(0:4, 4, 1/2), names.arg = 0:4, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "4 coins")
barplot(c(rep(0,3),dbinom(3, 4, 1/2),rep(0,1)), names.arg = 0:4, space = 0, col = "red", add = T)
```

*** =sample_code
```{r}
# The probability of getting 3 heads from 4 coins


```

*** =solution
```{r}
# The probability of getting 3 heads from 4 coins
dbinom(3, size = 4, prob = 0.5)

```

*** =sct
```{r}
test_function("dbinom", args = c("x", "size", "prob"))
```

--- type:VideoExercise lang:r xp:50 skills:1 key:8db7a7a20e
## Cumulative probability function


*** =video_link
//player.vimeo.com/video/154783078

--- type:NormalExercise lang:r xp:100 skills:1 key:bf295d9c99
## Binomial calculations (2)

Now it's your turn to have a go.

Remember the `pbinom()` function takes the same arguments as `dbinom()`

*** =instructions
What is the probability of getting **up to 3 heads** from 6 coins?
(ie. 0, 1, 2 or 3 heads)
*** =hint

*** =pre_exercise_code
```{r}
barplot(dbinom(0:6, 6, 1/2), names.arg = 0:6, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "6 coins")
barplot(c(dbinom(0:3, 6, 1/2),rep(0,3)), names.arg = 0:6, space = 0, col = "red", add = T)
```

*** =sample_code
```{r}
# The probability of getting up to 3 heads from 6 coins


```

*** =solution
```{r}
# The probability of getting up to 3 heads from 6 coins
pbinom(3, size = 6, prob = 0.5)

```

*** =sct
```{r}
test_function("pbinom", args = c("q", "size", "prob"))
```


--- type:VideoExercise lang:r xp:50 skills:1 key:9b2741b943
## Discrete vs continuous variables


*** =video_link
//player.vimeo.com/video/154783078


--- type:NormalExercise lang:r xp:100 skills:1 key:35334c600a
## Normal distribution calculations

The `pnorm()` function works just like the `pbinom()` function to calculate the cumulative probability, but of the normal distribution rather than the binomial. It takes the following arguments:

`pnorm(x, mean, sd)`

*** =instructions
What proportion of 19-year-old males would you expect to be under 170 cm tall?

- Mean = 176.5 cm
- Standard deviation = 7.30

*** =hint

*** =pre_exercise_code
```{r}
mean = 176.5
sd = 7.30
lb = 150
ub = 170
x <- seq(150, 205, length.out = 1000)
hx <- dnorm(x, mean = mean, sd = sd)
plot(x, hx, type = "n", xlab = "Height (cm)", ylab = "Probability", main = "Male Height at 19 years")
i <- x >= lb & x <= ub
lines(x, hx)
polygon(c(min(x[i]), x[i], max(x[i])), c(0, hx[i], 0), col = "red")
```

*** =sample_code
```{r}
# Proportion of 19-year-old males <170 cm


```

*** =solution
```{r}
# Proportion of 19-year-old males <170 cm
pnorm(170, mean = 176.5, sd = 7.30)

```

*** =sct
```{r}
test_function("pnorm", args = c("q", "mean", "sd"))
```
