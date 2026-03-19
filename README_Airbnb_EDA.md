# 🏙️ Airbnb NYC 2019 — Exploratory Data Analysis

> **EDA Capstone Project · Python · Pandas · Seaborn · Matplotlib**

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat-square&logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=flat-square)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Charting-11557c?style=flat-square)
![Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?style=flat-square&logo=googlecolab)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ajaya210/airbnb_Eda/blob/main/AirBnb_EDA_Project.ipynb)

---

## 📌 Project Overview

This project performs a comprehensive **Exploratory Data Analysis** on the Airbnb NYC 2019 dataset — analysing 48,895 listings across all five New York City boroughs. The goal is to surface actionable insights for three audiences:

- **Hosts** — how to price competitively and choose the right location
- **Investors** — which neighbourhoods offer the best returns
- **Airbnb Strategy** — where growth opportunities and market gaps exist

---

## ❓ Business Questions Answered

1. What are the most popular neighbourhoods and how do prices vary across them?
2. Which room types are most popular and most expensive?
3. Who are the top hosts and how concentrated is host dominance?
4. What factors correlate with higher Airbnb prices?
5. Where do guests leave the most reviews — and what does that signal?
6. What are the minimum stay preferences across NYC?
7. What is the best area for a host to invest in property?

---

## 🗂️ Dataset

**File:** `AB_NYC_2019.csv` — 48,895 rows × 16 columns

| Column | Type | Description |
|--------|------|-------------|
| `listing_id` | Numerical | Unique listing identifier |
| `listing_name` | Text | Listing title |
| `host_id` | Numerical | Unique host identifier |
| `host_name` | Categorical | Name of the host |
| `neighbourhood_group` | Categorical | Borough (Manhattan, Brooklyn, etc.) |
| `neighbourhood` | Categorical | Specific neighbourhood |
| `latitude` | Numerical | Geographic latitude |
| `longitude` | Numerical | Geographic longitude |
| `room_type` | Categorical | Type of accommodation |
| `price` | Numerical ★ | Nightly price (USD) |
| `minimum_nights` | Numerical | Minimum stay required |
| `number_of_reviews` | Numerical | Total reviews received |
| `reviews_per_month` | Numerical | Average monthly reviews |
| `host_listings_count` | Numerical | Total listings by that host |
| `availability_365` | Numerical | Days available in a year |
| `last_review` | — | **Dropped** — not used in analysis |

---

## 🔧 Data Wrangling

| Step | Action |
|------|--------|
| Missing Values | `listing_name` → "unknown"; `host_name` → "no_name" |
| Column Drop | `last_review` removed (irrelevant to analysis) |
| NaN Replace | `reviews_per_month` NaN → 0; cast to integer |
| Outlier Removal | IQR method applied to `price` column |
| Duplicate Check | ✅ Zero duplicate rows confirmed |
| Type Correction | Ensured correct dtypes for numerical columns |

---

## 📊 All 15 Visualisations

| # | Chart Title | Type | Key Insight |
|---|-------------|------|-------------|
| 01 | Price Range Distribution | Histogram | Most listings priced $50–$150 |
| 02 | Listings by Borough | Countplot | Manhattan & Brooklyn 19K+ each |
| 03 | Avg Price by Borough | Point Plot | Manhattan $146/day; Bronx $77/day |
| 04 | Price Distribution by Borough | Violin Plot | Manhattan has widest price diversity |
| 05 | Top Neighbourhoods by Listings | Bar Chart | Williamsburg #1, Bed-Stuy #2, Harlem #3 |
| 06 | Top Hosts by Listings | Bar Chart | Michael (383), David (368), John (276) |
| 07 | Active Hosts by Borough | Line Chart | Manhattan 19,501; Staten Island 365 |
| 08 | Avg Min Price by Neighbourhood | Scatter + Bar | Cheapest listings in Bronx & Staten Island |
| 09 | Room Type Counts | Pie Chart | Entire home 50%, Private 48%, Shared 2% |
| 10 | Stay Requirements | Bar Chart | 1–2 nights dominate (12K & 11K listings) |
| 11 | Total Reviews by Borough | Pie Chart | Brooklyn 43.3%, Manhattan 38.9% |
| 12 | Max Reviews by Borough | Pie Chart | Queens leads at 26.5% |
| 13 | Most Reviewed Room per Month | Strip Plot | Private rooms peak in Manhattan (50+/mo) |
| 14 | Correlation Heatmap | Heatmap | Price weakly correlated (0.17) with host count |
| 15 | Pair Plot | Pairplot | Pairwise relationships across numerical features |

