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

**Platform:** Maven Analytics

**Dataset:** `https://mavenanalytics.io/data-playground/financial-consumer-complaints`

**Source:** Consumer Financial Protection Bureau

**License:** Public Domain

**Data Dictionary**

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


---

## 4. Data Preparation

---





## 6. Key Findings


---

### Finding 1 — 250K Sessions Lost Per Cycle: The Problem Isn't the Ads, It's the Platform


 
**The insight:** Near-identical rates across all five channels eliminate ad quality as the root cause. Anonymous users hit a mandatory registration wall at the exact moment of highest purchase intent. This is a platform-level architectural barrier — not a media planning problem.

**Why it matters:** Approximately **250,000 sessions per cycle** are abandoned at the product page. These users are already on the platform, already paid for. Any improvement here requires zero additional acquisition spend.

---

### Finding 2 — Same Audience, Every Channel: Budget Reallocation Won't Fix This




**The insight:** The platform attracts the same audience composition regardless of channel. Shifting budget from Email to Adwords or Facebook does not change the type of user arriving — and therefore does not change the conversion outcome.
 
**Why it matters:** This suggests that the root cause is structural — the fix likely resides in product and engineering rather than media planning. Email's position as highest-volume channel makes it the single largest immediate opportunity — improving the Anonymous conversion experience on Email-sourced sessions alone could impact 224K sessions per cycle.

---

### Finding 3 — $331K Revenue in Active Deterioration (and $226K More Approaching the Edge)


**The insight:**

- At Risk and Cant Lose Them together contribute approximately **$331K (29.8% of total revenue)** despite showing prolonged inactivity patterns, making them the platform's most immediate retention priority.
- Loyal Customers remain active and contribute an additional **$226K (20.4%)**, but their purchase-gap behavior suggests a portion of the segment may require preventive engagement before transitioning into higher-risk inactivity patterns.
- Rather than interpreting this as guaranteed future revenue loss, the analysis highlights where retention monitoring and intervention efforts are likely to have the highest business relevance.

---

### Finding 4 — The Behavioral Clock: At Risk Customers Have Already Churned


**The insight:** At Risk customers are not "buying less often" — at 480 days vs the 91-day Champions benchmark, they exhibit behavioral patterns consistent with advanced disengagement. They simply haven't been classified as lost yet. The difference between Champions and At Risk suggests a meaningful behavioral shift rather than a simple gradual decline in activity.
 
**Why it matters:** Interval data determines intervention timing across all phases. Loyal Customers should be contacted at day 150 — before the 188-day threshold, not after.

---

### Finding 5 — Category Affinity: The Personalization Map Already Exists in the Data


**The insight:** At Risk customers were Jeans and Outerwear buyers before they became inactive. They are disengaged premium fashion buyers — not price-sensitive shoppers. A win-back email referencing their specific category ("Your favorite Jeans collection is waiting") is the right message, not a generic discount.
 
**Why it matters:** Precise sub-bucket targeting is possible without additional data collection. The personalization input already exists in purchase history — sub-buckets for At Risk: Jeans lovers · Fashion Hoodies lovers · Outerwear lovers.

---

### Finding 6 — Dataset Constraint: Low Frequency Is an Artifact

Even Champions average only 1.5 orders; Loyal Customers average 1.4. This is atypically low for fashion e-commerce — real-world Champions typically show 4–8+ orders per year.

**Why this matters:** This reflects a limitation of the synthetic TheLook dataset, not actual retention performance. To avoid amplifying this artifact, all financial projections in this analysis use AOV (not CLV) as the multiplier. RFM scoring remains valid as a relative ranking tool within this dataset, but absolute frequency thresholds would need recalibration for real business data.

---

## 7. Dashboard

Designed as a single narrative arc — not a daily monitoring tool, but a self-contained story flowing from problem identification to recommendation foundations.

