---
layout: page
title: Input
---

# File Upload
The app can analyze any textual data, uploaded as a **CSV** file with the following characteristics:

- Has **no header**.
- Is fully encoded in **utf-8**.
- **Text** has to be in the **first column**, and **dates (mm/dd/yyyy)** in the second column. No other date formats are accepted. 
- Text must have **no quoting**, and the **CSV separator** must **not** be **in the text field**.
- **Source weights** (optional) can be in the **third column**. Please note that **higher scores** indicate **more important sources**.
- Each user has a **maximum** allowed **file size**. Uploading bigger files is not allowed and they will be automatically deleted after upload.

You can analyze only one file at a time. The uploader will retain only the last uploaded CSV file, deleting the others.

------

## Validation
This function is used to validate the uploaded CSV file and verify that there are no errors. Please:

- specify the **CSV separator** and the **minimum length** of documents (has to be at least 3 characters);
- optionally choose to **validate weights** placed in the third column of the uploaded file;
- optionally choose to automatically **remove lines with errors**. Please **be careful**, as this will change the uploaded file;
- optionally choose to **remove all text documents (file rows) that contain** one or more words listed in the field named **prohibited words**.

The system will also offer the **possibility to download** the input file that has been corrected.

------

## Past Results Upload
<span style="color:#900C3F">**This function is only available to advanced users.**</span>

This function can be used to **merge the results** of different past analyses and produce a **unified report**. For example, youd could merge analyses carried out considering the same set of brands, but different timeframes.
In order to successfully merge results of past analyses, you have to:

- Upload a **single zip file** containing all the results of previous analyses. Do **not use folders** inside the ZIP file.
- Keep the **orignal form of file names, just adding numbers at their end** (1, 2, 3,..). They will be merged automatically. Names of files in the ZIP have **mandatory prefixes** (the same as the app output), see an example here: `SBS_R_FULL1.csv, SBS_R_FULL2.csv, ..., SBS_associations1.csv, SBS_associations2.csv, ..., SBS_mostcommon1.csv, SBS_mostcommon2.csv, ...`
- Do not include file different than those above-mentioned.
- Use the **FULL** version of **results** file and not the SMALL one.
- Remember that merging topic models, brand similarity and target words graphs is not allowed (as it has little sense). Please **avoid putting these files into the ZIP**.
- **Avoid overlap of dates** for the single brand.
- Remember that each user has a **maximum file size** allowed for the upload. Files above this limit will be automatically deleted after upload.
- Remember that you can upload only one zip file at a time. The uploader **will retain only the last uploaded zip file**, deleting the others.



