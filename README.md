# "Tesla Facility Insights Dashboard"

### Dashboard Link : https://github.com/bora23-04/-Tesla-Facility-Insights-Dashboard-on-power-bi.git

## Problem Statement

To analyze and visualize the distribution, growth, and operational details of Tesla facilities globally, enabling data-driven decision-making for resource allocation, network expansion, and performance optimization.

The objective is to build an interactive dashboard that provides insights into Tesla’s global infrastructure, including the distribution of Superchargers, Stores, and Service Centers across regions and facility growth over time. The dashboard aims to answer the following key questions:

1. What is the overall count and proportion of facility types (e.g., Superchargers, Stores, facility count)?
2. How are Tesla facilities distributed geographically across regions?
3. What trends can be observed in the growth of Tesla’s infrastructure over the years?
4. Which regions or facility types dominate the network, and where is Tesla underrepresented?
5. How does the facility distribution contribute to Tesla’s operational goals?

### Steps followed 

- Step 1 :  Understand the Data
Datasets Used:

IEA Global EV Data 2024.csv

Tesla Stations and Stores.csv

Objective:
Analyze Tesla’s facility distribution, growth trends, and type-based performance.

Initial Data Assessment:
Reviewed columns like rundate, type, region, latitude, longitude, and title.
Identified key metrics to visualize: facility count, facility growth over time, and geographical distribution.

- Step 2 : 
Import Data into Power BI

1.Open Power BI Desktop.

2.Import the datasets using the Get Data option and select CSV files.

3.Check the preview of the data and load it into Power BI.

- Step 3 : 
Data Cleaning and Transformation

Power Query Editor:

1.Removed unnecessary columns to streamline the dataset.

2.Parsed the rundate column to extract Year and Month using Transform > Date > Year/Month.

3.Renamed columns for better readability.

4.Handled null values or inconsistencies (e.g., missing regions or types).

5.Ensured latitude and longitude were in numeric format for mapping.

- Step 4 : 
Create Measures Using DAX

Created custom measures for insights:

-Total Facility Count:

Facility count = COUNTROWS(SUMMARIZE('tesla_stations_and_stores','tesla_stations_and_stores'[type]))

-cumulative value:

cumulative value = CALCULATE(SUM('IEA Global EV Data 2024'[value]),FILTER(ALL('IEA Global EV Data 2024'[year]),'IEA Global EV Data 2024'[year]<=MAX('IEA Global EV Data 2024'[year])))

-Region share:

Region_share = DIVIDE(SUM('IEA Global EV Data 2024'[value]),CALCULATE(SUM('IEA Global EV Data 2024'[value]),ALL('IEA Global EV Data 2024'[region])))

-YOY growth:

YOY_growth = DIVIDE(SUM('IEA Global EV Data 2024'[value]) - CALCULATE(SUM('IEA Global EV Data 2024'[value]),PREVIOUSYEAR('IEA Global EV Data 2024'[year])),CALCULATE(SUM('IEA Global EV Data 2024'[value]),PREVIOUSYEAR('IEA Global EV Data 2024'[year])),0)

- Step 5 :
Build Visualizations

Key Visuals Added:
Decomposition Tree: Start with total facilities and break it down by region, then by type.

Card Visuals with Insights: 

Shows the IEA value according to year.

Show the region with the most facilities.

Map Visual: Plotted Tesla facilities geographically using latitude and longitude.

Treemap: Showed the proportion of facility types and their contributions.

Slicers: Added interactive slicers for filtering city, region, or year.

Pie chart: Compare the share of facilities in different regions.

Line chart:using region and cumulative value.

Map visual: Compare the share of facilities in different regions.

Clustered Bar or Column Chart: find count of isopening by region, facility count by region and top 10 company.


        
# Snapshot of Dashboard (Power BI Service)
![Screenshot 2024-12-06 150817](https://github.com/user-attachments/assets/83aa9e4b-c50e-44fb-ab15-16e7ed4fd3fc)


 ![Screenshot 2024-12-06 150908](https://github.com/user-attachments/assets/0fc2f2ad-9b7b-4bc8-b34e-b9bd3be232f8)



