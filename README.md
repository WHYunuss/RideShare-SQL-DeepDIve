# 🚕 Uber & Lyft SQL Data Analysis Project

## 📊 Project Overview

This project presents a complete end-to-end SQL analysis of a large rideshare dataset containing thousands of Uber and Lyft ride records. Each ride includes attributes like cab type, price, distance, surge multiplier, and timestamps.

The goal was to simulate a real-world data analyst workflow — from raw data ingestion and cleaning to advanced querying and insight generation. Rather than executing isolated queries, the project was structured to reflect a mid-level SQL portfolio piece with practical, business-relevant skills.

---

## 📁 Dataset

**Source**: Uber & Lyft Rides Dataset  

- **Full Dataset**: `data/rides.csv` (too large to preview on GitHub)  
- **Sample Dataset**: `data/rides_sample.csv` (~1–2k rows, previewable)

### 🔑 Key Fields

| Field            | Description                                               |
|------------------|-----------------------------------------------------------|
| `distance`       | Distance of the ride in miles                             |
| `cab_type`       | Uber or Lyft                                              |
| `time_stamp`     | Epoch time when ride data was captured                    |
| `destination`    | Destination location                                      |
| `source`         | Starting location                                         |
| `price`          | Estimated ride cost (USD)                                 |
| `surge_multiplier` | Surge pricing factor (default = 1)                      |
| `id`             | Unique ride identifier                                    |
| `product_id`     | Internal product type                                     |
| `name`           | Ride type (e.g., UberPool, UberXL, Lyft Lux)             |

---

## 🛠️ Project Steps

### 1. Data Setup
- Created schema: `rides`
- Built raw staging table (all fields as `TEXT`)
- Loaded CSV data into staging
- Created cleaned table with appropriate data types (`NUMERIC`, `TIMESTAMP`, etc.)

### 2. Data Cleaning & Parsing
- Converted `time_stamp` from epoch to PostgreSQL `TIMESTAMP`
- Removed rows with missing/NULL values in `price` or `distance`
- Deduplicated data using `id`
- Replaced missing `surge_multiplier` with default value `1`

### 3. Exploratory Analysis
- Counted total rides per `cab_type`
- Listed all unique `ride types`
- Analyzed price distribution per ride type
- Measured frequency of surge multipliers > 1

### 4. Business-Oriented Insights
- Compared ride volumes between **Uber** and **Lyft**
- Calculated average price per ride type
- Analyzed surge pricing effect on total price
- Identified top 5 most expensive ride types
- Compared average ride distances between cab types
- Studied hourly and day-of-week ride patterns
- Measured correlation between price and distance

### 5. Advanced Metrics & Segmentation
- Created `price_per_mile = price / distance`
- Categorized rides into **Low / Medium / High** price tiers using `CASE`
- Estimated ride type **market share** per platform
- Analyzed surge behavior across different times of day

---

## 🔍 Key Findings

- **Uber vs Lyft**: One platform consistently dominated in ride volume
- **Premium Pricing**: Luxury options (UberBlack, Lyft Lux) cost 4–6x more than base rides
- **Surge Pricing**: Prices spiked significantly at night and on weekends
- **Distance vs Price**: Positive correlation, but not linear — short rides often had high base costs
- **Market Concentration**: A few ride types accounted for the majority of rides

---

## 🧠 SQL Skills Demonstrated

This project showcases intermediate to advanced SQL techniques:

### ✅ Aggregations
- `COUNT()`, `AVG()`, `SUM()`, `ROUND()`

### ✅ Conditional Logic
- `CASE WHEN` for ride tier segmentation

### ✅ Data Cleaning
- Handling `NULL`s
- Parsing epoch to timestamp
- Deduplication using `ROW_NUMBER()`

### ✅ Grouping & Filtering
- `GROUP BY`, `HAVING`

### ✅ Sorting & Limiting
- `ORDER BY`, `LIMIT`

### ✅ Window Functions
- `ROW_NUMBER() OVER()` for deduplication & top-N analysis
- `SUM() OVER()` for ride type market share

### ✅ Date & Time Functions
- `EXTRACT(HOUR FROM timestamp)`
- `EXTRACT(DOW FROM timestamp)`

### ✅ Statistical Analysis
- `CORR(distance, price)` to measure pricing correlation

---

## 📌 Next Steps (Optional)
- Add **dashboards** or **visualizations** using Tableau, Power BI, or Python
- Include **SQL views** or **stored procedures**
- Expand analysis with **real-time** or **streaming data**
---

## 📂 Folder Structure
Uber-Lyft-SQL-Analysis/
├── data/
│ ├── rides.csv
│ └── rides_sample.csv
├── scripts/
│ └── analysis_queries.sql
├── README.md

---

## 🧑‍💻 Author
**YY** - trying some of this & that
