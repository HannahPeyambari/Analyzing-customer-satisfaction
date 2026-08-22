# Customer Satisfaction Analysis — Olist Brazilian E-Commerce

**Author:** Hannah Peyambari
**Dataset:** [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle)
**Tools:** Python, Pandas, Seaborn, Matplotlib

---

## Executive Summary

This analysis examined over 110,000 orders on the Olist marketplace to identify what drives low customer review scores. Four hypotheses were tested: delivery delay, order cancellation, product category, and seller performance. The results show that **delivery delay** and **seller performance** are the strongest drivers of dissatisfaction, while cancellations and product category play a comparatively minor role. Delivery delay alone explains 30% of all 1-star reviews, and the worst-performing seller (verified against 206 orders) averaged a score of just 2.72 — worse than any product category in the dataset.

---

## Business Problem

Olist is a Brazilian e-commerce marketplace connecting small businesses to major retail channels. Understanding what drives negative customer reviews is critical for retaining sellers and buyers on the platform, protecting brand reputation, and prioritizing operational improvements. This analysis set out to answer:

> **What factors are most strongly associated with low customer review scores (1-star ratings), and which of these should Olist prioritize addressing?**

---

## Methodology

- **Data:** 9 relational CSV files covering orders, customers, order items, products, sellers, payments, reviews, and geolocation (2016–2018)
- **Approach:** Exploratory Data Analysis (EDA) and hypothesis testing, using `pandas` for data merging, cleaning, and aggregation, and `seaborn`/`matplotlib` for visualization
- **Reliability control:** For category- and seller-level analysis, a minimum sample size threshold (50 orders) was applied to avoid drawing conclusions from small, unreliable samples. Threshold validity was confirmed by checking that the retained sellers/categories still covered the majority of total order volume (77% for sellers)

---

## Key Findings

### 1. Delivery Delay — Strongest Driver
Only 6.46% of orders were delivered late, but this group's average score dropped sharply from 4.21 to 2.27. Late deliveries alone account for **30% of all 1-star reviews**, making this the single strongest factor identified.

### 2. Order Cancellation — Minor Overall Impact, but Severe When It Happens
Cancellations were rare (0.61% of orders) and explained only 3.69% of 1-star reviews overall. However, when an order *was* canceled, the outcome was almost always negative — **69.3%** of canceled orders received a 1-star review. Notably, 82.3% of all 1-star reviews came from orders marked as successfully "delivered," meaning the root cause of dissatisfaction lies elsewhere, not primarily in failed deliveries.

### 3. Product Category — Weak Effect
After filtering out categories with insufficient sample size (fewer than 50 orders, narrowing 73 categories down to 59 reliable ones), scores ranged narrowly from 3.49 (`office_furniture`) to 4.64 (`cds_dvds_musicals`). This spread is too small to explain most of the dissatisfaction on its own.

### 4. Seller Performance — Strong, Underexplored Driver
Despite 84.8% of sellers having fewer than 50 orders (and being excluded from the reliable analysis), the remaining 460 reliable sellers still covered 77.2% of total order volume. Among them, the worst-performing seller averaged just **2.72** — a stronger negative signal than any product category.

---

## Conclusion

Customer dissatisfaction on Olist is driven more by **how and when orders are fulfilled** than by **what is being sold**. Delivery delay and seller-level service quality are the two most actionable levers for improving customer satisfaction, while product category and order cancellation play a comparatively minor role.

---

## Recommendations

### 1. Seller Performance Monitoring
**Problem:** Certain sellers consistently drive dissatisfaction — the worst reliable seller averaged 2.72 across 206 orders.
**Recommendation:** Implement a public seller rating system — display average scores for sellers with 50+ orders, and show a "Building Track Record" label for newer/lower-volume sellers instead of a potentially misleading numeric score.
**Expected outcome:** More informed customer decisions, improvement incentives for underperforming sellers, and fair treatment of new sellers.

### 2. Delivery Delay Management
**Problem:** Late deliveries (6.46% of orders) disproportionately drive dissatisfaction, explaining 30% of 1-star reviews.
**Recommendation:** Allow cancellation with automatic refund for severe delays (14+ days); implement proactive delay notifications with compensatory discount codes; investigate root causes of extreme delays (e.g., seller-customer geographic distance) as a follow-up study.
**Expected outcome:** Reduced severity of dissatisfaction even where delays cannot be fully eliminated.

### 3. Product Category — Lower Priority
**Problem:** Product category shows only a weak relationship with dissatisfaction (3.49–4.64 score range).
**Recommendation:** Deprioritize category-specific initiatives until higher-impact issues (delivery, seller quality) are addressed. Revisit category analysis afterward, as some variation may stem from seller quality concentrated in specific categories rather than the product type itself.
**Expected outcome:** Better allocation of analytical and operational resources.

### 4. Cancellation Experience
**Problem:** Cancellations are rare but almost always result in a 1-star review (69.3%).
**Recommendation:** Process refunds immediately and automatically; send an empathetic explanation message; investigate whether cancellations correlate with predicted delays or seller stock shortages.
**Expected outcome:** Reduced negative reaction to cancellations even if the cancellation rate itself stays constant.

---

## Limitations

- This analysis is **correlational, not causal** — it identifies strong associations but does not establish that, for example, fixing delivery delay will proportionally reduce 1-star reviews.
- Seller- and category-level findings exclude entities with fewer than 50 orders to ensure statistical reliability; conclusions may not generalize to low-volume sellers/categories.
- The geographic distance hypothesis (seller-customer location) was not directly tested in this analysis and is proposed only as a follow-up research direction.
- Review text content (`review_comment_message`) was not analyzed in this phase and may contain additional insight into *why* customers were dissatisfied (e.g., product quality, packaging).

---

## Next Steps

- Test the geographic distance hypothesis using `customer_state` vs. `seller_state`
- Apply NLP techniques to review comments to uncover additional dissatisfaction themes (e.g., product quality, packaging, misleading listings)
- Explore whether specific sellers are concentrated in specific product categories, to disentangle seller effect from category effect
