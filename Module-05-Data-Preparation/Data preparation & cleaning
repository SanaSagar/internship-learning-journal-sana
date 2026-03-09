# Data Preparation & Cleaning 

---

# Data Cleaning in Excel

## Find & Replace
- Shortcut: `Ctrl + H`
- Enter text in **Find what**
- Leave **Replace with** blank to delete text
- Click **Replace All**

## Change Data Format
- Select column → Data Type dropdown
- Change **General → Number**
- Standardizes numeric values

## Remove Extra Spaces — TRIM
- Add new column
- Formula: `=TRIM(A2)`
- Drag to apply to full column
- Removes leading/trailing spaces and extra gaps

## Delete Blank Rows
- Select column
- Home → Find & Select → Go To Special → Blanks
- Right-click blank cell → Delete → Entire row

## Remove Duplicates
- Select column
- Data → Remove Duplicates
- Keeps only unique values

---

# Data Transformation in Excel

## Create Ratios
- Use division formula: `=G2/D2`
- Double-click fill handle to autofill
- Useful for density, percentages, comparisons

## Insert Pivot Table
- Select dataset → Insert → Pivot Table → New Worksheet

## Count Duplicates
- Drag field to **Rows**
- Drag same field to **Values**
- Shows frequency of each item

## Aggregate Data
- Rows → Categories
- Values → Numeric field
- Change Values to Sum / Average / Count

## Pivot Charts
- Insert chart from Pivot Table
- Use filters to focus on subsets
- Helps detect patterns & outliers

---

# Text to Columns in Excel

## Access Tool
- Select column → Data → Text to Columns

## Use Delimited Option
- Choose **Delimited** → Next
- Splits text using characters

## Custom Delimiter
- Choose **Other**
- Enter symbol like `(` or `-`
- Click Finish
- Repeat process for further splits

## Standard Delimiters
- Use built-in options like **Comma**, **Tab**

## Cleanup
- Delete extra columns
- Add headers
- Format neatly

---

# Data Aggregation in Excel

## Data Cleanup
- Delete empty columns
- Remove blank rows using Go To Special → Blanks

## Extract Date Features
- Convert to Table: Insert → Table
- Week: `=WEEKNUM(A2,1)`
- Month: `=TEXT(A2,"mmm")`
- Year: `=TEXT(A2,"yyyy")`

## Color Scales
- Select numeric column
- Conditional Formatting → Color Scales
- Highlights high/low clusters

## Pivot Aggregation
- Rows → Category
- Columns → Time (Week/Year)
- Values → Sum/Avg/Count

## Sparklines
- Insert → Sparklines → Line
- Shows trends inside cells

## Data Bars
- Conditional Formatting → Data Bars
- In-cell bar visualization

---

# Data Preparation Using Unix Shell

## Why Unix Tools
- Fast, lightweight, parallel processing
- Available on Linux, Mac, Google Colab

## Basic Commands
```bash
ls        # list files
ls -l     # detailed list

## Download Data
curl --location --continue-at - --output file.gz URL

## Decompress Files
gzip -d file.gz

## View File Content
head -n 5 file     # first lines
tail -n 5 file     # last lines

## Count Lines
wc -l file

## Extract Columns
cut -d " " -f 1 file

Pipes

| passes output to next command

## Sort & Count Unique
sort file
uniq -c

## Search Text
grep "text" file
grep -o "\S*bot\S*" file

## Replace Text
sed 's/old/new/g' file

## Convert Log to CSV
sed 's/\[\([^]]*\)\]/"\1"/g' log > log.csv

## Data Preparation in DuckDB
Create Sample Table
CREATE TABLE orders AS SELECT * FROM source;

## Exploratory Data Analysis
SELECT * FROM orders LIMIT 5;
DESCRIBE orders;
SELECT COUNT(*), AVG(amount) FROM orders;

## Export Data Formats
COPY orders TO 'orders.json' (FORMAT JSON);
COPY orders TO 'orders.parquet' (FORMAT PARQUET);

## Import Messy CSV
SELECT * FROM read_csv_auto('file.csv', ignore_errors=true);

## Data Cleaning
SELECT COALESCE(customer,'Unknown') FROM orders;
SELECT TRIM(LOWER(product)) FROM orders;
SELECT REGEXP_REPLACE(product,'\\s+',' ','g') FROM orders;

## Date Formatting
SELECT STRFTIME(order_date,'%Y-%m') FROM orders;

## Data Transformation
Binning Values
CASE 
 WHEN amount>700 THEN 'high'
 WHEN amount>300 THEN 'medium'
 ELSE 'low'
END

## Derived Columns
SELECT amount*0.1 AS tax FROM orders;

## Filtering & Dropping Columns
SELECT * FROM orders WHERE region='US';
SELECT * EXCLUDE region FROM orders;

## Aggregation & Pivot
SELECT region, COUNT(*), SUM(amount) 
FROM orders GROUP BY region;

## SELECT * FROM orders 
PIVOT(COUNT(*) FOR region IN ('US','EU'));

Setting Up dbt Project
Install dbt
pip install dbt
dbt --version

Initialize Project
git clone repo_url
cd repo_folder
dbt init project_name

Configure profiles.yml

Add account details

username & password

role, warehouse, database, schema

threads for parallel runs

Test & Run Models
dbt debug
dbt run

Push to GitHub
git add .
git commit -m "first commit"
git push
