---
layout: page
title: Extra
---

# Extra
These are additional functions that complement the main SBS analysis and reports.

## Keywords

This function can be used to find keywords in the uploaded text file (the algorithm is based on TF-IDF). The function will analyze all documents, regardless of their date.

Please specify the **CSV separator**, the **maximum number of keywords**, the **language** of the analysis (for stemming) and the **percentage of text to analyze**. A value of 1, for this last field, means that the full text will be analyzed; lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).

------

## Word Cloud

This function can be used to generate a word cloud, based on a list of keywords and weights.

Please upload a single **CSV file** (utf-8 format), with two columns - the first containing words and the second one weights. The first row (header) will be ignored. Through the form you will be able to choose the **shape** and **color** of the word clous, as well as the **maximum number of words** to show.

------

## Text Analysis

<span style="color:#900C3F">**This function is only available to advanced users.**</span>

The module allows the calculation of some additional textual and semantic metrics for the input documents. A brief description is provided in the following sections.

### Analyses

Basic textual metrics are calculated at every run (such us the number of types and tokens, for each document). In addition, you can choose to carry out these other analyses:

- `Complexity`: calculates the language complexity of each document. The function provides several metrics: the number of words of six or more letters (absolute and relative frequencies), the average word length and 3 other complexity scores calculated by using the TF-IDF function and taking into account the word frequency distribution.
- `Sentiment`: calculates the average language sentiment of each document. Scores can vary from -1 to 1, where positive values indicate a positive sentiment.
- `Emotions`: calculates several dimensions of the language used (such as the degree of positive and negative emotions, or the language orientation towards past or future). Scores are the relative word count and can vary from 0 to 100.
- `Crovitz`: calculates the relative frequencies of the [Crovitz's relational words](https://doi.org/10.1007/s11135-020-01038-x) that appear in each text. Scores can vary from 0 to 100.

### Parameters

- `Csv separator`: specifies the separator used in the CSV file. Insert a single character without quoting.
- `Percentage of text to analyze`: used when the analysis has to consider only a portion of each text document, for example just the title and lead of an online news. A value of 1 means that the full text will be analyzed, lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).
- `Language`: this is the language of uploaded texts (please be consistent and try to analyze one language at a time). 
- `Choose one or more analyses`: select the kind of analysis you want to carry out.

#### Optional parameters

- `Brand list`: use this field if you also want to check for the presence of *brand* in the documents and then average the general results by brand. A brand can be any word, such as the name of a product, or of a person. You have to list the brands without quotes, separating them with a comma.

- `Cluster brands`: sometimes it is useful to merge multiple words that represent a *brand*. Each *brand/concept* could be represented by a set of keywords. If this is the case, you can use the *cluster brands* field to specify the words to merge. For example we may want to have a single node for the word "pope" and the word "francis". The following syntax has to be used `"cluster1":["word1","word2",..], "cluster2":["word6","word8",..],..`. The same word cannot appear in multiple clusters.

  Additionally, asterisks can be used at the end of words, indicating that a specific word could be completed with any possible set of characters. For example, if the word `"asp*"` is used, this will match both the words `"aspirin"` and `"aspire"`. This also works with multiple words, for example `"financial sect*"` will match the words `"financial sector"`.

- `Time unit` and `Time intervals`: use this field if you also want to average results by time intervals.

- `Start time` and `End time`: these are the start and end time of the analysis, for the time interval averages.

------

## Image Explorer

<span style="color:#900C3F">**This function is only available to advanced users.**</span>

This module allows a in-depth analysis of the "SBS_associations.csv" file, produced by the main SBS analysis. Please upload the "**SBS_associations.csv**" file previously produced by the SBS analysis, **without changing its name or content** (encoding must always be utf8).

### Parameters

Basic textual metrics are calculated at every run (such us counting the number of associations). In addition, you can choose to carry out these other analyses:

- `Dimensions`: this field can be used to specify custom dimensions for the analysis of brand image. We use a dictionary to represent each dimension. The following syntax has to be used `"dimension_name1":["word1","word2",..], "dimension_name2":["word6","word8",..],..`. It is possible to repeat the same word in different dimensions. Please use the lowercase. The dimension name will not be considered as a word for the analysis.

  Additionally, asterisks can be used at the end of words, indicating that a specific word could be completed with any possible set of characters. For example, if the word `"asp*"` is used, this will match both the words `"aspirin"` and `"aspire"`. This also works with multiple words, for example `"financial sect*"` will match the words `"financial sector"`.

- `Language`: this is the language used for the analyses described in the following.

- `Analyses`: similarly to the Text Analysis function, you could choose to analyze the brand associations considering:

  - `Complexity`: calculates the language complexity. The function provides several metrics: the number of words of six or more letters (absolute and relative frequencies), the average word length and 3 other complexity scores calculated by using the TF-IDF function and taking into account the word frequency distribution.
  - `Emotions`: calculates several dimensions of the language used (such as the degree of positive and negative emotions, or the language orientation towards past or future).  Some dimensions might result empty, especially if you removed stop-words during the SBS analysis that produced the associations file.
  - `Crovitz`: calculates the frequencies of the [Crovitz's relational words](https://doi.org/10.1007/s11135-020-01038-x). Some dimensions might result empty, especially if you removed stop-words during the SBS analysis that produced the associations file.

Sentiment is not an option here, as it is already calculated for each brand (and time interval) by the main SBS analysis (which has been used to produce the SBS_associations.csv file).

### Output

Three files are generated by the Image Explorer module:

- `AssoOverall`: here we get a summary of the main textual associations of each brand (up to 600), summing frequencies over time.
- `AssoDimensionsOverall`: also in this case we sum frequencies over time, but we consider the dimensions and analyses specified in the parameters. For each dimension, we get:
  - `_count`: the count of matching associations (sum of frequencies);
  - `_rel`: the count of matching associations divided by the total number of associations for that brand;
  - `_reldim`: the count of matching associations divided by the total number of associations for that dimension, with respect to the different brands.
- `AssoDimensionsByTime`: here we get the same results of `AssoDimensionsOverall`, but for each time interval. `_rel` and `_reldim` are calculated considering the total number of matching associations in a time interval and the total number of matching associations in a time interval with respect to the other brands.