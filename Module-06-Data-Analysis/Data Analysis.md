# Model the Data: Correlation with Excel

## Step 1: Enable the Data Analysis ToolPak

Before starting the analysis, make sure the Excel Data Analysis ToolPak is enabled:

1. Go to **File** > **Options**  
2. Select **Add-ins** from the left panel  
3. At the bottom, ensure **Manage** is set to **Excel Add-ins**, then click **Go**  
4. Check **Analysis ToolPak** and click **OK**  
5. You can now access it from the **Data** tab under **Data Analysis**  

---

## Step 2: Generate a Correlation Matrix

1. Prepare your dataset by keeping only the required columns:  
   **New cases, New deaths, New vaccinations**  
2. Go to the **Data** tab → click **Data Analysis**  
3. Select **Correlation** → click **OK**  
4. **Input Range:** Select the three columns and check **Labels in first row**  
5. **Output Range:** Choose a location in the same sheet → click **OK**  

---

### Interpreting the Matrix Results

Correlation values range from **-1 to +1**:

- **New Cases vs. New Deaths**  
  - Correlation: **0.84**  
  - Interpretation: Very strong positive relationship  

- **New Vaccinations vs. New Deaths**  
  - Correlation: **0.23**  
  - Interpretation: Weak positive relationship  

---

## Step 3: Visualizing Data with Scatterplots

Scatterplots help in visually understanding correlations.

---

### Plot 1: New Cases vs. New Deaths

1. Select "New cases" (X-axis) and "New deaths" (Y-axis)  
2. Go to **Insert → Recommended Charts → All Charts → X Y (Scatter)**  
3. Click **OK**  
4. Add a trendline: **Chart Elements → Trendline**  
5. Format it (solid line, thicker, red color)  

**Insight:**  
The steep slope confirms the strong positive correlation (**0.84**).

---

### Plot 2: New Vaccinations vs. New Deaths

1. Arrange data with "New vaccinations" (X-axis) and "New deaths" (Y-axis)  
2. Insert a scatter plot using the same steps  
3. Add and format the trendline  

**Insight:**  
The flatter slope reflects a weaker correlation (**0.23**).  
Initially, low vaccination levels correspond to higher deaths, while increasing vaccinations show a gradual decline in deaths.

---

# Model the Data: Regression with Excel

## Variables in this Analysis

- **Dependent Variable (Y):** New deaths  
- **Independent Variables (X):**  
  - New cases  
  - New tests  
  - New vaccinations  
  - Stringency index  

---

## Step 1: Data Preparation

Prepare the dataset for better interpretation:

1. Create three new columns:  
   - **New cases per 1000**  
   - **New tests per 1000**  
   - **New vaccinations per 1000**  

2. Calculate values by dividing original data by 1000  

---

## Step 2: Running the Regression Tool

1. Go to the **Data** tab → click **Data Analysis**  
2. Select **Regression** → click **OK**  
3. **Input Y Range:** Select **New deaths**  
4. **Input X Range:** Select all independent variables  
5. Check **Labels** if headers are included  
6. Choose **New Worksheet Ply** for output  
7. Click **OK**  

---

## Step 3: Interpreting the Output

Analyze the regression output using the following metrics:

---

### 1. Adjusted R Square

- **Value:** **0.816**  
- **Meaning:**  
  About **81.6%** of the variation in new deaths is explained by the independent variables.  

---

### 2. Significance F (Model Validity)

- **Result:** Less than **0.05**  
- **Meaning:**  
  The regression model is statistically significant and a good fit.  

---

### 3. P-values (Variable Significance)

- **New cases, New tests, New vaccinations**  
  - P-values < 0.05  
  - These variables are statistically significant  

- **Stringency index**  
  - P-value = **0.11** (> 0.05)  
  - Not statistically significant → should not be relied upon  

---

### 4. Coefficients (Understanding Relationships)

- **New cases per 1000:** ~**7**  
  - For every 1000 new cases, deaths increase by 7  

- **New tests per 1000:** **0.69**  
  - For every 1000 tests, deaths increase by 0.69  

- **New vaccinations per 1000:** **-0.07**  
  - Indicates a slight decrease in deaths  
  - Effect is very small → not strong enough for firm conclusions  

