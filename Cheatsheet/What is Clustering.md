# What is Clustering ?

Clustering is a type of unsupervised machine learning that groups a set of objects in such a way that objects in the same group (called a cluster) are more similar to each other than to those in other groups.

<img width="1031" height="796" alt="image" src="https://github.com/user-attachments/assets/ae5e2bcb-8158-45a3-8903-096cfccabb52" />

Unlike supervised learning, clustering works with unlabeled data. The goal is not to predict a specific outcome but to discover hidden structures and patterns within the data.

## Key Concepts

* Cluster: A collection of data points that are similar to one another.
* Centroid: The center point of a cluster, often representing the average position of all points within that cluster.
* Distance Metric: The method used to measure the similarity between data points. Common examples include Euclidean distance (straight-line distance) and Manhattan distance.

## Common Algorithms

* K-Means: One of the most popular clustering algorithms. It partitions data into a pre-defined number of clusters (K) by iteratively assigning each data point to the nearest cluster centroid and then updating the centroids based on the new assignments.
* Hierarchical Clustering: This method builds a hierarchy of clusters. It can be either "agglomerative" (bottom-up, where each data point starts as a cluster and pairs are merged) or "divisive" (top-down, where the entire dataset is one cluster that is split).
* DBSCAN (Density-Based Spatial Clustering of Applications with Noise): This algorithm groups together data points that are closely packed together, marking as outliers’ data points that lie alone in low-density regions. It's particularly useful for finding arbitrarily shaped clusters and identifying noise.
Applications

## Clustering is used in many fields, including:

* Market Segmentation: Grouping customers with similar buying behaviors to tailor marketing campaigns.
* Image Segmentation: Dividing an image into multiple segments to simplify its analysis.
* Anomaly Detection: Identifying outliers or fraudulent transactions by finding data points that do not fit into any cluster.
* Biology: Grouping genes with similar expression patterns.

