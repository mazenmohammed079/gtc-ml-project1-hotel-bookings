# gtc-ml-project1-hotel-bookings
# GTC ML Project 1 — Hotel Bookings (Data Cleaning & Preprocessing)

## Overview
This project is part of **GTC ML Project 1**.  
The goal is to clean and preprocess the **Hotel Bookings dataset** so it is ready for a machine learning model that predicts cancellations.  
No modeling was done; the focus was only on **EDA, data cleaning, and preprocessing**.

## Steps I Followed

### Phase 1: EDA & Data Quality Report
- Checked dataset shape, data types, and summary statistics.
- Identified missing values using **missingno** and heatmaps.
- Detected outliers in `adr` and `lead_time` using boxplots & violin plots.
- Found duplicates and invalid rows (0 total guests).

### Phase 2: Data Cleaning
- **Missing values handled**:
  - `agent` & `company` -> filled with `0` (meaning “None”).
  - `country` -----------> filled with the most frequent country (mode).
  - `children` ----------> filled with median.
- **Duplicates removed**.
- **Outliers capped**: `adr` values > 1000 set to 1000; extreme `lead_time` smoothed with IQR.
- **Invalid rows dropped**: bookings with 0 guests.
- **Dates fixed**: created proper `arrival_date`.

### Phase 3: Feature Engineering & Preprocessing
- Created new features:
  - `total_guests = adults + children + babies`
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
  - `is_family` (binary flag for families)
  - Extra: `guest_density`, `weekend_ratio`, `high_season`
- Removed **data leakage**: dropped `reservation_status` & `reservation_status_date`.
- Encoded categorical variables:
  - One-Hot Encoding for low-cardinality categories.
  - Frequency Encoding for high-cardinality features like `country`.
- Final dataset split into **train (80%)** and **test (20%)**.

## Files in Repo
- `hotel_bookings.csv` ----------------> raw dataset  
- `hotel_bookings.ipynb` --------------> notebook with EDA, cleaning & preprocessing  
- `hotel_bookings_cleaned_full.csv` ---> cleaned dataset  

### Conclusion
The raw dataset was transformed into a clean, consistent, and ML-ready dataset.  
All missing values, outliers, and duplicates were handled, and useful new features were engineered.  
This ensures a solid foundation for building a future **cancellation prediction model**.
