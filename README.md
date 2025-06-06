Global COVID-19 Data Analysis - Power BI
This Power BI project provides an interactive dashboard to explore and analyze the global progression of the COVID-19 pandemic.

Objective:
To transform raw, cumulative COVID-19 time-series data into a structured format suitable for detailed analysis and visualization, enabling users to track daily trends, total impacts, and key epidemiological metrics across different regions.

Data Source:
Johns Hopkins University Center for Systems Science and Engineering (CSSE) COVID-19 Data:

time_series_covid19_confirmed_global.csv - (https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv)
time_series_covid19_deaths_global.csv - (https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_US.csv)
time_series_covid19_recovered_global.csv - (https://github.com/CSSEGISandData/COVID-19/blob/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_recovered_global.csv)

Methodology:

Data Extraction (Power Query):
Utilized Power Query's Web connector to directly import CSV files from the JHU CSSE GitHub repository.
Data Transformation (Power Query M Language):
Unpivoting: Transformed the date columns (each representing a day's cumulative count) into a tabular format with Date and Value columns for confirmed, deaths, and recovered data separately.
Data Type Handling: Implemented robust data type conversions, specifically addressing mixed date formats using "Change Type Using Locale" to ensure accurate date parsing. Error handling was also integrated to manage potential data inconsistencies.
Table Merging: Performed a series of Full Outer merges on Province/State, Country/Region, Lat, Long, and Date to combine the three individual datasets (Confirmed, Deaths, Recovered) into a single, comprehensive COVID_Global_Data fact table.
Data Modeling (Power BI Desktop):
Created a dedicated Calendar dimension table using DAX to establish a continuous date range and enable powerful time intelligence calculations.
Established one-to-many relationships between the Calendar table and the COVID_Global_Data fact table (and potentially other dimension tables like Location if created).
Calculated Measures (DAX):
Developed key DAX measures to derive analytical metrics:
Total Confirmed Cases, Total Deaths, Total Recovered
Daily New Confirmed Cases (calculates day-over-day difference)
Daily New Deaths
Case Fatality Rate % (Total Deaths / Total Confirmed Cases)
Rolling 7-Day Average Daily New Cases (for trend smoothing)
Interactive Visualizations:
Designed a user-friendly dashboard interface incorporating:
KPI Cards for overall metrics.
Line charts for daily and cumulative trend analysis.
Geographical maps to visualize regional impact.
Dynamic slicers for interactive filtering by date ranges and countries.
How to Use:

Clone this repository.
Open the COVID_Dashboard.pbix file in Power BI Desktop.
Refresh the data to pull the latest information from the JHU CSSE GitHub.
Explore the interactive dashboard.
Future Enhancements:

Integration of vaccination data.
Sentiment analysis from news sources.
Predictive modeling for future trends.

Results:
![WhatsApp Image 2025-06-06 at 18 37 01_71ca96f2](https://github.com/user-attachments/assets/127389d1-257c-4f93-9d78-fee66325d86a)
