# Global Airbnb Performance Dashboard

An end-to-end Power BI project analyzing Airbnb listing, host, and review data across 10 major global cities — built to uncover growth trends, host quality signals, and city-level rating patterns.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-217346?style=flat)

---

## Overview

This project turns raw Airbnb listing and review data into an interactive Power BI dashboard covering:
- **Overview** — platform growth over time, room type mix, and headline KPIs
- **Ratings** — city-level rating performance, host quality (Superhost share), and pricing by room type
- **Reviews** *(in progress)* — reviewer frequency distribution and host trust indicators (identity verification / profile completeness)

The dashboard is designed as a portfolio piece demonstrating data modeling, DAX measure design, and dashboard storytelling — not just default chart drops.

---

## Dataset

Sourced from Inside Airbnb–style listing and review exports across **10 cities**: Paris, Rome, New York, Sydney, Mexico City, Rio de Janeiro, Cape Town, Bangkok, Istanbul, and Hong Kong.

| File | Rows | Description |
|---|---|---|
| `Listings.csv` | ~279,700 | One row per listing: host details, location, property/room type, pricing, and review-score breakdowns |
| `Reviews.csv` | ~5,373,000 | One row per review: `listing_id`, `review_id`, `date`, `reviewer_id` |
| `Listings_data_dictionary.csv` | 33 fields | Field-level definitions for the Listings table |
| `Reviews_data_dictionary.csv` | 4 fields | Field-level definitions for the Reviews table |

**Data model:** `Listings[listing_id]` (1) → `Reviews[listing_id]` (many), with a Date table related to `Reviews[date]` for time-intelligence.

---

## Tools
Power BI Desktop · DAX · Power Query (M) · Git LFS (for hosting the `.pbix` on GitHub)

---

## Report Pages

### 1. Overview
- KPI cards: total cities, total hosts, most common property type, total reviews, total listings
- **Line chart** — new listings by year, broken out by room type (Entire Place, Private Room, Shared Room, Hotel Room), annotated with platform lifecycle stages (Introduction → Growth → Maturity → COVID-19 dip → Reinvention)
- Narrative callout on the 2015 listings peak, the 2016–17 profitability turnaround, and the 2019–20 COVID slowdown

### 2. Ratings
- **Combo chart (line + stacked column)** — Superhost vs. non-Superhost listings by city, with a cumulative % line
- **Clustered bar chart** — average price by room type
- **Clustered column chart** — average overall rating by city
- **Pivot table** — detailed sub-ratings by city (Accuracy, Cleanliness, Communication, Location, Value)
- Narrative callout: Paris, NYC, and Sydney account for ~48% of total reviews; Mexico City and Rio rate highest overall, Hong Kong and Istanbul lowest — with Cleanliness and Value consistently the weakest sub-scores

### 3. Reviews *(planned)*
- Reviewer frequency distribution (how many reviews a typical reviewer leaves)
- Cumulative % of reviewers by review count, highlighting outlier "power reviewers"
- Seasonality of reviews by city (ribbon chart)
- Host trust indicators: identity verification × profile picture completeness

---

## Key Insights
- Airbnb listings grew steadily from launch through 2015, dipped in 2015–16, returned to full-year growth by 2017, then stalled again with COVID-19 in 2019–20
- Paris, New York, and Sydney together account for **almost half of all listings and 48% of reviews**
- Mexico City and Rio de Janeiro are the **highest-rated** cities overall; Hong Kong and Istanbul the **lowest**
- **Cleanliness** and **value-for-money** are the most consistently weak sub-ratings across cities — a candidate lever for host-side improvement programs

---

## How to Use

```bash
git clone https://github.com/<your-username>/airbnb-performance-dashboard.git
```

The `.pbix` is tracked via **Git LFS** (file size ~260 MB, over GitHub's 100 MB direct-push limit). Make sure Git LFS is installed before cloning:

```bash
git lfs install
git clone https://github.com/<your-username>/airbnb-performance-dashboard.git
```

Open `airbnb_dashboard.pbix` in **Power BI Desktop** to explore the report. Raw source files (`Listings.csv`, `Reviews.csv`) and their data dictionaries are included for reference/reproducibility.

---

## Project Structure

```
airbnb-performance-dashboard/
├── airbnb_dashboard.pbix              # Power BI report (tracked via Git LFS)
├── data/
│   ├── Listings.csv
│   ├── Listings_data_dictionary.csv
│   ├── Reviews.csv
│   └── Reviews_data_dictionary.csv
├── .gitattributes                     # Git LFS tracking rules
└── README.md
```

---

## Author
**[aakash jaiswar]** — [www.linkedin.com/in/aakash-jaiswar

](#) · [[GitHub](https://github.com/aakashjaiswar007)](#)
