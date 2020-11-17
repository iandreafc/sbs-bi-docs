---
layout: page
title: Analysis and Results
---

# Analysis and Results
### SBS Run

This will calculate the Semantic Brand Score and generate graphical reports, according to the uploaded text file and the chosen parameters.

- Clicking on **Run** will start the analysis, which could take some time. You can exit the app and come back to check the status, or just click on the **Check Status** button. You will receive an email when the analysis end, if this has been set in the parameters.
- When the analysis ends you are able to **download results** and **visualize reports** online. Each report can also be **saved**, as running a new analysis will delete it. Please note that each user has a maximum number of reports that can be saved.
- The analysis can be **stopped** in case of errors.
- Please note that **some graphs** (such as the topic modeling network) are **only visible online**.

### Interpretation of reports
For a comprehensive description of graphs and a full example, please read <a href="https://arxiv.org/ftp/arxiv/papers/2001/2001.11479.pdf" target="_blank">this paper</a>.

## Keywords

This function can be used to find keywords in the uploaded text file (the algorithm is based on TF-IDF). The function will analyze all documents, regardless of their date.

Please specify the **CSV separator**, the **maximum number of keywords**, the **language** of the analysis (for stemming) and the **percentage of text to analyze**. A value of 1, for this last field, means that the full text will be analyzed; lower values indicate a lower percentage of text to analyze (e.g. 0.5 = the initial 50% of each document).

## Saved Reports

In this page you can see your saved reports and delete those that you do not need anymore. Please consider that every user has a **maximum number of reports** that can be saved. After this limit has been reached, you have to delete old reports in order to save new ones.

## Graphs only
<span style="color:#900C3F">**This function is only visible to advanced users.**</span>

Can be used when you have uploaded a ZIP file with past results, to produce merged graphs. See the [**Past Results Upload**](upload.md#past-results-upload) section, for details.