- **Stringency index:** **2.71**  
  - Suggests stricter policies increase deaths  
  - However, since P-value > 0.05, this result is not statistically reliable  
  - Indicates need for deeper analysis  

---
# Forecast Functions in Excel (Linear Regression & Time Series)

## Introduction

In this tutorial, we explore the **FORECAST function in Microsoft Excel**.

The `FORECAST` function performs **linear regression behind the scenes** and uses it to predict future values.

A synonym for this function is: FORECAST.LINEAR



Both functions work exactly the same.


# Dataset Used

We will use a **Height and Weight dataset** from Kaggle.

The dataset contains information about **25,000 people**, including:

- Height (in inches)
- Weight (in pounds)

For demonstration purposes, we will only use **1,000 rows**.

Example data:

| Height (inches) | Weight (pounds) |
|-----------------|----------------|
| 65 | 120 |
| 68 | 140 |
| 70 | 155 |

---

# Converting Units to Metric

Since the dataset uses **inches and pounds**, we convert them to **metric units**.

## Convert Height (Inches → Centimeters)

Formula:

```

Height_cm = Height_inches * 2.54

````

Example Excel formula:

```excel
=A2 * 2.54
````

---

## Convert Weight (Pounds → Kilograms)

Formula:

```
Weight_kg = Weight_pounds / 2.20462
```

Example Excel formula:

```excel
=B2 / 2.20462
```

After conversion, drag the formulas down to apply them to the entire dataset.

---

# Visualizing the Data

To understand the relationship between height and weight, we create a **scatter plot**.

Steps:

1. Select the **Height (cm)** column.
2. Select the **Weight (kg)** column.
3. Insert → Chart → **Scatter Plot**

Observation:

* Height ranges roughly **160 cm to 185 cm**
* Weight ranges roughly **50 kg to 65 kg**
* There is a **positive linear relationship** between height and weight.

---

# Using the FORECAST Function

The syntax of the function is:

```excel
=FORECAST(x, known_y's, known_x's)
```

Where:

* `x` → Value we want to predict for
* `known_y's` → Dependent variable (target)
* `known_x's` → Independent variable

---

# Example: Predict Weight from Height

Suppose we want to predict the **weight of a person who is 170 cm tall**.

```excel
=FORECAST(170, WeightRange, HeightRange)
```

Example result:

```
170 cm → predicted weight ≈ 56 kg
```

---

# Reverse Prediction (Height from Weight)

We can also reverse the variables.

Example:

Predict **height for a person weighing 75 kg**.

```excel
=FORECAST(75, HeightRange, WeightRange)
```

Example result:

```
75 kg → predicted height ≈ 180 cm (≈ 6 feet)
```

---

# Forecasting Multiple Values

Suppose we want predictions for several heights:

| Height |
| ------ |
| 150    |
| 155    |
| 160    |
| 165    |
| 170    |

One way is to copy the formula:

```excel
=FORECAST(A2, WeightRange, HeightRange)
```

Then drag the formula down.

However, this approach is **inefficient** because each formula calculates regression independently.

---

# Using the TREND Function

A better approach is using the `TREND` function.

Syntax:

```excel
=TREND(known_y's, known_x's, new_x's)
```

Example:

```excel
=TREND(WeightRange, HeightRange, NewHeightRange)
```

Benefits:

* Computes regression **once**
* Applies predictions to the **entire array**
* Automatically fills the column

`TREND` returns the same values as `FORECAST`.

---

# Compatibility with Google Sheets

These functions are also available in **Google Sheets**:

* `FORECAST`
* `FORECAST.LINEAR`
* `TREND`

You can:

1. Save the Excel file
2. Open in Google Sheets
3. Edit
4. Save and reopen in Excel

Everything works perfectly.

---

# Limitation of Linear Regression

Linear regression works well for **simple linear relationships**.

However, it performs poorly for **cyclical or seasonal data**.

Example:

Traffic data across time.

Dataset:

| DateTime    | Number of Vehicles |
| ----------- | ------------------ |
| 01-01 08:00 | 25                 |
| 01-01 09:00 | 40                 |
| 01-01 10:00 | 32                 |

