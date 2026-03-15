
## Session 3 

Data Analysis using Python and Pandas
This notebook demonstrates how to perform basic data analysis using Python and Pandas on a dataset of card transactions.

Pandas is a powerful Python library used for data manipulation and analysis.

Resources to learn Pandas:

https://pandas.pydata.org/
https://pandas.pydata.org/docs/user_guide/10min.html
https://youtube.com/playlist?list=PL-osiE80TeTsWmV9i9c58mdDCSskIFdDS
Dataset
We analyze a card transactions dataset stored in Parquet format.

Parquet is a column-based storage format that is:

Faster than CSV
Smaller in size
Efficient for analytics
Step 1: Download Dataset
# Download dataset
!curl -C- -o transactions.parquet "https://drive.usercontent.google.com/download?id=1XGvuFjoTwlybkw0cc9u34horMF9vMhrB"
Step 2: Import Required Library
import pandas as pd
Pandas is used to load, clean, and analyze tabular data.

Step 3: Load Dataset
df = pd.read_parquet("transactions.parquet")
This reads the parquet file into a Pandas DataFrame.

Step 4: View First Few Rows
df.head()
head() displays the first 5 rows of the dataset.

Step 5: Inspect Dataset Structure
df.info()
This shows:

number of rows
column names
data types
memory usage
missing values
Step 6: Summary Statistics
df.describe()
This generates statistical information such as:

count
mean
standard deviation
minimum value
maximum value
quartiles
For all numerical columns.

Step 7: View Column Names
df.columns
This lists all columns present in the dataset.

Step 8: Check Unique Values
Example:

df["merchant"].unique()
This shows all unique merchants present in the dataset.

Step 9: Count Unique Values
df["merchant"].nunique()
This returns the number of unique merchants.

Step 10: Value Counts
df["merchant"].value_counts()
Shows how many transactions occurred for each merchant.

Step 11: Filter Data
Example: Transactions greater than 1000

df[df["amount"] > 1000]
This filters rows where transaction amount is greater than 1000.

Step 12: Select Specific Columns
df[["merchant", "amount"]]
This selects only the specified columns.

Step 13: Group By Operation
Group transactions by merchant:

df.groupby("merchant")["amount"].sum()
This calculates total spending per merchant.

Step 14: Average Transaction Per Merchant
df.groupby("merchant")["amount"].mean()
This calculates average transaction amount per merchant.

Step 15: Sorting Values
df.sort_values("amount", ascending=False)
Sorts the dataset based on transaction amount.

Step 16: Top Transactions
df.sort_values("amount", ascending=False).head()
Displays the largest transactions.

Step 17: Basic Data Filtering Example
Transactions from a specific merchant:

df[df["merchant"] == "Amazon"]
Step 18: Multiple Conditions
df[(df["amount"] > 500) & (df["merchant"] == "Amazon")]
Filters rows where:

amount > 500
merchant is Amazon
Step 19: Save Processed Data
df.to_csv("transactions_cleaned.csv", index=False)
Exports the DataFrame into a CSV file.

Data Analysis with Databases
Databases are where most transactional data resides.
Instead of exporting everything into CSV files, analysts often query the database directly.

In this notebook we demonstrate how to:

Connect to a database
Run SQL queries from Python
Analyze the results using Pandas
Query the Database
There are many ways to connect to and query a database.

In Python, a common approach is using:

SQLAlchemy → database connection
Pandas → executing queries and analyzing results
Step 1: Database Connection
stats_connection = "mysql+pymysql://guest:relational@db.relational-data.org/stats"
This connection string contains:

Database type → mysql
Driver → pymysql
Username → guest
Password → relational
Database host → db.relational-data.org
Database name → stats
Step 2: Create Engine and Connect
import pandas as pd
import sqlalchemy as sa

engine = sa.create_engine(
    "mysql+pymysql://guest:relational@db.relational-data.org/stats"
)

pd.read_sql("SELECT COUNT(*) FROM posts", engine)
This verifies that we successfully connected to the database and counts the rows in the posts table.

Step 3: Helper Function for Queries
Instead of writing pd.read_sql() every time, we create a helper function.

def query(sql):
    return pd.read_sql(sql, engine)
Now we can easily run SQL queries.

Example Query
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
This query:

Groups posts by user
Counts how many posts each user made
Sorts users by post count
Dataset Note
The user names are None because the dataset is anonymized.

How Concentrated Are the Posts?
A common question in online communities:

Do 20% of users create 80% of the content?

This is related to the Pareto Principle (80/20 rule).

Step 4: Count Posts per User
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
This produces a table showing:

