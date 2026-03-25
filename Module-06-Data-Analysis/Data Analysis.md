# Data Cleaning in Excel 
Excel is a handy tool for cleaning smaller datasets, especially when you want quick results without coding.

---

## 1. Find & Replace

This feature helps you quickly edit or remove unwanted values.

- Use `Ctrl + H` to open the dialog box  
- Enter the text you want to find  
- Leave the replace field empty if you want to remove it  
- Click **Replace All** to apply changes across the sheet  

---

## 2. Formatting Data Types

Ensuring correct data types avoids calculation errors.

- Select the required column  
- Go to the format dropdown in the toolbar  
- Change from **General** to **Number** or any suitable format  

This standardizes values and improves consistency.

---

## 3. Removing Extra Spaces (TRIM)

Extra spaces can cause mismatches in data.

- Create a new column  
- Use formula: `=TRIM(A2)` (adjust cell reference)  
- Drag the formula down  

It removes leading, trailing, and extra internal spaces.

---

## 4. Deleting Blank Rows

To clean incomplete data:

- Select a column  
- Go to **Find & Select → Go To Special → Blanks**  
- Right-click highlighted cells  
- Choose **Delete → Entire Row**  

---

## 5. Eliminating Duplicates

To keep only unique records:

- Select your data column  
- Go to **Data → Remove Duplicates**  

Excel will filter out repeated entries automatically.

---

# Data Transformation in Excel

Data transformation helps create meaningful insights from raw values.

---

## 1. Creating Calculated Fields

You can generate new metrics using formulas.

- Example: `=B2/C2`  
- Apply to entire column using autofill  

Useful for ratios like density, percentages, etc.

---

## 2. Using Pivot Tables

Pivot Tables summarize large datasets easily.

- Select dataset → **Insert → Pivot Table**  
- Choose new worksheet  
- Drag fields into **Rows, Columns, and Values**  

---

## 3. Counting Occurrences

To check frequency:

- Drag a field (e.g., Country) into **Rows**  
- Drag same field into **Values**  

It shows how many times each value appears.

---

## 4. Aggregating Data

To summarize numbers:

- Add categories (Country, City) in **Rows**  
- Add numeric field (Population) in **Values**  
- Change aggregation (**Sum, Average, Count**)  

---

## 5. Detecting Outliers with Charts

Visual tools make patterns clearer.

- Insert a chart from Pivot Table  
- Filter specific categories  
- Look for unusually high/low values  

---

# Text to Columns (Excel)

This tool splits messy text into structured columns.

---

## Steps:

- Select the column  
- Go to **Data → Text to Columns**  
- Choose **Delimited**  

### Using Custom Delimiters

- Select **Other**  
- Enter symbols like `(` or `-`  
- Split data step-by-step  

### Using Standard Delimiters

- Choose options like **Comma** or **Tab**  
- Click **Finish** to separate values  

---

## Final Cleanup

- Remove unwanted columns  
- Add proper headers  
- Format neatly  

---

# Data Aggregation in Excel

Aggregation helps identify trends and patterns.

---

## 1. Prepare Data

- Remove blank rows/columns  
- Ensure clean dataset before analysis  

---

## 2. Extract Time Data

Create new columns:

- Week → `=WEEKNUM(A2)`  
- Month → `=TEXT(A2,"mmm")`  
- Year → `=TEXT(A2,"yyyy")`  

---

## 3. Conditional Formatting

Use color scales:

- Highlight values  
- Apply **Color Scale**  

Helps identify high/low trends visually.

---

## 4. Pivot-Based Aggregation

- Rows → Category (e.g., Location)  
- Columns → Time (Week/Month)  
- Values → Numeric data  

---

## 5. Sparklines

Mini charts inside cells:

- Go to **Insert → Sparklines**  
- Select data range  

Shows trend quickly.

---

## 6. Data Bars

- Apply via **Conditional Formatting**  

Helps compare values visually within cells.

---
# Data Preparation Using Unix Shell Commands

## Introduction

we explore how to perform **data preparation using Unix shell commands**.

