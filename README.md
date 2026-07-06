# StaySmart Consulting: Airbnb Listing Segmentation with Clustering & PCA

## Overview
This project applies unsupervised machine learning to segment NYC Airbnb listings into meaningful groups, helping a boutique property management consultancy (StaySmart Consulting) advise hosts on pricing, amenities, and marketing strategy. By clustering listings based on price, availability, guest experience, and property characteristics, the analysis identifies natural listing "personas" — from budget-friendly high-activity units to premium, low-turnover properties.

## Business Context
StaySmart Consulting advises short-term rental property managers in a competitive market. Understanding how listings naturally group together — rather than relying on borough or price alone — helps hosts benchmark their properties, identify underpriced or overpriced units, and tailor amenity bundles to the right guest segment.

## Objective
- Perform exploratory data analysis (EDA) on Airbnb listing data
- Apply Principal Component Analysis (PCA) for dimensionality reduction
- Cluster listings using K-Means and Hierarchical (Agglomerative) Clustering
- Compare clustering results on the original feature space vs. the PCA-transformed space
- Interpret resulting segments and translate them into actionable business recommendations

## Dataset
`airbnb_listings_dataset.csv` — 319 NYC listings, 18 features, including:
- `neighborhood_group`, `neighborhood`, `room_type`
- `price`, `minimum_nights`, `availability_365`
- `number_of_reviews`, `review_rate_month`, `average_rating`
- `accommodates`, `bedrooms`, `bathrooms`
- `has_wifi`, `has_kitchen`, `has_ac`, `host_is_superhost`
- `distance_to_center_km`

No missing values or duplicates were present in the raw data.

## Methodology
1. **Data Cleaning & EDA**: univariate distribution analysis, skew checks, correlation heatmap, categorical encoding via one-hot/dummy variables
2. **Feature Scaling**: standardized (z-score) all features prior to clustering
3. **K-Means Clustering (Original Feature Space)**
   - Determined optimal *k* using the elbow method (WCSS/distortion) and silhouette scores
   - Selected **k = 4** clusters
4. **Hierarchical Clustering**
   - Tested multiple distance metrics (Euclidean, Chebyshev, Mahalanobis, Cityblock) and linkage methods (single, complete, average, weighted)
   - Selected the combination with the highest cophenetic correlation
   - Visualized results with dendrograms
5. **Principal Component Analysis (PCA)**
   - Reduced dimensionality to 10 components, explaining ~80% of total variance
6. **K-Means Clustering (PCA-Transformed Space)**
   - Re-ran elbow and silhouette analysis on PCA components
   - Selected **k = 5** clusters
7. **Comparison**: evaluated cluster profiles and segment sizes before vs. after PCA to assess how dimensionality reduction affects segmentation

## Key Findings
- Listings separate into distinct segments based primarily on **price, size (accommodates/bedrooms/bathrooms), review activity, and location**
- One segment consistently represents **budget-friendly, high-activity** listings (lower price, higher review volume)
- Another segment represents **premium, larger properties** with higher price and lower turnover
- Clustering on PCA-transformed data produced a different optimal cluster count (5 vs. 4), highlighting how dimensionality reduction can reveal finer-grained segment structure
- Segment profiles translate into concrete recommendations: pricing adjustments, amenity bundling, and targeted marketing by segment

## Tools & Libraries
- **Python**: pandas, numpy
- **Visualization**: matplotlib, seaborn, yellowbrick (SilhouetteVisualizer)
- **Machine Learning**: scikit-learn (KMeans, AgglomerativeClustering, PCA, StandardScaler)
- **Statistics**: scipy (linkage, dendrogram, cophenetic correlation, distance metrics)
- **Cluster Selection**: kneed (KneeLocator for elbow detection)

## Repository Contents
- `StaySmart_Consulting_Clusturing.ipynb`: full analysis notebook (EDA, PCA, K-Means, hierarchical clustering, cluster interpretation)
- `airbnb_listings_dataset.csv`: source dataset (319 listings, 18 features)
- `README.md`:  project overview and documentation

## Author
Raksha Chabhadia,
MBA Business Analytics
