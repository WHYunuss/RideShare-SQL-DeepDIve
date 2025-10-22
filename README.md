# Uber & Lyft SQL Data Analysis Project

## Project Overview

This project is a complete end-to-end SQL analysis of a large rideshare dataset containing thousands of Uber and Lyft ride records. Each ride includes details like cab type, price, distance, surge multiplier, and timestamps.

The goal was to simulate a real-world data analyst workflow — from ingesting and cleaning raw data to writing exploratory and business-driven SQL queries. Instead of running disconnected queries, the project follows a logical structure that reflects the kind of work you'd do in a mid-level analytics role.

---

## Dataset

**Source**: Uber & Lyft Rides Dataset  

- **Full Dataset**: `data/rides.csv` (too large to preview on GitHub)  
- **Sample Dataset**: `data/rides_sample.csv` (smaller, previewable version with ~1–2k rows)

### Key Fields

| Field               | Description                                               |
|---------------------|-----------------------------------------------------------|
| `distance`          | Distance of the ride in miles                             |
| `cab_type`          | Uber or Lyft                                              |
| `time_stamp`        | Epoch time when ride data was captured                    |
| `destination`       | Destination location                                      |
| `source`            | Starting location                                         |
| `price`             | Estimated ride cost (USD)                                 |
| `surge_multiplier`  | Surge pricing factor (default = 1)                        |
| `id`                | Unique ride identifier                                    |
| `product_id`        | Internal product type                                     |
| `name`              | Ride type (e.g., UberPool, UberXL, Lyft Lux)             |

---

## Project Steps

### 1. Data Setup

- Created schema: `rides`
- Built a raw staging table (all fields as `TEXT` to avoid parsing errors)
- Loaded the CSV data into staging
- Created a cleaned table with proper data types (`NUMERIC`, `TIMESTAMP`, etc.)

### 2. Data Cleaning & Parsing

- Converted `time_stamp` from epoch to PostgreSQL `TIMESTAMP`
- Removed rows with missing or null values in critical fields (`price`, `distance`)
- Deduplicated rides using `id`
- Replaced missing surge multipliers with the default value of 1

### 3. Exploratory Analysis

- Counted total rides per cab type
- Listed all unique ride types
- Analyzed price distributions per ride type
- Checked how often surge multipliers were above 1

### 4. Business-Oriented Insights

- Compared ride volumes between Uber and Lyft
- Calculated average price per ride type
- Analyzed the effect of surge pricing on total ride cost
- Found the top 5 most expensive ride types
- Compared average ride distances across cab types
- Explored hourly and day-of-week ride trends
- Measured correlation between ride distance and price

### 5. Advanced Metrics & Segmentation

- Created a new column: `price_per_mile = price / distance`
- Segmented rides into low, medium, and high price tiers using `CASE`
- Estimated market share of each ride type within Uber and Lyft
- Analyzed surge trends by time of day

---

## Key Findings

- **Uber vs Lyft**: One platform consistently had more rides than the other
- **Premium Pricing**: Luxury rides like UberBlack and Lyft Lux were 4–6x more expensive than base options
- **Surge Impact**: Surge pricing caused major price spikes, especially on weekends and late nights
- **Distance vs Price**: There's a positive correlation, but it's not linear — short rides often have higher base costs
- **Market Share**: A few popular ride types made up the majority of bookings

---

## SQL Skills Demonstrated

This project includes a wide range of intermediate-to-advanced SQL techniques:

### Aggregations
- `COUNT()`, `AVG()`, `SUM()`, `ROUND()`

### Conditional Logic
- `CASE WHEN` for creating price tiers

### Data Cleaning
- Handling nulls and missing values
- Parsing timestamps
- Deduplicating with `ROW_NUMBER()`

### Grouping & Filtering
- `GROUP BY`, `HAVING`

### Sorting & Limiting
- `ORDER BY`, `LIMIT`

### Window Functions
- `ROW_NUMBER()` for deduplication and top-N analysis
- `SUM() OVER()` to calculate market share

### Date & Time Functions
- `EXTRACT(HOUR)` and `EXTRACT(DOW)` for time-based trends

### Statistical Functions
- `CORR(distance, price)` to check price-distance relationship

---

## Business Case (Optional Narrative)

Imagine Uber's pricing team brings you on board to help them understand ride patterns, surge pricing behavior, and how Lyft is competing in shared markets. Your SQL analysis helps them decide when to promote certain ride types, how to adjust surge pricing strategies, and where Uber might be losing ground to Lyft.

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


## 📌 Next Steps (Optional)
- Add **dashboards** or **visualizations** using Tableau, Power BI, or Python
- Include **SQL views** or **stored procedures**
- Expand analysis with **real-time** or **streaming data**
---


## 🧑‍💻 Author
**YY** - trying some of this & that
