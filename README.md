# Digital_marketing
Data-Driven Insights for Digital Marketing Campaigns
The primary objective is to analyze marketing data, create dashboards, and share actionable insights to optimize digital marketing campaigns.

An analysis of Google Analytics 4 (GA4) data, built as a Power BI dashboard. The goal is to understand which channels, audiences and landing pages bring users and conversions, and where marketing spend gives the best return.

 Domain:Marketing & Advertising
 Tools:Excel (data prep), Power BI (analysis and dashboard)

---

Problem Statement

Marketing campaigns often run without clear insights, so it is hard to see what works and what wastes budget. This project turns raw GA4 data into KPIs and an interactive dashboard that supports data-driven decisions and better ROI.

---

Dataset

GA4 export with multiple sheets:

| Sheet | What it contains |
|---|---|
| Landing Page | Sessions, users, new users, avg. engagement time, key events, revenue |
| Channel Group (first user) | Users, engaged sessions, cost, impressions, key events, revenue |
| Session Primary Channel Group | Users, sessions, engaged sessions, engagement rate, key events, revenue |
| Age, Gender, Country, Interests | Audience breakdown of users |

---

 Data Cleaning

The data was already clean. Only one fix was needed:

-Average engagement timewas stored as text in minutes (e.g. `2m 30s`).
- In Excel, I split the text, trimmed the spaces, converted minutes to seconds (`minutes * 60`), and joined the parts with `=` to build a formula in a helper column.
- Everything else (analysis, KPIs, visuals) was done in Power BI.

---

KPIs Calculated

| KPI | Formula |
|---|---|
| CTR | Key events / Impressions x 100 |
| CPC | Spend / Key events |
| ROI | (Revenue - Cost) / Cost x 100 |
| Conversion Rate | Key events / Engaged sessions x 100 |

These were created as DAX measures in Power BI.

---

Dashboard

The dashboard has 4 pages.

- 1. Landing Page Analysis
![Landing Page Analysis](images/landing_page_analysis.PNG)

- 2. Audience Analysis (Age, Gender, Country, Interests)
![Analysis by Age and Country](images/analysis_based_on_age_and_country.PNG)

- 3. Channel Analysis (Traffic Acquisition)
![Digital Marketing Channel Analysis](images/digital_marketing_channel_analysis.PNG)

- 4. Marketing Performance Dashboard (ROI and Cost vs Revenue)
![Digital Marketing Dashboard](images/digital_marketing_dashboard.PNG)

---

Key Insights

 Landing pages 
- The home page (`/`) gets the most sessions (about 67K), followed by `(not set)` (about 26K). All other pages get very few sessions.
- The pages that produce the most key events are product pages, then `/shop/apparel` and `/checkout`. Product pages are what drive actions, not the home page.

 Audience 
- Conversion rate is highest for ages35-44, 45-54 and 25-34 , and drops sharply for55-64 and 65+ .
- TheUnited Stateshas by far the most users, followed by Canada and India.
-Taiwanhas the highest conversion rate by country, even though its user count is small.
-Technologyis the top interest category.
- A large share of users haveunknownage and gender.

 Channels 
-Directbrings the most sessions (about 76K), but has a low engagement rate (38%) and the lowest conversion rate among the main channels (0.2).
-Organic VideoandReferralhave the best engagement and conversion rates, but very low traffic.
-Organic Searchis the second biggest source of sessions (about 11K) and has a solid engagement rate (about 65%).
-Paid SearchandEmailshow 0% engagement rate in the session data, which needs checking.

 Cost and ROI 
- Overall: conversion rate 38.63%, total revenue about 5.07K, CPC 0.04, ROI 684.30.
-Organic Searchgives the best return, with revenue of about 2.8K against a cost of about 0.1K (ROI about 2,237).
-Directhas a positive ROI (about 136).
-Cross-network, Organic Shopping and Organic Socialhave an ROI of -100 (spend with no revenue).

---

Recommendations

1. Invest more inOrganic Search , since it has the highest ROI.
2. GrowOrganic Video and Referraltraffic. These channels engage and convert well but are small today.
3. Improve thehome pagewith clearer links to product pages, since product pages drive the most key events.
4. Target the25-54 age group , which converts best.
5. Review or pause spend on channels with an ROI of -100.
6. Fix tracking for `(not set)` landing pages and unknown age/gender to get cleaner data.

---

Limitations

- Many users have unknown age and gender, and many sessions have `(not set)` as the landing page.
- Some channels have very low volume, so their rates can look extreme.
- Cost data is only available for some channels.

---

Repository Structure

```
data/Raw # GA4 Raw dataset (Excel)
data/Cleaned #Cleaned file
Screenshots/# Dashboard screenshots
PowerBI/ #.pbix # Power BI file
Report_and_recommendations/ PPT file

README.md
```

---

How to Use

1. Download the `.pbix` file from this repository.
2. Open it in Power BI Desktop.
3. Use the slicers (Age, Gender, Country, Channel) to explore the data.
