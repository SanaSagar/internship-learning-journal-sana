### Week 4 Notes — APIs, Geocoding and Data Extraction
## 1. Extracting Backend APIs from Websites

->Finding Hidden APIsOpen Browser Developer Tools → Network tab
- Perform an action (search, click, scroll)
- Observe backend API calls
- Copy the Request URL

->API URL Structure
Host / Path ? key=value & key=value
%20 → space
%2C → comma

->Fetching API Data in Python
import requests
response = requests.get(URL)
data = response.json()

->Handling Malformed JSON
Sometimes APIs return broken JSON.
Steps:
1.Locate start/end of JSON using .find()
2.Slice valid portion
3.Convert using json.loads()

## 2. Geocoding with Geopy (Nominatim)
Setup
from geopy.geocoders import Nominatim
geolocator = Nominatim(user_agent="myapp")

-user_agent must be lowercase, no spaces

->Forward Geocoding
Convert address → coordinates

location = geolocator.geocode("IIT Madras")
location.latitude
location.longitude

->Reverse Geocoding
Convert coordinates → address
geolocator.reverse((lat, lon))

->Batch Geocoding with Pandas
Apply geocoding to DataFrame columns.

->Handling Missing Values
Invalid addresses return None → handle with conditions.

->Rate Limiting
Nominatim blocks frequent requests.

from geopy.extra.rate_limiter import RateLimiter
geocode = RateLimiter(geolocator.geocode, min_delay_seconds=1)

->Language Parameter
geolocator.geocode("Delhi", language="hi")

## 3. Wikipedia Python Package
->Installation
pip install wikipedia

->Search Articles
wikipedia.search("Artificial Intelligence")

->Summary
wikipedia.summary("Artificial Intelligence", sentences=2)

->Full Page Data
page = wikipedia.page("Artificial Intelligence")
page.title
page.url
page.images
page.references
page.html()

## 4. Scraping IMDb Using Browser JavaScript
Steps
1.Open IMDb page
2.Press F12 → Console
3.Run extraction script

Extraction Script
copy(
  $$(".ipc-metadata-list-summary-item").map(item => [
    item.querySelector(".ipc-title-link-wrapper")?.href,
    item.querySelector(".ipc-title__text")?.textContent,
    item.querySelectorAll(".cli-title-metadata-item")[0]?.textContent,
    item.querySelector(".ipc-rating-star")?.textContent
  ])
)

Convert to CSV
Paste copied data into JSON-to-CSV converter.

## 5. Dynamic Web Scraping with Playwright
Problem
requests cannot fetch JavaScript-rendered content.

Solution

Use Playwright browser automation.

Installation
pip install playwright

Example
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.firefox.launch()
    page = browser.new_page()
    page.goto(url)
    html = page.content()

Playwright Features
- Capture screenshots
- Wait for elements to load
- Click buttons
- Fill forms
- Automate login

## 6. PDF Scraping and Table Extraction
Libraries
- BeautifulSoup → parse webpage
- Requests → download PDFs
- OS → manage folders
- Tabula → extract tables

Download PDFs
for link in soup.select("a[href$='.pdf']"):
    filename = link['href'].split('/')[-1]

Extract Tables from PDF
tabula.convert_into("file.pdf", "output.csv", pages=18)

## 7. Converting Documents to Markdown (MarkItDown)
Installation
pip install markitdown

Convert PDF
from markitdown import MarkItDown
md = MarkItDown()
result = md.convert("file.pdf")
print(result.text_content)

Supported Formats
PDF, Word, Excel, HTML, JSON, CSV, Images (OCR), ZIP

## 8. LLM-Based Website Scraping
Why Use LLMs
- Understand messy HTML
- Extract structured data
- Reduce manual parsing

Workflow
1. Fetch webpage
2. Extract text
3. Send to LLM
4. Request structured output

## 9. Chrome Remote Debugging for Scraping Logged-in Sites
Start Chrome in Debug Mode
chrome.exe --remote-debugging-port=9222

Connect Using Playwright
browser = p.chromium.connect_over_cdp("http://localhost:9222")


Allows reuse of logged-in sessions.

## 10. Scheduled Scraping with GitHub Actions
Purpose
- Automate scraping at fixed intervals.

Steps
1. Create scraping script
2. Add GitHub Actions workflow (.yml)
3. Use cron schedule
4. Auto-commit scraped data

## 11. Making Open Data Useful

Data Pipeline
Fetch → Parse → Aggregate

Best Practices
-Preserve raw files
-Convert to structured JSON
-Combine into CSV/Database

Using LLMs
-Clean messy text
-Normalize values
-Extract structured fields

## 12. Product Design Principles for Data Projects

- Make URLs shareable
- Prefer fast static websites
- Use search instead of complex filters
- Focus on readable design
- Ensure mobile compatibility

## 13. Supporting Different Users

Provide:

- Simple browsing interface
- Downloadable CSV files
- Reproducible notebooks
- Clear documentation and data dictionary
