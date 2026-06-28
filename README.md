# Veridi Logistics — Delivery Performance Audit
**By Joel Obinyebi**

---

## A. Executive Summary

Analysis of 96,470 Veridi Logistics deliveries revealed that 8.1% 
of orders were delivered late with Northeast Brazil being the worst 
affected region. Alagoas state had the highest late delivery rate 
at 23.93%. The data confirms the CEO's suspicion that late deliveries 
directly impact customer satisfaction. On Time deliveries averaged 
4.29 stars while Super Late deliveries averaged only 1.79 stars,
a drop of 2.5 stars. Audio and Electronics categories had the highest 
late delivery rates at 12-13% while Books and Telephony products 
performed best at 3-4%. Monthly trend analysis revealed crisis periods 
in November 2017 and March 2018 where late rates exceeded 20% likely 
due to Black Friday demand spikes and logistics capacity issues.

---

## B. Project Links

- **Link to Notebook:** [Google Colab Notebook](https://colab.research.google.com/drive/1XbdQKl8NETHM4Lc6SflA0vsbJ7mvzgAF)
- **Link to Dashboard:** [Looker Studio Dashboard](https://datastudio.google.com/s/q_rQ-ze2CjE)
- **Link to Presentation:** [Dashboard PDF Export](https://drive.google.com/file/d/1XbdQKl8NETHM4Lc6SflA0vsbJ7mvzgAF/view)

---

## C. Technical Explanation

### Data Cleaning
The raw dataset consisted of multiple CSV files that were joined 
into a single master dataset using Pandas merge operations equivalent 
to SQL LEFT JOINs. Key cleaning steps included:

- **Duplicate rows:** The reviews table contained multiple reviews 
  per order. To avoid row duplication during joining, review scores 
  were averaged per order using groupby before merging.

- **Missing values:** Orders with missing delivery dates were excluded 
  from delay analysis since they represented cancelled or unavailable 
  orders that never reached customers.

- **Date conversion:** Delivery date columns were converted from 
  string format to datetime using pd.to_datetime() to enable 
  accurate date arithmetic.

- **Small sample sizes:** Monthly analysis excluded months with 
  fewer than 100 orders to avoid misleading percentage calculations 
  from statistically insignificant sample sizes.

### Candidate's Choice: Monthly Late Delivery Trend Analysis

I added a Monthly Late Delivery Trend analysis that tracks the 
percentage of late deliveries across each month from October 2016 
to August 2018.

**Business Justification:**
This feature adds specific business value because it answers a 
critical question the static analysis cannot, is the late delivery 
problem getting worse or better over time? The analysis revealed 
two major crisis periods:

- **November 2017 (14.31% late):** Likely caused by Black Friday 
  demand surge overwhelming logistics capacity.

- **March 2018 (21.36% late):** The worst month on record suggesting 
  a major logistics breakdown possibly due to post-holiday backlog 
  or operational disruption.

This insight enables the CEO to correlate specific events with 
delivery failures and proactively increase logistics capacity during 
predicted high-demand periods directly preventing future customer 
dissatisfaction.

---

## D. Data Cleaning Checklist

- [x] Loaded raw CSVs into notebook
- [x] Performed correct joins on order_id and customer_id
- [x] Fixed duplicate rows from 1-to-many joins
- [x] Excluded cancelled and unavailable orders
- [x] Handled missing delivery dates
- [x] Converted date columns to datetime format
- [x] Filtered small sample sizes from monthly analysis

---

## E. Pre-Submission Checklist

### Repository & Code Checks
- [x] **My GitHub Repo is Public.**
- [x] **I have uploaded the `.ipynb` notebook file.**
- [x] **I have uploaded a PDF export** of the notebook.
- [x] **I have NOT uploaded the raw dataset.**
- [x] **My code connects to Google Drive for reproducibility.**

### Deliverable Checks
- [x] **Dashboard link is publicly accessible.**
- [x] **Presentation PDF link is publicly accessible.**
- [x] **README has been replaced with my own documentation.**

### Completeness
- [x] I have completed **User Stories 1-4.**
- [x] I have completed the **Candidate's Choice** challenge.
- [x] I have justified my Candidate's Choice in this README.
