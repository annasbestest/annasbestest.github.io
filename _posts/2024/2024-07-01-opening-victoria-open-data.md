---
layout: post
title: "Opening up Victoria’s open data platform"
---



The State Government of Victoria's _"open data platform"_ <a href="https://www.data.vic.gov.au/about-datavic">DataVic</a> is promoted as _"the place to discover and access Victorian Government open data."_

However, every time I’ve attempted to use it, I’ve struggled to discover any interesting data that is more than a twenty-row Excel table.

### The problem
The DataVic platform:
- Has limited functionality for discovering and exploring data
- Doesn't allow searches on data columns or sample data

### The idea
Having recently watched a <a href="https://www.youtube.com/watch?v=PwFrN3dFiwY">demonstration</a> on how to query Google Gemini Pro's large <a href="https://blog.google/technology/ai/long-context-window-ai-models/">context window</a>, I realised that with some web scraping and data preparation, I could create a large text file profiling all available datasets on DataVic. Feeding this text file into Gemini's context window might allow me to quickly perform discovery analyses of the DataVic library.

### The approach
I wrote a script that downloaded every available CSV from the DataVic platform and created a "master_data_profile.txt" that contains the profile of every CSV dataset. The profiling for each CSV included:
- Filename
- Dataset pagee URL and description
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
The best way to demonstrate the capabilities of Google Gemini is to DIY on the <a href="https://aistudio.google.com">Google AI Studio</a> platform, using the <a href="https://www.youtube.com/watch?v=PwFrN3dFiwY">demonstration</a> video linked above as a general guide and importing the <a href="https://github.com/sc0h0/openingvicgovdata/blob/main/master_data_profile.txt">master_data_profile.txt</a> into the context window. Here are some inspiring examples.

#### Example: As an aspiring data scientist...

<figure>
  <img src="/assets/vicopendata/eg_datascientist.png" alt="" loading="lazy">
</figure>

#### Example: As a Member of Parliament...

<figure>
  <img src="/assets/vicopendata/example2.png" alt="" loading="lazy">
</figure>


### The serious
At some point, we've all been on the receiving end of a large email distribution list where someone is at their wit's end, trying to track down an obscure dataset and broadcasting their struggle to over 500 staff. Or, like in my experience, used an inferior dataset not knowing a more granular and accurate equivalent was available.

An internal _data discovery tool_ having capabilities like those demonstrated above could drive business efficiency in terms of effort to identify and acquire accurate and relevant data, as well as promoting awareness of organisational data, and innovating with data that is otherwise under-utilised.

While this was a quick and dirty bedroom experiment, it's worth noting that in the last three months, Google Gemini's token size has increased from 1.5M to 2M tokens which translates to capacity of profiling around 1200 datasets in a given context.

### Resources
My GitHub repository containing master dataset profile and scripts used to scrape data: https://github.com/sc0h0/openingvicgovdata

