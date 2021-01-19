---
layout: page
title: Parameters
---

# SBS Parameters
Specifying the correct parameters is essential to the app functioning and the correct run of the analysis. In the *Generate* tab, you will find mandatory basic settings and optional advanced settings.

#### Basic Settings

- `Name of uploaded file`: name of the file to be analyzed. This is generally auto-completed.
- `Csv separator`: specifies the separator used in the CSV file. Insert a single character without quoting.
- `Time unit` and `Time intervals`: specifies the time interval for the calculation of the Semantic Brand Score. For example, you might want to calculate a daily score, or aggregate the texts produced in one week.
- `Start time` and `End time`: these are the start and end time of the analysis. This setting is particularly important when you want to restrict the analysis to a specific timeframe (but the CSV you uploaded has more data).
- `Brand list`: it is the list of *brands* to be analyzed (can be any word, such as the name of a product, or of a person). You have to list the brands without quotes, separating them with a comma.
- `Language`: this is the language of uploaded texts (please be consistent and try to analyze one language at a time). This setting will be used for the calculation of sentiment, for stemming/lemmatization and for the removal of stopwords.
- `Min co-occurrence frequency`: textual co-occurrences that are below this threshold will be filtered out. Must be an integer bigger or equal to 1 (1 means no filtering). This value can have a strong impact on the computation time (higher values, faster analysis).  The calculation of co-occurrences depends on the time periods specified for the analysis.
- `Generate topic models `: if set to "yes" topic modeling will be performed and added to the graphical report. It can be resource intensive. The "yes and only" option allows to simplify the process and only carry out a topic modeling, without calculating the SBS and producing its related reports. In the case of a "yes and only" choice:
  - no time intervals will be considered (all text documents with a date between `Start time` and `End time` will be used);
  - please ignore the `Link fiter adjustment for topics` parameter and consider the `Min co-occurrence frequency` instead. Value is usually higher than that of an analysis carried out on time intervals.
- `Send email at the end`: if checked, the system will send an email when the analysis ends.

#### Advanced Settings

- `Cluster brands`: sometimes it is useful to merge multiple words that represent a *brand*. Each *brand/concept* could be represented by a set of keywords. If this is the case, you can use the *cluster brands* field to specify the words to merge. For example we may want to have a single node for the word "pope" and the word "francis". The following syntax has to be used `"cluster1":["word1","word2",..], "cluster2":["word6","word8",..],..`. Words have to be unique and the same word cannot appear in multiple clusters.
- `Custom stopwords`: can be used to specify custom stopwords, i.e. words that will be ignored during the analysis. Custom stopwords have to be listed without quotes and separated by a comma.
- `Use different languages for stopwords`: sometimes it is necessary to remove stopwords from multiple dictionaries (languages). This field is also helpful when the language of the uploaded text is not available for the parameter `Language`. Use the `SKIP` option in case you do not wish to remove stopwords (you can still remove custom stopwords).
- `Stemming or Lemmatization`: choose whether to apply stemming (recommended) or lemmatization.
- `Use a different language for stemming or lemmatization`: this field can be used to select an alternative language for stemming or lemmatization, with more choices with respect to the parameter `Language`. The choice might affect the calculation of *Sentiment* which is not supported for all languages. Use the `SKIP` option in case you do not wish to apply stemming or lemmatization. Please note that stemming supports more languages.
- `Connectivity approximation`: when the value is set lower than 1, the calculation is approximated considering a random subset of nodes in the network. Please note that results might change between different runs of the analysis, if the calculation is approximated (value < 1). The lower the value, the higher the approximation. 
- `Percentage of text to analyze`: used when the analysis has to consider only a portion of each text document, for example just the title and lead of an online news. A value of 1 means that the full text will be analyzed, lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).
- `Min doc lenght`: excludes the text documents with a number of characters below this threshold.
- `Word co-occurrence range`: indicates the range of the maximum distance between words, to determine a co-occurrence. Values of 5 or 7 are usually good and results are often robust with respect to this parameter, when the values are within a reasonable range (2 to 20). 
- `Distinctiveness centrality alpha`: is the value of the alpha coefficient used to calculate Distinctiveness Centrality and therefore Diversity. Can be any number >= 1. Setting a value of 1 is recommended.
- `Use source weight`: if this is checked, the analysis will be performed considering source weights.
- `Calculate setiment`: if checked, the system will additionally calculate brand sentiment.
- `Max number of topics`: indicates the maximum number of topics that should be considered for topic modeling.
- `Link fiter adjustment for topics`: this is a parameter similar to that of `Min co-occurrence frequency` and it is used to remove low-weight links prior to topic modeling. Please consider that the topic modeling is carried out on the whole dataset (networks are not split by period of analysis). Set this parameter to 1, or increase it to filter out more links. We usually recommend values between 0.75 and 1.25.
- `Generate Graphs`: if checked, the system will produce the graphical report, as a result of the analysis.
- `Save parameters`: choosing a name will save the parameters and they could be imported in the future. 
- `Skip text pre-processing`: use this if you have uploaded an input file that has already been pre-processed. Please be very careful as you might get errors, if the raw input has not been correctly processed. 

To save a configuration click on *Generate Parameters File*. Please note that in case of errors the configuration will not be saved.

## Saved Configurations
This function can be used to import previously saved parameters. Once imported they will be visible on the *Generate* page.