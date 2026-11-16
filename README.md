# Consumer Financial Protection Bureau (CFPB): Financial Consumer Complaints Analytics

An end-to-end data analytics project using Microsoft Excel to analyze Bank of America's consumer complaints from 2017 to 2023. The project aims to identify complaint trends, understand recurring financial product issues, evaluate company response patterns, and provide actionable recommendations to improve customer experience and operational performance.

**Jump to:**

1. [Why This Matters](#why-this-matters)
2. [Project Background](#project-background)
3. [Data Structure](#data-structure--initial-checks)
4. [Executive Summary](#executive-summary)
5. [Insights Deep Dive](#insights-deep-dive)
6. [Recommendations](#recommendations)
7. [Assumptions & Caveats](#assumptions-and-caveats)

# Why This Matters

Consumer complaints are a direct signal of where a company's products, service, or processes are breaking down. For a bank the size of Bank of America, even a small percentage shift in complaint volume represents thousands of frustrated customers — and a compliance risk with regulators like the CFPB. This project turns raw complaint data into a clear view of _where_ friction is happening, _how fast_ it's being resolved, and _what_ should be prioritized next.

# Project Background

Bank of America operates in the financial services industry, serving consumers through various financial products, including checking and savings accounts, credit cards, mortgages, and loans.

As a financial institution, the company must manage consumer complaints submitted through the Consumer Financial Protection Bureau (CFPB). Analyzing these complaints provides an opportunity to understand customer dissatisfaction, identify recurring issues, and evaluate the company's complaint-handling performance.

This project analyzes consumer complaints submitted between 2017 and 2023 to identify patterns and potential operational gaps.

**The analysis focuses on four key areas:**

- **Complaint Trends:** Identify annual, quarterly, and monthly complaint patterns.
- **Product and Issue Analysis:** Determine which financial products and issues generate the highest complaint volumes.
- **Company Response Analysis:** Evaluate how the company responds to and resolves consumer complaints.
- **Response Timeliness:** Investigate patterns associated with untimely company responses.

**Analytical Questions:**

1. Do consumer complaints show seasonal or temporal patterns?
2. Which financial products generate the most complaints, and what are their most common issues?
3. How are consumer complaints typically handled and resolved?
4. What insights can be identified from complaints with untimely responses?

**Tools:** Microsoft Excel

**Dataset:** [Financial Consumer Complaints – Maven Analytics](https://mavenanalytics.io/data-playground/financial-consumer-complaints)

**Data Source:** Consumer Financial Protection Bureau (CFPB)

**Analysis Period:** 2017–2023

**Note on Scope:** The underlying dataset spans 2017–2023. However, the detailed metrics in this report — including the 9,131-case total and monthly trend analysis — reflect the January–August 2023 window, the period with the most complete and granular data available for deep-dive analysis.

# Data Structure & Initial Checks

The dataset contains consumer complaint records associated with Bank of America, including submission information, consumer locations, financial products, reported issues, and company responses.

The dataset includes the following key attributes:

- **Complaint ID:** Unique identification number for each complaint.
- **Submitted via:** Channel used to submit the complaint.
- **Date submitted:** Date the CFPB received the complaint.
- **Date received:** Date the CFPB sent the complaint to the company.
- **State:** Consumer's reported state.
- **Product and Sub-product:** Financial product associated with the complaint.
- **Issue and Sub-issue:** Specific problems reported by consumers.
- **Company public response:** Company's optional public-facing response.
- **Company response to consumer:** Company's response or resolution description.
- **Timely response?:** Indicates whether the company provided a timely response (Yes/No).

**Initial Data Quality Checks:**

- Duplicate complaint IDs and records.
- Date format and chronological consistency.
- Missing values in sub-product, sub-issue, and response-related columns.
- Consistency of categorical values.
- Completeness of company response descriptions.
- Missing and inconsistent timely response indicators.

**Data Preparation:**

Data cleaning and transformation were performed using Microsoft Excel. The preparation process included:

- Checking and removing confirmed duplicate records.
- Standardizing categorical values.
- Handling missing values in relevant columns.
- Extracting Year, Month, and Quarter from submission dates.
- Creating Product Category and Issue Category.
- Calculating the interval between CFPB complaint receipt and company referral.
- Creating derived complaint status classifications based on documented response rules.

**Key Formulas & Techniques Used:**

- `IF` / nested `IF` statements to classify derived complaint status from response-description text.
- `DATEDIF` to calculate the interval between CFPB receipt and company referral.
- `PivotTables` for cross-tabulating Product × Timeliness, State × Volume, and Channel × Response status.
- Conditional formatting and slicers to support dashboard interactivity.

The prepared dataset supports temporal analysis, product comparisons, issue classification, geographical analysis, and company response evaluation.

# Executive Summary

### Overview of Findings

Between January and August 2023, total complaint volume reached 9,131 cases, remaining stable at 1,000–1,200 monthly complaints before experiencing a sharp 71.8% spike in July (1,749 cases) and subsequently dropping to a period low of 717 cases in August. The primary driver of customer friction is concentrated in Bank Accounts (4,085 complaints) and Customer Service & Account Management (3,586 complaints), with California, Florida, Texas, and New York accounting for over 46% of all submissions. Overall company performance remains strong with an 83.6% closure rate and 78% timely response rate, though Web submissions and Bank Account issues represent the highest absolute volume of delayed responses.

### Dashboard

![dashboard](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/dashboard.png)

**How to read this dashboard:** The top cards show total complaint volume, closure rate, and timely-response rate at a glance. The center chart tracks monthly complaint trends, while the side panels break volume down by product, state, and submission channel. Use the filters to isolate a specific product or time period.

The Video interactive dashboard can be found [here](https://drive.google.com/file/d/1FjpmM9RbKXqZfwlWRQULeD8Lc6RGBnoV/view?usp=sharing)

The Presentation slides can be found [here](https://docs.google.com/presentation/d/1pvmLhxUX7YFAiYhBU4EB5sRK51rTdY3I/edit?usp=sharing&ouid=114150187847434890312&rtpof=true&sd=true)

The Brief project can be found [here](https://docs.google.com/document/d/1b5swpvRKZlnClwrqJiQujOx_FLEmT9B2/edit?usp=sharing&ouid=114150187847434890312&rtpof=true&sd=true)

# Insights Deep Dive

### 1. Complaint Trends

![Monthly Complaint Trend](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/complaints-trend.png)

- **Core Trend:** Complaint volume remained relatively stable between 1,000 and 1,200 per month across Q1 and Q2 2023.

- **Peak Spike:** July 2023 saw an unusual surge, peaking at 1,749 complaints a **71.8% increase** from June (1,018 complaints).

- **Sharp Drop:** Following the July peak, volume dropped by **59.0%** in August 2023 down to 717 complaints, hitting the lowest point of the period observed.

💡 **Why it matters:** A 71.8% spike in a single month suggests a specific trigger - a policy change, system issue, or external event - rather than normal fluctuation. Identifying the root cause of July's surge could prevent similar spikes from recurring and reduce regulatory scrutiny tied to sudden volume increases.

### 2. Most Complained-About Products

![Product Complaint Volume & Timeliness](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/product-complaints.png)

- **Largest Untimely Volume:** **Bank Accounts** recorded the highest raw count of untimely responses ("No") at **256 complaints**, representing **49.0%** of all non-timely cases (256 out of 522).

- **Highest Untimely Rate (Proportional Risk):** While low in total volume, **Loans** has the highest untimely response rate at **11.5%** (3 out of 26), followed by **Debt Collection** at **6.2%** (15 out of 243) and **Bank Accounts** at **6.3%** (256 out of 4,085).

- **Highest On-Time Resolution:** **Mortgages** achieved the highest timely response rate ("Yes") at **86.4%** (310 out of 359), closely followed by **Money Transfer & Services** at **83.5%** (507 out of 607).

💡 **Why it matters:** Bank Accounts drive both the highest complaint volume and the highest raw count of untimely responses. This combination makes it the single biggest lever for improving overall customer experience — fixing issues here would have a larger impact than addressing any other product category.

### 3. Issue Complaints

![Issue Category Breakdown](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/issue-complaints.png)

- **Highest Untimely Volume:** **Customer Service & Account Management** accounts for the highest raw count of untimely responses ("No") with **217 complaints**, representing **42.5%** of all non-timely cases (217 out of 510).
- **Highest Relative Untimely Risk:** **Bank Accounts & Overdrafts** has the highest proportion of untimely responses at **8.5%** (15 out of 177), followed by **Credit Reporting** at **7.1%** (98 out of 1,382) and **Debt Collection** at **6.3%** (13 out of 207).

- **Highest Timely Resolution:** **Mortgages & Home Loans** achieved the highest timely response rate ("Yes") at **83.2%** (153 out of 184), whereas **Bank Accounts & Overdrafts** had the lowest at **62.1%** (110 out of 177).

💡 **Why it matters:** Customer Service & Account Management issues account for over 42% of all delayed responses. Since this is an internal process (not a product defect), it's one of the most directly fixable pain points — likely tied to staffing, training, or workflow bottlenecks rather than external factors.

### 4. Company Response Performance

![Company Response Status](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/complaints-response.png)

- **High Resolution Rate:** The vast majority of complaints (**84%**) have been resolved and closed.

- **Active Backlog:** A minority share of **16%** of complaints remain actively in progress.

  💡 **Why it matters:** A 16% active backlog means roughly 1 in 6 complaints is still unresolved. If this backlog grows faster than it's cleared, it compounds over time — turning a manageable queue into a systemic delay problem that affects customer trust and regulatory standing.

### 5. Timely Response Rate

![Timely Response Rate](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/resolution.png)

- **Majority Timely Resolved:** The vast majority (**78%**) of complaints have been answered/resolved in a timely manner ("Yes").

- **Pending Workload:** **16%** of complaints are currently pending resolution ("Pending").

- **Untimely Responses:** A small fraction of **6%** were not addressed in a timely manner ("No").

💡 **Why it matters:** While 6% seems small, untimely responses carry outsized regulatory risk under CFPB rules — timeliness violations can trigger compliance reviews regardless of overall resolution quality. Tracking this metric closely protects the company from risk that isn't proportional to its size.

### 6. Geographic Distribution

![Geographic Distribution of Complaints](https://muchammadwr.github.io/consumer-financial-protection-bureau/images/world-map.png)

- **Top Volume States:** **California (CA)** leads by a massive margin with **1,827 complaints** (20.0% of total volume), followed by **Florida (FL)** with **995**, **Texas (TX)** with **749**, and **New York (NY)** with **633**.

- **Geographic Concentration:** The top 4 states combined account for **4,204 complaints** (over **46%** of the 9,131 grand total), showing high concentration in heavily populated states.

- **Low Volume States:** States like **South Dakota (SD)** and **Wyoming (WY)** recorded the lowest counts with just **2 complaints** each.

💡 **Why it matters:** Nearly half of all complaints originate from just 4 states. This means targeted regional interventions — rather than broad nationwide changes — could resolve a disproportionate share of total complaint volume more efficiently.

### 7. Submitted Via Complaints

| Channel         | No      | Pending   | Yes       | Total     | % Timely |
| --------------- | ------- | --------- | --------- | --------- | -------- |
| **Web**         | 473     | 1,303     | 6,188     | 7,964     | 77.7%    |
| **Phone**       | 29      | 132       | 615       | 776       | 79.3%    |
| **Referral**    | 17      | 51        | 247       | 315       | 78.4%    |
| **Postal mail** | 3       | 8         | 65        | 76        | 85.5%    |
| **Total**       | **522** | **1,494** | **7,115** | **9,131** | —        |

- **Dominant Channel:** **Web** is the primary submission method, accounting for **7,964 complaints** (**87.2%** of total volume).

- **Highest Untimely Risk:** **Web** also generates the highest rate of non-timely responses ("No"), representing **90.6%** (473 out of 522) of all untimely complaints across channels.

- **Consistent Timeliness across Channels:** Overall timeliness ("Yes") remains high at around **77% to 85%** across all submission methods, with **Postal mail** showing the highest timeliness rate (**85.5%**).

💡 **Why it matters:** Web is both the dominant channel (87% of volume) and the riskiest for delays. Since digital submissions are likely the easiest to automate and triage, this is a high-leverage opportunity — improving the web complaint pipeline would reduce untimely responses across the majority of all cases.

# Recommendations:

Based on the insights and findings above, we would recommend the Customer Experience, Compliance, and Operations teams at Bank of America to consider the following:

- Complaints spiked 71.8% in July 2023 compared to June, then dropped sharply the following month. **Set up automated monitoring to flag unusual month-over-month complaint spikes early, so the root cause can be investigated before it repeats.**

- Bank Accounts generated the highest complaint volume (4,085) and the highest number of untimely responses (256). **Prioritize process improvements for Bank Account services, as this product category has the largest impact on both complaint volume and response delays.**

- Customer Service & Account Management issues accounted for the highest number of untimely responses (217, or 42.5% of all delayed cases). **Review staffing, training, and workflow processes within Customer Service, since this is an internal bottleneck that can be addressed directly.**

- Web submissions made up 87.2% of total complaint volume and 90.6% of all untimely responses. **Focus digital process improvements on the Web complaint channel first, as fixing it would reduce delays across the largest share of all cases.**

- California, Florida, Texas, and New York together accounted for over 46% of all complaints. **Pilot operational improvements in these four states first, as targeted action here will have the broadest impact relative to effort.**

# Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

- Missing sub-product and sub-issue entries were recoded as "Not specified," assuming these reflect cases where no sub-classification applied or was reported, rather than data entry errors.

- Missing company public response values were recoded as "No public response provided," assuming this reflects an absence of public commentary rather than a failure to respond to the consumer directly.

- Complaint status (e.g., closed, pending) was derived using standardized rule mappings based on response description text, assuming these mappings accurately reflect the true outcome of each complaint.

- The interval between "Date received" and "Date submitted" was assumed to represent only the CFPB-to-company referral time, not the company's actual internal handling or resolution time.

- Complaint volume was treated as a proxy for customer dissatisfaction, assuming it reasonably represents broader friction trends even though it does not capture every dissatisfied customer who did not file a formal complaint.