When plotted, traffic data shows:

* Daily peaks
* Weekly patterns
* Weekend drops
* Holiday effects

This pattern is **seasonal**, not linear.

---

# Linear Prediction on Traffic Data

Using TREND:

```excel
=TREND(VehicleValues, DateTimeValues, FutureDateTimes)
```

Result:

* Predicts around **20 vehicles**
* Slight upward slope
* Fails to capture peaks and valleys

This shows **linear regression is not suitable for seasonal data**.

---

# Using FORECAST.ETS (Time Series Forecasting)

For cyclical data, Excel provides:

```
FORECAST.ETS
```

This uses **Exponential Triple Smoothing (ETS)**.

Syntax:

```excel
=FORECAST.ETS(target_date, values, timeline, [seasonality], [data_completion], [aggregation])
```

---

# Example Usage

```excel
=FORECAST.ETS(A2, $B$2:$B$1000, $A$2:$A$1000)
```

Where:

* `A2` → Target date
* `B2:B1000` → Vehicle counts
* `A2:A1000` → Timeline

---

# Optional Parameters

## Seasonality

Defines the repeating cycle.

Example:

```
24 → season repeats every 24 data points
```

Example for hourly traffic data:

```
24 = daily pattern
```

If omitted, Excel **automatically detects seasonality**.

---

## Data Completion

Handles missing values.

Options:

```
1 → Interpolation (default)
0 → Missing values treated as zero
```

---

# Comparing Predictions

When plotted together:

| Line   | Meaning         |
| ------ | --------------- |
| Blue   | Actual data     |
| Orange | Linear forecast |
| Green  | ETS forecast    |

Observations:

* Linear prediction → almost flat line
* ETS prediction → follows seasonal patterns better

---

# Key Takeaways

### FORECAST / FORECAST.LINEAR

* Uses **linear regression**
* Works well for **linear relationships**
* Poor for seasonal data

### TREND

* Same as FORECAST
* More efficient for **multiple predictions**

### FORECAST.ETS

* Designed for **time series forecasting**
* Captures **seasonality**
* Better for **cyclical data**

---
---
# Outlier Detection in Excel

## Introduction

In data analysis, it is important to identify **outliers** — values that are significantly higher or lower than the rest of the dataset.

Outliers may occur because of:

- Data entry mistakes
- Measurement errors
- Rare but valid observations

These values can distort statistical analysis such as **mean, regression, or forecasting**, so detecting them early is important. :contentReference[oaicite:1]{index=1}

---

# What is an Outlier?

An **outlier** is a data point that lies far away from the majority of data values.

Example dataset:

| Values |
|------|
| 10 |
| 12 |
| 13 |
| 14 |
| 15 |
| 200 |

Here **200** is clearly far away from the rest of the values and is considered an outlier.

Outliers can significantly impact the **average and statistical interpretation of data**. :contentReference[oaicite:2]{index=2}

---

# Dataset Example in Excel

Suppose we have a dataset like this:

| Student | Score |
|------|------|
| A | 52 |
| B | 55 |
| C | 60 |
| D | 58 |
| E | 95 |

In this dataset, **95 may be an outlier** depending on the statistical distribution.

---

# Method 1: Detect Outliers Using Sorting

The simplest method:

### Steps

1. Select the dataset
2. Go to **Data → Sort**
3. Sort values **Ascending or Descending**
4. Look for unusually large or small numbers

Example sorted dataset:

| Score |
|------|
| 52 |
| 55 |
| 58 |
| 60 |
| **95** |

The value **95** stands out as a potential outlier.

---

# Method 2: Detect Outliers Using Quartiles (IQR Method)

A more statistical approach uses the **Interquartile Range (IQR)**.

### Step 1: Calculate Quartiles

Use Excel's `QUARTILE` function.

