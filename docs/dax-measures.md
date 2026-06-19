# DAX Measures

## Overview

The Power BI dashboard uses DAX measures to calculate key outbreak metrics and support interactive analysis.

The measures are organized in a dedicated table called:

```text id="gq866b"
_Measures
```

This keeps the model easier to maintain and separates business calculations from raw data fields.

## Main Measures

### Total Outbreaks

Counts the total number of outbreak records.

```DAX id="ejew11"
Total Outbreaks =
COUNTROWS('ob_report')
```

### Active Outbreaks

Counts outbreaks that are currently active.

```DAX id="gxb368"
Active Outbreaks =
CALCULATE(
    [Total Outbreaks],
    'ob_report'[Status] = "Active"
)
```

### Closed Outbreaks

Counts outbreaks that are no longer active.

```DAX id="5fza1u"
Closed Outbreaks =
CALCULATE(
    [Total Outbreaks],
    'ob_report'[Status] = "Closed"
)
```

### Active Rate

Calculates the percentage of outbreaks that are active.

```DAX id="l9ljdw"
Active Rate =
DIVIDE(
    [Active Outbreaks],
    [Total Outbreaks]
)
```

### Average Duration

Calculates the average outbreak duration in days.

```DAX id="0qi6w9"
Average Duration =
AVERAGE('ob_report'[Duration Days])
```

### New Outbreaks Last 7 Days

Counts outbreaks that started in the last seven days.

```DAX id="c6i18a"
New Outbreaks Last 7 Days =
CALCULATE(
    [Total Outbreaks],
    FILTER(
        'ob_report',
        'ob_report'[Date Outbreak Began] >= TODAY() - 6
            && 'ob_report'[Date Outbreak Began] <= TODAY()
    )
)
```

### Distinct Institutions

Counts the number of unique healthcare institutions in the data.

```DAX id="oudjgr"
Distinct Institutions =
DISTINCTCOUNT('ob_report'[Institution Name])
```

## Supporting Calculated Columns

### Status

Creates a readable status label from the active flag.

```DAX id="yiqfuv"
Status =
IF(
    'ob_report'[Active] = "Y",
    "Active",
    "Closed"
)
```

### Duration Days

Calculates outbreak duration. For active outbreaks, the calculation uses today's date as the temporary end date.

```DAX id="wst51g"
Duration Days =
DATEDIFF(
    'ob_report'[Date Outbreak Began],
    COALESCE('ob_report'[Date Declared Over], TODAY()),
    DAY
)
```

## How the Measures Are Used

The measures are used in:

* KPI cards
* trend visuals
* active versus closed outbreak analysis
* outbreak type breakdowns
* causative agent analysis
* active outbreak detail table

Because the measures respond to slicers, users can analyze outbreak metrics by:

* Month Year
* status
* setting
* outbreak type
* causative agent

## Screenshot

The DAX measures table is shown in:

```text id="k5bgav"
screenshots/development/11_dax_measures.png
```
