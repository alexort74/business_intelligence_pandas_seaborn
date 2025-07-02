# Project Reflection – *ENIAC Discount Strategy*

## Summary
This project analyses ENIAC’s 14-month order history (≈ 44 k completed orders, 58 k order-lines, 6 k SKUs, €14.6 M revenue) to answer one question:

> **Should ENIAC keep using aggressive discounts or pivot to a premium-price positioning?**

The study cleans the dataset, maps price / volume dynamics, and quantifies how discount depth affects revenue by category and season.  
Outputs include:

* **SQL queries & Pandas notebooks** – data cleaning, promo-price fixes, revenue vs. discount metrics.  
* **Slide deck** – ten-slide executive presentation outlining insights and a phased pricing roadmap.

## Languages and Libraries Used
| Layer | Tools / Libraries |
|-------|-------------------|
| Data wrangling | Python 3.11 (`pandas`, `numpy`, `pyjanitor`), PostgreSQL-style SQL |
| Visualisation | `matplotlib`, `seaborn` |
| Presentation | PowerPoint (`Eniac_Discount_case_study_final.pdf`) |
| Version control | Git / GitHub |

## Key Learnings
* **Discount elasticity isn’t one-size-fits-all.**  
  *High-rev / high-vol categories (Storage, Audio/Video) respond well to 20–25 % promos (r ≈ 0.45), whereas low-rev accessories (Cables, Cases) show near-zero lift.*
* **93 % of order-lines already carry a discount** (median 17 % off) – blanket promos are eroding margin with limited upside.
* **Seasonality dominates.**  
  *Black Friday & December drive ~70 % QoQ revenue spikes; discount depth should be layered on seasonal demand, not used to create it.*
* **Data-driven “sweet spot.”**  
  *Targeted, category-specific discount tiers outperform blanket cuts and preserve premium positioning on flagship devices.*

## Challenges Overcame
* **Data quality gaps** – messy `promo_price`, missing `customer_id`, no cost-of-goods, and 79 % orders in non-completed states; solved via SQL filters and imputation.
* **Outlier mitigation** – extreme prices skewed medians; applied IQR winsorisation before elasticity modelling.
* **Short time-series** – only 14 months; supplemented correlation analysis with seasonality flags to avoid over-fitting.

## Additional Reflections
* Next analytic step: build a time-series model (seasonality + discount depth) and an elasticity scorecard per SKU (Δ units / Δ price).
* Adding a `unit_cost` column to the product master and a `discount_reason` flag would unlock true margin ROI monitoring.
* Clear, visually simple slides (price landscape, discount vs. revenue matrix) helped non-technical stakeholders grasp why *targeted* discounts beat “one big sale.”

