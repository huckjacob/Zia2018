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

# Methods

<!--Decide on your methods:  use "variable analysis" or other appropriate descriptors.  Make sure to choose at least one graphical method and at least one numerical method.!-->

#Results

<!--Divide this section into two sub-sections:  One for your descriptive  results and one for your inferential results.!-->

## Descriptive Results

### Graphical Descriptive Results

<!--Graphical results here.  Make sure to show your code.  Provide appropriate labels for axes, giving units if possible, and provide a good title for the graph, too.  Use the graphical results to describe the patterns if any that exist in the data as focused toward the research question!-->

### Numerical Descriptive Results

<!--Numerical results go here. Use the numerical results to describe the patterns if any that exist in the data as focused toward the research question!-->

## Inferential Results

<!--State hypothesis clearly.  Make sure your discussion of the inferential test covers all the aspects that the test output produces, such as test statistic, p-value etc.  Make a decision about the null hypothesis, explain the assumptions on which the selected test/procedure was based, and why the chosen procedure satisfys the assumptions and is appropriate to answer the research question!-->


# Discussion and Conclusion

<!--Discussion and conclusion here.  If you found a relationship be sure to consider whether the relationship occurs because one of the variavbles causes the other, or whether they perhasps are related for some other reason.  Watch the chapter 6 videos from the GeorgeTown videos collection.!-->


```r
ZiaData <- readXL("D:/Project_folders/Zia2018/Data for bill stat class.xlsx", rownames=FALSE, header=TRUE,
   na="", sheet="Sheet1", stringsAsFactors=TRUE)
```


```r
ZiaData <- readXL("D:/Project_folders/Zia2018/Zia_Fixed_Data.xlsx", rownames=FALSE, header=TRUE, na="", 
  sheet="Sheet1", stringsAsFactors=TRUE)
```


```r
scatterplotMatrix(~Air.Temp..C+Ground.wind.speed.m.s+rH..ground+Scorpion.distance.from.vegetation.cm+Soil.Temp..C,
   regLine=FALSE, smooth=FALSE, diagonal=list(method="density"), data=ZiaData)
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4-1.png)


```r
with(ZiaData, cor.test(Air.Temp..C, Scorpion.distance.from.vegetation.cm, alternative="two.sided", 
  method="pearson"))
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  x and y
## t = 0.33312, df = 44, p-value = 0.7406
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.2436894  0.3355689
## sample estimates:
##        cor 
## 0.05015688
```


```r
with(ZiaData, cor.test(Ground.wind.speed.m.s, Scorpion.distance.from.vegetation.cm, 
  alternative="two.sided", method="pearson"))
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  x and y
## t = 0.42128, df = 44, p-value = 0.6756
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.2311686  0.3472908
## sample estimates:
##        cor 
## 0.06338289
```


```r
with(ZiaData, cor.test(rH..ground, Scorpion.distance.from.vegetation.cm, alternative="two.sided", 
  method="pearson"))
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  x and y
## t = -1.2495, df = 44, p-value = 0.2181
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.4511625  0.1111632
## sample estimates:
##        cor 
## -0.1851084
```


```r
with(ZiaData, cor.test(Scorpion.distance.from.vegetation.cm, Soil.Temp..C, alternative="two.sided", 
  method="pearson"))
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  x and y
## t = -1.6852, df = 44, p-value = 0.09903
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.50073595  0.04745984
## sample estimates:
##        cor 
## -0.2462307
```


