# Ecommerce Data Cleaning & Exploration

## Objective
This project explores an e-commerce dataset containing user session information and website activity data.

The original goal was to create a PostgreSQL database and answer specific questions about customer behavior. However, significant data quality issues were discovered during analysis, requiring numerous caveats and limiting the confidence of findings.

These initial analysis challenges effectively shifted the project focus into a demonstration of how to develop strategies for critical data assessment, pragmatic decision-making, and transparent communication of limitations.

## Dataset Description

The [dataset](data/raw) includes multiple tables containing the following types of information:

[`all_sessions.csv`](data/raw/all_sessions.csv):

* User sessions on a website or platform
* User information (fullvisitorid, country, city)
* Transactions (totaltransactionrevenue, transactions)
* User behavior (timeonsite, pageviews, sessionqualitydim)
* Product details (productsku, v2productname, v2productcategory, productvariant)

[`analytics.csv`](data/raw/analytics.csv):

* More granular user session data, broken down by visit number
* Similar metrics to the 'all_sessions.csv' file
* Potential revenue details (revenue, unitprice)

[`products.csv`](data/raw/products.csv):

* Product master list with inventory information
* Sentiment analysis data for products (sentimentscore, sentimentmagnitude)

[`sales_by_sku.csv`](data/raw/sales_by_sku.csv):

* Aggregated sales figures for each product

[`sales_report.csv`](data/raw/sales_report.csv):

* Combined data related to sales including product information, stock information, and customer sentiment data

**Important Note:** The dataset lacks documentation and personnel for consultation.  All insights and assumptions should be interpreted with this context in mind.

## Tools Used

**Environment:** Jupyter Notebooks within Visual Studio Code

**Database:** PostgreSQL (accessed with PostgreSQL extension in VS Code)

**Data Manipulation and Analysis:**
* iPython-SQL
* pandas
* NumPy

**Visualization:**
* matplotlib

## Repository Structure

This project's repository contains directories and notebooks primarily focused on data exploration, cleaning, and analysis within a database environment.

[`data/`](data/raw): Contains the original CSV datasets provided for the project.

[`notebooks/`](notebooks/): Includes Jupyter notebooks detailing each step of the data integrity assessment and analysis.

[`images/`](images/): Contains images that highlight the results of analysis.


## Data Analysis Methodology

The process for this project follows these primary steps, organized into separate Jupyter Notebooks:

### Database Setup and Import

[`01_db_setup.ipynb`](./notebooks/01_db_setup.ipynb):
* Establishes a PostgreSQL database, creates necessary tables, and imports the provided CSV data.

### Data Integrity Assessment

[`02_data_integrity_assessment.ipynb`](./notebooks/02_data_integrity_assessment.ipynb):
* Assesses data quality issues in key columns (e.g., 'visitid', 'totaltransactionrevenue'), focusing on duplication, mismatches, and null values.
* Investigates patterns within data quality problems, exploring potential causes.
* Documents cleaning decisions and assumptions necessary for further analysis.

### Provisional Analysis

[`03_provisional_analysis.ipynb`](./notebooks/03_provisional_analysis.ipynb):
* Acknowledges significant data quality limitations.
* Attempts to answer the original analysis questions, explicitly outlining assumptions required and interpreting outcomes with caveats.

## Original Analysis Questions

1. What percentage of unique visitors to the site make a purchase?

2. What are the top channelgroupings for each country?

3. What are the top 10 products based on unique visitor viewings?

4. How many visits did the top 10 unique site visitors make?

5. How does average timeonsite compare between visits that ended in a purchase?

## Data Quality Findings

Initial data exploration uncovered the following significant issues impacting analysis:

**Session Tracking** (*visitID*):
* Duplicated visitid values within tables and mismatches between the analytics and all_sessions tables prevent reliable tracking of individual user sessions.

**Null Values:** Several key columns have substantial quantities of null values, including:
* totaltransactionrevenue: ...
* (Add more high-impact null value findings here)

## Provisional Analysis Results
This section shows the results of the original analysis questions, with specific reference to how data quality findings impact the answers.

### Question 1: Conversion Rate
    What percentage of unique visitors to the site make a purchase?

**Provisional Findings:**

Based on [state assumptions], approximately X% of unique visitors appear to have made a purchase.

**Data Quality Impacts:**

These findings are unreliable because of:
* [add findings]
* [add findings]
* [add findings]

### Question 2: Top Channel Groupings
    What are the top channelgroupings for each country?

**Provisional Findings:**

Based on [state assumptions], the top channel groupings for each country are as follows...

**Data Quality Impacts:**

These findings are unreliable because of:
* [add findings]
* [add findings]
* [add findings]

### Question 3: Most Viewed Products
    What are the top 10 products based on unique visitor viewings?

**Provisional Findings:**

Based on [state assumptions], the top 10 products with the highest unique visitor views are...

**Data Quality Impacts:**

These findings are unreliable because of:
* [add findings]
* [add findings]
* [add findings]

### Question 4: Most Frequent Visitors
    How many visits did the top 10 unique site visitors make?

**Provisional Findings:**

Based on [state assumptions], the top 10 visitors...

**Data Quality Impacts:**

These findings are unreliable because of:
* [add findings]
* [add findings]
* [add findings]

### Question 5: Timeonsite for Purchasing Customers
    How does average timeonsite compare between visits that ended in a purchase?

**Provisional Findings:**

Based on [state assumptions], timeonsite for customers who made a purchase...

**Data Quality Impacts:**

These findings are unreliable because of:
* [add findings]
* [add findings]
* [add findings]

## AI Assistance Acknowledgement

This project was developed with the assistance of AI tools to streamline the development process and refine the final product. These tools included:

* **GitHub Copilot**: Supported code generation for repetitive tasks, offered optimizations, and aided in refining data cleaning and analysis scripts.
* **Gemini AI**: Contributed to the development of project strategy and refinement of documentation by acting as a proofreader and source of critical feedback.

