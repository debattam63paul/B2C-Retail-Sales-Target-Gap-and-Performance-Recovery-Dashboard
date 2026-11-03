# B2C Retail Sales Target Gap & Performance Recovery Dashboard

An end-to-end retail sales analytics project using Microsoft Excel and Power Query to evaluate sales performance, identify target gaps, investigate underperforming stores, regions and products, and develop actionable business strategies for sales recovery and profitability improvement.

---

## 1. Project Objective

To evaluate retail sales performance against established targets, identify underperforming regions, stores and products, pinpoint major contributors to sales shortfalls, and prioritize targeted recovery strategies to improve sales achievement, strengthen store and product performance, and maximize overall profitability.

---

## 2. Business Problems

The project addresses the following business questions:

1. Are stores achieving their monthly sales targets?
2. Which regions, stores, product categories and products are underperforming?
3. Where are the largest sales shortfalls occurring?
4. Which stores and products require immediate management attention?
5. What business factors could be contributing to the sales target gap?
6. What corrective actions should management prioritize to recover lost sales without compromising profitability?

---

## 3. Project Overview

| Particulars        | Details                                              |
| ------------------ | ---------------------------------------------------- |
| Project Type       | Business Intelligence & Retail Sales Analytics       |
| Industry           | B2C Retail                                           |
| Analysis Period    | January 2024 – December 2025                         |
| Primary Tool       | Microsoft Excel 2019                                 |
| Data Cleaning      | Power Query                                          |
| Data Analysis      | Excel Pivot Tables & Calculated Fields               |
| Data Visualization | Excel Interactive Dashboard                          |
| Reporting          | Dynamic KPI Cards, Charts, Slicers & Action Matrices |

### Dataset Structure

The project uses four interconnected datasets:

| Dataset        | Description                                                                                                  |
| -------------- | ------------------------------------------------------------------------------------------------------------ |
| Store_Master   | Store information, including store ID, name, region, city, store type, size and manager.                     |
| Product_Master | Product information, including product ID, name, category, subcategory, brand, list price and standard cost. |
| Target_Table   | Product-specific monthly sales targets for individual stores.                                                |
| Sales_Fact     | Monthly summarized actual sales records for different stores and products.                                   |

The raw and cleaned versions of all four datasets are maintained in the project workbook.

---

## 4. Data Cleaning & Preparation

Data cleaning was performed using **Power Query** to improve data consistency, accuracy and reliability before analysis.

### Store Master

- Removed measurement-unit suffixes from store-size values and converted them into numeric format.
- Standardized date formats using the appropriate regional locale.
- Corrected inconsistent store names, region names, city names and store types.
- Applied Trim, Clean and proper text capitalization.
- Standardized Store_ID into uppercase.
- Replaced missing descriptive attributes with "Unknown".
- Removed 2 duplicate records.
- Flagged conflicting information associated with ST001, ST013 and ST019 for further investigation.

### Product Master

- Removed currency suffixes from list prices and converted them into decimal values.
- Standardized product identifiers, product names, brands and category labels.
- Corrected inconsistent product naming and category spellings.
- Applied Trim, Clean and proper capitalization.
- Replaced missing descriptive text values with "Unknown".
- Removed 5 duplicate records.
- Retained and flagged missing Product_ID and Standard_Cost_INR values.
- Flagged conflicting product information associated with identical product IDs.

### Target Table

- Restricted dashboard analysis to January 2024–December 2025 without deleting out-of-period source records.
- Converted Target_Month into a proper date format.
- Removed currency suffixes from target sales and converted them into decimal values.
- Standardized Store_ID and Product_ID by removing hyphens, applying Trim and Clean, and converting identifiers into uppercase.
- Retained and flagged null or non-positive target units and missing target sales.
- Retained missing target growth percentages.
- Checked duplicate records and identified conflicting combinations of Target_Month, Store_ID and Product_ID.
- Flagged missing business-key components and duplicate business-key combinations.

### Sales Fact

- Converted sales month, discount percentage and transaction-line columns into appropriate data types.
- Removed unit and currency suffixes from units sold, gross sales, net sales, COGS and gross profit.
- Standardized Store_ID and Product_ID for consistent data mapping.
- Removed 51 duplicate records.
- Retained negative sales, cost, units and unusual discount values where the documented methodology did not require their removal.
- Created validation flags for negative net sales, profit-related issues, missing target information, blank identifiers and out-of-period records.
- Integrated target information using a common Store_ID + Product_ID + Month mapping key.
- Enriched sales records with store and product attributes using their respective master tables.

