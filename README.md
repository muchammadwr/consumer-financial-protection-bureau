# Consumer Financial Protection Bureau: Financial Consumer Complaints Analytics

> **End-to-end analytics project** using Excel Spreadsheets to identify patterns, products, and issues complaint from customers

---

## Table of Contents

1. [Business Understanding](#1-business-understanding)
2. [Data Understanding](#2-data-understanding)
4. [Data Preparation](#4-data-preparation)
5. [Key Findings](#6-key-findings)
6. [Dashboard](#7-dashboard)
7. [Insights & Recommendations](#8-insights--strategic-recommendations)

---

## 1. Business Understanding

### 1.1 Background
Bank of America, like all financial institutions, is required to handle consumer complaints submitted through the Consumer Financial Protection Bureau (CFPB). Between 2017 and 2023, a large volume of complaints was logged covering a wide range of products credit cards, mortgages, bank accounts, debt collection, and more along with the specific issues raised, how each complaint was submitted, and how the company responded. This data is publicly available but exists largely as raw, unstructured records: thousands of rows of dates, categories, and response types that are not yet organized into any decision-ready form.

Without analysis, this data offers little practical value. It’s unclear whether complaint volume follows any predictable pattern over time, which products or issues are driving the bulk of customer dissatisfaction, how the company typically resolves disputes, and whether there are gaps in responsiveness that could point to operational weaknesses. These are not rhetorical questions they have real implications for customer experience, regulatory risk, and resource allocation, but they remain unanswered as long as the data sits unexamined.

By systematically analyzing this complaint data, the project aims to surface clear, evidence-based insights: whether complaints spike during certain periods, which products and issues deserve the most attention, how consistent the company’s resolution practices are, and what patterns (if any) distinguish complaints that receive untimely responses. These insights would allow a bank’s customer experience, compliance, or operations teams to prioritize improvements where they matter most, rather than relying on assumptions. For a portfolio project, this also demonstrates the ability to move from a messy real-world dataset to structured, actionable findings a core data analyst skill


### 1.2 Objectives
Derived directly from the background above, the objectives are:
1.	Identify temporal patterns in complaint volume determine whether complaints rise or fall seasonally, monthly, or around specific events, to understand if complaint intake is predictable.
2.	Determine which products and issues drive the most complaints rank products by complaint volume and break down the most frequent issues within each, to pinpoint where customer pain is concentrated.
3.	Evaluate how complaints are resolved analyze the distribution of company response types (e.g., closed with explanation, closed with monetary relief) to understand the bank’s typical resolution behavior.
4.	Investigate the drivers of untimely responses examine whether certain products, issues, states, or submission channels correlate with late responses, to identify potential operational bottlenecks or risk areas.

### 1.3 Analytical Questions
1.	Do consumer complaints show any seasonal patterns?
2.	Which products present the most complaints? What are its most common issues?
3.	How are complaints typically resolved?
4.	Can you learn anything from the complaints with untimely responses?

---

## 2. Data Understanding

### 2.1 Data Dictionary

This project uses publicly available consumer complaint data from the Consumer Financial Protection Bureau (CFPB) to analyze complaints associated with Bank of America between 2017 and 2023.

The dataset contains information about complaint submission channels, submission dates, consumer locations, financial products, reported issues, company responses, and response timeliness. These attributes provide a foundation for understanding complaint patterns, identifying recurring consumer concerns, and evaluating the company's response characteristics.

The data understanding phase focuses on examining the dataset structure, interpreting the meaning of each field, identifying data quality issues, and determining the variables relevant to the analytical objectives.

**Platform:** Maven Analytics

**Dataset:** `https://mavenanalytics.io/data-playground/financial-consumer-complaints`

**Source:** Consumer Financial Protection Bureau

**License:** Public Domain





| **Field** | **Description** |
|---|---|
| Complaint ID | The unique identification number for a complaint |
| Submitted via | How the complaint was submitted to the CFPB |
| Date submitted | The date the CFPB received the complaint |
| Date received | The date the CFPB sent the complaint to the company |
| State | The state of the mailing address provided by the consumer |
| Product | The type of product the consumer identified in the complaint |
| Sub-product | The type of sub-product the consumer identified in the complaint (not all Products have Sub-products) |
| Issue | The issue the consumer identified in the complaint (possible values are dependent on Product) |
| Sub-issue | The sub-issue the consumer identified in the complaint (possible values are dependent on Product and Issue, and not all Issues have corresponding Sub-issues) |
| Company public response | The company's optional public-facing response to a consumer's complaint. Companies can choose a response from a pre-set list of options that will be posted on the public database. For example, "Company believes complaint is the result of an isolated error." |
| Company response to consumer | This is how the company responded. For example, "Closed with explanation." |
| Timely response? | Whether the company gave a timely response (Yes/No) |

### 2.2 Data Quality Assessment

The dataset is inspected in Microsoft Excel to understand its structure and identify potential data quality issues before analysis.

The assessment focuses on:

Duplicate records: Check for duplicate complaint IDs and records.

Date fields: Verify date formats and chronological consistency.

Missing values: Identify blank cells in sub-product, sub-issue, and response-related columns.

Categorical consistency: Review values in State, Product, and Issue.

Company responses: Examine the completeness of public responses and consumer response descriptions.

Timely response: Inspect the available Yes/No values and identify blank records.

The findings from this assessment determine the data cleaning and preparation steps described in the next phase.

---

## 3. Data Preparation

Data preparation is performed in Microsoft Excel to improve data consistency and create additional variables for analysis. The original source columns are retained wherever possible, while new columns are added for analytical purposes.

### 3.1 Data Cleaning and Transformation

| Column | Action | Description |
|---|---|---|
| Complaint ID | Check duplicates | Check for duplicate complaint IDs and remove confirmed duplicate records where appropriate. |
| Date submitted | Sort dates | Sort records from oldest to newest to support chronological inspection. |
| State | Clean values | Standardize inconsistent formatting and correct identifiable data-entry inconsistencies. |
| Product | Clean values | Standardize product labels where necessary. |
| Sub-product | Handle blanks | Replace blank cells with `Not specified`. |
| Issue | Clean values | Standardize inconsistent formatting and labels where necessary. |
| Sub-issue | Handle blanks | Replace blank cells with `Not specified`. |
| Company public response | Handle blanks | Replace blank cells with `No public response provided`. |
| Company response to consumer | Clean values | Review and standardize response descriptions where necessary. |
| Timely response? | Handle blanks | Retain `Yes` and `No` values and classify blank values as `Pending` only when justified by the data; otherwise, use `Unknown`. |

### 3.2 Feature Engineering

Additional columns are created in Excel to support temporal analysis, response performance measurement, and categorical comparisons.

| New Column | Source Column | Description |
|---|---|---|
| Year | Date submitted | Extract the year from the submission date. |
| Month | Date submitted | Extract the month from the submission date. |
| Quarter | Date submitted | Identify the calendar quarter (Q1–Q4). |
| Response Time (Days) | Date submitted and Date received | Calculate the difference between the two dates to measure the time between CFPB receipt and company referral. |
| Product Category | Product | Group existing product labels into broader categories to simplify product-level analysis. |
| Issue Category | Issue | Group similar complaint issues into broader categories to simplify issue-level analysis. |
| Complaint Status | Company response to consumer | Create a derived status using documented Excel classification rules, such as `Closed` and `In Progress`, where the source data supports the classification. |

**Note:** The source dictionary defines `Date submitted` as the date the CFPB received the complaint and `Date received` as the date the CFPB sent it to the company. Therefore, their difference measures the interval between CFPB receipt and company referral, not the company's response time. Actual response time requires a valid company response date.

### 3.3 Excel Implementation

The following Excel formulas can be used to create the additional date columns, assuming the source data has been formatted as an Excel Table named `Complaints`.

| New Column | Example Formula |
|---|---|
| Year | `=YEAR([@[Date submitted]])` |
| Month | `=TEXT([@[Date submitted]],"mmmm")` |
| Quarter | `="Q"&ROUNDUP(MONTH([@[Date submitted]])/3,0)` |
| Date Interval (Days) | `=[@[Date received]]-[@[Date submitted]]` |

For `Product Category` and `Issue Category`, create a consistent mapping table that assigns each original label to a broader category. ChatGPT can assist in proposing these mappings, which should then be reviewed and applied consistently in Excel.

For `Complaint Status`, use an Excel formula only after defining classification rules based on the actual response values. A populated response field alone does not confirm that a complaint has been resolved.

### 3.4 Data Preparation Outcome

The prepared dataset is intended to support the following analysis:

- Complaint trends by year, month, and quarter.
- Complaint distribution across product and issue categories.
- Geographical comparisons by state.
- Analysis of company response patterns and timely response indicators.
- Examination of the interval between CFPB receipt and company referral.

The prepared data is then used for exploratory data analysis (EDA) to identify trends, recurring complaint issues, and potential operational gaps in Bank of America's complaint-handling process.


---





# Executive Summary

### Overview of Findings

Explain the overarching findings, trends, and themes in 2-3 sentences here. This section should address the question: "If a stakeholder were to take away 3 main insights from your project, what are the most important things they should know?" You can put yourself in the shoes of a specific stakeholder - for example, a marketing manager or finance director - to think creatively about this section.

[Visualization, including a graph of overall trends or snapshot of a dashboard]



# Insights Deep Dive
### Category 1:

* **Main insight 1.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 2.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 3.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 4.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.

[Visualization specific to category 1]


### Category 2:

* **Main insight 1.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 2.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 3.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 4.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.

[Visualization specific to category 2]


### Category 3:

* **Main insight 1.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 2.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 3.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 4.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.

[Visualization specific to category 3]


### Category 4:

* **Main insight 1.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 2.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 3.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.
  
* **Main insight 4.** More detail about the supporting analysis about this insight, including time frames, quantitative values, and observations about trends.

[Visualization specific to category 4]



# Recommendations:

Based on the insights and findings above, we would recommend the [stakeholder team] to consider the following: 

* Specific observation that is related to a recommended action. **Recommendation or general guidance based on this observation.**
  
* Specific observation that is related to a recommended action. **Recommendation or general guidance based on this observation.**
  
* Specific observation that is related to a recommended action. **Recommendation or general guidance based on this observation.**
  
* Specific observation that is related to a recommended action. **Recommendation or general guidance based on this observation.**
  
* Specific observation that is related to a recommended action. **Recommendation or general guidance based on this observation.**
  


# Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

* Assumption 1 (ex: missing country records were for customers based in the US, and were re-coded to be US citizens)
  
* Assumption 1 (ex: data for December 2021 was missing - this was imputed using a combination of historical trends and December 2020 data)
  
* Assumption 1 (ex: because 3% of the refund date column contained non-sensical dates, these were excluded from the analysis)



