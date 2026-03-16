# Austin Airbnb Investment Analysis

Data-driven strategy for identifying the most profitable Airbnb investment segment in Austin, Texas using machine learning and market segmentation.

This project combines **K-Means clustering** and **XGBoost regression** to analyze the Austin Airbnb market and identify the property segment that delivers the strongest risk-adjusted return for investors.

---

## Project Presentation

Full presentation slides:

[View the presentation](Presentation/Airbnb_Pricing_Presentation.pptx)

---

# Project Overview

Austin has one of the most active short-term rental markets in the United States, with thousands of listings spanning very different price points, property sizes, and occupancy patterns.

For an investor considering entering the Airbnb market, the key question is not simply whether the market is profitable, but **which segment of properties delivers the most reliable return**.

This project answers three core questions:

• What factors drive Airbnb nightly prices?  
• Which properties maintain the highest booking rates?  
• Which market segment offers the best risk-adjusted return for investors?

Using machine learning and clustering techniques, the analysis identifies the optimal property type, pricing strategy, and investment approach.

---

# Dataset

Source: Inside Airbnb

Raw dataset:

- 5,835 Airbnb listings
- 54 variables

After data cleaning:

- 3,130 model-ready observations
- features include price, bedrooms, bathrooms, property type, neighbourhood, amenities, and booking availability

Key preprocessing steps included:

- removing columns with high missing rates
- converting string price fields to numeric
- capping extreme price outliers above the 99th percentile
- feature engineering for amenities such as hot tubs, pools, and washer availability

:contentReference[oaicite:0]{index=0}

---

# Methodology

Two complementary machine learning approaches were used to analyze the market.

## 1. Market Segmentation — K-Means Clustering

K-Means clustering was used to segment the Airbnb market based on key listing attributes:

- price
- bedrooms
- bathrooms
- accommodates
- room type
- review score
- availability

Cluster selection was evaluated using:

- elbow method
- silhouette score

The optimal segmentation was **k = 3 clusters**, which provided meaningful and interpretable market segments for investors.

Segments identified:

| Cluster | Segment | Avg Price | Booking Rate |
|-------|-------|-------|-------|
| Cluster 0 | Mid-Range Entire Homes | $174 | **34%** |
| Cluster 1 | Premium Large Homes | $479 | 22% |
| Cluster 2 | Budget Private Rooms | $85 | 23% |

Cluster 0 represents the most attractive investment segment.

:contentReference[oaicite:1]{index=1}

---

## 2. Price Prediction — XGBoost Regression

A regression model was built to predict nightly rental prices.

Target variable:

log(price)

Models tested:

- Log Linear Regression
- Random Forest
- Base XGBoost
- Tuned XGBoost (Optuna)

Training/testing split:

80 / 20

Evaluation metrics:

- Adjusted R²
- Mean Absolute Percentage Error (MAPE)

Model comparison results:

| Model | Train R² | Test Adj R² | MAPE |
|------|------|------|------|
| Log Linear | 0.714 | 0.622 | 33.1% |
| Random Forest | 0.958 | 0.613 | 36.4% |
| Base XGBoost | 0.910 | 0.652 | 32.4% |
| **Tuned XGBoost** | 0.787 | **0.671** | **31.5%** |

The **tuned XGBoost model** achieved the best out-of-sample performance and was selected as the final model.

:contentReference[oaicite:2]{index=2}

---

# Key Findings

### 1. Bedrooms Are the Strongest Price Driver

Bedrooms account for the largest share of feature importance (~22%), indicating that property size strongly influences nightly pricing.

### 2. Mid-Range Homes Achieve the Highest Occupancy

The mid-range segment averages:

- $174 per night
- **34% booking rate**

This segment has the highest occupancy and the largest market share.

### 3. Amenities Can Significantly Increase Price

Listings with hot tubs average:

$472 per night vs $274 without

This represents nearly a **$200 nightly premium**.

### 4. Location Is a Critical Pricing Factor

Neighborhoods such as:

- Tarrytown
- Zilker
- Bryker Woods

command significantly higher prices than the Austin average.

:contentReference[oaicite:3]{index=3}

---

# Investment Recommendation

The analysis suggests the optimal Airbnb investment strategy in Austin is:

**Property Type**

2-bedroom entire home

**Location**

central Austin neighborhoods

**Target Guests**

3–4 guests

**Pricing Strategy**

$150 – $200 per night

This strategy balances nightly rate and occupancy to generate stable revenue.

Estimated annual revenue:

$174 × 34% occupancy × 365 days  
≈ **$21,600 per year**

Adding high-value amenities such as a hot tub could increase annual revenue to approximately **$26,000**.

:contentReference[oaicite:4]{index=4}

---

# Tools and Technologies

Python  
Pandas  
Scikit-learn  
XGBoost  
Optuna  
Matplotlib / Seaborn  

---

# Project Structure
airbnb-price-model

data/
memo/
notebooks/
presentation/
README.md


---

# Author

Yiran Liu  
MSBA Candidate  
Wake Forest University