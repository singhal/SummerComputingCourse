## Making graphs
- some stats stuff:
	- continuous vs. discrete
	- longitudinal vs. not
- We will be using ggplot, which is a very powerful way of creating graphs
- But, it comes with a bit of a learning curve
- And, be sure to include ggplot when doing a Google
- graphics
	- `geom_histogram`
	- `geom_point`
	- `geom_line`
	- `geom_boxplot`
	- `geom_density`
- notice what I'm not teaching you: bar graphs & pie charts
	- there is a reason
	- they are almost never a good option
- multiple categories within a graph
- `facet_wrap` (1 level) and `facet_grid` (2 levels)
- Some basic stats: `geom_smooth()`
- **Questions**
	1. Make a histogram that shows how many showers are taken across all groups
		- play around with `bin_width`
		- what does `bin_width` do?
	2. Make a scatterplot that shows if there is a connection between tacos eaten and beers drunk
	3. Make a boxplot that shows if there are differences in beer consumption across genders
	4. Make a boxplot that shows if there are differences in taco consumption across populations
	5. Make a single histogram that shows how coffee consumption is different across groups
	6. Make multiple histograms that shows how coffee consumption is different across groups
	7. Make multiple histograms that shows how coffee consumption is different across groups and genders
	8. Make a single scatterplot that shows if there is a connection between tacos eaten and beers drunk, that also shows the different populations
	9. Make a graph that visually describes the difference between beer consumption between gender in the nerd category.
	10. Make a scatterplot that shows if there is a connection between tacos eaten and beers drunk & add in a smooth line
	11. From your exploration of the stereotypes data make three hypotheses about the data.
	12. Make me a pretty graph - explore color options etc to make it suit your style