Unix tools are powerful because they are: - **Fast** -- written in C -
**Agile** -- instant feedback while running commands -
**Parallelizable** - **Available everywhere** -- Linux, Mac, and
environments like Google Colab

Example command:

``` bash
!ls
```

Lists files in the current directory.

# Downloading Data Using curl

Example:

``` bash
curl --location --continue-at - --output s.net-April-2024.gz <URL>
```

### Important Options

  Option            Description
  ----------------- ------------------------------
  --location        Follow redirects
  --continue-at -   Resume interrupted downloads
  --output          Save the downloaded file

Check files:

``` bash
ls
```

Detailed view:

``` bash
ls -l
```

------------------------------------------------------------------------

# Decompressing Files

``` bash
gzip --decompress s.net-April-2024.gz
```

Compressed file (5.8 MB) may become much larger after decompression.

------------------------------------------------------------------------

# Viewing File Content

## First Lines

``` bash
head -n 5 s.net-April-2024
```

## Last Lines

``` bash
tail -n 5 s.net-April-2024
```

Typical log fields include: - IP address - Date/time - Request type -
HTTP response code - Response size - Referrer - User agent

------------------------------------------------------------------------

# Counting Requests

``` bash
wc -l s.net-April-2024
```

Counts number of requests (lines).

------------------------------------------------------------------------

# Extracting IP Addresses

``` bash
!cut --delimeter " " --fields 1 s.net-April-2024 | head -n 5
```

Options:

  Option   Meaning
  -------- --------------
  --delimiter       delimiter
  --fields      field number

Preview:

``` bash
!cut --delimeter " " --fields 1 s.net-April-2024 | head -n 5
```

------------------------------------------------------------------------

# Using Pipes


The `|` passes output from one command to the next.

------------------------------------------------------------------------

# Sorting Data

``` bash
!cut --delimeter " " --fields 1 s.net-April-2024 | sort | -n 5
```

------------------------------------------------------------------------

# Counting Unique Requests

``` bash
!cut --delimeter " " --fields 1 s.net-April-2024 | sort | uniq --count | head -n 30
```
u can see the 30 IPs with number of duplications

------------------------------------------------------------------------

# Finding Most Active IPs

``` bash
!cut --delimeter " " --fields 1 s.net-April-2024 | sort | uniq --count | sort --key -1n | tail
```

Options:

  Option   Meaning
  -------- ------------------
  -key      sort by column 1
  -1n      sort alphabetically 

------------------------------------------------------------------------

# Investigating Bots

Example:

``` bash
grep "^IP_ADDRESS" s.net-April-2024 | head
```

Bots may identify themselves in the user agent string.

Example:

    Mozilla/5.0 compatible DataForSEO bot

------------------------------------------------------------------------

# Searching With grep

``` bash
grep "bot" s.net-April-2024
```

Better regex search:

``` bash
grep -o "\S*bot\S*" s.net-April-2024
```

------------------------------------------------------------------------

# Finding Most Active Bots

``` bash
grep -o "\S*bot\S*" s.net-April-2024 | sort | uniq -c | sort -k1 -n | tail
```

Example bots discovered: - GoogleBot - AppleBot - BingBot - DataForSEO
Bot - PetalBot

------------------------------------------------------------------------

# Converting Log to CSV

Example log date:

    [10/Apr/2024:10:22:15 +0000]

Convert brackets to quotes:

``` bash
sed 's/\[\([^]]*\)\]/"\1"/g' s.net-April-2024 > log.csv
```

------------------------------------------------------------------------

# Preview Converted File

``` bash
head log.csv
```

------------------------------------------------------------------------

# Create Smaller Sample

``` bash
head -n 1000 log.csv > small.csv
```

------------------------------------------------------------------------

# Opening in Excel

Steps:

1.  Download file
2.  Rename `.csv` → `.txt`
3.  Open in Excel
4.  Select **Delimited**
5.  Choose **Space delimiter**

------------------------------------------------------------------------

# Handling Data Issues

