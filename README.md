# Session-2.2-assignment-rahul-sharma
Acagild session 2.2 assignment 

1. Read multiple JSON files into a directory to convert into a dataset.
I have files text1, text2, text3 in the directory JSON

Ans 1 -> 

setwd("Users/Desktop/json")
temp = list.files(pattern="text*.")
myfiles = lapply(temp, read.delim)
library("rjson")
json_file <- "myfiles"
library(jsonlite)
out <- jsonlite::fromJSON(json_file)
out[vapply(out, is.null, logical(1))] <- "none"
data.frame(out, stringsAsFactors = FALSE)[,1:5]
View(out)

2.  Parse the following JSON into a data frame.
js<-'{
"name": null, "release_date_local": null, "title": "3 (2011)",
"opening_weekend_take": 1234, "year": 2011,
"release_date_wide": "2011-09-16", "gross": 59954
}

Ans 2 ->

library(rjson)
data.frame(t(unlist(fromJSON(js))))
   title opening_weekend_take year release_date_wide gross
3 (2011)                 1234 2011        2011-09-16 59954

3.  Write a script for Variable Binning using R

Ans 3 ->

x <- c(0,1,3,4,2,4,2,5,43,432,34,2,34,2,342,3,4,2)
binned.x <- as.factor(ifelse(x > 10,"10+",x))
