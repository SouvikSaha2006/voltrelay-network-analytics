# VoltRelay Energy: Network Reliability, Unit Economics & Capital Allocation Analysis

**Team:** The MetaMinds (Souvik Saha & Manas Kumar)  
**Event:** Gradient Learning Data Analytics Hackathon (Nov 2026)

## Quick Links
* **Interactive Google Colab Notebook:** [Open in Google Colab](YOUR_COLAB_SHARE_LINK_HERE)
* **Executive Analysis Report (PDF):** [View Full Report](./VoltRelay_Energy_Analysis_Report.pdf)
* **3-Minute Walkthrough Video:** [Watch Video Presentation](YOUR_VIDEO_LINK_HERE)

---

## 1. Business Problem
Between January 2024 and June 2025, **VoltRelay Energy** nearly tripled its monthly completed battery swaps (103,508 to 303,196) across six Indian cities (**Bengaluru, Delhi NCR, Hyderabad, Pune, Mumbai, and Jaipur**). However, top-line growth masked severe summer reliability drops, rising 30-day rider churn (reaching 17.23% in 2025Q2), and per-swap margin erosion. This analysis isolates the primary operational drivers across 8 relational datasets (`3.87M+` swap attempts) to guide VoltRelay's next operating budget.

## 2. Data Hygiene & Audit Summary
* **Test Station Removal:** Excluded `STN-TST-01` and `STN-TST-02` (`62,031` internal test rows removed; `3,814,982` verified operational attempts retained).
* **Firmware `v3.2.0` Timezone Fix:** Corrected a `+5h 30m` logging offset across `139,490` events (Mar 10 – Apr 14, 2025).
* **Geographic & Outlier Cleaning:** Standardized `21` city spelling variants into `6` canonical cities, clamped `9,592` sensor readings `>100%`, nullified `15,287` odometer reset outliers (`<0` or `>250 km`), and controlled for CSAT selection bias (`14.15h` vs `17.15h` resolution time).

## 3. Core Findings & Visual Evidence
| Analytical Area | Primary Finding | Supporting Metric |
| :--- | :--- | :--- |
| **Thermal & 3W Stockouts** | Heatwaves trigger cabinet stockouts during 19:00–22:00 peaks, hitting 3W riders hardest. | Failure jumps **2.7x** on Heat Alert days (**5.51% $\rightarrow$ 14.93%**); **3W failure is 10.39%** vs. **5.45% for 2W**. |
| **Charger Bottleneck** | Legacy `Gen1` stations cannot replenish packs fast enough during evening rush hours. | `Gen1` takes **91.8 min/pack** vs. **42.1 min** on `Gen3` (**7.23%** vs. **4.56%** failure rate). |
| **Supplier Defect** | `Kyron` 2W batteries suffer rapid State-of-Health collapse, forcing repeat swaps. | **100% of Kyron 2W packs (1,385/1,385)** retired after **-38.7% SoH drop**; **16.7% less range** (53.3 km vs. ~64.0 km). |
| **B2B Margin Trap** | #1 volume partner `ZipDrop` (`FP-03`) underperforms #2 `FeastFly` (`FP-01`) in profit. | Post-amendment **28% discount** + peak exemption cuts margin to **Rs. 30.49/swap** (**Rs. 4.53M less** total margin than FeastFly). |
| **Rider Retention** | Early stockout exposure—not marginal wait time—drives new-rider churn. | Churned riders saw **7.69% failure** in their first 3 swaps vs. **5.91%** for retained riders. |

## 4. Prioritized Capital Allocation Recommendations
1. **Reject Exclusive Contract Under Current Terms (`ZipDrop`):** Cap B2B volume discounts at **15%–18%** and remove peak-surcharge exemptions to recover **~Rs. 3.5M–4.2M** in annual margin.
2. **Retrofit 51 `Gen1` Stations to `Gen3` Chargers:** Prioritize upgrades and 3W slots in **Jaipur, Delhi NCR, and Hyderabad** ahead of summer heatwaves, cutting charge times by **54%**.
3. **Terminate `Kyron` 2W Procurement:** Shift 100% of battery CapEx to **Amptek and Cellora** with SoH warranty SLAs and active cabinet cooling.
4. **Expand Peak/Off-Peak Dynamic Pricing Network-Wide:** Pair evening peak pricing (`19:00–22:00`) with updated B2B peak clauses to capture **+Rs. 17–18 incremental margin/swap**.

## 5. Mandatory AI Tool Disclosure
In accordance with hackathon rules, **Google Gemini** was used as an analytical assistant to structure the Python data-cleaning pipeline, verify aggregations, format visualizations, and edit report documentation. All code execution, statistical checks, and recommendations were validated directly on the VoltRelay dataset.