User	Number of Posts
Step 5: Compare Top 20% Users
post_count.PostCount.iloc[:len(post_count)//5].sum() / post_count.PostCount.sum()
Explanation:

len(post_count)//5 → top 20%
.sum() → total posts by those users
divide by total posts
Result:

Top 20% of users generate ~76% of posts

This is close to the Pareto distribution.

Does Age Predict Reputation?
The users table contains:

Age
Reputation
We want to check whether age influences reputation.

Step 6: Fetch Aggregated Statistics
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
This query retrieves aggregated statistics needed to compute correlation.

Correlation Result
The calculated correlation is about:

~1.7%
Interpretation:

Age and reputation have almost no relationship.

This means older users do not necessarily have higher reputation.

How Many Views Increase Reputation by 1 Point?
Hypothesis:

More profile views may increase user reputation.

Step 7: Fetch Required Aggregates
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
This gathers statistics needed to estimate the relationship between views and reputation.

Inspect the Data Directly
To better understand the relationship:

reputation = query("SELECT Views, Reputation FROM users")
reputation
Calculate Mean Values
reputation.mean()
This computes the average views and reputation across users.

Interpretation
The analysis suggests that:

Users with more profile views tend to have higher reputation
However, the relationship is not perfectly linear
Reputation depends on many other factors like:

Answers posted
Question quality
Community voting
Lessons
This notebook demonstrates how to combine:

SQL for querying data
Pandas for analysis
SQLAlchemy for database connections
Together they form a powerful workflow for data analysis directly from databases.

Useful libraries:

https://pandas.pydata.org/
https://docs.sqlalchemy.org/
What Else Should You Know for Exams?
You should also know about SQLite.

SQLite is:

A lightweight database
Serverless
Stored in a single file
Website:

https://sqlite.org/

It is widely used in:

Mobile apps
Embedded systems
Small applications

---

## Session 4

Data Analysis with Datasette
Datasette is an open-source multi-tool created by Simon Willison for exploring and publishing data. It instantly turns any SQLite database into a web interface with powerful exploration features, built-in JSON APIs, and visualization capabilities—all without requiring you to write any code upfront. It is highly effective for data journalism, analysis workflows, and sharing datasets with both technical and non-technical audiences.

Installation and Quickstart
You can install Datasette and its companion tools using standard Python package managers like pip or uv, or via Homebrew:

pip install datasette
To start Datasette with a SQLite database, simply run:

datasette your_database.db
This will launch a web server at http://localhost:8001, giving you an instant interface to explore your data.

Core Analysis Features
The Interactive Interface
The database homepage displays all available tables, row counts, and a SQL query box. Clicking on any table name opens a view equipped with interactive features:

Sorting: Sort data simply by clicking the column headers.
Pagination: Easily navigate through large datasets.
Column Menus: Access faceting and filtering options via the cog icon next to column headers.
Faceting for Discovery
Faceting is a core feature for exploratory analysis. It allows you to see the distribution of values within a column.

By selecting "Facet by this", Datasette generates clickable counts of each category (e.g., showing how many orders are "completed", "pending", or "cancelled").
You can apply multiple facets simultaneously to reveal deeper patterns in your data, such as looking at product categories across different regions.
Filtering Data
Datasette provides robust filtering options to drill down into specific subsets of data. You can stack these filters to answer specific questions. Supported filter types include:

Exact match
Text contains
Numeric comparisons (e.g., quantity > 1)
Date ranges
Advanced Analysis
Running SQL Queries
While Datasette does not require SQL knowledge for basic exploration, it offers a built-in SQL editor for complex analysis. You can safely execute custom SQL queries because the database is opened in read-only mode. Just like standard tables, your query results can be faceted, filtered, and exported.

Creating Canned Queries
If you have frequently run analyses, you can save them as named "canned queries." By defining these in a metadata.json file and launching Datasette with the -m flag, these queries will appear in the sidebar, effectively turning Datasette into a self-service analytics portal.

Exporting and Publishing
Exporting Data and API Access
Everything you see in the Datasette interface can be exported as raw data.

Links at the bottom of the page allow you to export the current view (respecting all active filters) to CSV, JSON, or newline-delimited JSON.
Datasette includes built-in API access; you can simply append .json to any URL to retrieve the data programmatically.
Publishing to the Web
Datasette includes a publish command that allows you to bundle your SQLite database into a Docker container and deploy it directly to the internet using serverless hosting providers like Google Cloud Run or Heroku.

datasette publish cloudrun your_database.db
Once deployed, your database becomes a public API and interactive web interface for anyone to explore.

Ecosystem Tools
Plugins
Datasette supports custom templates, CSS, and an extensive ecosystem of plugins to enhance your analysis:

datasette-cluster-map: Visualizes records with latitude and longitude data on an interactive map.
datasette-vega: Allows you to plot line charts and graphs (e.g., tracking date-time data against case numbers).
datasette-copyable: Generates copy-and-pasteable data formats, such as LaTeX tables.
Data Preparation with sqlite-utils
Before analyzing data in Datasette, you can use a companion CLI tool called sqlite-utils. It is designed to manipulate SQLite databases, making it easy to:

Insert large CSV files into SQLite database tables.
Extract columns with duplicate strings into separate joined tables to clean the data.
Enable full-text search on specific columns.
Data Analysis with DuckDB and Parquet
1. What is DuckDB?
DuckDB is an in-process analytical SQL database designed for fast analytical queries.
It is optimized for OLAP (Online Analytical Processing) workloads and works efficiently with large datasets.

Key Features
Runs inside Python, R, or applications (no server required).
Optimized for analytical queries on large datasets.
Uses columnar storage, which improves performance for analytics.
Supports SQL queries directly on files like:
CSV
Parquet
JSON
Pandas DataFrames
Very fast compared to Pandas for large data processing.
DuckDB is often called the "SQLite for analytics".

2. What This Code Is About
This notebook demonstrates:

Using Parquet as a data storage format
Comparing file formats (CSV, JSON, SQLite, Parquet)
Comparing performance of Pandas vs DuckDB
Running SQL queries directly on Parquet files
Combining Pandas and DuckDB operations
The dataset used is:

2015 Flights Dataset

It contains flight information such as:

Departure delay
Arrival delay
Flight distance
Other flight metrics
The goal is to show that:

DuckDB can perform analytical queries much faster and with less memory than Pandas.

3. Step-by-Step Implementation
Step 1 – Install Required Libraries
!pip install duckdb pandas sqlalchemy sqlite3
Step 2 - Download Dataset
!curl https://github.com/plotly/datasets/raw/master/2015_flights.parquet --output 2015_flights.parquet
Step 3 – Load Data Using Pandas
import pandas as pd

df = pd.read_parquet('2015_flights.parquet')
df.head()
Step 4 – Compare Storage Formats
Convert to CSV

%timeit df.to_csv('2015_flights.csv', index=False)
Convert to JSON

%timeit df.to_json('2015_flights.json', orient='records')
Convert to SQLite

%timeit df.to_sql('2015_flights', 'sqlite:///2015_flights.db', index=False, if_exists='replace')
Save as Parquet

%timeit df.to_parquet('2015_flights.saved.parquet')
Step 5 – Check File Sizes
!ls -la 2015_flights.*
Comparision of file size :

Format	Size	Performance
CSV	Large	Slow
JSON	Very Large	Slow
SQLite	Medium	Moderate
Parquet	Small	Fast
Step 6 – Perform Analysis Using Pandas
Find the number of unique flight distances for each departure delay.

delays = df.groupby('DEPARTURE_DELAY')['DISTANCE'].nunique()
delays[delays.index > 0]
Measure Pandas Performance

%timeit df.groupby('DEPARTURE_DELAY')['DISTANCE'].nunique()
Typical execution time: ~5 seconds

Step 7 – Perform Same Query Using DuckDB
import duckdb

delays = duckdb.query("""
SELECT
    DEPARTURE_DELAY,
    COUNT(DISTINCT DISTANCE)
FROM "2015_flights.parquet"
GROUP BY DEPARTURE_DELAY
ORDER BY DEPARTURE_DELAY
""").df()
DuckDB is ~20–25x faster than Pandas.

Step 8 – Run DuckDB Using a Connection
conn = duckdb.connect(database=':memory:', read_only=False)

delays = conn.execute("""
SELECT
DEPARTURE_DELAY,
COUNT(DISTINCT DISTANCE)
FROM "2015_flights.parquet"
GROUP BY DEPARTURE_DELAY
ORDER BY DEPARTURE_DELAY
""").df()
Explanation

Creates an in-memory DuckDB database and executes SQL queries.
Advantages:

No external database required

Very fast processing

Step 9 – Query Pandas DataFrame Using DuckDB
DuckDB can query Pandas DataFrames directly.

df = pd.read_parquet('2015_flights.parquet')

delays = duckdb.sql("""
SELECT
DEPARTURE_DELAY,
COUNT(DISTINCT DISTANCE)
FROM df
GROUP BY DEPARTURE_DELAY
ORDER BY DEPARTURE_DELAY
""").df()
DuckDB treats the Pandas DataFrame df as a SQL table.

Much faster than Pandas.

Step 10 – Combine DuckDB and Pandas
Example:
Segment flights by distance:

SELECT
CASE
WHEN DISTANCE < 1000 THEN 'Short'
WHEN DISTANCE < 2000 THEN 'Medium'
ELSE 'Long'
END AS flight_type
This categorizes flights into:

Category	Distance
Short	< 1000
Medium	1000–2000
Long	> 2000

---

## Session 5

Vibe Analysis
Vibe analysis is analyzing data as if the analysis itself doesn't exist—you focus only on business outcomes, skipping intermediate steps. This approach emerged from vibe coding, where you code as if code doesn't exist. With vibe analysis, you give an LLM full context, state your goal, and review only the answers. The LLM handles exploration, cleaning, modeling, visualization, and deployment.

Core Vibe Analysis Workflow
From data to deployed insights without manual coding.

Automated exploration: Using LLMs to generate and test hypotheses.
Data quality automation: Detecting non-obvious issues and creating validation rules.
Visual storytelling: Building publication-ready data stories with style transfer.
Meta-prompting techniques: Improving prompts before execution.
The Traditional Data Science Workflow vs. Vibe Analysis
A data scientist typically:

Explores the data (EDA, profiling, types, missing values)
Cleans it (deduping, anomalies, schemas)
Models it (features, algorithms, parameters)
Explains it (narratives, visualizations, slides)
Deploys it (APIs, dashboards, reports)
Anonymizes it (synthetic data for case studies)
Vibe analysis automates most of this cycle.

What's Dying (Automated Tasks)
EDA: Profiling, types, missing values, deduping, anomaly detection.
Scaffolds: Loaders, schemas, docstrings, README files, tests.
AutoML: Feature selection, model choice, parameter tuning, metrics.
Code writing: LLMs can fill in 80% from specifications.
Explainers: Generating narratives, visuals, presentations.
Forms: Project reports, timesheets, documentation.
What's Rising (Critical Skills)
Leadership: Setting the right goal and allocation across human and AI teams.
Problem framing: Precise prompts that reduce iteration cycles.
Eval design: Automated validation with binary checks and LLM-as-judge.
Invariants: Defining ontologies, declaring truths and constraints.
Verticalization: Domain-specific datasets and workflows as competitive moats.
Trust & taste: Auditing AI output, telling compelling stories.
Automated Hypothesis Generation
Instead of manually exploring data, use LLMs to generate business hypotheses automatically. Let the LLM test everything in parallel. When done, have it craft an executive summary you can directly present.

Vibe Analysis Workflow Steps
1. Provide Context
Upload your dataset to ChatGPT, Claude, or Codex. Give it business context.

2. Request Comprehensive Analysis
Ask for specific analyses OR ask it to discover insights. The LLM will write Pandas/NumPy code, run statistical tests, generate visualizations, and create summaries.

3. Let it Work Autonomously
Use Agent Full Access mode to eliminate approval prompts. Run multiple agents in parallel—one for analysis, one for planning, one for visualization.

4. Find Non-Obvious Insights
Have the LLM focus on surprising patterns, such as data errors, anomalies, or quality issues.

Visual Data Stories
Create beautiful, interactive visualizations styled after leading publications.

Style Transfer Technique: Instead of specifying every detail, reference a style (e.g., "in the style of the New York Times").
Generate and Publish: The agent generates index.html, style.css, and script.js. You can then publish this directly to GitHub Pages.
Creating Synthetic Data with Hypotheses
Don't generate random fake data. Instead, align synthetic data with business hypotheses. The LLM creates data where these patterns hold, making it useful for demos and case studies without exposing real data.

Meta-Prompting
Use LLMs to optimize your prompts before running analysis.

Write your initial prompt.
Add: "Suggest an improved prompt for this".
Review the improved version.
Run the improved prompt in a fresh session.
Parallel Chat Strategy
Run multiple chats in parallel so you don't wait for agents to finish:

Chat 1: Main analysis and coding.
Chat 2: "What interesting, useful analysis can I run on this dataset?"
Chat 3: "Find the most interesting, useful, non-obvious insights."
Error Detection and Validation
Multi-model review: Ask different models to find errors. Many eyes make bugs shallow.
Checksum validation: Ask the LLM to provide category totals that sum to the overall total.
Post-validation prompts: After analysis, ask the LLM to find errors in its own analysis.
Context Management and Session Hygiene
Reset over repair: Long conversations accumulate bad assumptions ("context rot"). Start a fresh chat with a clean prompt instead of iterating through broken context.
Summarize and restart: Have the LLM summarize the prompt that will yield the exact final result, and run it in a new window.
Meta-Analysis
Analyze your analysis process by reviewing LLM action logs to continuously improve prompts, tools, and workflows.

Risk Mitigation Strategies
When shipping LLM insights to executives:

Frame safe questions: Focus on general business recommendations, options with tradeoffs, or directional insights.
Reduce error likelihood: Write code first then analyze, add citations for insights, request checksums.
Post-validation: Ask the LLM to find errors, use multiple models, run automated statistical checks.