### Data Quality Management

A separate Data Quality Log documents the following:

- Source table and data quality issue.
- Raw data evidence and examples.
- Resolution technique and cleaning process.
- Treatment and validation outcome.

**Important:** Not every data quality issue was resolved by deleting or replacing records. Missing values, conflicting identifiers and questionable business records were retained and flagged wherever appropriate to preserve data traceability and support further investigation.

---

## 5. Data Analysis & Business Calculations

The cleaned Sales_Fact dataset was used as the primary analytical table.

The following calculated measures were developed:

| Metric                 | Calculation                                                         |
| ---------------------- | ------------------------------------------------------------------- |
| Gross Sales            | Units Sold × List Price                                             |
| Net Sales              | Gross Sales − Discount Amount                                       |
| COGS                   | Units Sold × Standard Cost                                          |
| Gross Profit           | Net Sales − COGS                                                    |
| Target Achievement %   | Net Sales / Target Sales                                            |
| Sales Shortfall        | MAX(0, Target Sales − Net Sales)                                    |
| Gross Profit Margin %  | Gross Profit / Net Sales                                            |
| MoM Net Sales Growth % | (Current Month Sales − Previous Month Sales) / Previous Month Sales |

### Data Validation & KPI Treatment

To ensure more reliable reporting, the dashboard calculations incorporate the documented validation flags:

- Data_Validation_Flag
- Sales_Flag
- Target_Flag
- Profit_Flag

These flags help exclude inappropriate records from relevant KPI calculations without unnecessarily deleting potentially useful source information.

---

## 6. Dashboard KPIs

The interactive dashboard contains five primary performance indicators:

| KPI                   | Purpose                                             |
| --------------------- | --------------------------------------------------- |
| Actual Net Sales      | Measures total realized sales revenue.              |
| Target Sales          | Measures the planned sales target.                  |
| Target Achievement %  | Evaluates actual sales performance against targets. |
| Sales Shortfall       | Quantifies the sales gap requiring recovery.        |
| Gross Profit          | Measures profitability after cost of goods sold.    |
| Gross Profit Margin % | Evaluates profitability relative to net sales.      |

---

## 7. Interactive Dashboard Components

### Dynamic Filters (Slicers)

- Year: 2024 and 2025.
- Region: Enables geographical performance analysis.

All connected charts and analytical tables respond to the selected filters.

### Charts & Visualizations

1. Actual Sales vs Target Sales Trend
2. Month-on-Month Net Sales Growth
3. Product Category-wise Sales Contribution
4. Target Achievement by Product Category
5. Sales Shortfall by Product Category
6. Top 5 Stores by Sales Shortfall
7. Top 5 Products by Sales Shortfall

### Management Decision-Support Tables

**1. Sales Performance Recovery Priority List**

Identifies the five stores with the lowest target achievement and highlights the three products with the highest sales shortfall within each selected store.

This helps management prioritize underperforming stores and identify their major product-level performance gaps.

**2. Sales Recovery Action Matrix**

Classifies performance into four severity levels:

- Critical
- High
- Moderate
- On-Target

The classification considers target achievement and sales shortfall thresholds, helping management prioritize corrective actions based on performance severity.

---

## 8. Key Business Insights

The following findings were identified from the dashboard for the January 2024–December 2025 analysis period.

### Overall Sales Performance

- Total actual net sales reached **₹213.13 Cr** against a target of **₹234.06 Cr**.
- Overall target achievement was approximately **91%**.
- The reported sales shortfall was **₹19.88 Cr**.
- Total gross profit was approximately **₹56.69 Cr**.
- Overall gross profit margin was approximately **26.60%**.
- Actual sales declined by approximately 1.61% in 2025 compared with 2024.
- Target achievement declined from 92% in 2024 to 91% in 2025.
- Only 5 out of 24 months met or exceeded their monthly sales targets.

### Regional Performance

- **East:** Highest sales shortfall of approximately ₹6.30 Cr, with 90% target achievement. The region's high sales contribution also contributes to its larger absolute shortfall.
- **Northeast:** Lowest target achievement at approximately 83%, with a shortfall of ₹1.49 Cr.

### Monthly Performance

- October 2025 recorded the largest monthly target gap of approximately ₹1.75 Cr.
- Despite this, October 2025 also recorded the highest month-on-month sales growth of approximately 20%.

### Product Category Performance

- **Electronics:** Highest sales shortfall of approximately ₹9.84 Cr.
- **Home & Kitchen:** Lowest target achievement at approximately 87%, with a shortfall of approximately ₹3.34 Cr.