Sometimes URLs contain quotes like:

    "devotional songs"

This can break CSV structure.

Solutions: - Clean rows manually - Preprocess quotes

------------------------------------------------------------------------

# Useful Commands

  Command   Purpose
  --------- ------------------
  ls        list files
  curl      download data
  gzip      decompress
  head      view first lines
  tail      view last lines
  wc        count lines
  cut       extract columns
  sort      sort values
  uniq      count duplicates
  grep      search text
  sed       modify text


# Data Preparation in DuckDB

DuckDB's SQL engine is highly efficient for data preparation and can handle large files quickly. Below is a comprehensive guide to data preparation techniques using the DuckDB CLI, mimicking real-world business data patterns. 

## 1. Creating Sample Data
Before working with messy production data, it is best to set up a controlled environment. You can generate a sample dataset to simulate common e-commerce scenarios like missing customer info, seasonal patterns, and geographic segmentation. 

```sql
duckdb sample.duckdb <<'SQL'
CREATE OR REPLACE TABLE orders AS
SELECT
  seq AS order_id,
  CASE WHEN seq % 5 = 0 THEN NULL ELSE 'Customer ' || seq END AS customer,
  date '2025-01-01' + CAST(seq % 15 AS INTEGER) AS order_date,
  CASE WHEN seq % 3 = 0 THEN 'Widget ' || seq ELSE 'Gadget ' || seq END AS product,
  round(random()*1000, 2) AS amount,
  CASE WHEN seq % 4 = 0 THEN 'EU' ELSE 'US' END AS region
FROM range(1, 50) tbl(seq);
SQL
```

To practice handling corrupted CSV files (like unescaped quotes or missing delimiters), you can simulate a messy file.

```bash
cat <<'EOF' > messy_orders.csv
order_id,customer,order_date,product,amount,region
1,Customer 1,2025-01-01,Widget 1,100,US
2,Customer 2,2025-01-02,Gadget 2,200,US
3,Customer 3,2025-01-03,Gadget 3,300,EU
EOF
```

You can also create a large dataset to practice memory-efficient chunk processing for files too large to fit in RAM.

```sql
duckdb sample.duckdb <<'SQL'
COPY (SELECT seq AS id, random() AS val FROM range(100000)) TO 'big.csv';
SQL
```

## 2. Exploratory Data Analysis (EDA)
Quick exploratory analysis helps you understand the data structure and quality, preventing costly mistakes caused by missing values or incorrect data types.

```sql
-- Preview and get stats
SELECT * FROM orders LIMIT 5;
DESCRIBE orders;
SELECT COUNT(*) AS n, AVG(amount) AS avg_amount FROM orders;
```

## 3. Data Ingestion and Format Conversion
Converting data formats ensures your cleaned data can reach every stakeholder in their preferred format, whether it's Parquet for analytics, JSON for APIs, or CSV for Excel.

```sql
COPY (SELECT * FROM orders) TO 'orders.json' (FORMAT JSON);
COPY (SELECT * FROM orders) TO 'orders.parquet' (FORMAT PARQUET);
```

When dealing with real-world, malformed CSV files, you can instruct DuckDB to ignore errors so your pipeline doesn't break.

```sql
-- Skip bad lines while loading
SELECT * FROM read_csv_auto('messy_orders.csv', ignore_errors = true);
```

You can also seamlessly combine data from various formats (CSV, JSON, Parquet) without maintaining separate processing pipelines.

```sql
CREATE TABLE json_orders AS SELECT * FROM read_json_auto('orders.json');
CREATE TABLE parquet_orders AS SELECT * FROM read_parquet('orders.parquet');

SELECT * FROM orders
UNION ALL
SELECT * FROM parquet_orders;
```

## 4. Data Cleaning
### Handling Missing Values
Rather than excluding incomplete records entirely, strategic imputation preserves data for analysis.

```sql
-- Replace null customer names
SELECT COALESCE(customer, 'Unknown') AS customer FROM orders;
```

### String and Regex Operations
Standardizing text ensures accurate grouping and search functionality. You can use simple string operations or regular expressions for more complex patterns like fixing inconsistent spacing.

