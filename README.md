# Customer Segmentation

## 🔹 Introduction

This project applies unsupervised machine learning to segment customers from a grocery firm's database. Using KMeans clustering combined with PCA (Principal Component Analysis) for dimensionality reduction, the project groups customers into distinct behavioral segments to help the business better understand and serve its customer base.

**Main notebook:** `segmentation.ipynb`
**Local app & deployment:** `app.py`, `templates/`
**Requirements:** `requirement.txt`

## 🔹 Objectives

- Cluster customers using KMeans and PCA on a real-world groceries firm dataset.
- - Identify distinct customer types based on demographics, spending habits, and family structure.
  - - Provide actionable business insights to tailor products and marketing by customer segment.
   
    - ## 🔹 Dataset & Features
   
    - - **Source:** Kaggle — [Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)
      - - **Records:** 2,240 customers with 29 original features
        - - **Key Features:** Year_Birth, Education, Marital_Status, Income, Kidhome, Teenhome, Recency, MntWines, MntFruits, MntMeatProducts, MntFishProducts, MntSweetProducts, NumDealsPurchases, NumWebPurchases, etc.
         
          - ## 🔹 EDA Highlights
         
          - - **Missing values:** 24 missing values in Income column — handled by dropping.
            - - **Outliers:** Detected and removed extreme Income and Age outliers.
              - - **Feature Engineering:** Created new features such as `Age`, `Spent` (total spending), `Customer_For` (tenure), `Family_Size`, `Is_Parent`, and simplified `Education` and `Marital_Status` categories.
                - - **Scaling:** Applied StandardScaler before PCA and clustering.
                 
                  - ## 🔹 Methodology
                 
                  - **Dimensionality Reduction (PCA)**
                  - - Reduced feature space to 10 principal components.
                    - - 10 components explain ~85% of cumulative variance, balancing information retention and computational efficiency.
                     
                      - **Clustering (KMeans)**
                      - - Used Elbow Method (KElbowVisualizer) to determine the optimal number of clusters: **k = 6**.
                        - - KMeans is well-suited for grouping without requiring labeled data; optimal k = 6 groups customers meaningfully.
                         
                          - ## 🔹 Results — Cluster Profiles
                         
                          - | Cluster | Age  | Income    | Spent    | Customer_For | Notes |
                          - |---------|------|-----------|----------|--------------|-------|
                          - | 0       | 56.3 | 40,290    | 76       | 279 days     | Low-income, low-spending parents |
                          - | 1       | 53.0 | 67,363    | 1,135    | 447 days     | Mid-high income, high spenders |
                          - | 2       | 52.6 | 77,807    | 1,431    | 341 days     | High-income, highest spenders (48.3% of total spending) |
                          - | 3       | 43.9 | 29,932    | 95       | 342 days     | Young, low-income, low-spending |
                          - | 4       | 58.4 | 57,413    | 655      | 357 days     | Older, mid-income, moderate spenders |
                          - | 5       | 52.5 | 49,577    | 496      | 469 days     | Loyal long-term customers, moderate income |
                         
                          - ✅ **Key finding:** Cluster 2 (20.5% of customers) accounts for 48.3% of total spending — the highest-value segment.
                          - - Customers are mostly parents (old and various income types).
                            - - Significant opportunity to increase spending among Clusters 0 and 3 (low-spending segments).
                             
                              - ## 🔹 Conclusion
                             
                              - 1. Data required NULL, outlier, and format handling before modeling.
                                2. 2. Feature engineering (Age, Spent, Family_Size, Is_Parent, etc.) improved cluster interpretability.
                                   3. 3. PCA reduced dimensions for KMeans, which classified customers into 6 meaningful groups.
                                      4. 4. Most customers are parents of varying ages and income levels.
                                         5. 5. There are strong opportunities to increase spending and loyalty, especially in underserved segments.
                                           
                                            6. ## 🔹 Executive Summary
                                           
                                            7. This project segments 2,240 grocery store customers into 6 distinct clusters using KMeans clustering on PCA-reduced features. After data cleaning, outlier removal, and feature engineering, the clustering reveals key behavioral groups: high-value spenders (Cluster 2, ~48% of revenue), loyal long-term customers (Cluster 5), and low-income/low-spending groups (Clusters 0 and 3). These insights enable targeted marketing, personalized product recommendations, and strategic investment in high-value customer retention.
