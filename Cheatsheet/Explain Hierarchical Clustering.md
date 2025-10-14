# Hierarchical Clustering

Hierarchical Clustering is a type of unsupervised machine learning algorithm that builds a hierarchy of clusters, represented as a tree structure called a dendrogram. Unlike K-means, it does not require a pre-specified number of clusters (K); instead, the number of clusters is determined by cutting the tree at a certain height.

<img width="979" height="531" alt="image" src="https://github.com/user-attachments/assets/68cde256-e405-4155-a459-ccdf9c87fe27" />

## The Two Main Approaches
Hierarchical clustering methods are broadly categorized into two types, based on whether they follow a "bottom-up" or "top-down" approach:

### 1. Agglomerative (Bottom-Up) 🌿
* Process: This is the most common approach. It starts by treating every single data point as its own cluster (i.e., N clusters for N data points).
* Mechanism (Merger): It then iteratively merges the two closest clusters at each step.
* Termination: The process continues until only one single cluster remains, containing all data points.

### 2. Divisive (Top-Down) 🌳
* Process: This approach starts with all data points belonging to one large cluster.
* Mechanism (Splitting): It then iteratively splits the cluster into two smaller, more dissimilar sub-clusters at each step.
* Termination: The process continues until every single data point is its own individual cluster.

## Key Components and Concepts

A. The Dendrogram
The result of hierarchical clustering is a dendrogram, which is a tree diagram that visually records the sequences of merges or splits .

* Vertical Axis: Represents the distance (or dissimilarity) between clusters when they were merged. A tall vertical line indicates that the clusters merged at that point were very far apart.
* Horizontal Axis: Represents the data points or the clusters themselves.
* Determining Clusters: To get the final clusters, you draw a horizontal line across the dendrogram at a chosen distance level (a "cutoff"). The number of vertical lines this horizontal line intersects is the resulting number 
of clusters (K).

B. Linkage Criteria
In Agglomerative Clustering, we need a rule to measure the distance between two existing clusters, A and B. This rule is called the linkage criterion:

|Linkage|	Description|
|--------|---|
|Single Linkage|	Distance is the minimum distance between any two points in the two clusters (the closest pair). Tends to produce elongated clusters.|
|Complete Linkage|	Distance is the maximum distance between any two points in the two clusters (the farthest pair). Tends to produce compact, spherical clusters.|
|Average Linkage|	Distance is the average distance between all pairs of points across the two clusters.|
|Ward's Method|	Measures the increase in the Within-Cluster Sum of Squares (WCSS) that results from merging the two clusters. It minimizes variance and often produces compact clusters of roughly equal size.|

## Advantages and Disadvantages

|Feature|	Advantage	|Disadvantage|
|--------|---|---|
|No K Required|	The number of clusters can be decided by inspecting the dendrogram afterward.|	Less scalable than K-means (slower for very large datasets).|
|Hierarchy|	Provides a detailed view of the relationships between data points at different levels of similarity.|	Once a merge or split is made, it cannot be undone.|


Note : We will leverage Agglomerative Clustering for our problem statement .

