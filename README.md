# DATA-512-Wildfire-Final-Project

## Project Goal 
This is an analysis of wildfires and how the smoke from wildfires affects the cities near them. I am running this analysis for Klamath Falls, Oregon. Klamath Falls is a city in southern Oregon, USA having a picturesque setting amid mountains and lakes. I will be working on finding how wildfires impact the healthcare system of Klamath Falls.
The main inspiration behind this project is that more frequently summers in the western US have been characterized by wildfires with smoke billowing across multiple western states. My research on the impact of wildfires on healthcare resources in Klamath Falls addresses a real and pressing issue. Wildfires, with their increasing frequency and intensity, have far-reaching consequences on communities, and the effects on public health are a critical aspect. My analysis of the correlation between wildfires, increased smoke levels, declining air quality, and the subsequent strain on healthcare resources is relevant and contributes valuable insights.


## Datasets

1. A geojson file dataset collected and aggregated by the US Geological Survey. This contains fire polygons for wildfires that have occurred across the USA. The file can be found here- https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81

2. An API accessing sample notebook to obtain the Air Quality Estimates for regions in the USA- https://drive.google.com/file/d/1bxl9qrb_52RocKNGfbZ5znHVqFDMkUzf/view?usp=sharing

3. A spreadsheet listing the assignments of different cities- https://docs.google.com/spreadsheets/d/1cmTW5fgU3KyH6JbrRao-qWjzu2GovKk_BkA7a-poGFw/edit#gid=1247370552

4. Hospital Dataset: This was taken from the Oregon Health Authority Hospital Reporting and can be found at https://www.oregon.gov/oha/hpa/analytics/pages/hospital-reporting.aspx

An extensive summary of hospital-related metrics can be found in this dataset, which is taken from the hospital reporting of the Oregon Health Authority. Here is a brief synopsis of the main columns from the website itself: 
•	AHA ID
o	Definition: Unique hospital identifier by the American Hospital Association.
•	Hospital Name
o	Definition: Full name of the hospital.
•	Hospital Short Name
o	Definition: Abbreviated name for the hospital.
•	Type
o	Definition: Classification of the hospital (e.g., general, specialty).
•	Critical Access
o	Definition: Binary indicator if the hospital is a critical access facility.
•	Temporal Indicators
o	Columns: Month, Quarter, Year.
o	Definition: Temporal information for data categorization.
•	Beds
o	Columns: Available Beds, Licensed Beds.
o	Definition: Capacity metrics for patient accommodation.
•	Discharges
o	Columns: Various categories (e.g., Medicare, Medicaid).
o	Definition: Number of patient discharges by payment source.
•	Patient Days
o	Columns: Various categories.
o	Definition: Total days patients spend in the hospital by payment source.
•	Procedures and Visits
o	Columns: Inpatient Surgeries, Births, ED Admissions, etc.
o	Definition: Metrics for surgeries, births, and various visits.
•	Charges
o	Columns: Various categories and payment sources.
o	Definition: Financial charges associated with different services.
•	Financials
o	Columns: Revenue, Expenses, Operating Margin, etc.
o	Definition: Financial metrics covering revenue, expenses, and margins.
•	Miscellaneous:
o	Columns: Cash and Short-Term Investments, Uncompensated Care, Tax Subsidies, etc.
o	Definition: Diverse metrics, including liquidity, uncompensated care, and subsidies.



## Important Consideration for the Data
The GeoJSON dataset provided by the USGS is extensive, encompassing around 136,000 fire occurrences that demanded comprehensive analysis. While utilizing Prof. David McDonald's reader-facilitated data loading, filtering this dataset involved the meticulous selection of fire occurrences relevant to the scope of this assignment, a task that consumed a substantial amount of time.

Additionally, extensive error handling was essential since not all fields were consistently present in every data row. An example of this is the 'rings' parameter, which required careful validation and appropriate handling.

It's worth noting that data is accessible for all years except 2021, 2022, and 2023 for analysis purposes.

Working with AQI data posed its unique challenges. In the case of our study city, Lewiston, Idaho, no monitoring stations are located within the city or within a 25-mile radius. The closest station is situated 50 miles away. Furthermore, there's no single station with complete data for all the analysis years, necessitating data aggregation from multiple station responses.

Because different weather stations operated in different years, data consolidation was mandatory across these two distinct stations.

Moreover, responses from the EPA API sometimes lack the 'aqi' parameter, requiring robust exception handling. In my city locations, data for gaseous pollutants was notably absent, with only data available for particulate pollutants, prompting the need for specialized handling in this specific scenario.

## Documentation

