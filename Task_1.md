---
title: 'Task 1: Getting and Cleaning the Data'
author: "ps7391"
date: "2019-02-18"
output: 
        html_document:
                  keep_md: yes
        md_document:
                  variant: markdown_github
        toc: true
        pdf_document: default
---



### Datasets

Large databases comprising of text in a target language are commonly used when generating language models for various purposes. In this exercise, you will use the **English database** but may consider three other databases in German, Russian and Finnish.

The goal of this task is to get familiar with the databases and do the necessary cleaning. After this exercise, you should understand what real data looks and how much effort you need to put into cleaning the data. When you commence on developing a new language, the first thing is to understand the language and its peculiarities with respect to your target. You can learn to read, speak and write the language. Alternatively, you can study data and learn from existing information about the language through literature and the internet. At the very least, you need to understand how the language is written: writing, existing input methods, some phonetic knowledge, etc.

Note that the data contain words of offensive and profane meaning. They are left there intentionally to highlight the fact that the developer has to work on them.

### Tasks to accomplish

1. Tokenization - identifyin appropriate tokens such as words, punctuation, and numbers. Writing a function that takes a file as input and returns a tokenized version of it.
2. Profanity filtering - removing profanity and other words you do not want to predict.

### Libraries

Load libraries.


```r
suppressPackageStartupMessages({
  library(downloader)
  library(tm)
  library(knitr)
  library(tidyverse)
  library(dplyr)
  library(dtplyr)
  library(data.table)
  library(ggthemes)
  library(wordcloud)
  library(ngram)
})
start <- Sys.time()
```

### Download and explore the data

#### Create a Data Directory


```r
# create a data dir
if (!file.exists("Data")){
  dir.create("Data")
}
```

