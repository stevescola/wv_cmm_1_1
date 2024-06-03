# wv_cmm_1_1
Create a dashboard to monitor article/Locale status or rating

## Problem Statement

Based on the contributions of the crowd source authors, each article will have a different level of information that describes the Locale or destination. Wiki Voyage assigns a rating to the article based on a simple scale as defined below:

**Outline:** Introduction and a template outline laid out for the article

**Usable:** Enough information to visit the destination and find basic services (eat and sleep) with some references to other highlights

**Guide:** Covers most areas of the template to varying degrees of detail and completion but may deviate from the intended structure

**Star:** Follows the template and all sections are well covered to offer guidance to any traveler

## Dashboard Views
In short, this dashboard will enable us to query quality based on rating/status of the article for a specific Locale, as well as understand the distribution of status in aggregate within a region at various levels.

### Primary Data Views
The primary views to enable the user to explore content quality include:
**Individual Locale View**
- locale_name_raw
- locale_type
- wv_article_rating
- locale_id_is_part_of
- locale_is_part_of_country_idb
- locale_is_capital = TRUE
_Depending on complexity, would also like to view peer Locales under immediate parent Locale_

**Country View**


### Querying and Filtering

- Query an individual Locale for rating by typing name
- Display global map with country coloring based on country article rating
- Select country on map to view 
- Query by country with child Locales organized by subdivisions and sorted by rating [star, guide, usable, outline]
- Filter adn display child locales to country as either city or subdivision on country map (based on GPS) with colored point based on wv_article_rating
- Evaluate the distribution of articles by rating/status
- Drilling down by Locale hierarchy level from country to district
- At the article/locale level, cross over to a view of completeness which includes a KPI or breakdown

## Understanding the Data
There will be two data sets that will be essential for this dashboard:
- Article Meta Data
- Locale Header Data

The article meta data which is generated during the processing provides the article rating or status, as well as other data elements that can be used for this. The key elements will be:

- locale_id: identifier to create join across tables
- wv_article_title
- wv_article_rating: refers to the status
- article_text_size
- locale_is_part_of_locale_id
- locale_is_part_of_country_id

The "-is_part_of-" from the Locale Header will establish the association with the parent article/Locale to create the geographic hierarchy.

The files with the data is attached

### Data Location in AWS
The two data sets for the dashboard are located in AWS and accessible through Athena

### Miscellaneous Requirements and Notes
- The wv_article_rating data includes the locale_type in the string.  This should be stripped to leave only the rating 

**Article Meta Data**
- s3://wikivoyage-etl-dev/the-dictionaries/article_meta/
- File is in the folder with the most recent date

**Locale Header File**
- s3://wikivoyage-etl-dev/the-dictionaries/locale_header_df/
- File is in the folder with the most recent date
