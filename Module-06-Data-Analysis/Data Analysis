# Module 5 – Session 1  
## Model the Data: Correlation & Regression in Excel

---

## 1. Enable Data Analysis ToolPak
1. Go to **File → Options**  
2. Click **Add-ins**  
3. At the bottom select **Manage: Excel Add-ins → Go**  
4. Check **Analysis ToolPak** → Click **OK**

Now you can access **Data → Data Analysis** in the ribbon.

---

# Correlation Analysis

## Step 1: Prepare Data
Keep only these columns:
- New Cases
- New Deaths
- New Vaccinations

Remove unnecessary columns.

## Step 2: Generate Correlation Matrix
1. Go to **Data → Data Analysis**
2. Select **Correlation → OK**
3. **Input Range:** Select the three columns  
4. Check **Labels in first row**
5. Choose **Output Range** in the same sheet
6. Click **OK**

## Interpretation
Correlation values range from **-1 to +1**.

- **New Cases vs New Deaths = 0.84**  
  → Very **strong positive correlation**

- **New Vaccinations vs New Deaths = 0.23**  
  → **Weak positive correlation**

---

# Scatterplot Visualization

## Plot 1: New Cases vs New Deaths
1. Select **New Cases (X-axis)** and **New Deaths (Y-axis)**
2. Go to **Insert → Charts → Scatter Plot**
3. Add **Trendline**

**Insight:**  
Trendline is steep → confirms **strong positive correlation (0.84)**.

---

## Plot 2: New Vaccinations vs New Deaths
1. Select **New Vaccinations (X-axis)** and **New Deaths (Y-axis)**
2. Insert **Scatter Plot**
3. Add **Trendline**

**Insight:**  
Trendline slope is small → **weak correlation (0.23)**.  
As vaccinations increased, deaths slightly decreased.

---

# Regression Analysis

## Variables
**Dependent Variable (Y):**
- New Deaths

**Independent Variables (X):**
- New Cases
- New Tests
- New Vaccinations
- Stringency Index

---

## Step 1: Data Preparation
Create new columns:
- New Cases per 1000
- New Tests per 1000
- New Vaccinations per 1000

Formula:
Value ÷ 1000


---

## Step 2: Run Regression
1. Go to **Data → Data Analysis**
2. Select **Regression**
3. **Input Y Range:** New Deaths
4. **Input X Range:**  
   - New Cases per 1000  
   - New Tests per 1000  
   - New Vaccinations per 1000  
   - Stringency Index
5. Check **Labels**
6. Select **New Worksheet Ply**
7. Click **OK**

---

# Interpreting Results

## 1. Adjusted R²
**Value: 0.816**

Meaning:
- **81.6% of variation in deaths** is explained by the model.

---

## 2. Significance F
- Value **< 0.05**

Meaning:
- The **overall regression model is statistically significant**.

---

## 3. P-values (Variable Importance)

| Variable | Result |
|--------|--------|
| New Cases | Significant |
| New Tests | Significant |
| New Vaccinations | Significant |
| Stringency Index | Not significant (P = 0.11) |

Only variables with **P < 0.05** should be trusted.

---

## 4. Coefficients (Impact on Deaths)

| Variable | Coefficient | Meaning |
|--------|--------|--------|
| New Cases /1000 | ~7 | 1000 cases → 7 more deaths |
| New Tests /1000 | 0.69 | 1000 tests → 0.69 more deaths |
| New Vaccinations /1000 | -0.07 | 1000 vaccinations → deaths decrease slightly |
| Stringency Index | 2.71 | Appears to increase deaths, but **not statistically valid** |

---

## Session 2
Forecast Functions in Excel (Linear Regression & Time Series)
Introduction
In this tutorial, we explore the FORECAST function in Microsoft Excel.

The FORECAST function performs linear regression behind the scenes and uses it to predict future values.

A synonym for this function is: FORECAST.LINEAR

Both functions work exactly the same.

