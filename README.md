# wv_cmm_1_1
Create a dashboard to monitor article/Locale status or rating

## Problem Statement

Based on the contributions of the crowd source authors, each article will have a different level of information that describes the Locale or destination. Wiki Voyage assigns a rating to the article based on a simple scale as defined below:

**Outline:** Introduction and a template outline laid out for the article

**Usable:** Enough information to visit the destination and find basic services (eat and sleep) with some references to other highlights

**Guide:** Covers most areas of the template to varying degrees of detail and completion but may deviate from the intended structure

**Star:** Follows the template and all sections are well covered to offer guidance to any traveler

In short, this dashboard will enable us to query quality based on rating/status of the article for a specific Locale, as well as understand the distribution of status in aggregate within a region at various levels.

The visualization will enable to the viewer to:

- Query an individual Locale rating
- Evaluate the distribution of articles by rating/status, drilling down by Locale hierarchy level from country to district
- At the article/locale level, cross over to a view of completeness which includes a KPI or breakdown
- Map and chart views

## Understanding the Data
There will be two data sets that will be essential for this dashboard:
- Article Meta Data
- Locale Header Data

The article meta data which is generated during the processing provides the article rating or status, as well as other data elements that can be used for this. The key elements will be:

- wv_article_title
- wv_article_rating: refers to the status
- article_text_size

Will also need to map to "is_part_of" from the Locale Header (associated by locale_id to create an association with the parent article/Locale in the geographic hierarchy.

The files with the data is attached: 

[article_meta.csv](https://github.com/stevescola/wv_cmm_1_1/files/10778033/article_meta.csv)

[locale_header.csv](https://github.com/stevescola/wv_cmm_1_1/files/10778034/locale_header.csv)
