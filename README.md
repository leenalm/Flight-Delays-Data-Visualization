## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Data Wrangling & Preparation](#2-data-wrangling--preparation)
3. [Univariate Exploration](#3-univariate-exploration)
4. [Bivariate Exploration](#4-bivariate-exploration)
5. [Multivariate Exploration](#5-multivariate-exploration)
6. [Key Insights & Operational Implications](#6-key-insights--operational-implications)
7. [Tools & Libraries](#7-tools--libraries)
8. [Skills Demonstrated](#8-skills-demonstrated)
   
# 📊 Flight Delays Data Visualization

This repository contains a comprehensive exploration and analysis of U.S. domestic flight delays, cancellations, and diversions using the `T_ONTIME_REPORTING.csv` dataset. The project investigates how departure time, day of the week, and flight distance influence flight performance.  

---

## 1️⃣ Project Overview  

**Author:** Leen Almudaifer  

The dataset consists of 539,747 flight-level records including:  

- Flight schedules (`FL_DATE`, `DEP_TIME`, `ARR_TIME`, `DISTANCE`)  
- Performance measures (`DEP_DELAY`, `ARR_DELAY`, `ARR_DELAY_NEW`)  
- Operational outcomes (`CANCELLED`, `DIVERTED`)  

The goal is to analyze patterns in delays, early/late arrivals, cancellations, and diversions, and to examine relationships with departure hour, day of the week, and flight distance.

---

## 2️⃣ Data Wrangling & Preparation  

- **Convert date and time:** `FL_DATE` → datetime, `DEP_TIME`/`ARR_TIME` → HH:MM strings  
- **Extract features:**  
  - `DEP_HOUR` & `ARR_HOUR` from times  
  - `DAY_OF_WEEK` from `FL_DATE`  
- **Split delays:** `ARR_DELAY` → `ARR_Late` (positive) and `ARR_Early` (negative)  
- **Categorical recoding:** Binary columns like `CANCELLED` and `DIVERTED` recoded to `"Yes"`/`"No"` for plots  

**Dataset Shape & Key Columns:**  

| Column | Description |
|--------|-------------|
| FL_DATE | Flight date |
| ORIGIN | Departure airport |
| DEST | Destination airport |
| DEP_TIME | Departure time (HH:MM) |
| DEP_DELAY | Departure delay (minutes) |
| ARR_TIME | Arrival time (HH:MM) |
| ARR_DELAY | Arrival delay (minutes) |
| ARR_Late / ARR_Early | Late / Early arrivals separated |
| CANCELLED | Flight cancelled (0/1 → No/Yes) |
| DIVERTED | Flight diverted (0/1 → No/Yes) |
| DISTANCE | Flight distance (miles) |

---

## 3️⃣ Univariate Exploration  

- **Flights by day of month:** Early January shows elevated flight counts, likely due to New Year travel.  
- **Cancellations:** Rare events; most flights are not cancelled. Binary recoding applied for visualization.  

---

## 4️⃣ Bivariate Exploration  

- **Departure Hour vs Late/Early Arrivals:**  
  - Early-morning flights (<4–5 AM) show higher late arrivals  
  - Early arrivals peak between 4–10 AM  
- **Diversion impact:** Diverted flights tend to depart slightly later than non-diverted flights  
- **Day-of-week patterns:**  
  - Thursdays & Fridays: highest late arrivals and cancellations  
  - Saturdays: lowest flight volume and delays  

---

## 5️⃣ Multivariate Exploration  

- **Average delay by DEP_HOUR and DAY_OF_WEEK:**  
  - Late arrivals concentrated early morning (<5 AM)  
  - Early arrivals peak between 4–5 AM  
- **Departure hour vs distance vs arrival status:**  
  - Short flights (<3,000 miles) mostly on time  
  - Longer flights more prone to delays  
  - Early departures (<4 AM) are likely to be late even for short distances  

**Observations:**  
- Multiple features interact: departure time, distance, and day-of-week jointly affect arrival delays  
- Operational trends (peak days, flight length) reinforce the patterns in late arrivals  
- Visualizations clarify temporal and operational impacts on punctuality  

---

## 6️⃣ Key Insights & Operational Implications  

1. Flights departing before 4 AM are more prone to delays due to night-time operational constraints.  
2. Longer flights have a higher probability of being late; flights under ~3,000 miles generally arrive on time.  
3. Peak travel days (Thursdays & Fridays) have higher cancellations, aligning with delay patterns.  
4. Departures between 4–8 AM are more likely to arrive early, benefiting from lighter traffic.  
5. Departure hour and flight distance are critical factors for predicting punctuality; combining them improves operational planning.  
6. Airlines can optimize staffing, ground operations, and buffer times for early and late departures to mitigate delays.  

---

## 7️⃣ Tools & Libraries  

- Python (pandas, NumPy)  
- Data Visualization: matplotlib, seaborn  
- Jupyter Notebook

---

## 8️⃣ Skills Demonstrated

1. Data cleaning and preparation for large datasets

2. Feature engineering for time-based analysis

3. Univariate, bivariate, and multivariate visualizations

4. Understanding operational patterns and performance metrics

5. Interpretation of delays, cancellations, and diversions for actionable insights
