Introduction and Data Frames
---

# Introduction
- why are we here?
- basic computer stuff
	- mantra: "computers are stupid"
	- how to talk to a computer
	- the importance of being organized
	- how to get help
		- the art of the good google
		- packages
		- `help()`		
- [brilliant advice](http://cierareports.org/blog/2013/10/18/rCourse2013/)
	- Every time you are presented with code that is unfamiliar to you
		- Ask: Do I understand every detail of the code?
		- Try to translate the code to plain English.
		- Play with it. Delete things, add things, and rearrange. Don’t be afraid, try it, it’s fun!
	- it is REALLY HARD to break your computer

# R Basics
- basics on how to use R
	- executing commands via script
	- executing on command line		
- data structures
	- remember our mantra: if you don't tell it to the computer, it doesn't know
	- how do we store our data so the computer knows it?
	
		```
		a = 2 + 2
		a <- 2 + 2
		```
	- the difference between 'naked' words and strings
	
		```
		print(apple)
		print("apple")
		```
	- variables
	- vectors
	- data frames
	- for later: matrices, lists, factors

##  Vectors
- Vectors are one of the most useful ways to store data in R
- It is basically a list of values
- The order matters

	```
	weight <- c(60, 72, 57, 90, 95, 72)
	height <- c(1.75, 1.8, 1.65, 1.9, 1.74, 1.91)
	```
	
## Question Set 1

1. Describe in plain English what `c()` does.
2. Compare your answer to the `c()` help file, which can be called with `?c()`.
3. Make a comment in your code explaining to yourself using a “hash tag” #. Don’t forget, anytime you precede text with #, it is not read into your code.
4. Make a plot that has weight on the x-axis and height on the y-axis using the plot().
5. BMI is weight divided by height. Create a new vector that contains BMI based on the weight and height vectors above.
6. Then try plotting height by BMI.
7. Make a vector called `myFamily` that lists all the ages in your immediate family.
8. Figure out the average age of people in your `myFamily` dataset. Note I didn’t tell you how to find averages in R. Google it.
	
## Let's get packages

- packages
	- `tidyr`: manipulates data frames
	- `dplyr`: manipulates data frames
	- `readr`: read in CSV files
	- `ggplot2`: the best way to graph in R
	- `cowplot`: changes ggplot2 to look cleaner
	- `ape`: phylogenetics
	- `ggmap`: makes maps
- want to install them using `install.packages()`
- could do it one at a time
- or could create a vector of all the packages we want
- and then install all at once

## Data Frames
- data frames are another powerful way of storing data in R
- a data frame could store whatever data you normally keep in an Excel table
- but it's better
- how to load them
	- load `tidyr`, `dplyr`, and `readr`
	- `read_csv`
- how to look at them
	- `names`: get column names
	- `head`: get first few rows
	- `tail`: get last few rows
	- `str`: get structure of data frame
	- `summary`: get a clean summary
	- `dim`, `Nrow`, `Ncol`: get shape of data frame
- two ways to get at rows
	- the `dplyr` way 
	- the `d$column` way
- how to subset them
	- `select`: select for certain columns
	- `filter`: select for certain rows
	
## Question Set 2

1. Select a data frame with just the beer and taco columns. What are its dimensions?
2. Filter the data frame to just have women & nerds.
3. How many people have more than 40 beers a week?
4. Why doesn't `nerds = filter(d, population == 'nerds')` work?
5. Why doesn't `nerds = filter(d, population == nerds)` work?

- how to manipulate them
	- `arrange`: sort by a column
	- `group_by`: focus on just looking at part of the dataset at a time
	- `mutate`: how to add column
	- how to join them
	
## Question Set 3
1. Figure out how to sort by a column in descending order (Google!)
2. What does R do if you try to sort a non-numerical column?
		
- how to describe them
	- `summarize` and `summarize_at` and `summarize_each`
		- with `summarize_at`, use `vars` and `funs`
	- `tally`
	- `n_distinct`
	- `count`: get the counts of column
	
## Question Set 4
1. How many nerds are there?
2. What is the maximum tacos eaten? (Google if you don't know how to find max!)
3. Subset the data to only nerds.
4. Subset the data to include only nerds and metalheads.
5. Subset the data to include only female nerds.
6. Which population takes the fewest showers?
7. Are the genders in each population about the same average age or not?
8. Add a column that expresses how much people are spending on tacos. What group spends the most on tacos?
	9. Which population has the highest rate of females who binge on coffee, but hardly ever drink alcohol?
	10. Ask one more question about the dataset that you are interested in. Subset the data accordingly.
