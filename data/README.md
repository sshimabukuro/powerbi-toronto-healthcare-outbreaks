\# Data



\## Data Source



This project uses public open data from the City of Toronto Open Data Portal.



\*\*Dataset:\*\* Outbreaks in Toronto Healthcare Institutions

\*\*Source:\*\* City of Toronto Open Data Portal

\*\*Dataset link:\*\* https://open.toronto.ca/dataset/outbreaks-in-toronto-healthcare-institutions/

\*\*Open data platform:\*\* CKAN

\*\*CKAN link:\*\* https://ckan.org/



\## Files Included



The raw CSV files are stored in the `data/raw/` folder.



The source files follow the naming convention:



```text

ob\_report\_YYYY.csv

```



where `YYYY` represents the year of the outbreak data.



Files included:



```text

data/raw/

├── ob\_report\_2019.csv

├── ob\_report\_2020.csv

├── ob\_report\_2021.csv

├── ob\_report\_2022.csv

├── ob\_report\_2023.csv

├── ob\_report\_2024.csv

├── ob\_report\_2025.csv

└── ob\_report\_2026.csv

```



\## Why the Data Is Included



The raw CSV files are included so the Power BI report can be reviewed and refreshed by someone who downloads this repository.



The dataset is public open data. Including the CSV files makes the project easier to inspect and reproduce.



\## How the Data Is Used



The Power BI report combines the yearly CSV files into one outbreak table using Power Query.



The report filters files that follow the outbreak report naming pattern and combines them into a single table for analysis.



The combined table is then used to analyze:



\* outbreak trends over time

\* active versus closed outbreaks

\* outbreak setting

\* outbreak type

\* causative agent

\* outbreak duration

\* institution-level active outbreak details



\## Refreshing the Power BI Report



The Power BI file uses a parameter called:



```text

DataFolderPath

```



To refresh the report on your own computer:



1\. Download or clone this repository.

2\. Open the Power BI file:



```text

powerbi/Toronto\_Healthcare\_Outbreaks.pbix

```



3\. In Power BI Desktop, go to:



```text

Home > Transform data > Edit parameters

```



4\. Update the `DataFolderPath` parameter so it points to your local copy of the `data/raw` folder.



Example:



```text

C:\\your-folder\\powerbi-toronto-healthcare-outbreaks\\data\\raw

```



5\. Click \*\*Apply Changes\*\*.

6\. Refresh the report.



\## Notes



The report was designed using data from 2019 onward to focus on COVID-19 and recent outbreak patterns.



The 2026 dataset was rated Gold quality, while previous years were rated Silver quality. Overall, the source data quality was strong and did not require significant manual cleaning.



One important data interpretation note is that `Coronavirus\*` and `COVID-19` were kept separate. The data portal documentation explains that `Coronavirus\*` refers to seasonal coronavirus and not COVID-19.



