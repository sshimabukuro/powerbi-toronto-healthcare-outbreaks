# Data Preparation

## Overview

This project uses yearly CSV files from the City of Toronto Open Data Portal. The files were combined in Power BI using Power Query to create one consolidated outbreak table for analysis.

The preparation process focused on:

* combining multiple yearly files
* validating data types
* reviewing data quality
* preserving the meaning of source values
* preparing the data for time-based analysis

## Source File Naming Convention

The source files follow this naming convention:

```text id="s01c4p"
ob_report_YYYY.csv
```

where `YYYY` represents the year of the outbreak data.

For this project, files from 2019 onward were loaded because the analysis focused on COVID-19 and recent outbreak patterns.

## Power Query Process

The yearly CSV files were loaded from a folder and combined into one table.

The main Power Query steps were:

1. Load files from the data folder.
2. Filter to include only CSV files.
3. Filter to include files that start with `ob_report`.
4. Remove hidden files.
5. Apply the file transformation function.
6. Expand the combined table.
7. Set the correct column data types.
8. Load the final table into the Power BI model.

This process allows new yearly outbreak files to be added to the folder and included in the report with minimal manual changes.

## DataFolderPath Parameter

The Power BI file uses a parameter called:

```text id="6lwb8n"
DataFolderPath
```

This parameter stores the folder path where the CSV files are located.

Using a parameter makes the report easier to refresh on another computer. A user who downloads this repository can update the parameter to point to their local copy of the `data/raw` folder.

Example:

```text id="b6jqvy"
C:\your-folder\powerbi-toronto-healthcare-outbreaks\data\raw
```

## Data Quality Review

The dataset quality was generally strong.

The 2026 dataset was rated Gold quality, while previous years were rated Silver quality. Because of the quality of the source data, significant manual data cleaning was not required.

The main validation checks included:

* confirming that date fields were loaded as dates
* reviewing categorical fields such as setting, type, status, and causative agent
* checking that yearly files were combined correctly
* ensuring duplicated files were not included
* confirming that the dashboard totals matched the expected filtered view

## Important Data Interpretation Decision

One important validation step involved the causative agent field.

The dataset included both:

```text id="x64rfw"
COVID-19
Coronavirus*
```

At first, it could seem reasonable to group these values together. However, the data portal documentation explains that `Coronavirus*` refers to seasonal coronavirus and not COVID-19.

For that reason, the two values were kept separate in the analysis.

This helped preserve the meaning of the original data and avoid overstating COVID-19-related outbreaks.

## Final Prepared Table

The final prepared table supports analysis by:

* outbreak start date
* declared over date
* active or closed status
* healthcare setting
* outbreak type
* causative agent
* institution name
* institution address
* outbreak duration

This table was then connected to a Calendar table for time-based reporting.
