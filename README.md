# 🛺 Rapido Ride Service – Business Analysis Dashboard

## 📊 Project Overview

This project is an interactive **Power BI Business Analysis Dashboard** built to analyze ride-hailing service performance using Rapido ride data.

The project demonstrates how raw ride-level transactional data can be transformed into meaningful business insights using **data cleaning, data modelling, DAX, KPI development, interactive filters, and data visualization**.

The dashboard focuses on understanding the operational, financial, vehicle/service, location, and payment performance of an online ride-booking platform.

The project is designed as a **Data Analyst / Business Analyst portfolio project** to demonstrate practical skills in business intelligence and data-driven decision-making.

---

# 🎯 Business Objective

The main objective of this project is to analyze ride-booking data and understand the key factors affecting the performance of a ride-hailing business.

The dashboard helps answer questions such as:

- How many rides are booked?
- How many rides are successfully completed?
- How many rides are cancelled?
- What is the completion rate?
- What is the cancellation rate?
- What is the total revenue?
- What is the average fare per ride?
- What is the total distance travelled?
- Which vehicle/service type generates the highest revenue?
- Which vehicle/service type has the highest ride volume?
- Which vehicle type has the highest completed rides?
- Which vehicle type has the highest cancelled rides?
- Which pickup location has the highest number of completed rides?
- Which destination has the highest number of completed rides?
- How does completed and cancelled ride volume change by day?
- Which payment methods are most commonly used?
- How is ride volume distributed across different vehicle types?
- What are the major operational and financial insights from the available data?

---

# 📁 Dataset

The project uses ride-level transactional data representing bookings made through a ride-hailing platform.

The dataset contains approximately:

- **50,000 total rides**
- **44,964 completed rides**
- **5,036 cancelled rides**
- Approximately **15 days of data across three months**

The dataset was used to perform operational, financial, vehicle, payment, and location-level analysis.

> **Note:** The dataset is used for educational and portfolio purposes and should not be considered official or real-time Rapido business data.

---

# 🧾 Dataset Columns

The main `rides_data` table contains ride-level information.

| Column | Description |
|---|---|
| `ride_id` | Unique identifier for each ride |
| `date` | Date of the ride |
| `time` | Time of the ride |
| `source` | Pickup/source location |
| `destination` | Destination location |
| `services` | Vehicle/service type selected |
| `ride_status` | Status of the ride, such as Completed or Cancelled |
| `payment_method` | Payment method used by the customer |
| `distance` | Distance travelled during the ride |
| `duration` | Duration of the ride |
| `ride_charge` | Ride/base charge |
| `misc_charge` | Additional or miscellaneous charges |
| `total_fare` | Total fare/revenue generated from the ride |

---

# 🧹 Data Preparation

The data was prepared and transformed using Power BI and Power Query.

The preparation process included:

- Understanding the structure of the raw dataset
- Checking available columns and data types
- Handling data-quality issues
- Creating calculated columns
- Creating DAX measures
- Extracting month information from the date column
- Creating business KPIs
- Creating vehicle/service categories
- Creating a separate vehicle image table
- Formatting numerical and currency values
- Creating completion and cancellation metrics
- Creating location-based metrics
- Creating payment-method analysis
- Preparing data for interactive Power BI visuals

---

# 🏗️ Data Modelling

The main table used in the dashboard is:

`rides_data`

This table contains the transactional ride-level data.

A supporting table named:

`vehicle_image`

was also created to associate each vehicle/service type with its corresponding image.

The `vehicle_image` table contains:

| Column | Purpose |
|---|---|
| `services` | Vehicle/service category |
| `images` | URL of the vehicle image |

Example:

| services | images |
|---|---|
| auto | auto.png |
| bike | bike.png |
| cab economy | cab.png |
| parcel | parcel.png |

The vehicle images were uploaded to the GitHub repository and hosted through GitHub URLs so that Power BI could use them as image URLs.

This was used to improve the visual appearance of the dashboard and create vehicle/service selection buttons containing images.

---

# 📐 Key DAX Measures

Several DAX measures were created to calculate important business KPIs.

## Total Rides

```
Total Rides =
COUNT(rides_data[ride_id])
```
## Completed Rides
```
Completed Rides =
CALCULATE(
    COUNT(rides_data[ride_id]),
    rides_data[ride_status] = "Completed"
)
```
## Cancelled Rides
```
Cancelled Rides =
CALCULATE(
    COUNT(rides_data[ride_id]),
    rides_data[ride_status] = "Cancelled"
)
```
## Completion Rate
```
Completion Rate =
DIVIDE(
    [Completed Rides],
    [Total Rides]
)
```
## Cancellation Rate
```
Cancellation Rate =
DIVIDE(
    [Cancelled Rides],
    [Total Rides]
)
```
## Total Revenue
```
Total Revenue =
SUM(rides_data[total_fare])
```
## Average Fare
```
Average Fare =
AVERAGE(rides_data[total_fare])
```
## Total Distance
```
Total Distance =
SUM(rides_data[distance])
```
# 📌 Dashboard KPIs