Electronics has the largest absolute shortfall because of its high sales contribution, while Home & Kitchen has the weakest target achievement.

### Store-Level Performance

- Hyderabad Mall 01 recorded the largest store-level sales shortfall of approximately ₹3.86 Cr.
- Other major shortfall contributors include Durgapur Mall 01, Ahmedabad Neighborhood 01, Surat Mall 01 and Lucknow Largeformat 01.

### Product-Level Performance

- Xiaomi Smartphone Essential 5 recorded the highest product-level sales shortfall of approximately ₹3.17 Cr.
- Electronics products repeatedly contributed to significant shortfalls in stores located in Durgapur, Hyderabad, Lucknow, Ahmedabad and Surat.

---

## 9. Business Recommendations & Recovery Strategies

Based on the identified performance gaps, the following strategies are recommended:

| Business Area                   | Recommended Action                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Critical Underperforming Stores | Immediately investigate pricing, product quality, stock availability, competitor offers and customer demand.                     |
| Electronics                     | Investigate weak-performing products and stores, improve availability and review competitive pricing and promotional strategies. |
| Home & Kitchen                  | Identify products with low target achievement and develop category-specific sales improvement strategies.                        |
| Northeast Region                | Investigate supply-chain constraints, product availability, seasonal demand and customer preferences.                            |
| East Region                     | Maintain its strong sales contribution while reducing absolute sales shortfalls through store- and product-level investigation.  |
| Slow-Moving Products            | Identify low-demand inventory, improve product visibility and consider suitable promotional campaigns.                           |
| Discount Management             | Avoid excessive discounting and protect gross profit during sales recovery initiatives.                                          |
| Store Management                | Learn from high-performing stores and replicate successful sales practices where appropriate.                                    |
| Performance Monitoring          | Introduce weekly sales monitoring and track recovery progress against defined targets.                                           |
| Management Accountability       | Assign responsible managers, corrective actions and timelines to priority stores and categories.                                 |
| Data Quality                    | Validate missing targets, conflicting records and questionable sales data before making management decisions.                    |

**Note:** These are recommended investigation areas and corrective strategies. Actual causes of the sales shortfall should be confirmed through further operational and customer-level investigation.

---

## 10. Tools & Techniques Used

**Microsoft Excel 2019**

- Advanced Excel formulas.
- Pivot Tables and Pivot Charts.
- Calculated Fields.
- Dynamic KPI Cards using helper cells.
- Slicers and Report Connections.
- Conditional formatting.
- Custom number formatting.
- Interactive dashboard development.

**Power Query**

- Data cleaning and transformation.
- Data type standardization.
- Handling missing and duplicate records.
- Text normalization.
- Data validation and flag creation.
- Data preparation and integration.

**Analytical Techniques**

- Target vs Actual Performance Analysis.
- Sales Gap Analysis.
- Regional and Store-Level Performance Analysis.
- Product Category and Product-Level Analysis.
- Profitability Analysis.
- Month-on-Month Growth Analysis.
- Severity-Based Performance Classification.
- Business Recommendations and Recovery Planning.

---

## 11. Key Project Deliverables

The project workbook contains:

1. Interactive Sales Performance Dashboard.
2. Insights and Recommendations.
3. Pivot Tables and Charts.
4. Cleaned Sales_Fact Dataset.
5. Cleaned Store_Master Dataset.
6. Cleaned Product_Master Dataset.
7. Cleaned Target_Table Dataset.
8. Raw versions of all four datasets.
9. Detailed Data Quality Log.

---

## 12. Business Value

This project demonstrates how raw retail sales data can be transformed into meaningful business intelligence through systematic data cleaning, analytical calculations, interactive visualization and performance-based recommendations.

It provides management with the ability to:

- Monitor sales performance against business targets.
- Identify regions, stores and products requiring attention.
- Quantify sales shortfalls and profitability.
- Prioritize critical recovery opportunities.
- Develop targeted corrective action plans.
- Monitor business performance and recovery progress.
- Make more informed, data-driven decisions.

---

## 13. Conclusion

The B2C Retail Sales Target Gap & Performance Recovery Dashboard goes beyond traditional sales reporting. It combines data preparation, data quality management, business performance analysis, interactive visualization and actionable recommendations into a single analytical solution.

The primary focus is not just to identify how much sales targets are missed, but also to determine where performance gaps occur, which stores and products require attention, and what actions management can take to improve sales achievement while maintaining profitability.

**This project demonstrates an end-to-end approach to solving a real-world retail business problem using Microsoft Excel and Power Query.**
