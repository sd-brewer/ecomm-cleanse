# Ecommerce Data Cleaning & Exploration

## Objective

This project explores an ecommerce dataset to answer the question: **"What percentage of unique visitors to the site make a purchase?"**

The project aimed to:

* Gain familiarity with SQL in Jupyter Notebooks.
* Conduct exploratory data analysis (EDA) to understand variables and identify data quality issues.
* Perform a targeted analysis to answer the guiding question.
* Demonstrate critical data assessment and effective communication of rationale.

## Dataset Description

The dataset (located in [`data/raw`](data/raw)) includes two tables:

* **`all_sessions.csv`:** User sessions, transactions, user behavior, and product details.
* **`analytics.csv`:** Granular session data, potential revenue details.

**Note:** The dataset lacks documentation, making insights and assumptions subject to interpretation.

## Tools Used

* **Environment:** Jupyter Notebooks within Visual Studio Code
* **Database:** PostgreSQL
* **Data Manipulation and Analysis:** iPython-SQL, Pandas

## Repository Structure

* [`data/raw`](data/raw): Original and processed CSV data.
* [`notebooks/`](notebooks/): Jupyter Notebooks detailing each project step.

## Notebooks & Methodology

1. **Database Setup and Import:**
   * [`01_db_setup.ipynb`](./notebooks/01_db_setup.ipynb): Creates the database and imports CSV data.

2. **Initial Data Preparation:**
   * [`02_initial_data_prep.ipynb`](./notebooks/02_initial_data_prep.ipynb): Assesses and addresses data quality issues in key columns, focusing on duplicates, mismatches, and null values.

3. **Data Exploration and Analysis:**
   * [`03_data_exploration_and_analysis.ipynb`](./notebooks/03_data_exploration_and_analysis.ipynb):
      * Defines ambiguous variables.
      * Investigates data quality patterns and potential causes.
      * Acknowledges limitations.
      * Answers the guiding analysis question.

## Key Data Quality Findings

* **Session Tracking (`visitID`):** Duplicated and mismatched values hinder reliable tracking.
* **Transaction Reporting:** Inconsistent revenue reporting across tables, missing values, and discrepancies in product and revenue data.

## Analysis Results: Conversion Rate

**Provisional Finding:** Approximately 4.83% of unique visitors made a purchase.

**Assumptions:**

* `fullvisitorid` uniquely identifies visitors.
* `visitid` represents distinct visits.
* `revenue` indicates a transaction.
* The `analytics` table is the source of truth for transactions.
* Analysis is limited to May 1st - August 1st, 2017.

**Data Quality Impacts:**

* **Session Tracking:** Inaccurate visitor identification could under or overestimate the conversion rate.
* **Transaction Reporting:** Inconsistent data may misrepresent the true number of transactions.

**Note:** The dataset's numerous issues make it difficult to provide an exhaustive list of caveats. This section highlights the primary impacts on the findings.

## AI Assistance

This project was developed with assistance from:

* **GitHub Copilot:** Code generation for repetitive tasks.
* **Gemini AI:** Refinement of project strategy and documentation.