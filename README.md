# Procurement Performance Dashboard 
<img width="1256" height="756" alt="Procurement Performance Dashboard" src="https://github.com/user-attachments/assets/75b53cc5-6cea-4f6c-ae66-c84545f0d29d" />

## Project Overview
This project is an end-to-end Data Analytics solution designed to evaluate corporate procurement performance over a 24-month period (January 2022 - January 2024). The dashboard provides procurement managers with actionable insights into budget allocation, vendor quality, compliance rates, and cost-saving achievements, enabling data-driven decisions for contract renewals and supply chain optimization.

## Business Objectives
* **Budget Visibility:** Track the total expenditure and its distribution across various item categories.
* **Vendor Quality Assessment:** Identify suppliers with the highest defect rates to mitigate supply chain risks.
* **Compliance Monitoring:** Measure supplier adherence to delivery and operational guidelines.
* **Negotiation Impact:** Highlight total cost savings achieved through negotiated pricing compared to standard unit prices.
* **Trend Analysis:** Monitor historical spending patterns to anticipate future cyclical budget needs.

## Key Insights & Findings
* **Critical Vendor Alert:** `Delta_Logistics` represents the highest supply chain risk, recording the highest defect rate (10.83%) and the lowest compliance rate (60.82%).
* **Top Performers:** `Epsilon_Group` and `Alpha_Inc` are the most reliable vendors, maintaining >93% compliance rates with defect rates below 3%.
* **Cost Saving Champion:** `Beta_Supplies` generated the highest cost savings (0.89M), indicating highly successful price negotiations, despite ranking lower in operational compliance.
* **Stable Expenditure:** The 45.37M total spend is distributed evenly across all categories (MRO, Office Supplies, Electronics, Raw Materials, Packaging), ranging from 17.9% to 22.3% per category.
* **Cyclical Peaks:** Historical time-series analysis reveals consistent spending spikes occurring annually around March.

## Data Modeling & DAX Measures
The dashboard utilizes custom DAX (Data Analysis Expressions) measures to transform raw transactional data into high-level strategic KPIs:

**1. Total Spend**
> `Total Spend = SUMX('Procurement KPI Analysis Dataset', [Negotiated_Price] * [Quantity])`

**2. Cost Savings**
> `Cost Savings = SUMX('Procurement KPI Analysis Dataset', ([Unit_Price] - [Negotiated_Price]) * [Quantity])`

**3. Defect Rate**
> `Defect Rate = DIVIDE(SUM('Procurement KPI Analysis Dataset'[Defective_Units]), SUM('Procurement KPI Analysis Dataset'[Quantity]))`

**4. Compliance Rate**
> `Compliance Rate = DIVIDE(CALCULATE([Total Orders], 'Procurement KPI Analysis Dataset'[Compliance] = "Yes"), [Total Orders])`

**5. Total Orders**
> `Total Orders = COUNT('Procurement KPI Analysis Dataset'[PO_ID])`

## Tech Stack & Tools
* **Data Visualization & Modeling:** Microsoft Power BI
* **Data Transformation:** Power Query
* **Formula Language:** DAX (Data Analysis Expressions)

## How to Use
1. Clone this repository to your local machine.
2. Open the `.pbix` file using Microsoft Power BI Desktop.
3. Interact with the dashboard by clicking on specific supplier bars or item category slices to cross-filter the data dynamically.
