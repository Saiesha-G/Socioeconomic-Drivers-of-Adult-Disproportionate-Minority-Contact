# Socioeconomic Drivers of Adult Disproportionate Minority Contact
Interactive dashboard displaying map of socioeconomic factors (eg. % poverty, education, age, etc.) and booking rate of census tracts for Charlottesville and Albemarle County.

# Census & Crime Analysis Dataset (Python)

## Overview

This project works with a dataset combining tract-level demographic data from the U.S. Census Bureau and booking data provided by the Albemarle-Charlottesville Regional Jail (ACRJ). It utilizes U.S. Census Bureau shapefiles to produce an interactive map of Charlottesville City and Albemarle County that displays socioeconomic indicators of booking rate for each census tract in that region.

The primary dataset used (merged_census_data.xlsx) includes geographic identifiers, population demographics, socioeconomic indicators, and crime-related metrics.

---

## Dataset Schema

### Geographic Identifiers

* `STATEFP` — State FIPS code
* `COUNTYFP` — County FIPS code
* `TRACTCE` — Census tract code
* `GEOID` — Unique geographic identifier
* `GEOIDFQ` — Fully qualified GEOID
* `NAME` — Tract name
* `NAMELSAD` — Legal/statistical area description
* `MTFCC` — Feature classification code
* `FUNCSTAT` — Functional status

---

### Geographic Features

* `ALAND` — Land area (square meters)
* `AWATER` — Water area (square meters)
* `INTPTLAT` — Internal latitude
* `INTPTLON` — Internal longitude
* `geometry` — Polygon geometry
* `Location` — Coordinate point

---

### Population & Demographics

* `Total Pop` — Total population
* `Med Age` — Median age
* `% Male` — Percentage male
* `% Female` — Percentage female

---

### Race & Ethnicity

* `%Black` — Black population percentage
* `%White` — White population percentage
* `% Hisp` — Hispanic population percentage
* `% Asian` — Asian population percentage

---

### Crime Metrics

* `Crime Count/Pop *100` — Crime rate per 100 residents
* `Black Crime %` — Crimes attributed to Black individuals
* `Black Crime % / Black population` — Adjusted Black crime rate
* `White Crime %` — Crimes attributed to White individuals
* `White Crime % / White population` — Adjusted White crime rate

---

### Education

* `% HS Grad` — High school graduation rate
* `% Bach+` — Bachelor's degree or higher
* `% Enrolled` — School enrollment rate

---

### Economic Indicators

* `Med HH Inc` — Median household income
* `Mean HH Inc` — Mean household income
* `% Poverty` — Poverty rate
* `Med Home Val` — Median home value
* `Med Rent` — Median rent
* `% Owner Occ` — Owner-occupied housing rate

---

### Administrative Fields

* `State` — State name
* `County` — County name

---

### Aggregated Fields

* `Sum of Race` — Total race counts
* `Sum of Gender` — Total gender counts

---

### Arrest / Booking Data

* `Row Labels` — Category labels
* `Count of BookingNumber` — Number of bookings
* `Average of Age` — Average age of individuals
* `Count of Race` — Count grouped by race

#### Race Breakdown (Bookings)

* `American Indian/Alaskan Native`
* `Asian or Pacific Islander`
* `Unknown`
* `Black4`
* `White6`

---

### Crime Severity

* `Felony` — Felony counts
* `Misdemeanor` — Misdemeanor counts

---

### Education (Booking Records)

* `High School Diploma Claimed`
* `GED Claimed`

---

### Clustering

* `Cluster #` — Cluster assignment for grouping analysis

---

## Example Usage (Python)

```python
import pandas as pd

# Load the merged census data from the excel file
df_census = pd.read_excel('/content/merged_census_data.xlsx')

print("Successfully loaded the data.")

# Display the shape (number of rows and columns) of the DataFrame
print("\nShape of the DataFrame (rows, columns):")
print(df_census.shape)

# Check for missing values in each column
print("\nMissing values in each column:")
missing_values = df_census.isnull().sum()
print(missing_values[missing_values > 0])

if missing_values.sum() == 0:
    print("No missing values found in the DataFrame.")

# Display descriptive statistics for numerical columns
print("\nDescriptive statistics for numerical columns:")
display(df_census.describe())

```

---

## Requirements

* Python 3.8+
* pandas
* numpy (optional)
* matplotlib / seaborn (optional for visualization)
* geopandas (for working with geometry)
* plotly.express (for dashboard visualization) 

---

## Notes

* Some column names include spaces — consider renaming for easier use:

```python
df.columns = df.columns.str.replace(" ", "_")
```

* Geometry fields may require GeoPandas:

```python
import geopandas as gpd
gdf = gpd.read_file("data.geojson")
```

---

## License

MIT License.

---

## Author

Saiesha Gohil

Department of Systems and Information Engineering, 
School of Engineering and Applied Sciences,
University of Virginia