🔗 [Open Dashboard in Looker Studio →](https://datastudio.google.com/reporting/fe05a7e8-44a2-4b7b-b4dd-2d945c90b409)

<img width="1020" alt="TheLook_E-commerce__Retention_ _Acquisition_Analysis_Dashboard" src="https://github.com/user-attachments/assets/b9e07b38-bc80-4fcc-be08-6ccecb83d599" />

**Layout:**
- **Top row** — 5 KPI scorecards: immediate executive summary before any chart is read
- **Upper section** — Acquisition story: funnel drop-off per channel (left) + session volume by user type (right)
- **Bottom left** — RFM Segment Bubble Map: revenue-at-risk in one view
- **Bottom right** — Purchase interval per segment (center) + Category affinity heatmap (right)

---

## 8. Insights & Strategic Recommendations
> *The recommendations below are based on observed behavioral patterns within the available dataset. Revenue figures represent historical contribution, not guaranteed future loss or recovery projections. Where future outcomes are discussed, they are framed as directional opportunities requiring validation through experimentation.*

### 8.1 Key Findings Summary

**Objective 1 — Acquisition:**
1. **Structural acquisition barrier:** ~250,000 sessions per cycle (per dataset) are lost between product view and purchase completion. The near-identical funnel pattern across channels strongly suggests a platform-level friction point — likely related to registration or checkout access requirements — rather than channel quality itself.
2. **Channel-agnostic drop-off:** The ~50% product-to-cart rate and 0% cart-to-purchase rate are identical across all five channels, indicating the issue is likely platform-wide and cannot be solved by reallocating marketing budget.

**Objective 2 — Retention:**

3. **Revenue concentration risk:** The top 4 segments account for 73% of total revenue. At Risk and Cant Lose Them together contribute $331K (29.8%) from segments in active deterioration, while Loyal Customers ($226K) are approaching behavioral thresholds associated with higher inactivity risk.
4. **Behavioral churn signal:** At Risk customers are purchasing at 5× the interval of Champions (480 vs 91 days) — suggesting that spontaneous re-engagement becomes increasingly unlikely without intervention.
5. **Untapped activation window:** Potential Loyalist (2,866 users, $205K revenue) are largely one-time buyers with a recency of just 36 days — creating a meaningful opportunity to encourage second-purchase behavior and future customer value growth.
6. **Category anchor:** Jeans consistently appears as the top revenue-driving category across premium segments (more than 10% revenue constribution per each premium segment) — consistently the #1 revenue driver for Champions, Loyal Customers, At Risk, and Cant Lose Them alike, enabling precise personalization without additional data collection.

---

### 8.2 What We Know About Potential Downside

Without intervention, the following revenue is associated with segments already showing deterioration:

| Segment | Revenue (12 mo) | Current Status |
|---------|-----------------|----------------|
| At Risk | $245,441 | Already inactive (248 days) |
| Cant Lose Them | $85,653 | Already inactive (309 days) |

Loyal Customers ($226,086) remain active but show early warning signs (approaching 188-day purchase gap). The proportion that would deteriorate without intervention cannot be accurately predicted from available data.

**What this means:** The $331K from already-deteriorating segments represents revenue that is unlikely to recover passively. For Loyal Customers, the appropriate next step is preventive monitoring — not assuming they will churn.

---

### 8.3 Pillar 1 — Acquisition Optimization (Anonymous Users)
 
**Problem:** Funnel analysis reveals two separate conversion barriers among Anonymous users:

- Approximately half of sessions never progress from product view to cart, suggesting a persuasion or purchase-intent issue.
- Sessions that do reach cart cannot complete checkout due to the mandatory registration requirement, resulting in a 0% cart-to-purchase rate.

Together, these drop-offs represent a significant loss of already-acquired traffic.
 
**Approach: Zero Additional Marketing Spend** — Improve conversion efficiency from existing traffic before increasing acquisition spend. Experiments are sequenced to isolate the effect of persuasion improvements versus checkout-friction reduction.
 
**Phase 1 — Product Page Optimization (Persuasion)**
 
| Element | Detail |
|---|---|
| Hypothesis | Adding social proof elements may improve product-to-cart progression |
| Design | A/B test on product page UI — Group A (standard layout) vs Group B (social proof + ratings visibility) |
| Randomization unit | session_id |
| Primary metric | Product-to-cart rate |
| Guardrail metric | Page load time must not increase materially |
| Success threshold | Positive statistically significant lift vs control |
| Potential implication (to be measured) | Higher downstream checkout opportunities if more users progress into cart |
| Exit criteria | If lift remains negligible after test period, prioritize friction-reduction experiments instead |
 
**Phase 2 — Cart Friction Reduction (One-Tap Sign-In)**
 
| Element | Detail |
|---|---|
| Hypothesis | Reducing registration friction may improve cart-to-registration progression |
| Design | A/B Test — Group A (standard registration flow) vs Group B (One-Tap Google Sign-In) |
| Randomization unit | session_id |
| Primary metric | Cart-to-registered-lead rate |
| Guardrail metric | Registration page bounce rate must not increase |
| Benchmark reference | Simplified checkout flows are commonly associated with improved conversion completion in e-commerce UX studies |
| Success threshold | Measurable lift relative to control group |
| Exit criteria | If impact remains limited, the barrier may require broader checkout-flow redesign |
 
---

### 8.4 Pillar 2 — Retention: Phase 1 (Reactive Win-back)
 
**Problem:** $331K in revenue (29.8%) sits within two deteriorating segments that have stopped purchasing but whose category preferences and contact information are known.
 
**Why Email?** Email accounts for 44.8% of all registered user sessions (81,421 of 181,741 combined sessions). Near-zero variable cost — leverages an existing database with no incremental acquisition spend.
 
**Why sequential, not parallel?** Running At Risk and Cant Lose Them simultaneously would split team focus, complicate measurement, and reduce the learnings transferable from one campaign to the next. At Risk goes first because its revenue pool is nearly 3× larger.
 
---

#### Phase 1A — At Risk Win-back (Weeks 1–3)
 
**Rationale for priority:** Largest single revenue-at-risk pool ($245K, 22.1% of total). The segment size is large enough to support an initial controlled experiment and directional measurement.

| Element | Detail |
|---|---|
| Strategy | Stratified A/B Test based on historical category affinity |
| Sub-buckets | Jeans lovers · Fashion Hoodies lovers · Swim lovers |
| Randomization | Independent 50/50 split within each subgroup |
| Group A (Control) | Generic re-engagement email |
| Group B (Treatment) | Personalized category-based re-engagement email |
| Conversion window | 30 days |
| Primary metric | Re-activation rate |
| Guardrail metric | Unsubscribe rate |
| Success threshold | Positive lift relative to control group |
| AOV reference | $105.24 (calculated from segment transaction data) |
| Revenue implication | Due to the segment's size (2,171 users) and existing purchase history, even modest improvements in re-activation rate may create meaningful incremental revenue without additional acquisition spend. |
| Exit criteria | If lift remains negligible, alternative channels or incentive structures should be evaluated |

---

#### Phase 1B — Cant Lose Them Win-back (Weeks 3–6, after Phase 1A results are measured)
 
**Rationale for sequencing after At Risk:** Although the revenue pool is smaller ($85K, 7.7%), this segment shows one of the platform's highest average transaction values ($152.89) and strong affinity toward premium categories such as Outerwear & Coats and Jeans. Results from Phase 1A serve as a directional learning input before expanding personalization efforts into a smaller but higher-value cohort.
 
**Why this segment still warrants intervention despite smaller population size:** The segment combines prolonged inactivity with relatively high AOV and CLV, suggesting that even limited re-activation improvements may produce meaningful business impact on a per-customer basis.
 
| Element | Detail |
|---|---|
| Strategy | Category-personalized win-back email |
| Focus categories | Jeans + Outerwear & Coats |
| Incentive approach | Test different re-engagement approaches (e.g., urgency framing, category personalization, or selective incentives) while monitoring margin impact |
| Group A (Control) | Generic re-engagement email |
| Group B (Treatment) | Personalized category-focused re-engagement email |
| Conversion window | 30 days |
| Primary metric | Re-activation rate |
| Guardrail metric | Net margin after discount must remain positive |
| AOV reference | $152.89 (calculated from segment transaction data) |
| Strategic implication | Despite smaller population size, the segment's higher AOV increases the value of each successful re-activation |
| Exit criteria | If net margin after campaign goes negative, reduce incentive or pause campaign |
 
---

### 8.5 Pillar 3 — Retention: Phase 2 (Preventive & Growth)

> Phase 2 runs in parallel after Phase 1A is launched. These are automated triggers — near-zero ongoing effort after initial setup.
>
> These interventions prioritize low-cost CRM automation as an initial experimentation layer. Additional channels (e.g., push notifications, onsite personalization, or paid retargeting) may be evaluated after baseline effectiveness is established.

---

#### Phase 2A — Loyal Customers: Pre-gap Triggered Email (Month 2, ongoing)
 
**Rationale:** This segment remains active (recency 92 days) and contributes $226K (20.4% of total revenue). Their average purchase gap is 188 days, making day 150 a potential intervention point to test whether early re-engagement can influence purchase behavior before the segment's historical average repurchase interval is reached.
 
| Element | Detail |
|---|---|
| Trigger | Automated email at day 150 post-last-purchase (38 days before the 188-day avg threshold) |
| Content | New arrivals in Jeans or Outerwear — initial test avoids discounting to evaluate whether reminder-based re-engagement alone influences purchase timing |
| Design | A/B test: Group A (no trigger) vs Group B (receives day-150 email) |
| Primary metric | Purchase rate before day 188 |
| Guardrail metric | Unsubscribe rate |
| Success threshold | Higher purchase rate in treatment group vs control |
| AOV reference | $128.88 (calculated from segment transaction data) |
| Revenue implication | This is a preventive intervention — the goal is to learn whether early re-engagement can influence purchase timing. Any reduction in revenue loss would need to be measured post-experiment. |
| Ongoing effort | Near-zero after initial automation setup |
 
> *Note: "Revenue defended" is not projected here because the natural churn rate for this segment without intervention cannot be determined from available data. The experiment is designed to measure whether the trigger has any detectable effect on purchase timing.*

---
 
#### Phase 2B — Potential Loyalist: Second Purchase Activation (Month 2–3)
 
**Rationale:** The 672-day avg_gap for this segment is a measurement artifact — it reflects the gap calculation across a multi-year dataset for users who have largely made only one purchase. The operative signal is their **recency of 36 days**. The segment size (2,866 users, $205K revenue) makes it a meaningful population for testing second-purchase activation strategies.
 
| Element | Detail |
|---|---|
| Trigger | Automated email at day 30 post-first-purchase |
| Content | Second-purchase voucher, personalized to first-purchase category (Intimates / Sleep & Lounge / Tops & Tees) |
| Design | This experiment primarily evaluates timing effectiveness rather than absolute incremental lift, since both groups receive an intervention. |
| Primary metric | Second purchase rate within 60 days |
| Guardrail metric | Voucher redemption rate |
| Success threshold | Positive lift in second purchase rate vs control (or between timing groups) |
| AOV reference | $71.39 (calculated from segment transaction data) |
| Revenue implication | This segment represents one-time buyers with recent activity. Even modest improvements in second purchase conversion could meaningfully affect long-term customer value trajectories. |
| Ongoing effort | Near-zero after automation setup |

> *Note on benchmarks: Industry second-purchase rates for one-time buyers vary widely (5-15% depending on category and incentive). Actual lift will be measured from the A/B test.*

---
 
#### Phase 2C — Champions: Value Maximization (Month 2–3, parallel)
 
**Rationale:** Champions are the healthiest segment — no rescue required. This intervention is opportunistic: test whether cross-sell recommendations can increase AOV without negatively affecting cart abandonment.

| Element | Detail |
|---|---|
| Strategy | Automated cross-sell recommendations at checkout |
| Recommendation logic | Jeans purchasers shown Fashion Hoodies & Sweatshirt / Sweaters (based on observed category affinity in this segment) |
| Design | A/B test — Group A (standard cart) vs Group B (cart + cross-sell) |
| Primary metric | Average Order Value (AOV) |
| Guardrail metric | Cart abandonment rate |
| Success threshold | Higher AOV in treatment group without material increase in cart abandonment |
| AOV reference | $121.94 (calculated from segment transaction data) |
| Revenue implication | If successful, this could increase per-transaction value for the platform's healthiest segment without additional acquisition cost. |
| Exit criteria | If cart abandonment increases meaningfully in treatment group, reduce recommendation prominence or pause |

> *Note: No AOV lift is projected here because the effect size cannot be known before the experiment. The test is designed to measure whether cross-sell recommendations have a detectable impact on transaction value.*

---
 
### 8.6 What We Won't Do (and Why)
 
**Hibernating & About to Sleep are not active win-back targets.** AOV of $42–$44 and CLV of ~$38, combined with purchase gaps exceeding 600 days, make the ROI case difficult to justify against higher-value opportunities. These segments are placed into an **automated low-touch email sequence every 3 months** — preserving optionality at negligible cost without committing resources better allocated elsewhere.
 
---
 
### 8.7 Exit Criteria
 
A recommendation without exit criteria is a commitment without conditions.
 
| Phase | Continue if | Adjust if | Stop if |
|---|---|---|---|
| At Risk win-back | Meaningful positive lift vs control | Positive but modest lift | No detectable lift after test window |
| Cant Lose Them | Margin remains positive | Margin compression observed | Margin turns consistently negative |
| Loyal Customers trigger | Earlier repurchase behavior improves | Engagement low but directional improvement exists | Unsubscribe or disengagement materially increases |
| Potential Loyalist trigger | Second purchase conversion improves vs baseline | Timing effect unclear | No meaningful behavioral difference observed |
| Champions cross-sell | AOV improves without material abandonment increase | Slight abandonment increase observed | Abandonment materially worsens |
| Acquisition Phase 1 | Product-to-cart conversion improves | Positive but inconclusive result | No detectable conversion improvement |
 
---
 
## Limitations & Methodology Notes
 
1. **Synthetic dataset:** TheLook is a generated dataset. `cart_to_purchase = 0%` for Anonymous and uniformly low `avg_orders` are by-design artifacts, not real business signals. Findings are directionally valid — not operationally prescriptive without real-data calibration.
2. **RFM trailing window vs. full history:** RFM scoring uses a 1-year trailing window. Large avg_gap values in At Risk (480 days) draw on multi-year purchase history beyond this window — inactivity severity should be validated against real business baselines before operational use.
3. **Potential Loyalist avg_gap:** The 672-day figure is a measurement artifact for largely single-purchase users. Recency (36 days) is the operative signal for this segment.
4. **AOV over CLV:** All financial projections use AOV as the multiplier — a deliberate choice to avoid amplifying the low-frequency artifact in this dataset. Champions average only 1.5 orders; real-world Champions would show 4–8+. CLV projections would silently overstate returns.
5. **A/B tests are forward-looking:** Historical data cannot be retroactively randomized. All experiment designs are recommendations to execute going forward.
6. **RFM as a relative ranking tool:** Segmentation remains valid for comparing value between segments within this dataset. Absolute frequency thresholds require recalibration against real business data before deployment.

---

*Dataset: [TheLook Ecommerce — Google BigQuery Public Data](https://console.cloud.google.com/marketplace/product/bigquery-public-data/thelook-ecommerce)*

*SQL: [SQL for Data Cleaning & Feature Engineering](https://github.com/nafidza/TheLook-Project/blob/main/sql-queries.sql)*

*EDA: [Python for EDA — Google Colab](https://colab.research.google.com/drive/1YXuW8Oy3rV-GknxEYwetqXd3Xl7fZ15n?usp=sharing)*

*Dashboard: [Looker Studio](https://datastudio.google.com/reporting/fe05a7e8-44a2-4b7b-b4dd-2d945c90b409)*