```excel
=QUARTILE(A2:A20,1)
````

This calculates **Q1 (First Quartile)**.

```excel
=QUARTILE(A2:A20,3)
```

This calculates **Q3 (Third Quartile)**.

---

### Step 2: Calculate IQR

```excel
=Q3 - Q1
```

Example:

```
IQR = Q3 - Q1
```

---

### Step 3: Calculate Outlier Limits

Lower Limit:

```excel
=Q1 - 1.5 * IQR
```

Upper Limit:

```excel
=Q3 + 1.5 * IQR
```

Any values **outside this range** are considered outliers.

Statistically, values beyond **1.5 × IQR** above Q3 or below Q1 are typically classified as outliers. ([Excel Maven][1])

---

# Example Calculation

Dataset:

| Values |
| ------ |
| 10     |
| 12     |
| 14     |
| 15     |
| 18     |
| 19     |
| 200    |

Suppose:

```
Q1 = 12
Q3 = 18
IQR = 6
```

Lower Bound:

```
12 - (1.5 × 6) = 3
```

Upper Bound:

```
18 + (1.5 × 6) = 27
```

Since **200 > 27**, it is an **outlier**.

---

# Method 3: Highlight Outliers with Conditional Formatting

Excel can automatically highlight outliers.

### Steps

1. Select the dataset
2. Go to **Home → Conditional Formatting**
3. Choose **New Rule**
4. Use a formula

Example formula:

```excel
=OR(A2<$LowerLimit, A2>$UpperLimit)
```

Then apply a color such as **red** to highlight the outliers.

---

# Visualizing Outliers Using Charts

Outliers become easier to see in charts.

### Use:

* **Scatter plots**
* **Box plots**

Box plots are especially useful because they show:

* Median
* Quartiles
* Outliers visually

---

# Why Outlier Detection Matters

Outliers can distort:

* Mean
* Regression models
* Machine learning models
* Forecasting accuracy

Therefore, identifying them is a **critical step in data cleaning and preprocessing**.

---

# When to Remove Outliers

Do **not always remove outliers** automatically.

You should check whether they are:

* Data entry errors
* Sensor measurement errors
* Legitimate rare events

Sometimes outliers contain **valuable information**.

---

# Data Analysis using Python and Pandas

This notebook demonstrates how to perform **basic data analysis using Python and Pandas** on a dataset of card transactions.

Pandas is a powerful Python library used for **data manipulation and analysis**.

Resources to learn Pandas:

- https://pandas.pydata.org/
- https://pandas.pydata.org/docs/user_guide/10min.html
- https://youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS

---

# Dataset

We analyze a **card transactions dataset** stored in **Parquet format**.

Parquet is a column-based storage format that is:

- Faster than CSV
- Smaller in size
- Efficient for analytics

---

# Step 1: Download Dataset

```python
# Download dataset
!curl -C- -o transactions.parquet "https://drive.usercontent.google.com/download?id=1XGvuFjoTwlybkw0cc9u34horMF9vMhrB"
```

---

# Step 2: Import Required Library

```python
import pandas as pd
```

Pandas is used to load, clean, and analyze tabular data.

---

# Step 3: Load Dataset

```python
df = pd.read_parquet("transactions.parquet")
```

This reads the **parquet file into a Pandas DataFrame**.

---

# Step 4: View First Few Rows

```python
df.head()
```

`head()` displays the **first 5 rows of the dataset**.

---

# Step 5: Inspect Dataset Structure

```python
df.info()
```

This shows:

- number of rows
- column names
- data types
- memory usage
- missing values

---

# Step 6: Summary Statistics

```python
df.describe()
```

This generates statistical information such as:

- count
- mean
- standard deviation
- minimum value
- maximum value
- quartiles

For all **numerical columns**.

---

# Step 7: View Column Names

```python
df.columns
```

This lists all columns present in the dataset.

---

# Step 8: Check Unique Values

Example:

```python
df["merchant"].unique()
```

This shows **all unique merchants** present in the dataset.

---

# Step 9: Count Unique Values

```python
df["merchant"].nunique()
```

This returns the **number of unique merchants**.

---

# Step 10: Value Counts

```python
df["merchant"].value_counts()
```

Shows how many transactions occurred for each merchant.

---

# Step 11: Filter Data

Example: Transactions greater than 1000

```python
df[df["amount"] > 1000]
```

This filters rows where **transaction amount is greater than 1000**.

---

# Step 12: Select Specific Columns

```python
df[["merchant", "amount"]]
```

This selects only the specified columns.

---

# Step 13: Group By Operation

Group transactions by merchant:

```python
df.groupby("merchant")["amount"].sum()
```

This calculates **total spending per merchant**.

---

# Step 14: Average Transaction Per Merchant

```python
df.groupby("merchant")["amount"].mean()
```

This calculates **average transaction amount per merchant**.

---

# Step 15: Sorting Values

```python
df.sort_values("amount", ascending=False)
```

Sorts the dataset based on **transaction amount**.

---

# Step 16: Top Transactions

```python
df.sort_values("amount", ascending=False).head()
```

Displays the **largest transactions**.

---

# Step 17: Basic Data Filtering Example

Transactions from a specific merchant:

```python
df[df["merchant"] == "Amazon"]
```

---

# Step 18: Multiple Conditions

```python
df[(df["amount"] > 500) & (df["merchant"] == "Amazon")]
```

Filters rows where:

- amount > 500
- merchant is Amazon

---

# Step 19: Save Processed Data

```python
df.to_csv("transactions_cleaned.csv", index=False)
```

Exports the DataFrame into a **CSV file**.

---


# Data Analysis with Databases

Databases are where most **transactional data** resides.  
Instead of exporting everything into CSV files, analysts often **query the database directly**.

In this notebook we demonstrate how to:

- Connect to a database
- Run SQL queries from Python
- Analyze the results using **Pandas**

---

# Query the Database

There are many ways to connect to and query a database.

In Python, a common approach is using:

- **SQLAlchemy** → database connection
- **Pandas** → executing queries and analyzing results

---

# Step 1: Database Connection

```python
stats_connection = "mysql+pymysql://guest:relational@db.relational-data.org/stats"
```

This connection string contains:

- Database type → `mysql`
- Driver → `pymysql`
- Username → `guest`
- Password → `relational`
- Database host → `db.relational-data.org`
- Database name → `stats`

---

# Step 2: Create Engine and Connect

```python
import pandas as pd
import sqlalchemy as sa

