# NYC Taxi Analysis – January 2025

## Dataset

NYC Yellow Taxi trip records for January 2025, covering two taxi companies (VendorID 1 and VendorID 2).

Includes pickup/dropoff times, trip distance, total fare, tip amount, and PULocationID. Taxi zone lookup maps PULocationID to borough and zone names.

## Questions Explored

- Revenue by hour
- Longest pickup zones
- Tips relative to trip distance
- Weekday vs weekend behavior
- Vendor performance comparison

## Key Findings

- Revenue peaks at commute hours.
- Longest trips originate mainly from: East Harlem South, Hollis, Great Kills, Tottenville, West Concourse, Pelham Bay/City Island, Kew Gardens, Midland Beach, Fordham South, St. Albans.
- Tip percentage and tip amount show very weak negative correlations with trip distance (correlation coefficients –0.128 and –0.095, respectively). Although the hourly charts appear to follow a similar trend, this is largely due to shared ride volume patterns across the day rather than a meaningful causal relationship between distance and tipping. Overall, tipping behavior is largely independent of trip distance.
- Weekdays show higher average fares than weekends.
- Vendor Performance: Vendor 1 generates the highest average trip revenue; Vendor 2 underperforms relative to Vendor 1.

## Feature Engineering & Cleaning

- Trip duration converted to minutes; outliers removed (zero distances, impossible speeds).
- Flags added: `long_trip` (>10 miles), `high_tip` (>20% tip), time and distance segments.
- Combined segments (`time × distance`) created for multi-dimensional insights.

---

## Tools & Technologies

- **Python 3.x**
- **Pandas** – data manipulation and aggregation
- **Jupyter Notebook** – analysis workflow
- **Parquet / CSV** – data storage formats
- **Git & GitHub** – version control and project tracking

---

## Methodology

### 1. Data Loading
- Loaded NYC Yellow Taxi data from Parquet and CSV formats.
- Verified column structure and data types.

### 2. Data Cleaning
- Removed invalid values (e.g., negative distances or fares).
- Handled missing values where necessary.
- Created derived features:
  - `hour`
  - `trip_duration_min`
  - `tip_pct`
  - `long_trip` indicator

### 3. Exploratory Data Analysis (EDA)
- Revenue analysis by hour of day
- Vendor performance comparison
- Pickup location (zone) aggregation
- Trip distance distribution analysis
- Tipping behavior analysis

### 4. Aggregation & Grouping
Grouped data by:
- `VendorID`
- `PULocationID`
- `hour`

Calculated:
- Average revenue
- Total revenue
- Trip counts
- Average distance
- Tip percentage

### 5. Statistical Validation
- Correlation analysis between:
  - `trip_distance` and `tip_pct`
  - `trip_distance` and `tip_amount`
- Verified numerical outputs before forming conclusions.

---

## Analytical Focus Areas

- Revenue concentration patterns
- Vendor performance differences
- Distance distribution and long-trip frequency
- Tipping behavior evaluation
- Time-of-day demand variation
