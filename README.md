# prac1
---
title: 'Homework 2'
author: "Vaidehe"
date: "2/2/2022"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

#### Due: 2/9/2022 before 11:59pm. Submit in Canvas (file upload).

1. Finish the in-class practice in Slides 3-12 in "Lecture 2-2-Practice for git", link: https://yumouqiu.github.io/DS202-Spring2022/Practice/practice01.html  
    a. Download the RMarkdown file with these homework instructions to use as a template for your work. Make sure to replace "Your Name" with your name.  
    b. In the RMarkdown file, write down table of team members, and their github repository links;   
the number of successful pull requests you made, and the github repository to which you requested a change;  
the number of pull requests you accepted, and the github repository from which you accepted.  
    c. Write down a list with at least 3 tips of how to make working with git/github easier  

2. Generate the graph of LifExp vs. gdpPercap for US, Canada (fixed data) and Australia by RMarkdown based on the data set "gapminder-5060", like what we did in the class.  
Please use Github to collaborate on this problem. For example, one member can create the plot of US in his/her repository. The other member will fork this repository, add the result for the second country, and make a pull request for merging into the main repository. Each member should at least analyze one country and make at least one pull request. **Please submit the RMarkdown file, the output file, and the screen shot of the successful pull request and the merge.**

```{r}
life5060 <- read.csv("https://raw.githubusercontent.com/ds202-at-isu/materials/master/01_collaborative-environment/data/gapminder-5060.csv")
head(life5060)
dim(life5060)
```
```{r}
canada1 <- life5060[life5060$country == "Canada", ]
head(canada1)
dim(canada1)
```
```{r}
canada1 %>% filter(year == 1957)
canada_fixed <- canada1 %>% mutate(
  lifeExp = replace(lifeExp, year==1957, 69.96)  
)
canada_fixed
```
```{r}
canada_fixed %>% ggplot(aes(x = gdpPercap, y = lifeExp)) +
  ggtitle("Canada")
  geom_line()
```
```{r}
A1 <- life5060[life5060$country == "Australia", ]
head(A1)
dim(A1)
```
```{r}
A1 %>% ggplot(aes(x = gdpPercap, y = lifeExp)) +
  ggtitle("Australia")
  geom_line()
```
```{r}
USA1 <- life5060[life5060$country == "United States", ]
head(USA1)
dim(USA1)
```
```{r}
USA1 %>% ggplot(aes(x = gdpPercap, y = lifeExp)) +
  ggtitle("United States")
  geom_line()

```

3. Write a paragraph (~200 words) describing an example of what you consider data science. Write your paragraph in R Markdown. Include at least 
    a. one link to a chart or an image and 
    b. at least one itemized or enumerated list.

    

Note: your submission is supposed to be fully reproducible, i.e. the TA and I will 'knit' your submission in RStudio. Including the link to the image is the tricky part here. Make sure that you don't use any file structure that depends on your computing environment.


For the submission: submit your solution in an **R Markdown file** and (just for insurance) submit the corresponding html (or Word) file with it.
