---
title       : Hypothesis Testing
description : Introducing hypothesis testing





--- type:VideoExercise lang:r xp:50 skills:1 key:b6260c0853
## Hypothesis testing


*** =video_link
//player.vimeo.com/video/227739062



--- type:VideoExercise lang:r xp:50 skills:1 key:0c94221b8b
## Is it a fair coin?


*** =video_link
//player.vimeo.com/video/227743190



--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:e5019bee9f
## Is it a fair coin? (2)

Which of the following do you do when $p < \alpha$ ?
*** =instructions
- accept the null hypothesis
- reject the alternative hypothesis
- reject the null hypothesis
- accept the alternative hypothesis

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 3)
```



--- type:VideoExercise lang:r xp:50 skills:1 key:f18d570d6a
## One tail or two?


*** =video_link
//player.vimeo.com/video/227745553



--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:8276675a79
## One tail or two? (2)

You've just seen a probability distribution with the critical region for a two-tailed test shaded red.

What percentage of the distribution was covered by the critical region?

*** =instructions
- 1%
- 2.5%
- 5%
- 10%
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 3)
```



--- type:VideoExercise lang:r xp:50 skills:1 key:6a1acb028b
## The binomial test in R


*** =video_link
//player.vimeo.com/video/227746218

--- type:NormalExercise lang:r xp:100 skills:1 key:5d094e21fe
## The binomial test in R (2)

You've just seen how to use the `binom.test()` function and now it's your turn.

*** =instructions

Perform a binomial test on the probability of getting 59 heads from 100 throws of a hypothetically fair coin.

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Binomial test on 59 heads from 100 throws

```

*** =solution
```{r}
# Binomial test on 59 heads from 100 throws
binom.test(59, 100, 0.5)

```

*** =sct
```{r}
test_function("binom.test", args = c("x", "n", "p"))
```



--- type:VideoExercise lang:r xp:50 skills:1 key:18228d8d30
## What is a p value?


*** =video_link
//player.vimeo.com/video/227747288


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:e8ee19a7a2
## What is a p value? (2)

The *p* value is the probability of...

*** =instructions
- getting the observed result due to chance
- getting the observed result assuming the null hypothesis is true
- getting the observed or a more extreme result assuming the null hypothesis is true
- getting a false negative
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 3)
```


--- type:VideoExercise lang:r xp:50 skills:1 key:4c7caf8521
## Possible outcomes of hypothesis tests


*** =video_link
//player.vimeo.com/video/227749035







--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:b70d5af5e7
## Possible outcomes of hypothesis tests (2)

Take a look at the plot on the right.

Do you think the probability of getting a false negative result with the blue distribution is approximately...

*** =instructions
- 0.5 %
- 2%
- 10%
- 50%
- 97%
*** =hint

*** =pre_exercise_code
```{r}
barplot(dbinom(30:90, 100, 0.5), names.arg = 30:90, space = 0, main = "100 coins", xlab = "No of heads", ylab = "Probability", col = "white", border = rgb(0,0,0,0.5))
barplot(dbinom(30:90, 100, 0.7), space = 0, col = rgb(0, 0, 0, 0), border = "blue", add = T)
#barplot(c(dbinom(30:39, 100, 0.5), rep(0, 21), dbinom(61:90, 100, 0.5)), space = 0, col = rgb(1,0,0,0.5), border = rgb(0,0,0,0.5), add = T)
barplot(c(dbinom(30:60, 100, 0.7), rep(0, 30)), space = 0, col = "blue", add = T)
abline(v = 31, col = "red")

```

*** =sct
```{r}
test_mc(correct = 2)
```
--- type:VideoExercise lang:r xp:50 skills:1 key:dc0eebd374
## Power


*** =video_link
//player.vimeo.com/video/227751750


--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:b06700136e
## Power (2)

Which of the following will result in the most statistically powerful experiment?

*** =instructions
- low dispersion and low difference between peaks
- high dispersion and high difference between peaks
- low dispersion and high difference between peaks
- high dispersion and low difference between peaks
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 3)
```

--- type:VideoExercise lang:r xp:50 skills:1 key:ba89b22b24
## Key points


*** =video_link
//player.vimeo.com/video/227754182
