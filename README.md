crimes-in-chicago
=================

The tabular representation of crimes data in Chicago in R language

## Created by Ivan Setiawan on Wednesday, 06/25/2014
## As a part of programming assignment with Truqua Enterprise

install.packages("googleVis")
library(googleVis)

## Get the data source from the website
crimes_stage <- read.csv("http://data.cityofchicago.org/views/x2n5-8w5q/rows.csv")

## Summary of the table
summary(crimes_stage)
attach(crimes_stage)

## Create lists of table which give details about the type of crimes and total occurences
cbind(table(crimes_stage$PRIMARY.DESCRIPTION))

## Create a barplot representation regarding the type of crimes
barplot(table(crimes_stage$PRIMARY.DESCRIPTION))

## Adding color, space, title, x-axis, and y-axis to the barplot of crimes
barplot(xtabs(~crimes_stage$PRIMARY.DESCRIPTION), space=T, col=rainbow(length(levels(crimes_stage$PRIMARY.DESCRIPTION))), main="Crimes in Chicago", xlab="Crimes Type", ylab = "Frequency")

## Create lists of table which give details about the crimes' locations and total occurences
cbind(table(crimes_stage$LOCATION.DESCRIPTION))

## Create a barplot representation regarding the crimes' locations
barplot(table(crimes_stage$LOCATION.DESCRIPTION))

## Adding color, space, title, x-axis, and y-axis to the barplot of crimes' locations
barplot(xtabs(~crimes_stage$LOCATION.DESCRIPTION), space=T, col=rainbow(length(levels(crimes_stage$LOCATION.DESCRIPTION))), main="Crimes Locations in Chicago", xlab="Location", ylab = "Frequency")

