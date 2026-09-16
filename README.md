# CMS Hospital Clients Satisfaction Survey 2026
**Goal: Evaluate patients satisfaction performance against HCAHPS guidelines.**  

This project tracks and benchmarks hospitals performance using standard CMS evaluation techniques:  
- Top-Box scores: Percentage of patients giving the highest possible rating.  
- Hospital vs State benchmark: side by side variance analysis of individual hospital performance against state thresholds to flag facilities falling below regional baselines.

## Overview
This project shows an end to end process of collecting, storing, cleaning, preparing and analyzing HCAHPS data:     

**Technology stack: Git v2.2, VSCode v1.137, Databricks Community Edition, Power BI v2.157.1354.0, AWS S3, Python v3.14.6, SQL (CTE, Window Functions, Joins)**.  
**Data Architecture:** Creating a landing zone on a AWS S3 bucket and designing a data warehouse using the medallion architecture with Bronze, Silver and Gold layers.  
**ETL:** Extracting, Transforming (data cleaning and preparation), and Loading data from source systems into the warehouse.  

## Specifications
**Data Sources**: Import data from two endpoints of the API at https://data.cms.gov/  
**Data Quality**: Cleanse and resolve data quality issues prior to analysis.  
**Integration**: Combine both sources into a single table designed for analytical queries.

## Repository Structure
```
hospital-clients-satisfaction2026/
│
├── databricks/notebooks                  # SQL scripts used in Databricks for ETL and transformations
│
├── ingestion/                            # Pyhton script used in VSCode to move data from API endpoints into AWS S3 landing zone
│
├── power bi/                             # Power bi application files including hospital-clients-satisfaction2026.pbip
│   ├── hospital-clients-satisfaction2026/  
│   ├── hospital-clients-satisfaction2026.SemanticModel/                  
│
├── .gitignore
|
└── README.md                           # Project overview and instructions
```
## Data architecture

<img width="3124" height="1172" alt="image" src="https://github.com/user-attachments/assets/6e88a560-daf6-4d3d-a72f-3987f367a97c" />


## Dashboard preview
### Main view - All states selected

<img width="974" height="548" alt="bi1" src="https://github.com/user-attachments/assets/49b80192-cdbd-48a6-bb54-f76df4aca946" />  

 
### State view - Specific state selected

<img width="973" height="549" alt="bi2" src="https://github.com/user-attachments/assets/5071cdef-a396-414e-be12-6cd86784b469" />  

  
### View filtered by hospital size

<img width="975" height="548" alt="bi3" src="https://github.com/user-attachments/assets/9f91b2ff-712e-4d7e-aab1-2d8abba9fb97" />  

  
### Hospital view - Specific hospital selected  
The administration of the Staten Island University Hospital could investigate the cleanliness of their rooms and their restfulness at night as their rating on these points fall behind the state average.  

<img width="972" height="547" alt="bi4" src="https://github.com/user-attachments/assets/174ae96f-3497-4752-ae29-215f51f63b21" />

  
## How to run this project
**Prerequisites**  
- Git v2.2
- VSCode v1.137 with Python v3.14.6 or newer
- Databricks Community Edition account
- Power BI v2.157.1354.0
- AWS account

**Steps**  
- Log in your AWS account, create a S3 bucket and a AWS access key.  
- Clone this repository in VSCode, add a .env file containing the S3 bucket name and AWS access key credentials.  
- Run ingestion.ipynb to collect the raw data and store it in AWS S3.  
- Connect your Databricks account to your github account and clone this repository in Databricks.  
- Run Bronze.ipynb, Silver.ipynb, Gold.ipynb and Validation tests.ipynb to generate the clean data.  
- Download the Power BI files locally.
- Open Power BI desktop and set up a connection with your Databricks account.  
- Find hospital-clients-satisfaction2026.pbip in the downloaded files and double click on it to access the dashboard and interact with it.

## Take it further
- Use Apache Airflow to automate the data collection.
- Use DirectQuery in Power BI instead of Import.
- A brief analysis reveals that smaller hospitals consistently outscored bigger medical centers. We could turn the dashboard into a report with more pages digging deeper into the elements yielding better ratings for these smaller facilities and how they perform against the revised CMS guidelines which includes a Care Coordination composite.
