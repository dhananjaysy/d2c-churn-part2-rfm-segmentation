# Part 2: RFM Segmentation & Retention Strategy

---

## Overview

This repository contains RFM-based customer segmentation and a targeted retention strategy for a D2C personal-care brand. Customers are segmented using Recency, Frequency, and Monetary scores combined with support ticket behaviour and discount usage patterns.

**Snapshot Date:** 2025-09-30  
**Customers:** 2,400  
**Segments:** 7

---

## Repository Structure

```
├── data/                        
├── charts/                      
├── rfm_segmentation.ipynb       
├── segments.csv                 
├── retention_strategy.md        
├── manual_review_cases.md       
├── README.md
└── requirements.txt
```
## Setup Instructions

### Clone the Repository

```bash
git clone <repository-url>
cd Part2-rfm-segmentation
```

### Create Virtual Environment

```bash
python -m venv venv
```

### Activate Virtual Environment

```bash
./venv/Scripts/Activate   #Windows
source venv/bin/activate  #Mac/Linux
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Run the Notebook
```bash
jupyter notebook rfm_segmentation.ipynb
```

Run all cells. `segments.csv` will be regenerated and charts saved to `charts/`.

---

## Segmentation Logic

| Segment | Rule | Churn Rate |
|---------|------|-----------|
| Champions | R≥4, F≥4, M≥4 | 10.0% |
| Loyal Customers | R≥3, F≥3, M≥3, low complaints | 24.0% |
| High-Value Unhappy | R≥3, F≥3, M≥3, tickets≥2, sentiment<0 | 34.5% |
| At-Risk | R≤2, F≥3 | 78.0% |
| Dormant | R≤2, F≤2, sessions=0 | 83.3% |
| Discount-Sensitive | avg_discount≥0.4, F≥2 | 47.4% |
| New/Low-Engagement | Remaining customers | 49.2% |

Non-RFM signals used: support ticket count, average sentiment score, return rate, avg discount %, web sessions (last 30d).

---

## Key Outputs

- `segments.csv` — 2,400 rows, 16 columns including segment name, R/F/M scores, and behavioural signals
- `retention_strategy.md` — Segment-wise retention recommendations and budget prioritization
- `manual_review_cases.md` — 10 real customer IDs with conflicting signals and reasoning