In order to read the wildfire data, the following example notebook provided by Professor David McDonald  was used under the CC-BY license.  
Example Notebook for Reading in the Wildfire Data - https://drive.google.com/file/d/1qNI6hji8CvDeBsnLDAhJXvaqf2gcg8UV/view  
We also used the GeoJSON reader provided by Professor David McDonald for the above purpose under the same license.  
Link - https://drive.google.com/file/d/1TwCkvdaw0MxJzW7NSDg6XxYQ0dvaS44I/view   
CC-BY License - https://creativecommons.org/licenses/by/4.0/ 
This project adheres to the recommended best practices for replication and documentation:
Jupyter Notebooks: detailed comments for data acquisition, processing, and analysis.
README File: Offers a general overview of the project, outlining its objectives, data sources, data processing procedures, and standards for reproducibility.
LICENSE File: Contains the MIT LICENSE for the project's code, ensuring it is freely usable, and the Creative Commons License.

## Code Files

1. DATA 512 Wildfire Part 1.ipynb-This ipynb notebook is for data acquisition and initial analysis 
2. epa_air_quality_history.ipynb- This is the notebook for the acquisition of AQI data
3. Final Analysis.ipynb- This notebook contains code for the comparative analysis and predictive modeling.

## Environment
Jupyter was used in order to run a .ipynb Notebook. Any editor that allows .ipynb notebooks can be used to run this project following the installation of the modules specified in the code.

## License
1. Creative Commons License: https://creativecommons.org/licenses/by/4.0/
2. This project is open-source and follows the MIT License. You are free to use and modify the code according to the terms of the MIT License.

## Data Files
1. USGS_Wildland_Fire_Combined_Dataset.json- The file having all the wildfire data
2. aqi_list.json- The file having AQI data for Klamath Falls
3. wildfires_klamath_falls.json- Smoke estimate till 2023
4. future_smoke_estimate.json- Smoke estimate from 2024 to 2048

## Steps to Reproduce:

Step 1: Data Acquisition 
Obtain the Wildfire and AQI data by collecting data from the specified sources and making API calls to gather additional information required for analysis.

Step 2: Data Filtering 
For Scope Filter the data acquired in Step 1 to include only wildfires that occurred within a 1250-mile radius from the source city and within the years 1963-2023.

Step 3: Smoke Estimate Calculation 
Calculate the smoke estimate using attributes from the filtered wildfire data.

Step 4: Time Series Forecasting and Prediction 
Utilize time series forecasting techniques to predict smoke levels for future dates in the city of interest based on the smoke estimates from Step 3.

Step 5: Visualization and Analysis 
Perform visualizations and analyses as prompted by the instructor:

- Create a histogram showing the number of fires at 50-mile intervals up to the specified maximum distance from your assigned city.
- Generate a time series graph displaying the total acres burned per year for fires within the specified distance from your city.
- Create a time series graph presenting both the fire smoke estimate and AQI estimate for your city.
- These steps outline the key phases of Data Acquisition, Data Preparation, and Data Analysis within the project. A much more detailed step-by-step procedure to reproduce this project is given in the notebook attached to this repository.

Step 6: Reading Hospital data
Read the hospital data and pre-process to make it suitable to use

Step 7: Plotting Visualization
We will plot the total available hospital beds and total hospital revenue over the years

Step 8: Predict future values
Using the predicted values of the smoke estimate, predict the hospital beds and total hospital revenue for the next 25 years

## Important Links

https://www.sciencebase.gov/catalog/file/get/61aa537dd34eb622f699df81?f=__disk__d0%2F63%2F53%2Fd063532049be8e1bc83d1d3047b4df1a5cb56f15&transform=1&allowOpen=true
https://aqs.epa.gov/aqsweb/documents/data_api.html
https://www.statsmodels.org/stable/generated/statsmodels.tsa.ar_model.AutoReg.html
https://drive.google.com/file/d/1qNI6hji8CvDeBsnLDAhJXvaqf2gcg8UV/view

## Limitations  

a. Availability of a good dataset: The additional data that I am using for extending this analysis has been pulled from the internet. It has been reported by the government of Oregon but its accuracy can always be questioned. Also, I would have loved to have access to a few more data points which would have increased the accuracy of my prediction model.

b. Accuracy of smoke estimate: The smoke estimate that I have created was based on the limited supply of data I had in the previous part. In reality, the AQI value analysis is based on the concentrations of several major air pollutants, each weighted to reflect its potential health impact. The common pollutants considered in the AQI calculation are Ground-level Ozone (O3), Particulate Matter (PM10 and PM2.5), Carbon Monoxide (CO), Sulfur Dioxide (SO2), Nitrogen Dioxide (NO2).

c. Unavailability of data: We do not have hospital data from 1963 to 2007. This limits the horizon of our analysis.

d. Assuming Autocorrelation: As we are using an autoregressive model for predicting the smoke estimate for the future 25 years, we are assuming that the values at the previous time steps are useful to predict the future values of the smoke estimate.

e. Other factors affecting the healthcare system: As we are doing an analysis on the smoke from wildfires, we have concentrated on it being the cause of the various impacts that we have talked about in the report. However, we need to mention that several other factors can have a direct impact on our research questions. For example, a general increase in the price of healthcare can be one of the reasons for an increase in the revenue of hospitals. Only wildfires cannot be blamed for this.


## Contact Detail

For any additional questions or feedback, please contact [Vritesh Gera] at [vriteshg@uw.edu]

