---
title: "Scorpion Study AVC"
author: "Put your name here!"
date: "Fall 2018"
output:
  html_document:
    df_print: paged
---



# Introduction

<!--In this section you explain what you are trying to show.  Where did the data come from?  What is the research or other question you are trying to answer?!-->
  
  First we load in the data and then we will take a look at it.
  And now we load the data
  
  ```r
  ZiaData <- readXL("Data for bill stat class.xlsx", rownames=FALSE, header=TRUE,
   na="", sheet="Sheet1", stringsAsFactors=TRUE)
  ```

# Methods

<!--Decide on your methods:  use "variable analysis" or other appropriate descriptors.  Make sure to choose at least one graphical method and at least one numerical method.!-->

#Results

<!--Divide this section into two sub-sections:  One for your descriptive  results and one for your inferential results.!-->


## Descriptive Results

### Graphical Descriptive Results

<!--Graphical results here.  Make sure to show your code.  Provide appropriate labels for axes, giving units if possible, and provide a good title for the graph, too.  Use the graphical results to describe the patterns if any that exist in the data as focused toward the research question!-->

  
  Here is our bar plot
  
  ```r
  with(ZiaData, Barplot(Scorpion.Location.standardized, xlab="Scorpion.Location.standardized", 
  ylab="Percent", col=palette()[2], scale="percent"))
  ```
  
  ![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png)

  
### Numerical Descriptive Results

<!--Numerical results go here. Use the numerical results to describe the patterns if any that exist in the data as focused toward the research question!-->

## Inferential Results

<!--State hypothesis clearly.  Make sure your discussion of the inferential test covers all the aspects that the test output produces, such as test statistic, p-value etc.  Make a decision about the null hypothesis, explain the assumptions on which the selected test/procedure was based, and why the chosen procedure satisfys the assumptions and is appropriate to answer the research question!-->


```r
local({
  .Table <- xtabs(~ Scorpion.Location.standardized , data= ZiaData )
  cat("\nFrequency counts (test is for first level):\n")
  print(.Table)
  binom.test(rbind(.Table), alternative='two.sided', p=.5, conf.level=.95)
})
```

```
## 
## Frequency counts (test is for first level):
## Scorpion.Location.standardized
##       open vegetation 
##         52          6
```

```
## 
## 
## 
## data:  x
## number of successes = 52, number of trials = 58, p-value =
## 3.158e-10
## alternative hypothesis: true probability of success is not equal to 0.5
## 95 percent confidence interval:
##  0.7883135 0.9610792
## sample estimates:
## probability of success 
##              0.8965517
```


# Discussion and Conclusion

<!--Discussion and conclusion here.  If you found a relationship be sure to consider whether the relationship occurs because one of the variavbles causes the other, or whether they perhasps are related for some other reason.  Watch the chapter 6 videos from the GeorgeTown videos collection.!-->






```r
ZiaData2 <- readXL("D:/Project_folders/Zia2018/Data for bill stat class.xlsx", rownames=FALSE, 
  header=TRUE, na="", sheet="Sheet1", stringsAsFactors=TRUE)
```


```r
local({
  .Table <- with(ZiaData2, table(Scorpion.Location.standardized))
  cat("\ncounts:\n")
  print(.Table)
  cat("\npercentages:\n")
  print(round(100*.Table/sum(.Table), 2))
})
```

```
## 
## counts:
## Scorpion.Location.standardized
##       open vegetation 
##         52          6 
## 
## percentages:
## Scorpion.Location.standardized
##       open vegetation 
##      89.66      10.34
```


