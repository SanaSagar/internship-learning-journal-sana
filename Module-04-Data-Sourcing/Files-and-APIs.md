## Week 4 – Day 1

### Session Summary

This session focused on API inspection, geocoding workflows, structured JSON extraction, and data sourcing from external platforms like BBC Weather and Wikipedia. The session demonstrated how real-world applications make API calls, how to analyze them using browser DevTools, and how to replicate those calls in Python.
The session also covered JSON parsing, handling partial JSON responses, geocoding and reverse geocoding using Nominatim (OpenStreetMap), batch geocoding with pandas, rate limiting, and extracting structured data such as city population tables and image URLs from Wikipedia pages.

### Concepts Covered

#### 🔹 API Inspection & Network Analysis
- Using Browser DevTools → Inspect → Network tab
- Identifying API request URLs
- Understanding HTTP methods (GET)
- Query parameters (latitude, longitude)
- Headers and request metadata
- Response analysis

#### 🔹 JSON & JSONP Handling
- JSON response structure
- Extracting nested fields
- JSON strings vs JSON objects
- Using `json.loads()`
- Partial JSON extraction
- Understanding JSONP format

#### 🔹 BBC Weather API
- Extracting latitude & longitude-based weather data
- Understanding dynamic URL parameters
- Formatting API calls using f-strings
- Parsing structured weather data

#### 🔹 Geocoding & Reverse Geocoding (Nominatim)
- Address → Latitude/Longitude (Geocoding)
- Latitude/Longitude → Address (Reverse Geocoding)
- Nominatim API endpoints
- Importance of User-Agent header
- Handling API rate limits
- Batch geocoding workflow

#### 🔹 Batch Processing with Pandas
- Loading CSV data
- Creating DataFrames
- Adding new columns
- Applying functions row-wise
- Exporting processed data

#### 🔹 Wikipedia Data Extraction
- Wikipedia search API
- Topic-based search queries
- Extracting summaries
- Page metadata extraction
- HTML table extraction
- Extracting images from page content
- List of cities & population data extraction

#### 🔹 Responsible API Usage
- Rate limiting
- Avoiding excessive calls
- Proper headers usage
- Ethical data sourcing practices
