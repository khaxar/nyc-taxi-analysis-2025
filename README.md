# NYC Taxi Analysis – January 2025

## Dataset

NYC Yellow Taxi trip records for January 2025, covering two taxi companies (VendorID 1 and VendorID 2).

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