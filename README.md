# Drive Smart, Maximise Profits: Data-Driven Insights to Boost NYC Taxi Company Revenue (2023)

## Project Overview
The New York City taxi industry faces stiff competition from rideshare platforms like Uber and Lyft, which now command over 86.1% of the market. To remain competitive, taxi companies must optimise fleet performance, pricing, and scheduling.  

This project analyses **NYC Taxi & Limousine Commission (TLC) trip data** to uncover revenue-boosting opportunities. By combining exploratory data analysis with actionable business insights, the project demonstrates how a data-driven approach can transform fleet management and profitability.  

Key focus areas include:  
- Top 10 Pickup & Drop-off Spots: Revenue-generating locations
- High-Earning Days: Best days of the week for business
- Rush Hour vs Non-Rush Hour: Worth driving in peak hours?
- Rate Code Analysis: Which fare types are most profitable?
- Trip Distance vs Revenue: Do longer trips always mean more money?
- Passenger Count Trends: How does the number of passengers affect total revenue? Are solo rides more profitable per mile than group rides?
- Trip Type Differences: Do different trip types show significant differences in revenue patterns?
- Traffic Surcharge Analysis: How much does the congestion surcharge contribute to overall revenue during peak hours?

---

## Executive Summary
This project analyses **NYC Taxi & Limousine Commission (TLC) trip data** to uncover patterns that can directly improve fleet profitability. By cleaning and preparing 68K+ trip records (retaining 60K valid trips), I identified revenue drivers across **zones, time, trip types, and passenger behaviour**.  

Key outcomes include:  
- **High-value zones (74 & 75)** driving over 30% of total revenue  
- **Tuesdays and weekday peaks (7–9 AM, 4–6 PM)** delivering the strongest earnings  
- **Short trips (<10 miles)** contributing the majority of revenue due to high volume  
- **Single-passenger rides** dominating revenue share (84%)  
- **Dispatch trips** yielding higher per-trip revenue but lower overall volume  

These findings led to **actionable recommendations** for driver allocation, scheduling, and partnerships that help taxi operators stay competitive against rideshare giants like Uber and Lyft.

---

## Key Question
*How can taxi companies leverage trip data to increase revenue and optimise fleet performance in New York City?*

---

