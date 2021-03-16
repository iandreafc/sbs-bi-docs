---
layout: page
title: Analysis
---

# Analysis
These are the main analyses and reports produced by the software.

## SBS Run

This will calculate the Semantic Brand Score and generate graphical reports, according to the uploaded text file and the chosen parameters.

- Clicking on **Run** will start the analysis, which could take some time. You can exit the app and come back to check the status, or just click on the **Check Status** button. You will receive an email when the analysis end, if this has been set in the parameters.
- When the analysis ends you are able to **download results** and **visualize reports** online. Each report can also be **saved**, as running a new analysis will delete it. Please note that each user has a maximum number of reports that can be saved.
- The analysis can be **stopped** in case of errors.
- Please note that **some graphs** (such as the topic modeling network) are **only visible online**.

### Interpretation of reports
For a comprehensive description of graphs and a full example, please read <a href="https://arxiv.org/ftp/arxiv/papers/2001/2001.11479.pdf" target="_blank">this paper</a> or you could watch the videos on this <a href="https://www.youtube.com/watch?v=CYvKdTgDJTU&list=PL_zqgcr1hn7TAOr0BfX93HXkZThVYeuL0&index=2" target="_blank">YouTube channel</a>. 

The reports of the main SBS analysis are briefly described in the following:

- **SBS time trends:** shows the time trends of the SBS scores. The first tab shows absolute (standardized) values, the second tab shows relative values with respect to the other brands.
- **Brand positioning:** compares brand importance (SBS) and brand sentiment.
- **SBS ranking and dimensions:** shows how each dimension of the SBS contributes to the average final ranking (SBS is rescaled in the range [0,300] and each dimension score can vary from 0 to 100).
- **Brand associations:** shows the most frequent and the unique associations, together with their frequency values.
- **Most frequent words:** shows the most frequent words for each time period.
- **Time trends of unique associations:** shows the time trends of the number of unique associations for each brand.
- **Target words:** shows a ranking of the words with the highest connectivity scores, considering the full period of analysis, with values rescaled in the range [0, 100].
- **Topic modeling:** shows the results of the network topic modeling.
  - ***Network:*** shows a network representing the main discourse topics. This graph might not be visible when you download the results on your local PC. Please put the files on a server in order to see it.
  - ***Representative words:*** shows the most representative words for each topics, ranked based on their <a href="https://arxiv.org/ftp/arxiv/papers/2001/2001.11479.pdf" target="_blank">importance score</a>. 
  - ***Brand/Topic associations:*** shows how much each brand is related to the different topics (percentage) and, in the second tab, how much each brand is important for the different topics. These values are calculated considering the strength of the brand connections with the most representative words of each topic (typically the top 300, not all words in the topic). In rare cases, it might happen that the prevailing topic for a brand is not the same as shown in the network graph. This is due to the fact that in the network graph all the words of a topic are considered and not only the most representative ones. If this is the case, we suggest referring to the results of these graphs, which are more accurate than the association resulting from the network.
  - ***Top topics:*** ranks the topics by importance.
  - ***Topic connections:*** shows the strength of connections among topics.

------

## Saved Reports

In this page you can see your saved reports and delete those that you do not need anymore. Please consider that every user has a **maximum number of reports** that can be saved. After this limit has been reached, you have to delete old reports in order to save new ones.

------

## Graphs only

<span style="color:#900C3F">**This function is only available to advanced users.**</span>

Can be used when you have uploaded a ZIP file with past results, to produce merged graphs. See the [**Past Results Upload**](upload.md#past-results-upload) section, for details.
