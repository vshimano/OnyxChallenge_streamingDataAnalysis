# OnyxChallenge_streamingDataAnalysis

# Onyx Data Challenge — Music Streaming Platform Analysis (May 2025)

A Power BI dashboard submitted to the [Onyx Data DataDNA Challenge](https://onyxdata.co.uk/data-dna-dataset-challenge/) — May–June 2025. The challenge dataset represents a fictional music streaming platform operating across 10 countries from 2021 to 2024, with data covering users, listening behaviour, subscription lifecycle events, content, and revenue.

---

## Challenge Context

Music streaming platforms face a range of operational and strategic challenges: fragmented visibility across users and subscription tiers, difficulty distinguishing engaged users from those at risk of churn, complex revenue signals distributed across multiple event types, and the ever-present risk of fraudulent or bot-like activity distorting performance metrics. This dashboard addresses those challenges through structured, multi-page analysis.

---

## Dataset Overview

| Dimension | Detail |
|-----------|--------|
| Period | 2021–2024 |
| Countries | 10 (Australia, Brazil, Canada, France, Germany, Japan, South Africa, Sweden, United Kingdom, United States) |
| Users | 961 |
| Listening sessions | ~224,000 |
| Subscription events | ~3,640 |
| Tracks | 774 |
| Artists | 448 |

**Data model:** Star schema with 2 fact tables (`fact_listening_session`, `fact_subscription_event`), 9 dimension tables, and 1 bridge table connecting playlists to tracks.

---

## Business Questions

1. **Revenue Health** — Is MRR growing, and which subscription events drive or erode it?
2. **User Segmentation** — Which tiers generate the most value, and how are users distributed globally?
3. **Churn Risk** — Which behavioural signals predict churn, and which do not?
4. **Fraud** — How pervasive is bot-like activity, and does it follow identifiable patterns?
5. **Content & Catalogue** — Which genres and artists drive engagement, and does algorithmic recommendation add value?

---

## Key Findings

### Revenue & Subscriptions
- MRR grew **+12.06% in 2024** but is decelerating — from 50% growth in 2022 to 25% in 2023 to 12% in 2024
- **Downgrades accelerated in 2024** — the most significant strategic risk signal in the data
- Users are evenly split across tiers (34% Family / 33% Premium / 32% Free), yet **Family generates 60% of revenue**
- ARPU grew **+30.15% in 2024** — revenue per user is improving despite the deceleration in total MRR growth
- Free tier generates **$0 subscription MRR** but contributes ad revenue through listening sessions

### Churn & Engagement
- **Session duration predicts churn** — retained users average ~1.67 min/session vs ~1.49 min for churned users, consistent across all tiers
- **Skip rate does not predict churn** — contrary to expectations, skip rates are similar between retained and churned users
- **New artist discovery predicts churn** — retained users discover more new artists across every tier and genre
- Annual churn rate: **16.4%** | Customer retention rate: **83.6%**

### Fraud
- **482 of 961 users (50%) are flagged** as belonging to a fraud cluster
- Fraud sessions account for **40–95% of sessions** depending on the hour
- **95.8% of midnight sessions are fraudulent** — dropping to ~40% during evening hours
- The overnight fraud spike is **uniform across all 10 countries** — this is a platform-wide systematic issue, not a regional one
- **Pop and Rock have the highest fraud session rates** (80%+); Electronic and Hip-Hop the lowest (45–48%)
- Fraud cluster users have **shorter session durations and lower skip rates** — consistent with bot-like looping behaviour rather than human listening

### Content & Catalogue
- **Pop and Rock** drive the most sessions across all tiers
- **Electronic** leads in new artist discovery rate (~19% for Free tier) — mainstream genres (Pop, Rock) show the lowest discovery rates
- **Algorithmic recommendations** drive more sessions than user-selected tracks but do not generate proportionally more revenue
- **Free tier discovers more new artists** than paid tiers across almost every genre — possibly reflecting exploratory behaviour without subscription commitment

---

## Dashboard Structure

| Page | Focus |
|------|-------|
| Executive Overview | 5 KPIs: Net MRR Growth, User Growth, ARPU, Customer Retention, Avg Session Duration |
| Revenue & Subscription Analysis | MRR trend, revenue drivers by event type, tier distribution, global user map |
| Engagement & Churn Risk | Session duration vs churn, skip rate vs churn, new artist discovery vs churn, fraud cluster behaviour |
| Listening Patterns & Fraud Detection | Sessions by month and day of week, listening activity by hour and country |
| Content & Catalogue | Genre preference by tier, artist discovery by genre, algorithm impact, top artists by session |

**Tooltip pages:** Country Detail, Fraud & Churn Detail, Hour Fraud Detail, Genre Revenue Detail, Artist Detail

---

## Tools & Technologies

| Category | Tools |
|----------|-------|
| Dashboard | Power BI Desktop |
| Data modelling | DAX, Power Query |
| Data model | Star schema, calculated columns, bridge table |
| Visualisations | Clustered column charts, line charts, filled map, donut charts, KPI cards |

---

## Repository Structure

```
Onyx_MusicStreaming_Challenge/
├── MusicStreaming_Dashboard.pbix   # Power BI report file
└── README.md                       # This file
```

---

## Limitations

- Dataset is synthetic — findings describe patterns within the fictional platform and are not generalisable to real-world streaming services
- Fraud flagging is based on a pre-existing `is_fraud_cluster` column in the data — the clustering methodology is not disclosed
- ARPU is calculated as total estimated revenue (ad + subscription) divided by active listeners — a different definition than traditional MRR-based ARPU
- Causal relationships cannot be established from observational data — session duration and discovery rate correlate with churn but do not necessarily cause it

---

## Author

**Victoria Shimanovich**  
PhD in Applied Mathematics | Data Analytics  
[LinkedIn](https://www.linkedin.com/in/your-profile) | [GitHub](https://github.com/your-username)
