# COVID-19 Trends Analysis & Time-Series Forecasting

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Pandas](https://img.shields.io/badge/Data%20Analysis-Pandas-150458?logo=pandas)
![Visualization](https://img.shields.io/badge/Visualization-Matplotlib%20%7C%20Seaborn%20%7C%20Plotly-orange)
![Forecasting](https://img.shields.io/badge/Forecasting-Prophet-0072B2)

An exploratory data analysis and time-series forecasting project examining the global spread of COVID-19. The notebook uses Python to analyze confirmed cases, deaths, recoveries, and active cases; compare selected countries; visualize geographic patterns; and generate short-horizon forecasts with Prophet.

> **Data period:** 22 January 2020 – 27 July 2020  
> **Coverage in the notebook:** 49,068 rows, 188 daily observations, and 187 country-level labels.

## Table of Contents
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [Dataset](#dataset)
- [Tools and Technologies](#tools-and-technologies)
- [Workflow and Analysis](#workflow-and-analysis)
- [Key Results and Observations](#key-results-and-observations)
- [Forecasting Approach](#forecasting-approach)
- [Project Structure](#project-structure)
- [Skills Demonstrated](#skills-demonstrated)

## Problem Statement

COVID-19 case counts changed rapidly across countries during the early stages of the pandemic. The goal of this project is to explore those changes using historical data, communicate trends through visualizations, compare country-level patterns, and build a baseline forecast for the following seven days.

The analysis focuses on:
- How confirmed cases and reported deaths changed over time globally.
- How the top 3 countries compared across confirmed, death, recovered, and active cases.
- How reported COVID-19 activity varied geographically.
- What a simple time-series model projected for confirmed cases, deaths, active cases, and recoveries over a seven-day horizon.

## Project Objectives

1. Load and inspect a structured COVID-19 dataset with Pandas.
2. Aggregate daily case counts for global trend analysis.
3. Visualize confirmed cases and deaths over time.
4. Identify and compare countries using reported case metrics.
5. Compare time-series patterns for the top 3 confirmed cases countries.
6. Build seven-day forecasts with Facebook/Meta Prophet.
7. Present geographic patterns with a Plotly choropleth map.
8. Document assumptions and limitations that matter when interpreting the results.

## Dataset

The notebook reads a cleaned COVID-19 dataset named `covid_19_clean_complete.csv`.

The dataset contains the following fields:

| Column | Description |
|---|---|
| `Province/State` | Province or state, where available |
| `Country/Region` | Country or region label |
| `Lat`, `Long` | Geographic coordinates |
| `Date` | Date of the observation |
| `Confirmed` | Reported confirmed cases |
| `Deaths` | Reported deaths |
| `Recovered` | Reported recoveries |
| `Active` | Reported active cases |
| `WHO Region` | WHO geographic region classification |

The notebook renames `Province/State` to `State` and `Country/Region` to `Country` for easier analysis. The date range and record counts above come from the notebook's loaded dataset.

**Data note:** These are historical reported figures, not current COVID-19 statistics. Reporting practices and data definitions may differ across locations and dates.

## Tools and Technologies

- **Python** — analysis workflow
- **Pandas** — data loading, grouping, aggregation, and reshaping
- **Matplotlib & Seaborn** — trend lines and comparative charts
- **Plotly Express** — interactive choropleth visualization
- **Prophet** — time-series forecasting

## Workflow and Analysis

### 1. Data loading and inspection
- Loaded the CSV into a Pandas DataFrame.
- Inspected its dimensions, columns, data types, and date coverage.
- Renamed country and state columns for readability.

### 2. Global trend analysis
- Grouped records by date and summed confirmed cases and deaths.
- Created line charts to show the progression of reported global totals over the study period.

### 3. Country-level comparison
- Aggregated the four main measures (`Confirmed`, `Deaths`, `Recovered`, and `Active`) by country.
- Ranked countries using confirmed-case and death totals produced by the notebook.
- Selected the United States, Brazil, and Russia for daily comparisons.


### 4. Country time-series visualizations
Created comparative line charts for the United States, Brazil, and Russia covering:
- Confirmed cases
- Deaths
- Recoveries
- Active cases

These plots help compare the direction and pace of reported case growth over the same historical period.

### 5. Geographic visualization
- Aggregated the case metrics by country.
- Used Plotly Express to create a world choropleth map colored by active-case values.

The map is intended as an exploratory view of geographic distribution. Its country values inherit the aggregation caveat described above.

### 6. Seven-day forecasting
- Prepared global daily totals for Prophet using the required `ds` (date) and `y` (target) columns.
- Fit separate Prophet models for confirmed cases, deaths, active cases, and recovered cases.
- Generated a seven-day future date range and visualized forecasts with prediction intervals.

## Key Results and Observations

The following observations are directly supported by the notebook's data and charts:

- The dataset contains **188 daily observations**, from **22 January through 27 July 2020**, with **49,068 rows** across its country/province-date records.
- Global reported confirmed cases increased from **555 on 22 January 2020** to **16,480,485 on 27 July 2020**.
- Global reported deaths increased from **17 on 22 January 2020** to **654,036 on 27 July 2020**.
- The notebook compares the United States, Brazil, and Russia across confirmed, death, recovered, and active case trends.
- Prophet was used to produce **seven-day forecasts** for confirmed cases, deaths, active cases, and recoveries, with forecast intervals available in its output.
- A Plotly choropleth map was created to explore the geographic distribution of active cases.

These figures describe the historical dataset and should not be read as current statistics. The notebook does not calculate formal forecast error metrics or validate predictions against subsequently observed data, so forecast accuracy has **not** been established.

## Forecasting Approach

The notebook uses Prophet, a time-series forecasting library, to model each global daily metric independently.

**Model inputs**
- `ds`: observation date
- `y`: daily global total for the metric being modeled

**Forecast horizon:** 7 days beyond the last observation (28 July – 3 August 2020).

The notebook displays the forecast and its lower/upper prediction bounds. These outputs are baseline projections based on the historical series; they are not causal estimates or epidemiological forecasts and should be interpreted with caution.


## Project Structure

```text
.
├── COVID-19_Analysis.ipynb
├── covid_19_clean_complete.csv
└── README.md
```

## Skills Demonstrated

- Exploratory Data Analysis (EDA)
- Data cleaning and schema inspection
- Group-by aggregation and time-series reshaping with Pandas
- Data visualization and comparative trend analysis
- Geographic data visualization
- Time-series forecasting with Prophet
- Communicating findings and documenting analytical limitations

---

*Built as a Python data analysis project exploring historical COVID-19 trends and baseline time-series forecasts.*
