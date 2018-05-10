# Programming Basics

## Functions
- why functions?
	- repeatable
	- readable
	- fewer mistakes
	
### Existing functions
Either R has them existing or you load them in a package

### Question Set 1
The number of birds banded at a series of sampling sites has been counted by
your field crew and entered into the following vector. Counts are entered in 
order and sites are numbered starting at one. Cut and paste the list into your
assignment and then answer the following questions by printing them to the
screen. Some R functions that will come in handy include `length()`, `max()`,
`min()`, `sum()`, and `mean()`.

	```
	number_of_birds <- c(28, 32, 1, 0, 10, 22, 30, 19, 145, 27, 
	36, 25, 9, 38, 21, 12, 122, 87, 36, 3, 0, 5, 55, 62, 98, 32, 
	900, 33, 14, 39, 56, 81, 29, 38, 1, 0, 143, 37, 98, 77, 92, 
	83, 34, 98, 40, 45, 51, 17, 22, 37, 48, 38, 91, 73, 54, 46,
	102, 273, 600, 10, 11)
	``

1. How many sites are there?
2. How many birds were counted at site 42?
3. How many birds were counted at the last site? Have the computer
   choose the last site automatically in some way, not by manually
   entering its position.
4. What is the total number of birds counted across all of the sites?
5. What is the smallest number of birds counted?
6. What is the largest number of birds counted?
7. What is the average number of birds seen at a site?

### Question Set 2
Familiarize yourself with the built-in functions `abs()`, `round()`, `sqrt()`, `tolower()`, and `toupper()`.  Use these built-in functions to print the following items:

1. The absolute value of -15.5.
2. 4.483847 rounded to one decimal place. *The function `round()` takes two
	   arguments, the number to be rounded and the number of decimal places.*
3. 3.8 rounded to the nearest integer. *You don't have to specify the number of
	   decimal places in this case if you don't want to, because `round()` will
	   default to using `0` if the second argument is not provided. Look at
	   `help(round)` or `?round` to see how this is indicated.*
4. `"species"` in all capital letters.
5. `"SPECIES"` in all lower case letters.
6. Assign the value of the square root of 2.6 to a variable. Then round the
	   variable you've created to 2 decimal places and assign it to another
	   variable. Print out the rounded value.
7. Do the same thing as task 6 (*immediately above*), but instead of creating
	   the intermediate variable, perform both the square root and the round on a
	   single line by putting the `sqrt()` call inside the `round()` call.

### Write your own functions

- Sometimes the functions you want don't exist, and you have to create your own functions
- Let's break down one of these
- Remember, computers are stupid, so we have to be very clear in what we are telling the computer we are trying to do

	```
	fahrenheit_to_kelvin <- function(temp_F) {
 	 temp_K <- ((temp_F - 32) * (5 / 9)) + 273.15
	  return(temp_K)
	}
	```
	
### Question Set 3

1. Write a function that converts pounds to grams (*there are 453.592 grams in one pound*). It should take a value in pounds as the input and return the equivalent value in grams (i.e., the number of pounds times 453.592). Use that function to calculate how many grams there are in 3.75 pounds.

2. The length of an organism is typically strongly correlated with it's body
mass. This is useful because it allows us to estimate the mass of an organism
even if we only know its length. This relationship generally takes the form:

		Mass = a * Length^b

	Where the parameters `a` and `b` vary among groups. This approach is
regularly used to estimate the mass of dinosaurs since we cannot weigh something
that is only preserved as bones. Write a function that estimates the mass of an organism in kg based on its length in meters for a particular set of parameter values, those for *Theropoda* (dinosaurs!) (where `a` has been estimated as `0.73` and `b` has been estimated as `3.63`.
	- Add a comment to this function so that you know what it does.
	- Use this function to print out the mass of a Spinosaurus that is 16 m long based on its reassembled skeleton. *Spinosaurus is a predator that is bigger,
and therefore, by definition, cooler, than that stupid Tyrannosaurus that
everyone likes so much.*
	- Create a new version of this function called `get_mass_from_length()` that estimates the mass of an organism in kg based on it's length in meters by taking length, a, and b as parameters. To be clear we want to pass the function all 3 values that it needs to estimate a mass as parameters. This makes it much easier
to reuse for all of the non-theropod species. Use this new function to estimate
the mass of a Sauropoda (`a = 214.44`, `b = 1.46`) that is 26 m long.

3. Measuring things using the metric system is the standard approach for
scientists, but when communicating your results more broadly it may be
useful to use different units (at least in some countries). Write a function
that converts kilograms into pounds (there are 2.205 pounds in a kilogram). Use
that function along with your dinosaur mass function to estimate the weight, in pounds, of a 12 m long Stegosaurus (*12 m is about as big as they come and nothing gets folks excited like a giant dinosaur*). In *Stegosauria*, `a` has been estimated as `10.95` and `b` has been estimated as `2.64` 

### Question Set 4

1. Go back to the stereotypes dataset. Make a function that will automatically make a histogram if you give it a column name. (_Hint_: check out this [guide](https://stackoverflow.com/questions/22309285/how-to-use-a-variable-to-specify-column-name-in-ggplot).)
2. Update this function so you can also specify `binwidth` from the function.
3. Go back to the stereotypes dataset. Make a function that will automatically make a scatterplot if you give it two columns names.
4. Update this function so you can also specify `color` from the function.

## Conditionals

- asking the computer to make decisions based on comparing things
- is one thing bigger / smaller / equal to the other?
- does a variable / file exist?

### Question Set 5

Create the following variables.

	```
	w <- 10.2
	x <- 1.3
	y <- 2.8
	z <- 17.5
	dna1 <- "attattaggaccaca"
	dna2 <- "attattaggaacaca"
	```

Use them to print whether or not the following statements are  `TRUE` or `FALSE`.

1. `w` is greater than 10
2. `w` + `x` is less than 15
3. `x` is greater than `y`
4.  2 * `x` + 0.2 is equal to `y`
5. `dna1` is the same as `dna2`
6. `dna1` is not the same as `dna2`
7. `w` is greater than `x`, and `y` is greater than `z`
8. `x` times `w` is between 13.2 and 13.5
9. `dna1` is longer than 5 bases (use `nchar()` to figure out how long a string is), or `z` is less than `w` * `x`

### Question Set 6
To determine if a file named `thesis_data.csv` exists in your working directory
you can use the code:

	```
	file.exists('thesis_data.csv')
	```

This code returns `TRUE` if the files exists and `FALSE` if it does not.

1. Write an `if` statement that loads the file using `read.csv()` only if the
   file exists.
2. Add an `else` clause that prints "OMG MY THESIS DATA IS MISSING. NOOOO!!!!" if the file doesn't exist.

### Question Set 7
The following function is intended to check if two geographic points are close
to one another. If they are it should return `TRUE`. If they aren't, it should
return `FALSE`. Two points are considered near to each other if the absolute
value of the difference in their latitudes is less than one and the absolute
value of the difference in their longitudes is less than one. Fill in the `_________` in the function to make it work.

   ``` 
   near <- function(lat1, long1, lat2, long2){
       # Check if two geographic points are near each other 
       if ((abs(lat1 - lat2) < 1) & (_________){
           near <- TRUE
       } else {
           near <- _________
       }
       return(near)
   }
   ```

- Improve the documentation for the function so that it is clear what near
   	means and what output the user should expect.
- Check if Point 1 (latitude = 29.65, longitude = -82.33) is near 
   Point 2 (latitude = 41.74, longitude = -111.83).
- Check if Point 1 (latitude = 29.65, longitude = -82.33) is near 
   Point 2 (latitude = 30.5, longitude = -82.8).
- Create a new version of the function that improves it by allowing the user to
   pass in a parameter that sets what "near" means. To avoid changing the
   existing behavior of the function (since some of your lab mates are using it
   already) give the parameter a default value of 1.
- Improve the documentation for the new function so that it reflects this new
   behavior
- Check if Point 1 (latitude = 48.86, longitude = 2.35) is near
   Point 2 (latitude = 41.89, longitude = 2.5), when near is set to 7.

## Loops

- Loops let you repeat the same code or analysis again and again for each value in a vector, or for each file in a diretory, or for each column in a dataframe ...
- You can also use `while` loops, which execute code as long as some condition is true, but we will not be using that today

### Question Set 8
The following code prints the first five whole numbers one line at a time:

	```
	for (i in 1:5){
	  print(i)
	}
	```

1. Modify this code to instead multiply each of the numbers 1 through 5 by 3, then print the result. 
2. Modify this code to go from 5 to 1 (instead of 1 to 5).
2. Use the vector `odds <- seq(1, 9, by = 2)` and a loop to square these numbers
   and print them one at a time. 
3. Instead of printing the values produced by this for loop, store them in a new
   vector named `output`. The following code provides a template for doing this: 

   ```
   output <- c()
   for (odd in _____) {
     _____ <- _____^2
     output <- c(output, odds_squared)
   }
   ```
   
### Question Set 9
Take the following vector of Stegosaur lengths

	```
	lengths <- c(10.1, 9.5, 11.2, 9.8, 10.4, 12.0, 11.5, 9.5,
	9.8, 10.0, 10.7, 10.2, 11.9, 9.7, 11.2, 11.8, 10.7)
	```

and estimate the mass in kilograms for each length using a `for` loop,
your function for estimating mass, `a = 10.95`, and `b = 2.64`. Print the
results in order.


### Question Set 10
The following code gets just the genus from strings that are scientific names and capitalizes the first letter of the genus name. The `str_extract` and `str_to_title` functions are from the `stringr` package, which is great for working with strings. 
	
	```
	waterbird <- "cygnus olor"
	waterbird_genus <- str_extract(waterbird, "\\w+")
	waterbird_genus_cap <- str_to_title(waterbird_genus)
	print(waterbird_genus_cap)
	```

Modify the code to loop over a vector of multiple scientific names and print the capitalized genus names to the screen one line at a time, using the following vector: 

	```
	waterbirds <- c("cygnus olor", "aix sponsa", "anas acuta")
	```