engine = sa.create_engine(
    "mysql+pymysql://guest:relational@db.relational-data.org/stats"
)

pd.read_sql("SELECT COUNT(*) FROM posts", engine)
```

This verifies that we **successfully connected to the database** and counts the rows in the `posts` table.

---

# Step 3: Helper Function for Queries

Instead of writing `pd.read_sql()` every time, we create a helper function.

```python
def query(sql):
    return pd.read_sql(sql, engine)
```

Now we can easily run SQL queries.

---

# Example Query

```python
query(
"""
SELECT
OwnerUserId,
COUNT(*) as PostCount
FROM posts
GROUP BY OwnerUserId
ORDER BY PostCount DESC
"""
)
```

This query:

1. Groups posts by user
2. Counts how many posts each user made
3. Sorts users by post count

---

# Dataset Note

The user names are `None` because the dataset is **anonymized**.

---

# How Concentrated Are the Posts?

A common question in online communities:

> Do **20% of users create 80% of the content?**

This is related to the **Pareto Principle (80/20 rule)**.

---

# Step 4: Count Posts per User

```python
post_count = query(
"""
SELECT
OwnerUserId,
COUNT(*) as PostCount
FROM posts
GROUP BY OwnerUserId
ORDER BY PostCount DESC
"""
)
```

This produces a table showing:

| User | Number of Posts |
|-----|-----|

---

# Step 5: Compare Top 20% Users

```python
post_count.PostCount.iloc[:len(post_count)//5].sum() / post_count.PostCount.sum()
```

Explanation:

- `len(post_count)//5` → top 20%
- `.sum()` → total posts by those users
- divide by total posts

Result:

> Top **20% of users generate ~76% of posts**

This is close to the **Pareto distribution**.

---

# Does Age Predict Reputation?

The `users` table contains:

- `Age`
- `Reputation`

We want to check whether **age influences reputation**.

---

# Step 6: Fetch Aggregated Statistics

```python
import numpy as np

stats_query = """
SELECT
COUNT(*) as n,
SUM(Age) as sum_age,
SUM(Reputation) as sum_rep,
SUM(Age * Reputation) as sum_age_rep,
SUM(Age * Age) as sum_age_sq,
SUM(Reputation * Reputation) as sum_rep_sq
FROM users
WHERE Age IS NOT NULL
"""

stats = query(stats_query)
stats
```

This query retrieves aggregated statistics needed to compute **correlation**.

---

# Correlation Result

The calculated correlation is about:

```
~1.7%
```

Interpretation:

> Age and reputation have **almost no relationship**.

This means older users do **not necessarily have higher reputation**.

---

# How Many Views Increase Reputation by 1 Point?

Hypothesis:

> More **profile views** may increase **user reputation**.

---

# Step 7: Fetch Required Aggregates

```python
sql = """
SELECT
COUNT(*) as n,
SUM(Views) as sum_views,
SUM(Reputation) as sum_rep,
SUM(Views * Reputation) as sum_views_rep,
SUM(Views * Views) as sum_views_sq
FROM users
"""

query(sql)
```

This gathers statistics needed to estimate the **relationship between views and reputation**.

---

# Inspect the Data Directly

To better understand the relationship:

```python
reputation = query("SELECT Views, Reputation FROM users")
reputation
```

---

# Calculate Mean Values

```python
reputation.mean()
```

This computes the **average views and reputation** across users.

---

# Interpretation

The analysis suggests that:

- Users with **more profile views tend to have higher reputation**
- However, the relationship is **not perfectly linear**

Reputation depends on many other factors like:

- Answers posted
- Question quality
- Community voting

---

# Lessons

This notebook demonstrates how to combine:

- **SQL** for querying data
- **Pandas** for analysis
- **SQLAlchemy** for database connections

Together they form a powerful workflow for **data analysis directly from databases**.

Useful libraries:

- https://pandas.pydata.org/
- https://docs.sqlalchemy.org/

---

# What Else Should You Know for Exams?

You should also know about **SQLite**.

SQLite is:

- A lightweight database
- Serverless
- Stored in a single file

Website:

https://sqlite.org/

It is widely used in:

- Mobile apps
- Embedded systems
- Small applications


# Geospatial Analysis with Python: Comprehensive Guide

## 1. Environment Setup
To begin, you need to install and import the core libraries.
* **Pandas**: Data manipulation.
* **Geopy**: Geocoding and distance calculations.
* **Folium**: Interactive map generation.
* **Geopandas**: Handling geospatial vector data (Shapefiles).

```python
import pandas as pd
import numpy as np
import folium
import geopy.distance
from geopy.geocoders import Nominatim
import geopandas

```

## 2. Distance Calculations

The `geopy` library allows you to calculate the geodesic distance between two points on the Earth's surface.

### A. Geocoding Locations

Convert address strings into latitude and longitude coordinates:

```python
geolocator = Nominatim(user_agent="geo_analysis")
loc1 = geolocator.geocode("Moradabad")
loc2 = geolocator.geocode("Dehradun")

coords_1 = (loc1.latitude, loc1.longitude)
coords_2 = (loc2.latitude, loc2.longitude)

```

### B. Calculating Distance

```python
# Calculate distance in Kilometers
dist = geopy.distance.distance(coords_1, coords_2).km
print(f"Distance between locations: {dist} km")

```

## 3. Working with Datasets

When dealing with multiple locations (e.g., store locations), we use Pandas to calculate distances relative to a central point.

```python
# Define a central reference point (e.g., Empire State Building)
center_point = (40.748488, -73.985238)

# Calculate distance for every row in a dataframe
def calculate_dist(row):
    store_coords = (row['lat'], row['lng'])
    return geopy.distance.distance(center_point, store_coords).km

df['distance_to_center'] = df.apply(calculate_dist, axis=1)

```

## 4. Interactive Data Visualization

Folium is used to create web-based maps. You can add markers and heatmaps to visualize the density of your data.

### A. Initializing the Map

```python
# Create a base map centered on a specific coordinate
m = folium.Map(location=[40.748488, -73.985238], zoom_start=12)

```

### B. Adding Markers and Popups

```python
for i, row in df.iterrows():
    folium.Marker(
        location=[row['lat'], row['lng']],
        popup=f"Store: {row['store_name']}",
        tooltip="Click for info"
    ).add_to(m)

# To view the map in a notebook
m

```

## 5. Advanced Analysis with GeoPandas

For spatial joining and working with boundaries (like borough or city shapes), use GeoPandas.

```python
# Convert a standard DataFrame to a GeoDataFrame
geom = geopandas.points_from_xy(df.lng, df.lat)
gdf = geopandas.GeoDataFrame(df, geometry=geom)

# Exporting to a Shapefile for use in GIS software
gdf.to_file('output_map/points.shp')

```

## Summary of Workflow

1. **Extract**: Load location data from Excel or CSV.
2. **Transform**: Use `geopy` to find coordinates and calculate distances.
3. **Analyze**: Filter data based on proximity or spatial boundaries.
4. **Visualize**: Plot results on an interactive `folium` map or export via `geopandas`.

---

# Geospatial Analysis: Creating Shapefiles with QGIS

## 1. Introduction to QGIS

QGIS is essential for storing geographic information (latitude, longitude, and demographics) for countries, states, and cities. While many shapefiles are available for free online, QGIS allows you to create custom ones when specific data is missing.

### Installation

* **Website**: [qgis.org](https://qgis.org)
* **Versions**: Available for Windows (32-bit and 64-bit), macOS, and Linux.
* **Recommended**: The standalone installer (e.g., version 3.16) is often sufficient for most geospatial tasks.

---

## 2. Navigating the Interface

* **Toolbars**: Located at the top. The **Digitizing Toolbar** is critical for creating new features.
* **Browser Panel**: Used to navigate your computer's files.
* **Layers Panel**: Displays all active maps and data layers in your project.
* **Panels Management**: Access missing panels via `View > Panels`.

---

## 3. Working with Existing Shapefiles

Free spatial data can be sourced from sites like **Diva-GIS**.

### Importing Data

1. Download and extract the zip file containing the shapefiles.
2. Drag and drop the `.shp` files into the QGIS Layers panel.
3. **Administrative Levels**: Shapefiles often come in layers (e.g., admin 0 for country, admin 1 for states, etc.).

### Analyzing Attributes

* **Attribute Table**: Right-click a layer and select `Open Attribute Table` to see data like names, IDs, and demographics.
* **Selection**: Selecting a row in the table highlights the corresponding area on the map.

### Customizing Appearance (Symbology & Labels)

* **Color**: Right-click layer > `Properties > Symbology` to change map colors.
* **Labels**: Right-click layer > `Properties > Labels > Single Labels`. Select a field (e.g., "Name 3") to display administrative names directly on the map.

---

## 4. Using Web Map Plugins

To see how your shapefile fits in the real world, use the **QuickMapServices** plugin.

1. Go to `Plugins > Manage and Install Plugins`.
2. Search for "Quick Map Services" and install.
3. Go to `Web > Quick Map Services > OSM > OSM Standard` to overlay your data on an OpenStreetMap base map.

---

## 5. Creating a Custom Shapefile (South Sudan Example)

When a country or region is missing from standard datasets, you can manually digitize it.

### Step-by-Step Creation

1. **New Layer**: Go to `Layer > Create Layer > New Shapefile Layer`.
2. **Configuration**:
* **Geometry Type**: Select **Polygon**.
* **Attributes**: Add fields like "Name" (Text type).


3. **Digitizing**:
* Select the layer and click **Toggle Editing** (pencil icon).
* Select **Add Polygon Feature**.
* Left-click along the boundaries of the region on the base map.
* Right-click to finish the polygon and enter attribute data (e.g., ID: 1, Name: South Sudan).



---

## 6. Exporting Your Work

Once created, you can export your data for use in other applications.

* **Shapefile (.shp)**: Standard format for GIS software.
* **KML File**: Ideal for viewing in **Google Earth**.
* **Process**: Right-click layer > `Export > Save Features As`. Choose your format and save location.

---

## 7. Verification in Google Earth

Double-clicking a saved KML file will open it in Google Earth, where the custom polygon you drew in QGIS will be overlaid precisely on the 3D globe, complete with the attributes you assigned.