---

## 🗺️ Borough Breakdown

| Borough | Listings | Avg Price | Total Reviews | Notes |
|---------|----------|-----------|---------------|-------|
| **Manhattan** | 19,501 | $146/day | 38.9% | Highest price; most listings |
| **Brooklyn** | 19,415 | ~$92/day | **43.3%** ★ | Most reviewed; Williamsburg #1 neighbourhood |
| **Queens** | 5,567 | ~$99/day | 14.2% | Highest max reviews (26.5%) |
| **Bronx** | 1,070 | $77/day | 2.6% | Lowest average price |
| **Staten Island** | 365 | ~$87/day | 1.0% | Fewest listings; growth opportunity |

---

## 🏠 Room Type Distribution

```
Entire Home / Apt  ████████████████████  22,784  (50.4%)
Private Room       ███████████████████   21,996  (48.6%)
Shared Room        █                      1,138   (2.5%)
```

---

## 🔗 Correlation Insights

| Variable Pair | Correlation | Interpretation |
|---------------|-------------|----------------|
| host_id ↔ listing_id | **0.58** (strong) | Multi-property hosts have unique IDs |
| host_listings_count ↔ availability_365 | **0.23** (moderate) | Bigger hosts keep more availability |
| price ↔ host_listings_count | **0.17** (weak) | Larger hosts charge marginally more |

---

## 🔑 Key Findings

- **Price range:** $20–$330; the sweet spot is $50–$150 (highest density)
- **Top neighbourhood:** Williamsburg (Brooklyn) by listing count
- **Top host:** Michael with 383 listings — nearly double #3 (John, 276)
- **Most reviewed borough:** Brooklyn at 43.3% of all reviews
- **Short stay dominance:** 1-night (12,067) and 2-night (11,080) minimums lead
- **Entire homes = private rooms:** Nearly 50/50 split in room type preference
- **Manhattan outlier:** Highest price AND most active hosts but faces saturation
- **Growth markets:** Queens, Bronx, Staten Island — underserved relative to demand signals

---

## 🏁 Business Conclusion

**For Hosts & Investors:**
Manhattan delivers the highest average price ($146/day) but faces intense competition. Brooklyn — especially Williamsburg and Bedford-Stuyvesant — offers a strong price-to-demand balance. Queens and the Bronx are underserved markets where new listings face less competition.

**For Airbnb Strategy:**
Host concentration is a risk — a small number of hosts (Michael, David, John) dominate supply. Short stays (1–2 nights) drive the vast majority of demand. Entire home and private room listings are near-equally popular, and maintaining both segments is critical for listing diversity and guest satisfaction.

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| **Language** | Python 3.x |
| **Data** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Charts Used** | Histogram, Countplot, Point Plot, Violin Plot, Bar, Pie, Strip Plot, Heatmap, Pairplot, Scatter |
| **Outlier Treatment** | IQR (Interquartile Range) method |
| **Environment** | Google Colab |

---

## 📦 Quickstart

```bash
# Clone the repository
git clone https://github.com/Ajaya210/airbnb_Eda
cd airbnb_Eda

# Install dependencies
pip install pandas numpy matplotlib seaborn

# Run notebook
jupyter notebook AirBnb_EDA_Project.ipynb
```

---

## 📁 Project Structure

```
airbnb_Eda/
│
├── AirBnb_EDA_Project.ipynb    # Main EDA notebook
├── AB_NYC_2019.csv             # Dataset
└── README.md
```

---

## 👤 Author

**Ajaya Kumar Pradhan**  
Data Analyst · Power BI Developer · ML Engineer  
📍 Bhubaneswar, Odisha, India

[![GitHub](https://img.shields.io/badge/GitHub-ajayaconnect-181717?style=flat-square&logo=github)](https://github.com/ajayaconnect)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/)

---

*Built as part of AlmaBetter Full Stack Data Science certification — EDA Capstone Project.*