```sql
-- Basic string trimming and lowering
SELECT DISTINCT TRIM(LOWER(product)) AS clean_product FROM orders;

-- Regex search and replace for multiple spaces
SELECT REGEXP_REPLACE(product, '\\s+', ' ', 'g') AS tidy_product FROM orders;
```

### Date Parsing
Converting raw dates into standard formats is critical for time-based business analysis, forecasting, and filtering.

```sql
SELECT order_id, STRFTIME(order_date, '%Y-%m') AS order_month FROM orders;
```

## 5. Data Transformation and Subsetting
### Conditional Logic (Binning)
Categorizing continuous data (like exact dollar amounts) into distinct segments helps drive targeted decision-making and performance analysis.

```sql
SELECT 
  order_id,
  CASE
    WHEN amount > 700 THEN 'high'
    WHEN amount > 300 THEN 'medium'
    ELSE 'low'
  END AS price_band
FROM orders;
```

### Derived Columns
You can easily create new business metrics (like tax calculations or formatting codes) directly from existing data.

```sql
SELECT *, amount * 0.1 AS tax, UPPER(region) AS region_code FROM orders;
```

### Filtering and Dropping Columns
Efficient filtering limits analysis to relevant subsets and allows you to exclude sensitive information (like PII).

```sql
SELECT order_id, amount FROM orders WHERE region = 'US';
SELECT * EXCLUDE region FROM orders;
```

## 6. Advanced Processing
### Processing in Chunks
For massive datasets that exceed memory limits, you can process data in manageable chunks.

```sql
SELECT * FROM read_csv_auto('big.csv') LIMIT 1000 OFFSET 0;
SELECT * FROM read_csv_auto('big.csv') LIMIT 1000 OFFSET 1000;
```

### Summaries and Pivots
Aggregating and pivoting detailed transaction data into high-level insights is foundational for strategic planning and executive dashboards.

```sql
-- Aggregation
SELECT region, COUNT(*) AS n_orders, SUM(amount) AS total 
FROM orders 
GROUP BY region;

-- Pivot by region
SELECT * FROM orders 
PIVOT(COUNT(*) FOR region IN ('US', 'EU'));
```

---
---

# Setting Up Your First dbt Project

**dbt (data build tool)** is an open-source project that handles the transformation piece of the ELT (Extract, Load, Transform) process by blending software engineering automation with SQL. 

Below are the steps to install dbt, initialize a project, configure your Snowflake connection, and push your work to GitHub.

## 1. Installation
Before installing, ensure you have **Python** and **Git** installed on your machine. You can install dbt globally using the command line via Python's package manager, pip. Once the installation finishes downloading its dependencies, verify it by checking the version.

```bash
pip install dbt
dbt --version
```

## 2. Project Initialization
There are two ways to start: you can either create a GitHub repository first and clone it, or create your files and push them to a repository later. Assuming you cloned an empty repository, navigate into it and initialize your skeleton dbt project. 

```bash
git clone <your_repository_url>
cd <your_repository_folder>
dbt init demo_dbt
```
This command generates a skeleton project containing core folders like `models`, `macros`, `snapshots`, and `tests`. 

## 3. Profile Configuration (Snowflake)
Initializing the project also creates a `.dbt` folder in your machine's user directory containing a `profiles.yml` file. This file splits up credentials based on environments (like `dev` and `prod`). 

## 4. Testing and Running Models
Before running your models, you should verify that your profiles and project files are correctly linked to your database. Once the debug command returns `connection is okay`, you can run your initial skeleton models.

```bash
# Test the connection to Snowflake
dbt debug

# Run your dbt models
dbt run
```

## 5. Version Control with Git
After your project is initialized and running successfully, it is time to push the project to your Git repository. If you have extra folder layers you don't want, simply move your files to the root directory before running the standard Git commands.

```bash
git add .
git commit -m "my first commit"
git push
```
Once pushed, your team can begin creating branches to collaborate on building out your data warehouse.