The dashboard contains the following major KPIs:

| KPI	| Value |
| --- | --- |
| Total Rides | 50K |
| Completed Rides	| 45K |
| Cancelled Rides	| 5K |
| Completion Rate	| 89.93% |
| Cancellation Rate	| 10.07% |
| Total Revenue	| ₹24.61M |
| Average Fare	| ₹547.39 |
| Total Distance	| 1.28M |
| Average Ride Distance	| 25.53KM |

These KPIs provide a quick overview of the operational and financial health of the ride-hailing business.

# 🖥️ Dashboard Pages

The Power BI report contains four major pages:

- Home
- Overview
- Vehicle
- Finance

## 🏠 1. Home Page

The Home page acts as the landing page of the dashboard.

It contains:

- Rapido branding
- Project title
- Business description
- Hero/illustration image
- Page navigation
- Navigation buttons

The page provides a simple introduction before users move into the detailed analysis.

### Navigation Buttons

The dashboard uses page navigator buttons for:

- Home
- Overview
- Vehicle
- Finance

This allows users to easily move between different analytical sections.

## 📊 2. Overview Page

The Overview page provides a high-level view of the ride-hailing business.

It contains:

- Completion Rate
- Cancellation Rate
- Total Revenue
- Total Rides
- Completed Rides
- Cancelled Rides
- Total Distance
- Average Fare
- Completed vs Cancelled Rides by Day
- Revenue by Vehicle Type
- Total Rides by Vehicle Type
- Top Pickup Location
- Top Destination

### 📈 Completed Rides vs Cancelled Rides by Day

A column chart was created to compare:

- Completed rides
- Cancelled rides

on a daily basis.

#### Business Purpose

This visual helps identify:

- Daily ride demand
- Daily completed rides
- Daily cancellations
- Fluctuations in operational performance
- High and low activity days

This can help identify whether cancellation behavior changes during periods of high ride demand.

### 💰 Revenue by Vehicle Type

A bar chart was created to compare total revenue generated by different vehicle/service types.

|Vehicle Type	| Revenue|
|---|---|
|Bike	| ₹9.82M|
|Auto	| ₹6.10M|
|Cab Economy	| ₹5.01M|
|Parcel	| ₹3.69M|

#### Key Observation

Bike is the highest revenue-generating service category.

Bike generates approximately ₹9.82M, which is significantly higher than the other service categories.

### 🚘 Total Rides by Vehicle Type

A donut chart was created to show the contribution of each vehicle/service type to total ride volume.

Approximate distribution:

|Vehicle Type	| Share of Total Rides|
|---|---|
|Bike	| 40.02%|
|Auto	| 24.65%|
|Cab Economy	| ~20%|
|Parcel	| ~15%|

#### Key Observation

Bike accounts for the largest share of total rides.

This makes bike service an important contributor to overall ride volume and revenue.

### 📍 Top Pickup – Completed Rides

A KPI/card visual was created to identify the pickup location with the highest number of completed rides.

Dashboard Result

Kothanur Landing – 20 completed rides

This metric helps identify locations with comparatively higher completed-ride demand.

### 📍 Top Destination – Completed Rides

A KPI/card visual was created to identify the destination with the highest number of completed rides.

Dashboard Result

Gottigere Landing – 21 completed rides

This can help identify locations that are frequently used as destinations.

## 🚗 3. Vehicle Page

The Vehicle page focuses on comparing performance across different vehicle/service types.

The page contains a detailed vehicle performance table.

### 📋 Vehicle Performance Table
|Vehicle Type	| Total Rides	| Total Revenue	| Completed Rides	| Cancelled Rides	| Average Fare	| Average Ride Distance|
|---|---|---|---|---|---|---|
|Bike	| 20,012	| ₹9,820,504.54	| 17,955	| 2,057	| ₹546.95	|25.46|
|Auto	| 12,327	|₹6,099,731.32	| 11,114	| 1,213	| ₹548.83	| 25.60|
|Cab Economy	| 10,202	| ₹5,006,233.04	| 9,148	| 1,054	| ₹547.25	|25.50|
|Parcel	| 7,459	| ₹3,686,514.15	| 6,747	| 712	| ₹546.39	| 25.64|
|Total	| 50,000	| ₹24,612,983.05	| 44,964	| 5,036	| ₹547.39	| 25.53|

### 📊 Active Rides by Vehicle Type

A vehicle-level visual was created to compare ride volume across the different services.

The ranking by ride volume is:

#### Bike > Auto > Cab Economy > Parcel

#### Business Insight

Bike has the highest ride volume and is therefore the most frequently used service in the analyzed dataset.

## 💳 4. Finance Page

The Finance page focuses on revenue and payment-method analysis.

It contains:

- Revenue-related KPIs
- Payment-method analysis
- Payment contribution
- Financial performance indicators
### 💰 Total Revenue

The dashboard reports total revenue of approximately:

₹24.61M

This represents the total fare generated across the analyzed ride dataset.

