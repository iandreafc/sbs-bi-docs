---
layout: page
title: Extra
---

# Extra
These are additional functions that complement the main SBS analysis and reports.

## Keywords

This function can be used to find keywords in the uploaded text file (the algorithm is based on TF-IDF). The function will analyze all documents, regardless of their date.

Please specify the **CSV separator**, the **maximum number of keywords**, the **language** of the analysis (for stemming) and the **percentage of text to analyze**. A value of 1, for this last field, means that the full text will be analyzed; lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).

## Word Cloud

This function can be used to generate a word cloud, based on a list of keywords and weights.

Please upload a single **CSV file** (utf-8 format), with two columns - the first containing words and the second one weights. The first row (header) will be ignored. Through the form you will be able to choose the **shape** and **color** of the word clous, as well as the **maximum number of words** to show.

## Text Analysis
<span style="color:#900C3F">**This function is only visible to advanced users.**</span>

The module allows the calculation of some additional textual and semantic metrics for the input documents. A brief description is provided in the following sections.

### Analyses

Basic textual metrics are calculated in every run (such us the number of types and tokens, for each document). In addition, you can choose to carry out these other analyses:

- `Complexity`: calculates the language complexity of each document. The function provides several metrics: the number of words of six or more letters (absolute and relative frequencies), the average word length and 3 other complexity scores calculated by using the TF-IDF function and taking into account the word frequency distribution.
- `Crovitz`: calculates the relative frequencies of the [Crovitz's relational words](https://doi.org/10.1007/s11135-020-01038-x) that appear in each text. Scores can vary from 0 to 100.
- `Emotions`: calculates several dimensions of the language used (such as the degree of positive and negative emotions, or the language orientation towards past or future). Scores are relative to the word count and can vary from 0 to 100.
- `Sentiment`: calculates the average language sentiment of each document. Scores can vary from -1 to 1, where positive values indicate a positive sentiment.

### Parameters

- `Csv separator`: specifies the separator used in the CSV file. Insert a single character without quoting.
- `Percentage of text to analyze`: used when the analysis has to consider only a portion of each text document, for example just the title and lead of an online news. A value of 1 means that the full text will be analyzed, lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).
- `Language`: this is the language of uploaded texts (please be consistent and try to analyze one language at a time). 
- `Choose one or more analyses`: select the kind of analysis you want to carry out.

#### Optional parameters

- `Brand list`: use this field if you also want to check for the presence of *brand* in the documents and then average the general results by brand. A brand can be any word, such as the name of a product, or of a person. You have to list the brands without quotes, separating them with a comma.
- `Cluster brands`: sometimes it is useful to merge multiple words that represent a *brand*. Each *brand/concept* could be represented by a set of keywords. If this is the case, you can use the *cluster brands* field to specify the words to merge. For example we may want to have a single node for the word "pope" and the word "francis". The following syntax has to be used `"cluster1":["word1","word2",..], "cluster2":["word6","word8",..],..`. Words have to be unique and the same word cannot appear in multiple clusters.
- `Time unit` and `Time intervals`: use this field if you also want to average results by time intervals.
- `Start time` and `End time`: these are the start and end time of the analysis, for the time interval averages.

