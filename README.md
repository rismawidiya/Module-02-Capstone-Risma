# Module-02-Capstone-Risma
This project analyses NYC taxi trip data to uncover insights that optimise fleet performance, maximise revenue, and improve scheduling by targeting high-value zones, peak hours, and profitable trip types.

# Drive Smart, Maximise Profits: Data-Driven Insights to Boost NYC Taxi Company Revenue

## Key Question:
*How can taxi companies leverage trip data to increase total revenue and optimise fleet performance in New York City?*

## Background:
Running a taxi company in New York City is becoming increasingly difficult with rideshare apps like Uber and Lyft handling over 75% of the market. This project explores NYC taxi trip data to uncover revenue-boosting insights, helping taxi operators make more informed decisions and improve their bottom line.

The project covers:
- Top 10 Pickup & Drop-off Spots – Revenue-generating locations
- High-Earning Days – Best days of the week for business
- Rush Hour vs. Non-Rush Hour – Worth driving in peak hours?
- Rate Code Analysis – Which fare types are most profitable?
- Trip Distance vs. Revenue – Do longer trips always mean more money?

## Data:
The analysis uses real-world data from the NYC Taxi & Limousine Commission (TLC). This dataset contains key features of thousands of taxi rides in NYC, such as trip times, locations, fares, payment methods, and more. You can access the dataset [here](https://drive.google.com/drive/folders/1NYHIL-RgVPW-HONz4pdzlcbIChF-c37N).

Key Features:
1. VendorID: Taxi provider
2. lpep_pickup_datetime: Trip start time
3. lpep_dropoff_datetime: Trip end time
4. passenger_count: Number of passengers
5. trip_distance: Distance traveled
6. PULocationID: Pickup location
7. DOLocationID: Drop-off location
8. RateCodeID: Fare type
9. payment_type: Payment method
10. fare_amount: Base fare
...and many more.

## Data Cleaning:
Before diving into the analysis, we first explored the dataset and handled missing values and outliers. This included:
- Removing irrelevant columns (e.g., VendorID, tip_amount)
- Imputing missing values logically based on column patterns
- Identifying and removing outliers, such as unusually high fares for short trips or zero-distance trips with charges.

After cleaning, we were left with 60,090 valid records (out of 68,211) to analyze.

## Data Analysis Results:

### 1. Top 10 Pickup & Drop-off Spots:
- **Top Pickup Spot:** Zone 74 with $176K in revenue
- **Top Drop-off Spot:** Zone 75 with $33K in revenue

### 2. High-Earning Days:
- **Best Day:** Tuesday with $150K in revenue
- **Worst Day:** Saturday and Sunday, both below $130K

### 3. Rush Hour vs. Non-Rush Hour:
- Peak revenue occurs between 3–6 PM, with a significant drop post-6 PM.

### 4. Airport Fare Types:
- **Highest Earning Fare:** Trips to JFK and Newark airports provide the highest revenue, especially for long-distance fares.

### 5. Trip Distance vs. Revenue:
- Medium-distance trips (5-30 miles) generate the highest revenue per trip. Long-distance trips (over 30 miles) yield mixed returns and may not always be as profitable.

## Actionable Recommendations

### 1. Zone-Based Fleet Optimisation:
- **Focus on top 10 locations especially East Harlem (Zones 74 & 75)**.
- **Actions:** Deploy **70% of fleet** during **6–10 AM** and **1–6 PM**, partner with 24/7 services.

### 2. Driver Shift Scheduling:
- **Weekdays** contribute **77%** of revenue, with **Tuesday** generating **~16%**.
- **Actions:** Allocate **80% of shifts** to **Mon–Fri**, prioritise **rush hours**, offer **$10 bonuses** for drivers with certain achievements.

### 3. Time-of-Day Efficiency:
- **12–5 AM** generates <10% of revenue.
- **Actions:** Assign **12% of fleet**, focus on nightlife areas, or use the time window for **maintenance**.

### 4. Standard Fare vs. Premium Trips:
- **Standard trips** average **$16**, **premium trips** offer higher fares (e.g., **JFK** at **$70**).
- **Actions:** Target **high-volume zones**, incentivise **premium trips** with **$10 bonuses** for drivers with certain achievements.

### 5. Short-Trip Maximisation:
- **Trips <10 miles** make up **75%+** of revenue.
- **Actions:** Offer **$25 bonus** for drivers who can complete **15 short trips** in one shift, focus on **downtown** and **transit hubs**.

## How to Use This Repository:
Clone this repository to run the analysis on your own device. Make sure to have the following dependencies installed:
- Python 3.x
- Pandas
- Matplotlib
- Seaborn
- Plotly
