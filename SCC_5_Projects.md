Projects
---

# Mini-Project Option 1: Roll Your Own
Start analyzing your own data set if you have one! I know at least four of you in this room can take this option.

# Mini-Project Option 2: Spatial Data in R
Historically, most biologists working with spatial data used ArcGIS, which is a very expensive and difficult to use program. (I'm so old I even was first trained on ArcGIS.) Increasingly, scientists are working with spatial data in R. This is because of a number of awesome packages, namely: `rgeos`, `sp`, `maptools`, `ggmap`, and `rgdal`. R is great to use to make maps & to figure out what are the characteristics at different points on Earth (i.e., temperature, elevation, land cover).

Getting too much into spatial data in R is beyond the scope of this workshop, but I want to give you a taste of how great it can be.

Here's an example of how to make a map.

	
	library(spocc)
	library(ggmap)

	# downloads species occurrences for a species of interest (to me!) from the GBIF database
	# google GBIF to learn more about it; it is awesome!
	ven_df1 = occ(query = "Encelia ventorum", 
	               from = "gbif")
	ven_df2 = data.frame(ven_df1$gbif$data)

	avg_long = mean(ven_df2$Encelia_ventorum.longitude, na.rm = T)
	avg_lat = mean(ven_df2$Encelia_ventorum.latitude, na.rm = T)

	# gets the map from Google
	# read the help for get_map to figure out what other options you have
	map = get_map(location = c(avg_long, avg_lat),  
	              maptype = "terrain", 
	              source = "google", 
	              zoom = 6)
	# actually plots the thing
	ggmap(map) + geom_point(data = ven_df2, 
	                        aes(x = Encelia_ventorum.longitude, 
	                            y = Encelia_ventorum.latitude), col="red")
	

I'll be honest. I learned `ggmap` for this workshop, and I thought it would be awesome, but for most of my work, this sort of map is too visually cluttered. Still, it is fun to play with. Try making your own map of your own favorite species, and try to make yours look better than mine does. Note that the key parameter in `get_map` is the `zoom` flag.

You can learn more here, at this awesome [tutorial](http://eriqande.github.io/rep-res-web/lectures/making-maps-with-R.html).

# Mini-Project Option 3: Phylogenetics
Those of you who are in my lab know that I prefer Python to R, but the main reason I use R is because it does a great job manipulating and plotting phylogenies. This is because of a number of awesome packages, namely: `ape`, `phytools`, `phangorn`, and `ggtree`.

Again, getting too much into phylogenetics in R is beyond the scope of this workshop, but I want to show you how much fun it can be.

Here's a short exercise which shows its power. These data were taken from [Moeller et al 2016](http://science.sciencemag.org/content/353/6297/380/tab-figures-data). Yay for Open Data! These are data from the gut microbiomes of hominids.

	
	# reads in the tree
	t = read.tree("Hominid_Bacteroidaceae_strains.tre")
	# sets all the branch colors to black at the start
	brcols = rep("black", length(t$edge.length))
	# identifies those phylogenetic tips that come from Bonobo, and colors them red
	brcols[ which(t$edge[, 2] %in% grep("Bonobo", t$tip.label)) ] = "red"
	# as above, but with gorilla
	brcols[ which(t$edge[, 2] %in% grep("Gorilla", t$tip.label)) ] = "blue"
	brcols[ which(t$edge[, 2] %in% grep("Human", t$tip.label)) ] = "green"
	brcols[ which(t$edge[, 2] %in% grep("Chimp", t$tip.label)) ] = "orange"
	# increases the plotting margins
	par(mar=c(0,0,0,0))
	# plots the tree
	# doesn't show tip labels because that makes the computer sad
	# does show branch colors, as defined by us
	plot(t, show.tip.label = F, edge.color = brcols)
	
What patterns do you notice in the phylogeny? You can also play around with the plotting (the help here is for the function `plot.phylo` to see how you can change it in different ways.)

I would recommend going through these great tutorials. There is a lot of overlap, but they are also have some unique functions they share.

- [Lars Schmitz's tutorial](http://schmitzlab.info/phylo.html)
- [The general wiki](https://www.r-phylo.org/wiki/HowTo/DataTreeManipulation)
- [Liam Revell's tutorial](https://lukejharmon.github.io/ilhabela/instruction/2015/07/02/introduction-phylogenies-in-R/)

# Mini-Project Option 4: Real Biological Data
Or, you can apply what we learned (particularly working with data frames and data visualization to a real biological dataset. These are data on patterns of small animal trapping from the Arizona desert over time (`Portal_Project_Trapping_v9.csv`). Each row represents one small animal trapped in the desert. Here are some questions I suggest you answer as you explore the data:

## Questions

0. What do the columns mean?
1. How many unique trapping events does this represent? 
2. How many years does this data set span?
3. How many genera are included in this data set?
4. How many species are included in this data set?
5. How many different types of taxa are included? What are they?
6. What species is the most represented in the data set?
7. What month lead to the most trapping success?
8. What are the average weights of each animal?
9. Is there any evidence that male and females in a species are different weights? (_Remember_: make a hypothesis, plot, and then do statistics!)
10. What species show changes in abundance through time?
11. Do any species show changes in mass through time?
12. Is there a relationship between the average mass of a species and its abundance? (_Remember_: make a hypothesis, plot, and then do statistics!)
13. More general question: your colleague Bob wants to use the data set to do an analysis of reptile changes through time. What do you think about Bob's idea?
14. More general question: you might have noticed that some years, there were many more total captures than others. There is a boring reason this could be: maybe the team was short on time or people, and didn't spend as much time in the field. There is an interesting biological reason: maybe the environmental conditions of that year reduced abundance, in total. How could you account for these biases?

## Here are some tutorials to guide you through the data set. 

- [Tutorial on Data](http://www.datacarpentry.org/R-ecology-lesson/03-dplyr.html)
- [Tutorial on Graphs](http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html)