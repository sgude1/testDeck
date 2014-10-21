---
title       : Developing Data Products Assignment
subtitle    : Finding Prime Numbers 
author      : sgude
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

-This application accepts an input from a user and determines the closest prime number to the number submitted.  
-It accepts positive values from 1 to 100,000  
-When evaluating the closest number it considers absolute value so the value returned may be higher or lower than the submission.  
-In the scenario where a user inputs a value that is equidistant between two primes, both are returned, for example 4 returns 3 and 5.

--- .class #id 

## How to Use

-Using the application is straightforward and should be intuitive for most users.  <br/><br/>
<b>Steps to Use</b><br/><br/>
1. Enter the number you would like to evaluate in the text box (note the number must be between 1 and 100,000 as noted in the application)  <br/>
2. Once you enter the number select the blue button titled "Find my Prime!"<br/>
3. The application will return two values upon submission:  <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a. It will redisplay the value you entered in the section titled "The closest prime number to your entry of:"  <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b. It will then display the result in the section titled: "is the prime number(s)"

--- .class #id 

## How it Works
-The code starts by generating a data table with values from 1 to 100,000.<br/>
-Next it evaluates whether each value in the table is a prime number and subsets the data to a list of only those numbers.<br/>
-Once it has that subset, it creates a new column which is equal to the absolute value of the prime numbers less the number the user provided.<br/>
-It returns the number(s) where the above calculation is minimized.<br/><br/>
The function in R code is:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;prime <- function(number){<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x <- data.table(a=1:100000,b=1)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x$b<-isprime(x$a)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x <- subset(x, b==1)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x$c<-abs(x$a-number)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;low<-min(x$c)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;guess <- subset(x, c==low)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;xx<-guess$a<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(xx)}
 
