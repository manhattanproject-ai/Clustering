# Kmeans Vs Hierarchical Vs DBSCAN

## Comparison of K-means (Partitioning), Hierarchical (Connectivity-based), and DBSCAN (Density-based) clustering, highlighting their core mechanisms, advantages, and limitations.

|Feature|	K-means (Partitioning) 💡|	Hierarchical (Agglomerative) 🌳| DBSCAN (Density-based) 🌌|
|--------|---|--------|---|
|Mechanism|	Iteratively shifts centroids to the mean of assigned points.|	Starts with individual points and merges the closest clusters sequentially.|	Groups points that are closely packed together (high density).|
|Cluster Shape|	Assumes spherical/globular and equal-sized clusters.|	Can produce various shapes, but often forms compact, balanced clusters with Ward's linkage.|	Can find arbitrary, non-convex shapes (e.g., C-shapes, rings).|
|Input Required|	Requires the number of clusters (K) to be specified beforehand.|	Requires a linkage method (e.g., Ward, Single) and a subsequent cutoff distance.|	Requires a neighborhood radius (ϵ/eps) and a minimum number of points (MinPts/min_samples).|
|Outliers/Noise|	Forces every point into a cluster (outliers skew centroids).|	Forces every point into a cluster (can be visualized as single branches).|	Explicitly labels points as "Noise" or outliers (points not dense enough).|
|Scalability|	Excellent (Fastest for large datasets).|	Poor (Complexity often $O(N^3)$ or $O(N^2)$ for large N).|	Fair/Good (Efficient for moderate to large datasets, faster than Hierarchical).|
|Main Use Case|	Customer Segmentation when clusters are expected to be distinct and spherical.|	Creating Taxonomies/Hierarchies (e.g., biological classification, document topics).|	Anomaly Detection and discovering clusters with complex shapes.|

## 📊 Comparison of Clustering Algorithm Performance

<img width="1203" height="672" alt="image" src="https://github.com/user-attachments/assets/06bc9ec0-3615-40e9-8536-4aacc833f092" />


### 1. K-Means Clustering

* Strength (Globular/Spherical Data): K-Means performs well on the first two columns where clusters are relatively compact and convex (roughly circular or blob-shaped).
* Weakness (Arbitrary Shapes): It fails dramatically on non-globular data. In the rings and crescent shapes (columns 4 and 5), K-Means incorrectly cuts across the clusters because it is designed to minimize the Within-Cluster Sum of Squares (WCSS), which biases it toward spherical boundaries.
* Weakness (Uneven Density/Size): It struggles when clusters have different densities or sizes (column 3).

### 2. Hierarchical Clustering (Agglomerative)

* Performance: The Hierarchical clustering shown here (likely using a method like Ward's or Complete Linkage) performs similarly to K-Means on the convex and dense clusters (columns 1 and 2).
* Weakness (Arbitrary Shapes): Like K-Means, it also fails on the non-convex shapes (rings and crescent) because standard linkage methods are generally designed to find compact, globular clusters.
* Weakness (Noisy Data): It performs poorly on the noisy, dense background (last column) as it forces every point to be part of a cluster.

### 3. DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

* Strength (Arbitrary Shapes): DBSCAN is the clear winner for non-convex (arbitrarily shaped) clusters (columns 4 and 5). It successfully identifies the outer ring, the inner ring, and the crescent shapes by grouping points based on local density.
* Strength (Noise/Outliers): It excels at handling noise (outliers). In columns 1 and 3, the black points are correctly labeled as outliers/noise and are not forced into any cluster.
* Weakness (Varying Density): It struggles when a single cluster contains regions of significantly different densities (column 3, where the green cluster is partially mixed with black noise points). Also, it struggles with the dense, unstructured data (last column).

In summary, the image effectively demonstrates that K-Means is suitable for spherical data, while DBSCAN is essential for datasets with complex, non-linear cluster boundaries and the need for robust outlier detection.
