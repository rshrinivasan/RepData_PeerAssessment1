---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---

## Global options and parameters

```r
#setwd("~/Documents/Coursera/datascience_jh/represearch/RepData_PeerAssessment1")
# set echo = TRUE globally. This is the default, setting it explicitly here
opts_chunk$set(echo = TRUE)
# we will be using the packages knitr to convert to markdown and html
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
### The mean and median total number of steps taken per day are 1.0766 &times; 10<sup>4</sup> and 10765


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