## Data
The analysis uses real-world data from the NYC Taxi & Limousine Commission (TLC). This dataset contains key features of thousands of taxi rides in NYC, such as trip times, locations, fares, payment methods, and more. You can access the dataset [here](https://drive.google.com/drive/folders/1NYHIL-RgVPW-HONz4pdzlcbIChF-c37N).

Key Features:
| Column                     | Description                                                                                               |
| -------------------------- | --------------------------------------------------------------------------------------------------------- |
| `VendorID`                 | Taxi provider (1 = Creative Mobile Technologies, 2 = VeriFone Inc.).                                      |
| `lpep_pickup_datetime`     | Date and time when the trip started.                                                                      |
| `lpep_dropoff_datetime`    | Date and time when the trip ended.                                                                        |
| `passenger_count`          | Number of passengers in the vehicle (driver-entered).                                                     |
| `trip_distance`            | Distance traveled in miles, recorded by the taximeter.                                                    |
| `PULocationID`             | TLC Taxi Zone ID where the trip started.                                                                  |
| `DOLocationID`             | TLC Taxi Zone ID where the trip ended.                                                                    |
| `RateCodeID`               | Final rate code used for the trip (e.g., standard rate, JFK, Newark).                                     |
| `store_and_fwd_flag`       | Indicates whether the trip data was temporarily stored before being sent (Y = Yes, N = No).               |
| `payment_type`             | How the passenger paid (e.g., credit card, cash, dispute).                                                |
| `fare_amount`              | Base fare calculated based on time and distance.                                                          |
| `mta_tax`                  | $0.50 tax applied to trips per New York City regulations.                                                 |
| `improvement_surcharge`    | $0.30 surcharge added to all trips.                                                                       |
| `tip_amount`               | Tip recorded for credit card payments (cash tips not included).                                           |
| `total_amount`             | Total amount charged for the trip (excluding cash tips).                                                  |
| `congestion_surcharge`     | Additional fee applied to trips during peak traffic periods.                                              |
| `ehail_fee`                | Booking fee for e-hail (electronic street-hail) rides.                                                    |
| `tolls_amount`             | Any toll charges applied to the trip.                                                                     |
| `trip_type`                | Indicates whether the trip was street-hail (1) or dispatch (2).                                           |
| `extra`                    | Additional charges such as late-night and rush hour surcharges.                                           |

---

## Data Cleaning
Before diving into the analysis, I first explored the dataset and handled missing values and outliers. This process includes:
- Removing irrelevant columns (e.g., VendorID, tip_amount)
- Imputing missing values logically based on column patterns (e.g., Missing `trip_type` imputed using the most common value per `RateCodeID` to keep fare–trip consistency)  
- Identifying and removing outliers (e.g. Unusually high fares for short trips or zero-distance trips with charges)

After cleaning, I was left with 60,090 valid records (out of 68,211) to analyse.

---

## Summary of Key Findings

### 1. Revenue by Taxi Zones
![Top 10 Pickup Zones](https://drive.google.com/uc?export=view&id=18NwDO7sqXNMIHZfWNaJQnHyzU3W5bYsQ)

#### Top 10 Pickup Locations by Total Revenue
| Rank | PULocationID | Total Revenue ($) |
|------|--------------|-----------------|
| 1    | 74           | 219,658.19      |
| 2    | 75           | 155,197.50      |
| 3    | 166          | 66,434.56       |
| 4    | 95           | 64,417.70       |
| 5    | 41           | 58,649.80       |
| 6    | 43           | 55,544.80       |
| 7    | 82           | 54,893.05       |
| 8    | 244          | 44,746.80       |
| 9    | 97           | 39,277.15       |
| 10   | 7            | 30,756.60       |

![Top 10 Drop-off Zones](https://drive.google.com/uc?export=view&id=1aeuirAdMUsSwqVrRpNjcZuLycgn_lwkV)

#### Top 10 Drop-off Locations by Total Revenue
| Rank | DOLocationID | Total Revenue ($) |
|------|--------------|-----------------|
| 1    | 236          | 45,246.92       |
| 2    | 75           | 40,481.14       |
| 3    | 238          | 38,176.45       |
| 4    | 138          | 37,707.00       |
| 5    | 74           | 36,666.10       |
| 6    | 239          | 30,137.50       |
| 7    | 166          | 28,291.11       |
| 8    | 41           | 27,201.40       |
| 9    | 42           | 26,935.35       |
| 10   | 263          | 26,739.43       |

- **Highest pickup revenue:** Zone 74 ($219,658 which is 19.1% of total revenue) and Zone 75 ($155,197 which is 13.5% of total revenue)  
- **Highest drop-off revenue:** Zone 236 ($45,247 which is 3.9% of total revenue)  
- Zones 74 and 166 appear in both pickup and drop-off lists, indicating high-traffic corridors.

### 2. Revenue by Day of the Week
![Top Day of the Week](https://drive.google.com/uc?export=view&id=1GYcjUypbXLi-DRF3XZDAo4jJdML2LtxV)

#### Total Revenue by Day of the Week
| Day       | Total Revenue ($) |
|-----------|-----------------|
| Monday    | 167,009.36      |
| Tuesday   | 193,347.87      |
| Wednesday | 166,643.68      |
| Thursday  | 175,134.84      |
| Friday    | 169,264.16      |
| Saturday  | 141,832.64      |
| Sunday    | 136,480.24      |

- **Tuesday:** Highest revenue ($193,348 which is 16.8% of total revenue)  
- Weekdays (Monday–Friday) consistently outperform weekends  
- Saturday ($141,833 which is 16.8% of total revenue) and Sunday ($136,480 which is 11.9% of total revenue) show lower revenue  
- Thursday shows a minor mid-week revenue boost

### 3. Hourly Revenue Trends
![Top Hour](https://drive.google.com/uc?export=view&id=1f_UHChKQjzmWevTj-xmrMnjcfpGULblZ)

#### Total Revenue by Hour
| Hour | Total Revenue ($) |
|------|-----------------|
| 0    | 18,176.46       |
| 1    | 15,167.70       |
| 2    | 11,037.20       |
| 3    | 10,554.65       |
| 4    | 7,712.05        |
| 5    | 8,072.54        |
| 6    | 15,250.40       |
| 7    | 40,446.88       |
| 8    | 51,396.04       |
| 9    | 56,079.71       |
| 10   | 59,574.67       |
| 11   | 61,022.05       |
| 12   | 62,125.18       |
| 13   | 66,642.55       |
| 14   | 75,141.13       |
| 15   | 86,646.95       |
| 16   | 95,303.25       |
| 17   | 94,717.68       |
| 18   | 93,401.37       |
| 19   | 71,689.81       |
| 20   | 54,277.35       |
| 21   | 39,072.75       |
| 22   | 31,369.82       |
| 23   | 24,834.60       |

- **Peak hours:** 4 PM–6 PM ($86,647–$95,303 which is 7.5%–8.3% of total revenue)  
- Morning peaks: 7 AM–9 AM ($40,447–$56,080 which is 3.5%–4.9% of total revenue)  
- Lowest revenue: 12 AM–6 AM ($7,712–$18,176 which is 0.7%–1.6% of total revenue)

### 4. Rate Code Revenue
![Top Rate Code](https://drive.google.com/uc?export=view&id=1taBQTvp90ERo1zJDPT1Wrqopm-61BWwo)

#### Total Revenue by Rate Code
| RatecodeID | Rate Code             | Total Revenue ($) |
|------------|---------------------|-----------------|
| 1          | Standard Rate        | 1,112,038.63    |
| 2          | JFK                  | 8,508.90        |
| 3          | Newark               | 1,801.45        |
| 4          | Nassau or Westchester| 5,604.90        |
| 5          | Negotiated Fare      | 21,758.91       |

- **Standard Rate (ID=1):** $1.11M which is 96.6% of total revenue (dominant revenue source)  
- **Negotiated Fares (ID=5):** $21.7K which is 1.9% of total revenue, high-value but low-volume  
- Airport trips (JFK, Newark) and suburban trips contribute minor revenue

### 5. Trip Distance vs. Revenue
![Top Trip Distance](https://drive.google.com/uc?export=view&id=16T2quy6gfA3IEK-JN5_AzteSJBCdguu3)
- Short trips (< 10 miles) generate **most total revenue** due to high volume  
- Long trips (> 20 miles) are less frequent and more variable in revenue

### 6. Passenger Count vs. Revenue
![Top Passenger Count](https://drive.google.com/uc?export=view&id=1_TSX61OYXs5iBuyFPymW6fPyfFGtnzG4)

#### Total Revenue by Passenger Count
| Rank | Passenger Count | Total Revenue ($) |
|------|-----------------|-----------------|
| 1    | 1               | 969,226.79      |
| 2    | 2               | 100,818.60      |
| 3    | 5               | 35,493.65       |
| 4    | 3               | 18,584.20       |
| 5    | 6               | 18,386.75       |
| 6    | 4               | 7,202.80        |

- Single-passenger trips: $969K which is 84.3% of total revenue (dominant)  
- Multi-passenger trips contribute minimally

### 7. Trip Type vs. Revenue
![Top Trip Type](https://drive.google.com/uc?export=view&id=1dMWK1uSCBLtIRCgSWAKcUfut8VlQOOfD)

#### Revenue by Trip Type
| Trip Type | Avg Revenue ($) | Median Revenue ($) | Trip Count | Total Revenue ($) |
|-----------|----------------|------------------|------------|-----------------|
| 1         | 19.11          | 15.95            | 59,142     | 1,130,085.82    |
| 2         | 31.66          | 23.05            | 620        | 19,626.97       |

- **Street-hail trips:** High volume, $1.13M which is 98.3% of total revenue  
- **Dispatch trips:** Higher average revenue ($31.66) but low total revenue ($19.6K which is 1.7% of total revenue)

### 8. Congestion Surcharge by Hour
![Top Hour](https://drive.google.com/uc?export=view&id=1ylJK8GfXOAGe4KrXiDuP44OJUOn4gvh2)

#### Total Congestion Surcharge by Hour
| Pickup Hour | Total Congestion Surcharge ($) |
|------------|-------------------------------|
| 0          | 412.50                        |
| 1          | 349.25                        |
| 2          | 225.50                        |
| 3          | 170.50                        |
| 4          | 107.25                        |
| 5          | 250.25                        |
| 6          | 651.50                        |
| 7          | 1,531.25                      |
| 8          | 2,186.00                      |
| 9          | 2,752.50                      |
| 10         | 2,898.50                      |
| 11         | 2,859.75                      |
| 12         | 2,878.50                      |
| 13         | 2,835.25                      |
| 14         | 3,077.25                      |
| 15         | 3,538.75                      |
| 16         | 3,630.00                      |
| 17         | 3,528.25                      |
| 18         | 3,797.50                      |
| 19         | 2,834.75                      |
| 20         | 2,018.50                      |
| 21         | 1,438.25                      |
| 22         | 1,041.75                      |
| 23         | 759.00                         |

- Peaks in late afternoon (3 PM–6 PM), max $3,797 at 6 PM  
- Lowest overnight (12 AM–5 AM)

---

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

---

## Actionable Recommendations

### 1. Driver Allocation & Scheduling
- Concentrate **20% of fleet** in **East Harlem & Manhattanville** (Zones 74, 75) during **weekday evenings (4–6 PM)** → +8% uplift.  
- Dedicate **10% of fleet** to **morning commutes** in **Zones 74 & 166** on **Mon/Wed/Fri** → +5% uplift.  
- Deploy **8% of fleet** to **business districts** (Zones 41, 43, 95) midday weekdays → +6% uplift.  
- Allocate **6% of fleet** to **weekend evenings** in nightlife zones (41, 43, 82).  
- Cut **overnight shifts** to ~2% of fleet (12–6 AM), as these hours generate <2% revenue.  

### 2. Fleet Composition & Trip Strategy
- Prioritise **sedans** for short, single-passenger rides (<10 miles).  
- Reserve larger vehicles for **dispatch/airport trips** (Zones 236, 238, 244).  
- Focus on **short-trip, high-turnover strategy** for higher fleet utilisation.  

### 3. Revenue & Pricing Optimisation
- Apply **dynamic pricing** during weekday evening peaks.  
- Offer **weekend ride incentives** to offset natural demand dips.  
- Scale up **dispatch trips & negotiated fares** to increase share of high-value rides.  

### 4. Operational Efficiency & Route Planning
- Use **geo-fencing** to hold drivers within top-performing zones during peaks.  
- Dynamically reallocate drivers between **business (day)** and **residential zones (evening)**.  
- Reduce idle time by trimming low-revenue overnight hours.  

### 5. Customer Experience & Marketing
- Market **off-peak discounts** to smooth demand.  
- Create **loyalty programs** for frequent commuters.  
- Promote **pre-booked dispatch trips** for premium passengers.  

### 6. Strategic Partnerships & Expansion
- Build partnerships with **business districts, event venues, and airports**.  
- Expand **corporate accounts** for weekday commuters.  
- Explore **nightlife partnerships** to maximise weekend evening demand.

---

## Driver Allocation Plan (Optimised)

| Plan Name                                | Days                  | Time Slot      | Zones            | % Fleet | Strategy Multiplier | Expected Uplift |
|------------------------------------------|-----------------------|----------------|------------------|---------|---------------------|-----------------|
| Evening_EastHarlem_Manhattanville        | Tue, Thu              | Evening (4–6)  | 74, 75           | 12%     | 1.08                | +8%             |
| Morning_Commute_Highzones                | Mon, Wed, Fri         | Morning (7–9)  | 74, 166          | 10%     | 1.05                | +5%             |
| Midday_BusinessDistricts_Weekdays        | Mon–Fri               | Daytime        | 95, 41, 43       | 8%      | 1.06                | +6%             |
| Weekend_Boost_Evenings                   | Sat, Sun              | Evening        | 41, 43, 82       | 6%      | 1.04                | +4%             |
| ShortTrip_Priority_AllDays               | All Days              | Day + Evening  | 74, 166, 95, 41, 43, 82 | 10% | 1.07                | +7%             |
| Dispatch_Negotiated_Focus                | All Days              | Day + Evening  | 244, 236, 238    | 4%      | 1.10                | +10%            |
| CongestionPeak_Target                    | Mon–Fri               | Evening (4–6)  | 74, 75, 166      | 5%      | 1.05                | +5%             |
| OffPeak_Reduction                        | All Days              | Night (12–6)   | All Zones        | 2%      | 1.00                | Neutral         |

**Note:** Remaining ~43% of fleet follows baseline allocation to maintain citywide coverage.  
**Clarification:** CongestionPeak_Target is an **add-on incentive strategy**, not double-counted with Evening_EastHarlem.  

---

## Projected Results

- **Baseline:** Avg. revenue per driver per shift = **$1,239.35**  
- **With allocation plan:** +37.47% uplift → **$1,703.70**
- **Per-driver gain:** +$464 per shift  

**Annualised Impact (1,000 drivers × 250 shifts/year):**  
= $464 × 250 × 1,000  
= **+$116M additional annual revenue potential**

---

## Impact

The optimised driver allocation plan delivers clear, quantifiable results:  

- **Revenue Growth**: Average revenue per driver per shift rises from **$1,239.35 → $1,703.70** (**+37.47% uplift**).  
- **Driver Earnings**: Each driver gains approximately **+$464 per shift**, directly boosting income and satisfaction.  
- **Annual Company Impact**: With **1,000 drivers × 250 shifts/year**, the plan generates **+$116M additional annual revenue potential**.  
- **Operational Efficiency**: Focused coverage in demand-heavy zones (East Harlem, Midtown business districts, weekend hotspots) while reducing oversupply during off-peak hours.  
- **Diversified Revenue**: The **Dispatch_Negotiated_Focus** strategy delivers up to **+10% uplift** in select partnerships, adding resilience beyond standard fares.  

This data-driven driver allocation strategy maximises revenue, enhances driver engagement, and positions traditional taxi operators to stay competitive in a rideshare-dominated market.  

---

- Presentation: [NYC TLC Presentation](https://drive.google.com/file/d/1dkPA2uDWO3S5fQpFm9UtwfnP4AgkNUAC/view?usp=sharing)
- Tableau Dashboard: [NYC TLC Dashboard](https://public.tableau.com/app/profile/risma.w.p./viz/NYCTLCDashboard_17562651808670/Dashboard#1)