Dataset Used
We will use a Height and Weight dataset from Kaggle.

The dataset contains information about 25,000 people, including:

Height (in inches)
Weight (in pounds)
For demonstration purposes, we will only use 1,000 rows.

Example data:

Height (inches)	Weight (pounds)
65	120
68	140
70	155
Converting Units to Metric
Since the dataset uses inches and pounds, we convert them to metric units.

Convert Height (Inches → Centimeters)
Formula:


Height_cm = Height_inches * 2.54

Example Excel formula:

=A2 * 2.54
Convert Weight (Pounds → Kilograms)
Formula:

Weight_kg = Weight_pounds / 2.20462
Example Excel formula:

=B2 / 2.20462
After conversion, drag the formulas down to apply them to the entire dataset.

Visualizing the Data
To understand the relationship between height and weight, we create a scatter plot.

Steps:

Select the Height (cm) column.
Select the Weight (kg) column.
Insert → Chart → Scatter Plot
Observation:

Height ranges roughly 160 cm to 185 cm
Weight ranges roughly 50 kg to 65 kg
There is a positive linear relationship between height and weight.
Using the FORECAST Function
The syntax of the function is:

=FORECAST(x, known_y's, known_x's)
Where:

x → Value we want to predict for
known_y's → Dependent variable (target)
known_x's → Independent variable
Example: Predict Weight from Height
Suppose we want to predict the weight of a person who is 170 cm tall.

=FORECAST(170, WeightRange, HeightRange)
Example result:

170 cm → predicted weight ≈ 56 kg
Reverse Prediction (Height from Weight)
We can also reverse the variables.

Example:

Predict height for a person weighing 75 kg.

=FORECAST(75, HeightRange, WeightRange)
Example result:

75 kg → predicted height ≈ 180 cm (≈ 6 feet)
Forecasting Multiple Values
Suppose we want predictions for several heights:

Height
150
155
160
165
170
One way is to copy the formula:

=FORECAST(A2, WeightRange, HeightRange)
Then drag the formula down.

However, this approach is inefficient because each formula calculates regression independently.

Using the TREND Function
A better approach is using the TREND function.

Syntax:

=TREND(known_y's, known_x's, new_x's)
Example:

=TREND(WeightRange, HeightRange, NewHeightRange)
Benefits:

Computes regression once
Applies predictions to the entire array
Automatically fills the column
TREND returns the same values as FORECAST.

Compatibility with Google Sheets
These functions are also available in Google Sheets:

FORECAST
FORECAST.LINEAR
TREND
You can:

Save the Excel file
Open in Google Sheets
Edit
Save and reopen in Excel
Everything works perfectly.

Limitation of Linear Regression
Linear regression works well for simple linear relationships.

However, it performs poorly for cyclical or seasonal data.

Example:

Traffic data across time.

Dataset:

DateTime	Number of Vehicles
01-01 08:00	25
01-01 09:00	40
01-01 10:00	32
When plotted, traffic data shows:

Daily peaks
Weekly patterns
Weekend drops
Holiday effects
This pattern is seasonal, not linear.

Linear Prediction on Traffic Data
Using TREND:

=TREND(VehicleValues, DateTimeValues, FutureDateTimes)
Result:

Predicts around 20 vehicles
Slight upward slope
Fails to capture peaks and valleys
This shows linear regression is not suitable for seasonal data.

Using FORECAST.ETS (Time Series Forecasting)
For cyclical data, Excel provides:

FORECAST.ETS
This uses Exponential Triple Smoothing (ETS).

Syntax:

=FORECAST.ETS(target_date, values, timeline, [seasonality], [data_completion], [aggregation])
Example Usage
=FORECAST.ETS(A2, $B$2:$B$1000, $A$2:$A$1000)
Where:

A2 → Target date
B2:B1000 → Vehicle counts
A2:A1000 → Timeline
Optional Parameters
Seasonality
Defines the repeating cycle.

Example:

24 → season repeats every 24 data points
Example for hourly traffic data:

24 = daily pattern
If omitted, Excel automatically detects seasonality.

Data Completion
Handles missing values.

Options:

1 → Interpolation (default)
0 → Missing values treated as zero
Comparing Predictions
When plotted together:

Line	Meaning
Blue	Actual data
Orange	Linear forecast
Green	ETS forecast
Observations:

Linear prediction → almost flat line
ETS prediction → follows seasonal patterns better
Key Takeaways
FORECAST / FORECAST.LINEAR
Uses linear regression
Works well for linear relationships
Poor for seasonal data
TREND
Same as FORECAST
More efficient for multiple predictions
FORECAST.ETS
Designed for time series forecasting
Captures seasonality
Better for cyclical data
Outlier Detection in Excel
Introduction
In data analysis, it is important to identify outliers — values that are significantly higher or lower than the rest of the dataset.

Outliers may occur because of:

Data entry mistakes
Measurement errors
Rare but valid observations
These values can distort statistical analysis such as mean, regression, or forecasting, so detecting them early is important. :contentReference[oaicite:1]{index=1}

What is an Outlier?
An outlier is a data point that lies far away from the majority of data values.

Example dataset:

Values
10
12
13
14
15
200
Here 200 is clearly far away from the rest of the values and is considered an outlier.

Outliers can significantly impact the average and statistical interpretation of data. :contentReference[oaicite:2]{index=2}

Dataset Example in Excel
Suppose we have a dataset like this:

Student	Score
A	52
B	55
C	60
D	58
E	95
In this dataset, 95 may be an outlier depending on the statistical distribution.

Method 1: Detect Outliers Using Sorting
The simplest method:

Steps
Select the dataset
Go to Data → Sort
Sort values Ascending or Descending
Look for unusually large or small numbers
Example sorted dataset:

Score
52
55
58
60
95
The value 95 stands out as a potential outlier.

Method 2: Detect Outliers Using Quartiles (IQR Method)
A more statistical approach uses the Interquartile Range (IQR).

Step 1: Calculate Quartiles
Use Excel's QUARTILE function.

=QUARTILE(A2:A20,1)
This calculates Q1 (First Quartile).

=QUARTILE(A2:A20,3)
This calculates Q3 (Third Quartile).

Step 2: Calculate IQR
=Q3 - Q1
Example:

IQR = Q3 - Q1
Step 3: Calculate Outlier Limits
Lower Limit:

=Q1 - 1.5 * IQR
Upper Limit:

=Q3 + 1.5 * IQR
Any values outside this range are considered outliers.

Statistically, values beyond 1.5 × IQR above Q3 or below Q1 are typically classified as outliers. ([Excel Maven][1])

Example Calculation
Dataset:

Values
10
12
14
15
18
19
200
Suppose:

Q1 = 12
Q3 = 18
IQR = 6
Lower Bound:

12 - (1.5 × 6) = 3
Upper Bound:

18 + (1.5 × 6) = 27
Since 200 > 27, it is an outlier.

Method 3: Highlight Outliers with Conditional Formatting
Excel can automatically highlight outliers.

Steps
Select the dataset
Go to Home → Conditional Formatting
Choose New Rule
Use a formula
Example formula:

=OR(A2<$LowerLimit, A2>$UpperLimit)
Then apply a color such as red to highlight the outliers.

Visualizing Outliers Using Charts
Outliers become easier to see in charts.

Use:
Scatter plots
Box plots
Box plots are especially useful because they show:

Median
Quartiles
Outliers visually
Why Outlier Detection Matters
Outliers can distort:

Mean
Regression models
Machine learning models
Forecasting accuracy
Therefore, identifying them is a critical step in data cleaning and preprocessing.

When to Remove Outliers
Do not always remove outliers automatically.

You should check whether they are:

Data entry errors
Sensor measurement errors
Legitimate rare events
Sometimes outliers contain valuable information.

---

