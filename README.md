# Archana--Project-2---Luxury-housing-sales-analysis
Luxury Housing Sales Analysis – Bengaluru

📌 Project Overview
---------------------------------------------------------------------------------------------------------------------------------------------------------------
The Luxury housing market is highly competitive and price-sensitive. Developers, real-estate agents, and buyers need data-driven insights to determine which features increase property value, understand buyer preferences, and forecast pricing trends

🎯 Business Objectives & Use Cases
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Market Intelligence: Identify high-performing localities, builder-wise trends, and configuration demand shifts.

Sales Optimization: Use booking and inquiry data to uncover drop-off patterns.

Buyer Persona Building: Use Buyer Type and Comment sentiment to group and understand buyer personas.

Competitive Pricing: Analyze pricing strategies across builders and market segments.

Amenity Score & Conversion: Determine the correlation between amenities and booking rates.

Quarterly Trend Tracking: Track real estate patterns across fiscal quarters to aid investment decisions.

📌 Tech Stack
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Python → Pandas, NumPy → Data cleaning, feature engineering, exploratory analysis

SQL→ sqlalchemy  → Data warehousing, schema design, and advanced querying

Visualization → Power BI (DAX, KPIs, Geo-maps)  → Interactive dashboard with KPIs, market insights, and visual storytelling

Domain → Real Estate Analytics

🐍 Python – Data Preparation & Feature Engineering
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Cleaned 100k+ raw records (removed duplicates, nulls, and inconsistencies). Filled missing numerical values using median or mean depending on the column (e.g., Unit_Size_Sqft → mean, Amenity_Score → mean, Ticket_Price_Cr → median). Normalized string columns: Micro_Market, Configuration, Ticket_Price_Cr. Standardized configuration labels: '3 BHK' → '3BHK', '4BHK+' → '4BHK+', etc. Handled missing comments: Buyer_Comments filled with 'No Comment'. Removed(1000) duplicate rows to ensure dataset consistency.

Engineered new features: Price_per_Sqft = (Ticket_Price_Cr * 10000000) / Unit_Size_Sqft Quarter_Number = Extracted from Purchase_Quarter Booking_Flag = 1 if Status == 'Booked' else 0

📂 Output → A clean, analysis-ready dataset.

🧠 SQL – Data Warehousing & Analysis
---------------------------------------------------------------------------------------------------------------------------------------------------------------
Created a SQLAlchemy database 'LUXURY_HOUSING_PROJ' Inserted cleaned dataset into table luxury_properties using SQLAlchemy Validated data insertion with COUNT, GROUP BY, and AVG queries Ensured normalized structure for efficient querying

Ran validation & analytical queries, e.g.:

#Total data count in datasets
query0="""SELECT COUNT(*) AS total_data FROM luxury_housing_sales_analysis;"""
res_0=pd.read_sql(query0,engine)
res_0


Connected dashboard to SQLAlchemy database.
---------------------------------------------------------------------------------------------------------------------------------------------------------------

📊 Power BI – Visualization & Insights

<img width="1152" height="631" alt="png1" src="https://github.com/user-attachments/assets/8180a1cd-ab52-41a5-9a17-cbdc6ce36b54" />

<img width="1137" height="637" alt="png2" src="https://github.com/user-attachments/assets/102c4860-efc2-442b-a8d9-629ae6ca5c5b" />

<img width="1127" height="640" alt="png3" src="https://github.com/user-attachments/assets/43988007-0254-4e3d-9ade-e9197328b617" />

Key Insights from the Dashboard
---------------------------------------------------------------------------------------------------------------------------------------------------------------
The dashboard explores ten main questions about luxury housing bookings and sales performance:
**1. Quarterly Booking Changes Across Micro-Markets**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A line chart titled "Count of Booking Flag by Quarter_Number and Micro_Market".

**Insight:** The chart tracks the volume of bookings ("Count of Booking Flag") over different quarters for specific micro-markets such as Bannerghatta, Bellary Road, Domlur, Electronic City, Hebbal, and Hennur Road.
The data visualization suggests fluctuations in bookings across these specific micro-markets quarter by quarter, likely showing which areas saw growth or decline at specific times. The exact trends for each market are visually represented by the intersecting lines.

**2. Correlation Between Amenity Score and Booking Success Rate**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A scatter plot titled "Average of Amenity_Score and Count of Project Name by Booking Success_Rate".

