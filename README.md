# Project Reflection – *ENIAC Discount Strategy*

## Summary
This project analyses ENIAC’s 14-month order history (≈ 44 k completed orders, 58 k order-lines, 6 k SKUs, €14.6 M revenue) to answer one question:

> **Should ENIAC keep using aggressive discounts or pivot to a premium-price positioning?**

The study cleans the dataset, maps price/volume dynamics, and quantifies how discount depth affects revenue by category and season. Outputs include:

* **Python notebooks** – data cleaning, promo-price fixes, revenue-vs-discount metrics.  
* **Slide deck** – ten-slide executive presentation outlining insights and a phased pricing roadmap.

## Languages and Libraries Used
| Layer | Tools / Libraries |
|-------|-------------------|
| Data wrangling | Python 3.11 (`pandas`, `numpy`) |
| Visualisation | `matplotlib`, `seaborn`, `tableau` |
| Presentation | PowerPoint (`Eniac_Discount_case_study_final.pdf`) |
| Version control | Git / GitHub |

## Key Learnings
* **Discount elasticity isn’t one-size-fits-all.** High-rev/high-vol categories (Storage, Audio/Video) respond well to 20–25 % promos (r ≈ 0.45) while low-rev accessories show near-zero lift :contentReference[oaicite:0]{index=0}.  
* **93 % of order-lines already carry a discount** (median 17 % off) :contentReference[oaicite:1]{index=1}—blanket promos erode margin with limited upside.  
* **Seasonality dominates.** Black Friday & December drive ~70 % QoQ revenue spikes; discounts work best layered on top of peak demand :contentReference[oaicite:2]{index=2}.  
* **Data-driven “sweet spot.”** Targeted, category-specific tiers outperform blanket cuts and preserve premium positioning on flagship devices.

## Key Insights
1. **Price landscape is highly dispersed** – median base price varies 10× across categories.  
2. **Discount saturation** – 93 % of order-lines are already discounted; median depth = 17 %.  
3. **Revenue lift is uneven** – discounts double revenue in some months, but payoff depends on category and seasonality :contentReference[oaicite:3]{index=3}.  
4. **Strong positive correlation (r ≈ 0.45)** between 20–25 % discounts and revenue in high-rev/high-vol segments; weak or zero correlation elsewhere.  
5. **Seasonal spikes** – Nov/Dec contribute ~70 % QoQ revenue growth; discount strategy must be season-aware.  

## Actions (Recommendations)
| # | Action | Detail | KPI Trigger |
|---|--------|--------|-------------|
| 1 | **Targeted discount tiers** | • Keep **20–25 %** promos for high-rev/high-vol categories (Storage, Audio/Video).<br>• Cap at **10 %** for high-vol/low-rev accessories (Cables, Cases).<br>• Limit premium devices to **≤ 10 %** “prestige” promos or bundle offers. | Revenue lift ≥ 15 % vs. baseline |
| 2 | **Experiment systematically** | A/B-test two discount tiers each season to refine elasticity measures. | Stat-sig winner (p < 0.05) |
| 3 | **Monitor discount ROI** | Deploy elasticity scorecard per SKU (Δ units / Δ price) and track margin impact monthly. | Margin erosion < 2 pp |
| 4 | **Enhance data for forecasting** | Add `unit_cost`, `discount_reason`, and `customer_id` fields; build time-series model (seasonality + discount depth) to forecast revenue :contentReference[oaicite:4]{index=4}. | Model MAPE < 10 % |
| 5 | **Limited-time promos on premium devices** | Run short “scarcity” promos (< 7 days) instead of blanket discounting to protect brand perception. | Premium ASP ≥ baseline |

## Challenges Overcame
* **Data quality gaps** – messy `promo_price`, missing `customer_id`, no cost-of-goods column, 79 % orders in non-completed states; solved via SQL filters and imputation.  
* **Outlier mitigation** – extreme prices skewed medians; applied IQR winsorisation before elasticity modelling.  
* **Short time-series** – only 14 months; supplemented correlation analysis with seasonality flags to avoid over-fitting.  
* **Executive brevity** – converted > 20 SQL outputs into < 10 clear visuals and a five-slide narrative.

## Additional Reflections
* Pairing geographic seasonality with discount elasticity made the case for targeted promos intuitive for non-technical stakeholders.  
* Maintaining one colour palette and icon set across notebooks and slides reinforced clarity.  
* Next step: automate daily KPI pulls and integrate coupon-code A/B results into the elasticity scorecard.