### 💳 Payment Method Analysis

The dataset contains several digital payment methods.

The dashboard analyzes:

- Paytm
- GPay
- Amazon Pay
- QR Scan
- Missing/blank payment records

Approximate distribution:

|Payment Method	|Ride Count|
|---|---|
|Paytm	| 11.32K|
|GPay	| 11.27K|
|Amazon Pay	| 11.23K|
|QR Scan	| 11.16K|
|Missing/Blank	| 5.04K|

#### Key Observation

The major digital payment methods have relatively similar usage.

This indicates that customers are distributed across multiple payment methods rather than depending heavily on a single option.

##🎨 Dashboard Design

The dashboard uses a Rapido-inspired visual design.

Main design elements include:

- Yellow-based theme
- Black typography
- Rounded KPI cards
- Vehicle illustrations
- Vehicle image buttons
- Page navigation buttons
- Interactive slicers
- Clean charts
- Consistent visual hierarchy
- Business-focused layout

The Home page uses a large hero illustration to create a visually engaging landing page.

The dashboard was designed to balance visual appeal with business readability.

## 📈 Visualizations Used

The dashboard uses different Power BI visual types for different analytical purposes.

### KPI / Card Visuals

Used for:

- Total Rides
- Completed Rides
- Cancelled Rides
- Total Revenue
-  Average Fare
- Total Distance
- Completion Rate
- Cancellation Rate
- Top Pickup
- Top Destination

### Column Chart

Used for:

Completed Rides vs Cancelled Rides by Day

### Bar Chart

Used for:

Revenue by Vehicle Type

### Donut Chart

Used for:

Total Rides Contribution by Vehicle Type

and

Payment Method Contribution

### Table Visual

Used for:

Vehicle Performance Details

The table compares:

- Total rides
- Revenue
- Completed rides
- Cancelled rides
- Average fare
- Average ride distance

### Payment Analysis Visual

Used to compare the distribution of rides across payment methods.

## 🔎 Key Business Insights

### 1. Strong Completion Performance

The overall completion rate is:

89.93%

This indicates that the majority of booked rides were successfully completed.

### 2. Cancellation Rate

The cancellation rate is:

10.07%

Approximately one out of every ten rides was cancelled.

This provides an opportunity to investigate the underlying reasons for cancellations.

### 3. Bike is the Strongest Service Category

Bike has the highest:

Total ride volume
Completed rides
Revenue contribution
Share of total rides

Bike recorded:

20,012 total rides

and approximately:

₹9.82M revenue

Therefore, bike service is the strongest category in this dataset.

### 4. Ride Volume is a Major Revenue Driver

Bike has both the highest ride volume and highest revenue.

This suggests that the difference in total revenue between vehicle types is strongly influenced by ride volume.

### 5. Average Fare is Relatively Consistent

Average fare across vehicle types is approximately:

₹546–₹549

This indicates that average fares are relatively similar between services.

Therefore, the large difference in total revenue appears to be driven more by ride volume than by major differences in average fare.

### 6. Average Ride Distance is Consistent

Average ride distance across vehicle types is approximately:

25.5

This suggests that the analyzed services have relatively similar trip lengths.

### 7. Payment Methods are Relatively Balanced

Paytm, GPay, Amazon Pay, and QR Scan have relatively similar ride volumes.

This indicates that customers are using multiple digital payment options.

### 8. Missing Payment Data

Approximately:

5K records

have missing payment-method information.

This should be addressed as part of data-quality improvement before using payment analysis for important business decisions.

### 9. High-Demand Locations

The dashboard identifies:

Top Pickup: Kothanur Landing – 20 completed rides

Top Destination: Gottigere Landing – 21 completed rides

These locations can be analyzed further to understand demand patterns.

## 💡 Business Recommendations

### 1. Focus on Bike Service

Bike is the largest contributor to both ride volume and revenue.

The business could investigate opportunities to:

- Increase bike availability
- Reduce customer waiting time
- Improve driver availability
- Optimize driver allocation
- Maintain service quality during peak periods

### 2. Investigate Ride Cancellations

With a cancellation rate of 10.07%, cancellation behavior should be analyzed further.

Cancellation analysis could be segmented by:

- Vehicle type
- Location
- Time
- Day
- Source
- Destination
- Payment method

This could help identify the main causes of cancellations.

### 3. Improve Payment Data Quality

Missing payment-method records should be investigated.

Possible improvements include:

- Mandatory payment-method capture
- Data validation
- Standardization of payment categories
- Better handling of null values
- Data-quality monitoring

### 4. Optimize High-Demand Locations

High-demand pickup and destination locations can be used to improve:

- Driver allocation
- Vehicle availability
- Customer waiting time
- Promotional campaigns
- Local marketing
- Demand forecasting

### 5. Analyze Service-Level Performance

Although bike has the highest volume, each service can be analyzed separately to understand:

- Completion rate
- Cancellation rate
- Revenue contribution
- Average fare
- Average distance

This can help determine where operational improvements are required.
