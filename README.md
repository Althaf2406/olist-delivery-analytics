# Predictive Analytics: E-Commerce Delivery Delay & Customer Satisfaction

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=python&logoColor=white)

## Project Overview
In the e-commerce industry, logistics speed and accuracy are the spearheads of customer satisfaction. Delivery delays can severely damage the reputation of sellers and the platform as a whole, which is directly reflected in the review scores given by customers.

This capstone project aims to dissect the issue of delivery delays using real-world transaction data from Brazil. By combining Root Cause Analysis, Geospatial Analysis, Machine Learning (Random Forest Classifier), and Natural Language Processing (NLP), this project provides a comprehensive analytical framework to identify delivery bottlenecks and predict customer dissatisfaction.

## Research Questions
1. How significant is the impact of late deliveries on customer review scores?
2. Who is responsible for the delays: slow packaging by the seller or lengthy transit times by the courier (carrier)?
3. Which logistics routes (from origin state to destination state) have the highest failure/delay rates?
4. What are the primary factors that trigger a customer to leave a bad review (1 or 2 stars)?
5. What are the main keywords customers complain about when their orders arrive late?

## Dataset
- **Source**: [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Size**: ~99,000 orders and customer reviews.
- **Features**: Complex relational data including order delivery timestamps, product details, dimensions, freight value, buyer and seller locations, and customer review text.

## Methodology & Tech Stack
1. **Data Wrangling & Feature Engineering**: Performed Inner Joins on multiple tables. Extracted new metrics from datetimes such as `seller_processing_days` and `courier_delivery_days`.
2. **Exploratory Data Analysis (EDA)**: Analyzed the distribution of Review Scores based on delivery timeliness status.
3. **Geospatial & Root Cause Analysis**: Identified the top 10 most frequently delayed product categories and mapped the logistics failure rates on interstate routes (Origin -> Destination).
4. **Predictive Modeling**: Built a Random Forest Classifier model using the `class_weight='balanced'` parameter to predict the probability of a customer giving a bad review, while simultaneously handling imbalanced data.
5. **Text Mining (NLP)**: Performed regex text-cleaning and Portuguese stopword removal to generate a WordCloud visualization of customer complaints.

## Key Findings & Business Insights

### 1. The Fatal Impact of Delays
Late orders have a very strong correlation with plummeting satisfaction. Customers who receive delayed goods consistently dominate the 1-Star Review Score category compared to customers whose goods arrive on time.

### 2. Couriers as the Primary Root Cause
Based on average day metrics, delays are very rarely caused by slow seller packaging (`seller_processing_days`). Conversely, the largest contributor to lengthy durations when orders are late is the transit process by the courier/expedition (`courier_delivery_days`).

### 3. Logistics Pain Points and Categories
There are specific logistics routes between states (e.g., SP to RJ) that experience the most severe delay percentages. Additionally, heavy/bulky product categories such as *cama_mesa_banho* (bed, bath & table) dominate the list of items frequently delivered late.

### 4. The Voice of the Customer (Text Mining)
Extracting a WordCloud from 1-star reviews empirically proves that customers are highly frustrated with time. Portuguese keywords such as "atraso" (delay), "demora" (slow/delay), and "nunca" (never arrived) are the most absolute complaints.

## Model Performance
The **Random Forest** classification model was evaluated using accuracy metrics and a Confusion Matrix to filter potentially dissatisfied customers. From the `feature_importances_` extraction, courier delivery time and freight value emerged as the most significant predictors of bad reviews.

## Business Recommendation for Platform & Logistics
1. **Stricter Expedition SLAs**: The Olist platform must re-evaluate Service Level Agreements (SLAs) with couriers, especially on identified "red" routes that frequently fail to meet time estimates.
2. **Dynamic Expectations**: The application system should provide more realistic arrival time estimates and buffer times for large-volume product categories, in order to manage customer expectations and prevent 1-star reviews.
3. **Recovery System**: Utilize the built Machine Learning model to detect "at-risk" late orders and proactively send apology coupons to customers before they even have a chance to leave a bad review.

---
**Author**: Muhammad Althaf Hilmi  
*Data Analytics Portfolio*
