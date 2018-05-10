Statistics!
---

- statistics in R
	- the good: easy to do
	- the bad: easy to do
- it can be so easy to do stats in R that you can get away with not really understanding what you are doing
- solution?
	- start with a hypothesis
	- visualize
	- build your intuition
	- test it
	
# Correlations

- what does a correlation measure?
- two versions
	- Pearson's: assumes normality
	- Spearman's: doesn't
- HYPOTHESIZE FIRST & THEN PLOT & THEN TEST
- `cor.test`
- Let's see if there is a correlation between showers taken and beer drunk

## Questions Set 1

1. Let's think about beer and coffee consumption. From what you know about these two things, would you think they would be correlated? Why or why not? 
		- Plot them. Do they look correlated?
		- Test if they are correlated. What is the p-value?
		- What does p-value mean again?
		- Was the approach you used a Pearson or a Spearman? (_Hint_: look at the output.)
		- Redo it to use the other approach. (_Hint_: don't know how? remember the different ways to get help.)
		- Which approach do you think is better for these data? Why?
2. What does a negative correlation mean vs. a positive correlation?
3. Test the correlation between age and shower.  From what you know about these two things, would you think they would be correlated? Why or why not? 
	- Plot them. Do they look correlated?
	- Test if they are correlated. What is the p-value?

# ANOVA

- I am not going to cover t-test, which is a special case of the ANOVA
- ANOVAs: used to tell if groups are different
- HYPOTHESIZE FIRST & THEN PLOT & THEN TEST
- `aov`, `summary`, and `TukeyHSD`
- Let's see if population type affects showers taken

## Question Set 2

1. Let's think about beer consumption & the different populations. From what you know about beer consumption, do you think it might differ across gropus? Why or why not? 
	- Plot them. Do the means look different across populations?
	- Does the variance (or, spread) look different across populations?
	- Test if they are different doing an ANOVA. What is the p-value?
	- If the p-value is significant, use a Tukey's HSD test to determine which groups, if any, are different.
	- Which groups are different? Is this similar to what you expected based on the boxplot?
2. Let's think about beer consumption & different genders, as well. We can test if the genders have different beer consumption. Do that analysis.
3. If you have multiple factors (in this case, gender and population), you can combine them into one ANOVA. There are two ways of including multiple factors, which mean different things statistically.
		
	```
	aov(DEPENDENT_VAR ~ INDEPENDENT_VAR1 + INDEPENDENT_VAR2)
	aov(DEPENDENT_VAR ~ INDEPENDENT_VAR1 * INDEPENDENT_VAR2)
	```
Try them out, and look at the difference in output. What is the difference? What are they telling you? It helps to follow up running the ANOVA using Tukey's HSD to know for sure.
4. Challenge yourself to figure out how to create one boxplot that shows populations on the X-axis, and for each population, has one box for females and another for males. (_Hint_: I would google ggplot2 and boxplot, and scroll through the pages to find one that has a graph like the one I want to see how to do it.)

# Linear Regression

- Asks if there is a linear relationship between one or more variables and a dependent variable
- Basically, a way of building a model to predict the values of the dependent variable
- A key question to always ask: "how good is my model at predicting things?"
- STATISTICAL SIGNIFICANCE DOES NOT MEAN BIOLOGICAL SIGNIFICANCE
- very similar format to `aov`
	
	```
	MY_LM = lm(DEPENDENT_VAR ~ INDEPENDENT_VAR1 + INDEPENDENT_VAR2)
	MY_LM = lm(DEPENDENT_VAR ~ INDEPENDENT_VAR1 * INDEPENDENT_VAR2)
	```

- build a linear model that predicts the amount of coffee drunk by at least two other variables that you think might be related
- `summary(MY_LM)` tells you which explanatory variables are significant and how good your model is overall (r-squared)
- `coefficients(MY_LM)` tells you about the coefficients before each independent variable
	- what do you think a negative coefficient means?
	
# PCA (Principal Component Analysis)

- PCAs are a way to simplify very complex data (much of might be correlated) into a few variables
- In this case, we could take all the data on beer, showers, etc and see if we can summarize them into a few variables
- This is super useful for a case when you have a ton of data (for example, you have lots of genes or when you have many different measures of climate)
- This is a challenge exercise -- I am going to guide you through it for you to do on your own

## Instructions

1. Create a data frame that just has the columns that correspond to patterns (i.e., consumption and shower habits)
2. Use `prcomp` to run a PCA on this data frame. (_Hint_: you will want to decide if you should use the `scale` flag or not. Read the help file to decide. Or do a Google to decide.)
3. Look at the PCA results. The key command is `summary(PCA_RESULTS)`, which will tell you how many new variables were created (PC1, PC2, etc.) that summarize the data and how much of the variation they explain. How many variables did you start with? If you just keep PC1 and PC2, how many do you end up with?
4. Next, try to plot what is called the scores. Figure out the dimensions of `PCA_RESULTS$x`. Compare it to the dimensions of the original data frame. What do you notice?
5. `PCA_RESULTS$x` holds the scores for each individual on each PC axis. Try to plot axis 1 against axis 2 and color each individual based off of gender.
		6. Try to plot axis 1 against axis 2 and color each individual based off of population.
