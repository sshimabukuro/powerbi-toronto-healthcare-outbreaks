# Data Model

## Overview

The Power BI report uses a simple model with one main outbreak table and a Calendar table.

The model was designed to support time-based analysis, interactive filtering, and clean dashboard reporting.

## Tables

### ob_report

The `ob_report` table is the main outbreak table.

Each row represents one outbreak record.

Main fields include:

* institution name
* institution address
* outbreak setting
* outbreak type
* causative agent
* date outbreak began
* date declared over
* active status

The yearly CSV files from 2019 onward were combined into this table using Power Query.

### Calendar

The `Calendar` table was created to support time-based analysis.

It includes date fields such as:

* date
* year
* month
* month name
* month year
* quarter
* start of month
* week start

The Calendar table is connected to the outbreak table using the outbreak start date.

## Relationship

The model uses a relationship between:

```text
Calendar[Date] -> ob_report[Date Outbreak Began]
```

This relationship allows the dashboard to analyze outbreaks by year, month, month year, and other date attributes.

## Why Use a Calendar Table?

A Calendar table keeps the model cleaner and supports better time-based reporting.

Instead of creating year and month fields directly in the outbreak table, the date attributes are stored in the Calendar table.

This approach helps with:

* Month Year filtering
* correct month sorting
* trend analysis over time
* cleaner model structure
* easier future enhancements

## Model Design Decision

The outbreak table was kept focused on event-level outbreak details.

The Calendar table was used for date grouping, sorting, and time filtering.

This design follows a simple star-schema approach, where the outbreak table acts as the fact table and the Calendar table acts as a date dimension.

## Screenshot

The model view is available in the repository:

```text
screenshots/development/09_data_model.png
```

