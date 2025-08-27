# Module-02-Capstone-Risma
This project analyses NYC taxi trip data to uncover insights that optimise fleet performance, maximise revenue, and improve scheduling by targeting high-value zones, peak hours, and profitable trip types.

# Drive Smart, Maximise Profits: Data-Driven Insights to Boost NYC Taxi Company Revenue

## Key Question:
*How can taxi companies leverage trip data to increase total revenue and optimise fleet performance in New York City?*

## Background:
Running a taxi company in New York City is becoming increasingly difficult with rideshare apps like Uber and Lyft handling over 75% of the market. This project explores NYC taxi trip data to uncover revenue-boosting insights, helping taxi operators make more informed decisions and improve their bottom line.

The project covers:
- Top 10 Pickup & Drop-off Spots: Revenue-generating locations
- High-Earning Days: Best days of the week for business
- Rush Hour vs Non-Rush Hour: Worth driving in peak hours?
- Rate Code Analysis: Which fare types are most profitable?
- Trip Distance vs Revenue: Do longer trips always mean more money?
- Passenger Count Trends: How does the number of passengers affect total revenue? Are solo rides more profitable per mile than group rides?
- Trip Type Differences: Do different trip types show significant differences in revenue patterns?
- Traffic Surcharge Analysis: How much does the congestion surcharge contribute to overall revenue during peak hours?

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

After cleaning, we were left with 60,090 valid records (out of 68,211) to analyse.

## Summary of Key Findings

### 1. Revenue by Taxi Zones
- **Highest pickup revenue:** Zone 74 ($219,658 which is 19.1% of total revenue) and Zone 75 ($155,197 which is 13.5% of total revenue)  
- **Highest drop-off revenue:** Zone 236 ($45,247 which is 3.9% of total revenue)  
- Zones 74 and 166 appear in both pickup and drop-off lists, indicating high-traffic corridors.

### 2. Revenue by Day of the Week
- **Tuesday:** Highest revenue ($193,348 which is 16.8% of total revenue)  
- Weekdays (Monday–Friday) consistently outperform weekends  
- Saturday ($141,833 which is 16.8% of total revenue) and Sunday ($136,480 which is 11.9% of total revenue) show lower revenue  
- Thursday shows a minor mid-week revenue boost

### 3. Hourly Revenue Trends
- **Peak hours:** 4 PM–6 PM ($86,647–$95,303 which is 7.5%–8.3% of total revenue)  
- Morning peaks: 7 AM–9 AM ($40,447–$56,080 which is 3.5%–4.9% of total revenue)  
- Lowest revenue: 12 AM–6 AM ($7,712–$18,176 which is 0.7%–1.6% of total revenue)

### 4. Rate Code Revenue
- **Standard Rate (ID=1):** $1.11M which is 96.6% of total revenue (dominant revenue source)  
- **Negotiated Fares (ID=5):** $21.7K which is 1.9% of total revenue, high-value but low-volume  
- Airport trips (JFK, Newark) and suburban trips contribute minor revenue

### 5. Trip Distance vs. Revenue
- Short trips (< 10 miles) generate **most total revenue** due to high volume  
- Long trips (> 20 miles) are less frequent and more variable in revenue

### 6. Passenger Count vs. Revenue
- Single-passenger trips: $969K which is 84.3% of total revenue (dominant)  
- Multi-passenger trips contribute minimally

### 7. Trip Type vs. Revenue
- **Street-hail trips:** High volume, $1.13M which is 98.3% of total revenue  
- **Dispatch trips:** Higher average revenue ($31.66) but low total revenue ($19.6K which is 1.7% of total revenue)

### 8. Congestion Surcharge by Hour
- Peaks in late afternoon (3 PM–6 PM), max $3,797 at 6 PM  
- Lowest overnight (12 AM–5 AM)

## Actionable Recommendations

### 1. Driver Allocation & Scheduling
- Deploy more drivers in **high-revenue pickup zones** (Zones 74, 75, 166) during peak hours  
- Increase fleet presence on **Tuesdays and Thursdays**, and during **morning (7–9 AM) and afternoon/evening (4–6 PM) peaks**  
- Reduce fleet presence during **low-demand hours (12–6 AM, late night)**

### 2. Fleet Composition & Trip Strategy
- Prioritise **sedans/standard cars** for single-passenger trips  
- Reserve larger vehicles for **airport transfers, events, or group rides**  
- Optimise dispatch for **short-distance, high-volume trips (< 10 miles)**

### 3. Revenue & Pricing Optimisation
- Leverage **dispatch trips and negotiated fares** for high-value revenue  
- Introduce **dynamic pricing** or surge pricing during afternoon/evening peaks (3–6 PM)  
- Promote **weekend rides** to offset natural dips in demand  
- Monitor long trips (> 20 miles) for inefficiencies (e.g., deadhead miles)

### 4. Operational Efficiency & Route Planning
- Position drivers near **overlapping high-revenue pickup and drop-off zones**  
- Adjust **pricing or incentives** during peak congestion hours  
- Coordinate with **airports, corporate clients, and event venues** to capture structured demand

### 5. Customer Experience & Marketing
- Promote **off-peak travel** as a cheaper alternative  
- Introduce **loyalty programs or promotions** for group rides or long trips  
- Educate passengers on **congestion impacts on pricing**

### 6. Strategic Partnerships & Expansion
- Develop partnerships for **airport transfers, corporate accounts, and negotiated fares**  
- Explore specialised markets to **reduce reliance on standard street-hail trips**  
- Refine **pricing models** based on high-revenue, short-distance trips