**Insight:** This visualization aims to determine if projects with higher amenity scores have a better booking success rate.
A single data point is visible around the middle of the graph (**approx. 0.5 Booking Success Rate and 4.0 Average Amenity Score**). This point represents the performance of a group of projects ("Count of Project Name"). The position of this point relative to the axes would indicate the current correlation (if any) shown by the underlying data set.

**3. Top Builders by Total Sales and Average Ticket Size**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A clustered bar chart titled "Sum of Ticket Price Cr and Average of Ticket Price_Cr by Builder".
 **Insight:**: This chart ranks builders by two metrics: total revenue generated ("Sum of Ticket Price Cr") and the average value of a single sale ("Average of Ticket Price_Cr").
Builders listed include Prestige, Total Environment, L&T Realty, SNN R, Godrej, Puravankara, and Sobha.
**Prestige** appears to have the highest total ticket sales (the largest blue bar), followed by Total Environment.
The chart allows for a comparison of whether top-selling builders achieve volume (high sum) or high value per sale (high average), revealing market positioning strategies.

**4. Highest and Lowest Booking Conversion Rates by Micro-Market**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A horizontal stacked bar chart titled "%GT Count of Booking Flag by Micro_Market and Booking Flag".

**Insight:** This visualization breaks down the success rate of bookings (Booked vs. Not Booked) as a percentage of total attempts per micro-market.
The chart clearly shows which micro-markets successfully convert the highest percentage of inquiries into confirmed bookings versus those with a high rejection or cancellation rate ("Not Booked" segment). Specific micro-markets can be identified as top performers based on the length of their "Booked" bar segment.

**5. Housing Configurations**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A donut chart (a variation of a pie chart) labeled "Sum of Booking_Success_Rate by Configuration".

**Insight:** The **3BHK** configuration is the most in-demand, accounting for a 33.30% booking success rate. The **5BHK** configuration has the lowest rate (13.54%), while the 4BHK and other configurations fall in between. 

**6. Builder Market Dominance**
   ---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A table with builders listed by quarterly performance.

**Insight:** Data is presented for builders like Brigade, Embassy, Godrej, Prestige, and Sobha across four quarters. **Prestige and Total Environment** appear to have the highest total booking success rates over the four quarters displayed. 

**7. Sales Channels**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** Two bar charts (one stacked, one clustered) showing "Count of Sales Channel" and "Count of Sales Channel by Sales_Channel and Booking Flag".

**Insight:** On the [site/channel] and Others are the primary sales channels.
The booking success rate (indicated by the blue segment) is roughly equal for both 'Booked' and 'Not Booked' statuses across all channels **(around 50.18% to 49.87%)**, suggesting consistent performance across these channels. 

**8. Possession Status & Buyer Type**
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Visualization:** A clustered bar chart for "Sum of Booking Success_Rate by Possession Status and Buyer Type".

**Insight:** The data compares booking success rates across different buyer types (CXO, HNI, NRI, Other, Startup Founder) based on whether the property is 'Under construction' or 'Ready to move' (implied by the two distinct bar clusters). **HNI and NRI** buyers have slightly higher success rates across both categories.

9.Most Housing projects Concentrated in bangalore
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Insights:** Map visualization of most Housing projects within Bangalore is **Central Areas and the East Areas**  have established luxury 

10.Top 5 Builders: 
---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Insights:** The top five builders in terms of revenue and booking success are ranked as follows:

**Prestige**: Highest revenue and booking success .

**Total Environment**: Second highest revenue and booking success.

**L&T Realty**: Third highest revenue and booking success .

**SNN Raj**: Fourth highest revenue and booking success .

**Godrej**: Fifth highest revenue and booking success

**DAX MEASURE:**
--
Booking_Success_Rate = 
DIVIDE(
    COUNTROWS(FILTER('public luxury_housing_sales_analysis','public luxury_housing_sales_analysis'[Booking_Flag] = "Booked")),
    COUNTROWS('public luxury_housing_sales_analysis')
)

📌 Results
---------------------------------------------------------------------------------------------------------------------------------------------------------------
✔ 100,000+ rows cleaned, standardized, and stored in SQL. ✔ Power BI dashboard with interactive, filter-based insights. ✔ Builder, buyer, and market-level intelligence for strategic decisions. ✔ Replicates a real-world BI pipeline for real estate analytics.


