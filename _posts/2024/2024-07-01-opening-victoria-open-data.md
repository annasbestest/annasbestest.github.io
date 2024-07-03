---
layout: post
title: "Opening up Victoria’s open data platform"
---



The State Government of Victoria's _"open data platform"_ <a href="https://www.data.vic.gov.au/about-datavic">DataVic</a> is promoted as _"the place to discover and access Victorian Government open data."_

However, every time I’ve attempted to use it, I’ve struggled to discover any interesting data that is more than a ~30 row Excel table. For example, the search function only references the dataset description, not the dataset name or fields.

### The problem
The DataVic platform:
- Provides insufficient discovery tools for exploring data
- Doesn't allow search on data columns or sample data

### The idea
Having recently watched a <a href="https://www.youtube.com/watch?v=PwFrN3dFiwY">demonstration</a> on how to query Google Gemini Pro's large context window, I realised that with some web scraping and data preparation, a large text file profiling all available datasets on DataVic might allow me to use Gemini to quickly perform discovery analyses of the DataVic library.

### The approach
I wrote a script that downloaded every available CSV from the DataVic platform and created a "master_data_profile.txt" that contains the profile of every CSV dataset. The profiling for each CSV included:
- Filename
- Dataset page and description
- Filesize and rows
- Columns and two rows of sample data

For example:

<figure>
  <img src="/assets/vicopendata/sample_json_2.png" alt="" loading="lazy">
  <figcaption>
    A sample json file profiling data available on DataVic
  </figcaption>
</figure>

I had some issues with programmatically opening Excel files (they were usually small tables anyway), so I decided to limit the analysis to simple CSVs. In total, there were around 670 CSV files. However, only 300 had more than 500 rows (I decided less than 500 rows is more a table rather than _data_). There should have been more CSVs, but it appears some of the APIs referenced by DataVic were broken.

<figure>
  <img src="/assets/vicopendata/nodata.png" alt="" loading="lazy">
  <figcaption>
    Broken links on VicGov.
  </figcaption>
</figure>

Noting that as of July 2024 the platform boasts around 5,700 datasets, that's far from the 300 that (in my opinion) are true datasets!

<figure>
  <img src="/assets/vicopendata/searches_main.png" alt="" loading="lazy">
  <figcaption>
    VicGov's claimed number of open datasets.
  </figcaption>
</figure>

### The fun
The best way to demonstrate the capabilities of Google Gemini is to DIY on the <a href="https://aistudio.google.com"></a>, using the video linked above as a general guide and importing the <a href="[https://aistudio.google.com](https://github.com/sc0h0/openingvicgovdata/blob/main/master_data_profile.txt)">master_data_profile.txt</a>. However, here are some inspiring examples.

#### Example: As an "eSafety advisor"...

<figure>
  <img src="/assets/vicopendata/example1.png" alt="" loading="lazy">
</figure>

#### Example: As a Member of Parliament...

<figure>
  <img src="/assets/vicopendata/example2.png" alt="" loading="lazy">
</figure>


### The serious
I can easily see this technology being used in large companies that have employees spending a lot of their time tracking down data or using one data source not knowning there is another, more reliable data source.
As of today, Gemini has around 2M available tokens which translates to profiling around 1200 datasets in a given context. 

### Resources
My GitHub repository containing master dataset profile and scripts used to scrape data: https://github.com/sc0h0/openingvicgovdata


### End
Feel free to fork and modify either repository (linked in the examples above) to set up your own Facebook Marketplace alerts!
