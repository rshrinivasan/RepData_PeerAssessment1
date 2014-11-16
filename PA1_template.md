Reproducible Research: Peer Assessment 1
---


## Global options and parameters

```r
#setwd("~/Documents/Coursera/datascience_jh/represearch/RepData_PeerAssessment1")
# set echo = TRUE globally. This is the default, setting it explicitly here
opts_chunk$set(echo = TRUE)
# we will be using the packages knitr to convert to markdown and html
# Using knit2html will generate the .md and .html files in the same directory
# as the working directory. A directory called figures will also be created 
# under the working directory if plots are generated.
library(knitr)
```


## Loading and preprocessing the data

```r
if (!file.exists('activity.csv')){
    unzip("activity.zip")
}
activity <- read.csv("activity.csv", header = TRUE)
```


## What is mean total number of steps taken per day?

```r
# calculate total number of steps grouped by day
totstepsbyday <- aggregate(steps~date, activity, sum, na.rm = TRUE)
# Q1 - Make a histogram of the total number of steps taken each day

hist(totstepsbyday$steps, col = "orange", main = "Total Steps taken each day",
      xlab = "Total number of steps taken each day")
```

![plot of chunk meanTotalStepsPerDay](figure/meanTotalStepsPerDay.png) 

```r
# Q2 - Calculate and report the mean and median total number of steps taken per day
meanstepsbyday <- round(mean(totstepsbyday$steps))
medianstepsbyday <- median(totstepsbyday$steps)
```
#### The mean and median total number of steps taken per day are 1.0766 &times; 10<sup>4</sup> and 10765


## What is the average daily activity pattern?

```r
# Q1 - Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) 
# and the average number of steps taken, averaged across all days (y-axis)

# calculate the average number of steps grouped by interval
avgstepsbyinterval <- aggregate(steps~interval, activity, mean)
# generate line chart
plot(avgstepsbyinterval$interval, avgstepsbyinterval$steps, type = 'l', col = 1, 
     main = "Average number of steps across all days",
     xlab = "Interval in minutes",
     ylab = "Average number of steps")
```

![plot of chunk avgDailyActivityPattern](figure/avgDailyActivityPattern.png) 

```r
# Q2 - Which 5-minute interval, on average across all the days in the dataset, 
# contains the maximum number of steps?

# find the row that has the maximum number of steps
rowWithMax <- which.max(avgstepsbyinterval$steps)
# get the values for the interval and steps corresponding to the rowWithMax row
avgstepsbyinterval[rowWithMax, ]
```

```
##     interval steps
## 104      835 206.2
```
#### The interval 835 corresponds to the maximum average number of steps  206.1698


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
